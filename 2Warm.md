#### Description

Can you convert the number 42 (base 10) to binary (base 2)?
# solucion 1

```python
PerfectBlack-picoctf@webshell:~$ python
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> bin(42)[2:]
'101010'
>>
>>picoCTF{101010}
````

# 03 bases 
# SOLUCION 1
```python
cyberchef 
input 
recipe From Base64
outpot l3arn_th3_r0p35
picoCTF{l3arn_th3_r0p35}
```
# 04 First Grep
#### Description

Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/495d43ee4a2b9f345a4307d053b4d88d/file)? This would be really tedious to look through manually, something tells me there is a better way.
# solucion 1

descargamos el archivo con wget  https://jupiter.challenges.picoctf.org/static/495d43ee4a2b9f345a4307d053b4d88d/file
PerfectBlack-picoctf@webshell:~$ ls
README.txt  file  flag
PerfectBlack-picoctf@webshell:~$ file file
file: ASCII text, with very long lines (4200)
PerfectBlack-picoctf@webshell:~$ cat file | grep pico
picoCTF{grep_is_good_to_find_things_dba08a45}
PerfectBlack-picoctf@webshell:~$ 


# 05 Obedient Cat
# SOLUCION 1
#### Description

```python
This file has a flag in plain sight (aka "in-the-clear").

PerfectBlack-picoctf@webshell:~$ 
PerfectBlack-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/fb851c1858cc762bd4eed569013d7f00/flag
--2025-02-12 18:49:58--  https://mercury.picoctf.net/static/fb851c1858cc762bd4eed569013d7f00/flag
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34 [application/octet-stream]
Saving to: 'flag'

flag                                            100%[======================================================================================================>]      34  --.-KB/s    in 0s      

2025-02-12 18:49:58 (16.7 MB/s) - 'flag' saved [34/34]

PerfectBlack-picoctf@webshell:~$ cat flag

picoCTF{s4n1ty_v3r1f13d_28e8376d}
``````
# 06 what's a net cat?

#### Description

Using netcat (nc) is going to be pretty important. Can you connect to `jupiter.challenges.picoctf.org` at port `41120` to get the flag?

# solucion 
conectarse al servidor 

``````
PerfectBlack-picoctf@webshell:~$ 
PerfectBlack-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 41120
You're on your way to becoming the net cat master
picoCTF{nEtCat_Mast3ry_3214be47}
``````

# 07 nice netcat....

``````
#### Description

There is a nice program that you can talk to by using this command in a shell: `$ nc mercury.picoctf.net 22342`, but it doesn't speak English...

PerfectBlack-picoctf@webshell:~$ nc mercury.picoctf.net 22342 
112 
105 
99 
111 
67 
84 
70 
123 
103 
48 
48 
100 
95 
107 
49 
116 
116 
121 
33 
95 
110 
49 
99 
51 
95 
107 
49 
116 
116 
121 
33 
95 
53 
102 
98 
53 
101 
53 
49 
100 
125 
10 
^C
PerfectBlack-picoctf@webshell:~$ 

USANDO https://toolbox.itsec.tamu.edu/#input=MTEyIA0KMTA1IA0KOTkgDQoxMTEgDQo2NyANCjg0IA0KNzAgDQoxMjMgDQoxMDMgDQo0OCANCjQ4IA0KMTAwIA0KOTUgDQoxMDcgDQo0OSANCjExNiANCjExNiANCjEyMSANCjMzIA0KOTUgDQoxMTAgDQo0OSANCjk5IA0KNTEgDQo5NSANCjEwNyANCjQ5IA0KMTE2IA0KMTE2IA0KMTIxIA0KMzMgDQo5NSANCjUzIA0KMTAyIA0KOTggDQo1MyANCjEwMSANCjUzIA0KNDkgDQoxMDAgDQoxMjUgDQoxMCANCg
picoCTF{g00d_k1tty!_n1c3_k1tty!_5fb5e51d}

``````
# 08 Glitch Cat
#### Description
Our flag printing service has started glitching!
Additional details will be available after launching your challenge instance.

# SOLUCION 1 
usamos el comando dado por la pagina ejecutamos python  y pegamos lo obtenido 
``````python
PerfectBlack-picoctf@webshell:~$  nc saturn.picoctf.net 64350
'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
^C
PerfectBlack-picoctf@webshell:~$ PYTHON
-bash: PYTHON: command not foun
PerfectBlack-picoctf@webshell:~$ python
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
'picoCTF{gl17ch_m3_n07_bda68f75}'
``````

# 09  Warmed Up

#### Description
What is 0x3D (base 16) in decimal (base 10)?

# solucion 
usamos python y el siguiente comando 

``````python
PerfectBlack-picoctf@webshell:~$ python
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print(int("0x3D", 16))
61
``````

# 10  plumbing
#### Description

Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 14291`.

# solucion 

usamos 
``````python
PerfectBlack-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 14291 > salida
^C
PerfectBlack-picoctf@webshell:~$ cat salida|grep pico
picoCTF{digital_plumb3r_ea8bfec7}
PerfectBlack-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 14291 |grep picp
^C
PerfectBlack-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 14291 |grep pico
picoCTF{digital_plumb3r_ea8bfec7}




R