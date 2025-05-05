# 01  Includes

# DESC

Can you get the flag?

Additional details will be available after launching your challenge instance.

# SOLUCION

````` python
Inicialmente nos metemos a la página y miramos el código fuente y nos metemos al style.css y script.js y en ambos nos da una parte de la bandera, solo los juntamos y obtenemos la bandera

```
style.css
body {
  background-color: lightblue;
}

/*  picoCTF{1nclu51v17y_1of2_  */

script.js
function greetings()
{
  alert("This code is in a separate file!");
}

//  f7w_2of2_df589022}

flag: picoCTF{1nclu51v17y_1of2_f7w_2of2_df589022}
```
````` 


# 02 - Inspect HTML

# DESC

Can you get the flag?Go to this [website](http://saturn.picoctf.net:61578/) and see what you can discover.
# SOLUCION

````` python
Nos metemos a la página y en la pista nos dice que usemos el inspector web, nos metemos al código fuente de la página y en la parte de abajo nos da la bandera directamente

```
|   |
|---|
|<!DOCTYPE html>|
||<html lang="en">|
||<head>|
||<meta charset="UTF-8">|
||<meta name="viewport" content="width=device-width, initial-scale=1.0">|
||<meta http-equiv="X-UA-Compatible" content="ie=edge">|
||<title>On Histiaeus</title>|
||</head>|
||<body>|
||<h1>On Histiaeus</h1>|
||<p>However, according to Herodotus, Histiaeus was unhappy having to stay in|
||Susa, and made plans to return to his position as King of Miletus by|
||instigating a revolt in Ionia. In 499 BC, he shaved the head of his|
||most trusted slave, tattooed a message on his head, and then waited for|
||his hair to grow back. The slave was then sent to Aristagoras, who was|
||instructed to shave the slave's head again and read the message, which|
||told him to revolt against the Persians.</p>|
||<br>|
||<p> Source: Wikipedia on Histiaeus </p>|
||<!--picoCTF{1n5p3t0r_0f_h7ml_fd5d57bd}-->|
||</body>|
||</html>|

flag: picoCTF{1n5p3t0r_0f_h7ml_fd5d57bd}
```
````` 


# 03 - IntroToBurp

# DESC


# SOLUCION

````` python
Para resolver este reto, primero interceptamos la petición POST con Burp después de poner los datos. Luego en la petición eliminamos el parámetro `OTP` de la petición antes de enviarla al servidor. Como el servidor está mal programado, al no recibir el OTP simplemente omite la validación del 2fa y nos deja entrar

```
POST /dashboard HTTP/1.1
Host: titan.picoctf.net:56853
Content-Length: 13
Cache-Control: max-age=0
Accept-Language: es-419,es;q=0.9
Origin: http://titan.picoctf.net:56853
Content-Type: application/x-www-form-urlencoded
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://titan.picoctf.net:56853/dashboard
Accept-Encoding: gzip, deflate, br
Cookie: session=.eJwljUsOgzAMRO-SdRckkF_3PQcyJGlLwUGJESpV716jLmfG7_kjxie9xVUcGO4HobiIsZbUU35F5BosaCVbBSCNBul86xrduGSCk4NOXtngrZGBubTNc4-wRMb2MsRyyjKtHHXnre84rlDrnks4H05EU6TpdtaPjLHHbWGKJ6naThvrfMPbVtn0t2I8kPji-wPVeTf9.Z_H3YA.JtV4iXJxFgJh8bFSwYqWfFBAK00
Connection: keep-alive

otp=123456789

borramos otp y nos da la flag

flag: picoCTF{#0TP_Bypvss_SuCc3$S_3e3ddc76}
```
````` 


# 04 ### Local Authority

# DESC

Can you get the flag?Go to this [website](http://saturn.picoctf.net:53169/) and see what you can discover.
# SOLUCION

````` python
Nos metemos a la página y nos logeamos, nos dice que el log in falló, nos metemos al código fuente en esa página y nos fijamos que hay un secuere.js, abrimos el archivo y ahí tenemos un checkpassword con el user y contraseña para logearnos

```
secure.js

function checkPassword(username, password)
{
  if( username === 'admin' && password === 'strongPassword098765' )
  {
    return true;
  }
  else
  {
    return false;
  }
}

user: admin
password: strongPassword098765

flag: picoCTF{j5_15_7r4n5p4r3n7_05df90c8}
```
````` 


# 05  Power Cookie

# DESC

Can you get the flag?Go to this [website](http://saturn.picoctf.net:63136/) and see what you can discover.
# SOLUCION

````` python
La pista nos dice que si sabemos modificar cookies, si sabemos, entonces nos metemos a la página y le damos en continuar como invitado y nos dice que no podemos ingresar, miramos la cookie y en value está en "0" la cambiamos a "1" y recargamos página y nos deja entrar para poder ver la bandera en ella

```
--continue as a guest
--We apologize, but we have no guest services at the moment.

Cookie: value "0"
Cookie: value "1"

flag: picoCTF{gr4d3_A_c00k13_0d351e23}

````` 


# 06 - Roboto Sans
# DESC
The flag is somewhere on this web application not necessarily on the website. Find it.

Additional details will be available after launching your challenge instance. 
# SOLUCION

````` python
Ingresamos a la página y nos metemos a código fuente para ver si encontramos la bandera, no encontramos nada, después nos metemos a la página pero ingresando /robots.txt y vemos que hay como cadenas codificadas, las metemos al cyberchef y nos indica que es js/myfile.txt, ingresamos y nos da la bandera

```
Ingresamos con robots.txt: http://saturn.picoctf.net:54141/robots.txt

User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/

Cyberchef: 

Input: anMvbXlmaWxlLnR4dA==

Recipe: from Base64

Output: js/myfile.txt

ingresamos: http://saturn.picoctf.net:54141/js/myfile.txt

flag: picoCTF{Who_D03sN7_L1k5_90B0T5_22ce1f22}
```
````` 



# 07 - Secrets
# DESC
We have several pages hidden. Can you find the one with the flag?The website is running [here](http://saturn.picoctf.net:51633/).
# SOLUCION

````` python
Nos metemos a la página y vemos el código fuente y nos fijamos que tiene un secret, nos metemos a la página usando /secret, después nos sale un gif diciendo que vamos por buen camino, nos metemos al código fuente y hay un hidden fil y agregamos el /hidden, por último miramos el código fuente de esa página y hay un superhidden lo agregamos y nos da la bandera

```
http://saturn.picoctf.net:50846/secret/
http://saturn.picoctf.net:50846/secret/hidden/
http://saturn.picoctf.net:50846/secret/hidden/superhidden/

Aparece un texto que dice que "Finally. You found me. But can you see me"

Hacemos ctrl+a y selecciona todo el texto de la página y vemos la bandera seleccionada en la página

flag: picoCTF{succ3ss_@h3n1c@10n_790d2615}
```
````` 


# 08 - SQLiLite
# DESC
Can you login to this website?Try to login [here](http://saturn.picoctf.net:58866/).

# SOLUCION

````` python
Ingresamos a la página e intentamos logearnos, nos dice que no es posible y miramos que tenemos que ingresar con una inyección SQL que la más básica es: ' or 1 == 1;' al ingresar nos dice que no está a simple vista la bandera, nos metemos al código fuente y ahí está

```
Log in
username: admin
password: ' or 1 == 1;'

usamos ctrl+u para ver código fuente

|   |
|---|
|<pre>username: admin|
||password: &#039; or 1 == 1;|
||SQL query: SELECT * FROM users WHERE name=&#039;admin&#039; AND password=&#039;&#039; or 1 == 1;&#039;|
||</pre><h1>Logged in! But can you see the flag, it is in plainsight.</h1><p hidden>Your flag is: picoCTF{L00k5_l1k3_y0u_solv3d_it_d3c660ac}</p>|

flag: picoCTF{L00k5_l1k3_y0u_solv3d_it_d3c660ac}
```
````` 


# 09   Unminify
# DESC
#### Description

I don't like scrolling down to read the code of my website, so I've squished it. As a bonus, my pages load faster!Browse [here](http://titan.picoctf.net:49959/), and find the flag!

# SOLUCION

````` python
Usando consola linux Simplemente usamos un comando curl + página + grep pico para filtrar esa palabra en el código fuente

```
vSalazarZ-picoctf@webshell:~$ curl http://titan.picoctf.net:52445/ | grep picoCTF
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1352  100  1352    0     0  17206      0 --:--:-- --:--:-- --:--:-- 17333
<!doctype html><html lang="en"><head><meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1"><title>picoCTF - picoGym | Unminify Challenge</title><link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png"><style>body{font-family:"Lucida Console",Monaco,monospace}h1,p{color:#000}</style></head><body class="picoctf{}" style="margin:0"><div class="picoctf{}" style="margin:0;padding:0;background-color:#757575;display:auto;height:40%"><a class="picoctf{}" href="/"><img src="picoctf-logo-horizontal-white.svg" alt="picoCTF logo" style="display:inline-block;width:160px;height:90px;padding-left:30px"></a></div><center><br class="picoctf{}"><br class="picoctf{}"><div class="picoctf{}" style="padding-top:30px;border-radius:3%;box-shadow:0 5px 10px #0000004d;width:50%;align-self:center"><img class="picoctf{}" src="hero.svg" alt="flag art" style="width:150px;height:150px"><div class="picoctf{}" style="width:85%"><h2 class="picoctf{}">Welcome to my flag distribution website!</h2><div class="picoctf{}" style="width:70%"><p class="picoctf{}">If you're reading this, your browser has succesfully received the flag.</p><p class="picoCTF{pr3tty_c0d3_622b2c88}"></p><p class="picoctf{}">I just deliver flags, I don't know how to read them...</p></div></div><br class="picoctf{}"></div></center></body></html>
vSalazarZ-picoctf@webshell:~$ 

No se ve aquí en este texto pero en el webshell se marcan en color la palabra picoCTF y solo son 3, es fácil identificar, la bandera es: 

flag: picoCTF{pr3tty_c0d3_622b2c88}
```

## Solución 2

[](https://github.com/vSalazarZ/Hacking-Notes/blob/main/Pico%20CTF/Web%205/09-Unminify.md#soluci%C3%B3n-2)

En esta solución usaremos un método más fácil, nos metemos al código fuente y usamos ctrl+f se nos abre un buscador de palabras y buscamos picoCTF, hay 18 resultados, simplemente vamos buscando rápidamente de uno por uno y en menos de 20 segundos encontramos la bandera

```
CTRL+U en la página
CTRL+F en el código fuente
Filtramos la palabra en la búsqueda "picoCTF" 1/18 ⌃ ⌄ x
Vamos viendo en la búsqueda y encontramos la flag 

flag: picoCTF{pr3tty_c0d3_622b2c88}
```
````` 


# 10 - WebDecode
# DESC
Do you know how to use the web inspector?Start searching [here](http://titan.picoctf.net:57569/) to find the flag
# SOLUCION

````` python
Nos metemos a la página y vamos inspeccionando, le picamos en _about_ e inspeccionamos ahí y vemos una cadena de caracteres que está decodificada, la matemos en un decodificador y nos dá la bandera

```
Cadena: cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMjgzZTYyZmV9

Cyberchef

input: cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMjgzZTYyZmV9

Recipe: Base64

Output: picoCTF{web_succ3ssfully_d3c0ded_283e62fe}

flag: picoCTF{web_succ3ssfully_d3c0ded_283e62fe}
```
````` 


# 0
# DESC

# SOLUCION

````` python

````` 




