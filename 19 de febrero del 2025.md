# Binary Search
#### Description

Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools!You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/19/challenge.zip)

`ssh -p 54961 ctf-player@atlas.picoctf.net`Using the password `1db87a14`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!

# solucion 
PerfectBlack-picoctf@webshell:~$ ssh -p 54961 ctf-player@atlas.picoctf.net
ctf-player@atlas.picoctf.net's password: 
Permission denied, please try again.
ctf-player@atlas.picoctf.net's password: 
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Lower! Try again.
Enter your guess: 250
Lower! Try again.
Enter your guess: 125
Higher! Try again.
Enter your guess: 188
Higher! Try again.
Enter your guess: 219
Lower! Try again.
Enter your guess: 204
Lower! Try again.
Enter your guess: 196
Lower! Try again.
Enter your guess: 192
Lower! Try again.
Enter your guess: 190
Lower! Try again.
Enter your guess: 189
Congratulations! You guessed the correct number: 189
Here's your flag: picoCTF{g00d_gu355_1597707f}
Connection to atlas.picoctf.net closed.


#   reto1 Codebook
#### Description

Run the Python script `code.py` in the same directory as `codebook.txt`.

- [Download code.py](https://artifacts.picoctf.net/c/2/code.py)
- [Download codebook.txt](https://artifacts.picoctf.net/c/2/codebook.txt)
-
# solucion

PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/2/codebook.txt
--2025-02-20 05:03:23--  https://artifacts.picoctf.net/c/2/codebook.txt
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.92, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27 [application/octet-stream]
Saving to: 'codebook.txt'

codebook.txt                                    100%[======================================================================================================>]      27  --.-KB/s    in 0s      

2025-02-20 05:03:23 (1.06 MB/s) - 'codebook.txt' saved [27/27]

PerfectBlack-picoctf@webshell:~$ ls
README.txt  challenge.zip  codebook.txt  files  files.zip  home
PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/2/code.py
--2025-02-20 05:04:48--  https://artifacts.picoctf.net/c/2/code.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.92, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1278 (1.2K) [application/octet-stream]
Saving to: 'code.py'

code.py                                         100%[======================================================================================================>]   1.25K  --.-KB/s    in 0s      

2025-02-20 05:04:48 (13.9 MB/s) - 'code.py' saved [1278/1278]

PerfectBlack-picoctf@webshell:~$ 
PerfectBlack-picoctf@webshell:~$ python code.py
picoCTF{c0d3b00k_455157_7d102d7a}
PerfectBlack-picoctf@webshell:~$ 



# #  reto2 convertirme.py


# descripción

Ejecute el script de Python y convierta el número dado de decimal a binario para obtener la bandera.[Descargar script de Python](https://artifacts.picoctf.net/c/22/convertme.py)

# solucion 

PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/22/convertme.py
--2025-02-20 05:06:47--  https://artifacts.picoctf.net/c/22/convertme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.92, 3.160.22.128, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.92|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1189 (1.2K) [application/octet-stream]
Saving to: 'convertme.py'

convertme.py                                    100%[======================================================================================================>]   1.16K  --.-KB/s    in 0s      

2025-02-20 05:06:47 (1018 MB/s) - 'convertme.py' saved [1189/1189]

PerfectBlack-picoctf@webshell:~$ ls
README.txt  challenge.zip  code.py  codebook.txt  convertme.py  files  files.zip  home
PerfectBlack-picoctf@webshell:~$ cat convertme.py

import random



def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + chr(0x23) + chr(0x15) + chr(0x5f) + chr(0x05) + chr(0x08) + chr(0x2a) + chr(0x1c) + chr(0x5e) + chr(0x1e) + chr(0x1b) + chr(0x3b) + chr(0x17) + chr(0x51) + chr(0x5b) + chr(0x58) + chr(0x5c) + chr(0x3b) + chr(0x42) + chr(0x53) + chr(0x5c) + chr(0x0d) + chr(0x5e) + chr(0x50) + chr(0x4d) + chr(0x00) + chr(0x13)


num = random.choice(range(10,101))

print('If ' + str(num) + ' is in decimal base, what is it in binary base?')

ans = input('Answer: ')

try:
  ans_num = int(ans, base=2)
  
  if ans_num == num:
    flag = str_xor(flag_enc, 'enkidu')
    print('That is correct! Here\'s your flag: ' + flag)
  else:
    print(str(ans_num) + ' and ' + str(num) + ' are not equal.')
  
except ValueError:
  print('That isn\'t a binary number. Binary numbers contain only 1\'s and 0\'s')
PerfectBlack-picoctf@webshell:~$ python convertme.py
If 36 is in decimal base, what is it in binary base?
Answer: 100100
That is correct! Here's your flag: picoCTF{4ll_y0ur_b4535_762f748e}
PerfectBlack-picoctf@webshell:~$ 

#  reto3fixme1.py
#### Descripción

Corrija el error de sintaxis en este script de Python para imprimir la bandera.[Descargar script de Python](https://artifacts.picoctf.net/c/27/fixme1.py)
# solucion
PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/27/fixme1.py
--2025-02-20 05:13:41--  https://artifacts.picoctf.net/c/27/fixme1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.43, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 837 [application/octet-stream]
Saving to: 'fixme1.py'

fixme1.py                                       100%[======================================================================================================>]     837  --.-KB/s    in 0s      

2025-02-20 05:13:41 (37.8 MB/s) - 'fixme1.py' saved [837/837]

PerfectBlack-picoctf@webshell:~$ ls 
README.txt  challenge.zip  code.py  codebook.txt  convertme.py  files  files.zip  fixme1.py  home
PerfectBlack-picoctf@webshell:~$ cat fixme1.py

import random



def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + chr(0x23) + chr(0x15) + chr(0x5a) + chr(0x07) + chr(0x00) + chr(0x46) + chr(0x0b) + chr(0x1a) + chr(0x5a) + chr(0x1d) + chr(0x1d) + chr(0x2a) + chr(0x06) + chr(0x1c) + chr(0x5a) + chr(0x5c) + chr(0x55) + chr(0x40) + chr(0x3a) + chr(0x5f) + chr(0x53) + chr(0x5b) + chr(0x57) + chr(0x41) + chr(0x57) + chr(0x08) + chr(0x5c) + chr(0x14)

  
flag = str_xor(flag_enc, 'enkidu')
  print('That is correct! Here\'s your flag: ' + flag)

PerfectBlack-picoctf@webshell:~$ nano fixmex.py
PerfectBlack-picoctf@webshell:~$ python fixme1.py
  File "/home/PerfectBlack-picoctf/fixme1.py", line 20
    print('That is correct! Here\'s your flag: ' + flag)
IndentationError: unexpected indent
PerfectBlack-picoctf@webshell:~$ nano fixme1.py
PerfectBlack-picoctf@webshell:~$ python fixme1.py
That is correct! Here's your flag: picoCTF{1nd3nt1ty_cr1515_182342f7}
PerfectBlack-picoctf@webshell:~$ 

#  reto4

PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/5/fixme2.py
--2025-02-20 05:19:46--  https://artifacts.picoctf.net/c/5/fixme2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.92, 3.160.22.128, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.92|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1029 (1.0K) [application/octet-stream]
Saving to: 'fixme2.py'

fixme2.py                                       100%[======================================================================================================>]   1.00K  --.-KB/s    in 0s      

2025-02-20 05:19:46 (32.6 MB/s) - 'fixme2.py' saved [1029/1029]

PerfectBlack-picoctf@webshell:~$ ls
README.txt  challenge.zip  code.py  codebook.txt  convertme.py  files  files.zip  fixme1.py  fixme2.py  fixmex.py  home
PerfectBlack-picoctf@webshell:~$ cat fixme2.py

import random



def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + chr(0x23) + chr(0x15) + chr(0x58) + chr(0x18) + chr(0x11) + chr(0x41) + chr(0x09) + chr(0x5f) + chr(0x1f) + chr(0x10) + chr(0x3b) + chr(0x1b) + chr(0x55) + chr(0x1a) + chr(0x34) + chr(0x5d) + chr(0x51) + chr(0x40) + chr(0x54) + chr(0x09) + chr(0x05) + chr(0x04) + chr(0x57) + chr(0x1b) + chr(0x11) + chr(0x31) + chr(0x5f) + chr(0x51) + chr(0x52) + chr(0x46) + chr(0x00) + chr(0x5f) + chr(0x5a) + chr(0x0b) + chr(0x19)

  
flag = str_xor(flag_enc, 'enkidu')

Check that flag is not empty
if flag = "":
  print('String XOR encountered a problem, quitting.')
else:
  print('That is correct! Here\'s your flag: ' + flag)


PerfectBlack-picoctf@webshell:~$ nano fixme2.py
PerfectBlack-picoctf@webshell:~$ python fixme2.py
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_4863e11b}
PerfectBlack-picoctf@webshell:~$ 


#  reto5
PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/12/level1.py
--2025-02-20 05:25:06--  https://artifacts.picoctf.net/c/12/level1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.92, 3.160.22.128, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.92|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 876 [application/octet-stream]
Saving to: 'level1.py'

level1.py                                       100%[======================================================================================================>]     876  --.-KB/s    in 0s      

2025-02-20 05:25:06 (27.7 MB/s) - 'level1.py' saved [876/876]

PerfectBlack-picoctf@webshell:~$ 
PerfectBlack-picoctf@webshell:~$ ls
README.txt  challenge.zip  code.py  codebook.txt  convertme.py  files  files.zip  fixme1.py  fixme2.py  fixmex.py  home  level1.py
PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/12/level1.flag.txt.enc
--2025-02-20 05:25:28--  https://artifacts.picoctf.net/c/12/level1.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.92, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30 [application/octet-stream]
Saving to: 'level1.flag.txt.enc'

level1.flag.txt.enc                             100%[======================================================================================================>]      30  --.-KB/s    in 0s      

2025-02-20 05:25:28 (1.69 MB/s) - 'level1.flag.txt.enc' saved [30/30]

PerfectBlack-picoctf@webshell:~$ ls
README.txt  challenge.zip  code.py  codebook.txt  convertme.py  files  files.zip  fixme1.py  fixme2.py  fixmex.py  home  level1.flag.txt.enc  level1.py
PerfectBlack-picoctf@webshell:~$ cat level1.py
THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################


flag_enc = open('level1.flag.txt.enc', 'rb').read()



def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "8713"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_1_pw_check()
PerfectBlack-picoctf@webshell:~$ cat level1.flag.txt.enc
[gE]__TgS^S

           JPerfectBlack-picoctf@webshell:~$ 
PerfectBlack-picoctf@webshell:~$ nano decrypt_flag.py
PerfectBlack-picoctf@webshell:~$ python decrypt_flag.py
La bandera es: picoCTF{545h_r1ng1ng_1b2fd683}
PerfectBlack-picoctf@webshell:~$ 

#  reto6

PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/13/level2.py
--2025-02-20 05:29:33--  https://artifacts.picoctf.net/c/13/level2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.128, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 914 [application/octet-stream]
Saving to: 'level2.py'

level2.py                                       100%[======================================================================================================>]     914  --.-KB/s    in 0s      

2025-02-20 05:29:33 (30.8 MB/s) - 'level2.py' saved [914/914]

PerfectBlack-picoctf@webshell:~$ wgwt https://artifacts.picoctf.net/c/13/level2.flag.txt.enc
-bash: wgwt: command not found
PerfectBlack-picoctf@webshell:~$ ls
README.txt  challenge.zip  code.py  codebook.txt  convertme.py  decrypt_flag.py  files  files.zip  fixme1.py  fixme2.py  fixmex.py  home  level1.flag.txt.enc  level1.py  level2.py
PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/13/level2.flag.txt.enc
--2025-02-20 05:30:51--  https://artifacts.picoctf.net/c/13/level2.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.43, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level2.flag.txt.enc'

level2.flag.txt.enc                             100%[======================================================================================================>]      31  --.-KB/s    in 0s      

2025-02-20 05:30:51 (28.4 MB/s) - 'level2.flag.txt.enc' saved [31/31]

PerfectBlack-picoctf@webshell:~$ cat level2.py
THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################

flag_enc = open('level2.flag.txt.enc', 'rb').read()



def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_2_pw_check()
PerfectBlack-picoctf@webshell:~$ Please enter correct password for flag:
-bash: Please: command not found
PerfectBlack-picoctf@webshell:~$ python level2.py
Please enter correct password for flag: de76
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_489dea9a}
PerfectBlack-picoctf@webshell:~$ 


#  reto7

PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/34/runme.py
--2025-02-20 05:35:38--  https://artifacts.picoctf.net/c/34/runme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.16, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 270 [application/octet-stream]
Saving to: 'runme.py'

runme.py                                        100%[======================================================================================================>]     270  --.-KB/s    in 0s      

2025-02-20 05:35:38 (11.7 MB/s) - 'runme.py' saved [270/270]

PerfectBlack-picoctf@webshell:~$ ls
README.txt     code.py       convertme.py     files      fixme1.py  fixmex.py  level1.flag.txt.enc  level2.flag.txt.enc  runme.py
challenge.zip  codebook.txt  decrypt_flag.py  files.zip  fixme2.py  home       level1.py            level2.py
PerfectBlack-picoctf@webshell:~$ python3 runme.py
picoCTF{run_s4n1ty_run}
PerfectBlack-picoctf@webshell:~$ 

#  reto8

PerfectBlack-picoctf@webshell:~$ ssh -p 57322 ctf-player@titan.picoctf.net
The authenticity of host '[titan.picoctf.net]:57322 ([3.139.174.234]:57322)' can't be established.
ED25519 key fingerprint is SHA256:4S9EbTSSRZm32I+cdM5TyzthpQryv5kudRP9PIKT7XQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[titan.picoctf.net]:57322' (ED25519) to the list of known hosts.
ctf-player@titan.picoctf.net's password: 
Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_8306c99d}
Connection to titan.picoctf.net closed.
PerfectBlack-picoctf@webshell:~$ 

#  reto9


PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/17/level3.py
--2025-02-20 05:43:54--  https://artifacts.picoctf.net/c/17/level3.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.43, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1337 (1.3K) [application/octet-stream]
Saving to: 'level3.py'

level3.py                                       100%[======================================================================================================>]   1.31K  --.-KB/s    in 0s      

2025-02-20 05:43:55 (44.9 MB/s) - 'level3.py' saved [1337/1337]

PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/17/level3.flag.txt.enc
--2025-02-20 05:44:16--  https://artifacts.picoctf.net/c/17/level3.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.92, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level3.flag.txt.enc'

level3.flag.txt.enc                             100%[======================================================================================================>]      31  --.-KB/s    in 0s      

2025-02-20 05:44:17 (1.16 MB/s) - 'level3.flag.txt.enc' saved [31/31]

PerfectBlack-picoctf@webshell:~$ wgwr 
Display all 3154 possibilities? (y or n)
PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/17/level3.hash.bin
--2025-02-20 05:44:42--  https://artifacts.picoctf.net/c/17/level3.hash.bin
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.128, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16 [application/octet-stream]
Saving to: 'level3.hash.bin'

level3.hash.bin                                 100%[======================================================================================================>]      16  --.-KB/s    in 0s      

2025-02-20 05:44:42 (1.27 MB/s) - 'level3.hash.bin' saved [16/16]

PerfectBlack-picoctf@webshell:~$ ls
README.txt     code.py       convertme.py     files      fixme1.py  fixmex.py  level1.flag.txt.enc  level2.flag.txt.enc  level3.flag.txt.enc  level3.py
challenge.zip  codebook.txt  decrypt_flag.py  files.zip  fixme2.py  home       level1.py            level2.py            level3.hash.bin      runme.py
PerfectBlack-picoctf@webshell:~$ cat level3.py
import hashlib

THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################

flag_enc = open('level3.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level3.hash.bin', 'rb').read()


def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()


def level_3_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")
level_3_pw_check()

The strings below are 7 possibilities for the correct password. 
(Only 1 is correct)
pos_pw_list = ["f09e", "4dcf", "87ab", "dba8", "752e", "3961", "f159"]

PerfectBlack-picoctf@webshell:~$ nano check_password.py
PerfectBlack-picoctf@webshell:~$ python3 check_password.py
Contraseña correcta: 87ab
PerfectBlack-picoctf@webshell:~$ 
PerfectBlack-picoctf@webshell:~$ python3 level3.py
Please enter correct password for flag: 87ab
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_cd6ed2eb}
PerfectBlack-picoctf@webshell:~$ 

# reto10
PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/35/serpentine.py
--2025-02-20 05:48:52--  https://artifacts.picoctf.net/c/35/serpentine.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.16, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2550 (2.5K) [application/octet-stream]
Saving to: 'serpentine.py'

serpentine.py                                   100%[======================================================================================================>]   2.49K  --.-KB/s    in 0s      

2025-02-20 05:48:52 (99.0 MB/s) - 'serpentine.py' saved [2550/2550]

PerfectBlack-picoctf@webshell:~$ ls
README.txt     check_password.py  codebook.txt  decrypt_flag.py  files.zip  fixme2.py  home                 level1.py            level2.py            level3.hash.bin  runme.py
challenge.zip  code.py            convertme.py  files            fixme1.py  fixmex.py  level1.flag.txt.enc  level2.flag.txt.enc  level3.flag.txt.enc  level3.py        serpentine.py
PerfectBlack-picoctf@webshell:~$ cat serpentine.py

import random
import sys



def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + chr(0x23) + chr(0x15) + chr(0x5c) + chr(0x01) + chr(0x57) + chr(0x2a) + chr(0x17) + chr(0x5e) + chr(0x5f) + chr(0x0d) + chr(0x3b) + chr(0x19) + chr(0x56) + chr(0x5b) + chr(0x5e) + chr(0x36) + chr(0x53) + chr(0x07) + chr(0x51) + chr(0x18) + chr(0x58) + chr(0x05) + chr(0x57) + chr(0x11) + chr(0x3a) + chr(0x0f) + chr(0x0e) + chr(0x59) + chr(0x06) + chr(0x4d) + chr(0x55) + chr(0x0c) + chr(0x0f) + chr(0x14)


def print_flag():
  flag = str_xor(flag_enc, 'enkidu')
  print(flag)


def print_encouragement():
  encouragements = ['You can do it!', 'Keep it up!', 
                    'Look how far you\'ve come!']
  choice = random.choice(range(0, len(encouragements)))
  print('\n-----------------------------------------------------')
  print(encouragements[choice])
  print('-----------------------------------------------------\n\n')



def main():

  print(
'''
    Y
  .-^-.
 /     \      .- ~ ~ -.
()     ()    /   _ _   `.                     _ _ _
 \_   _/    /  /     \   \                . ~  _ _  ~ .
   | |     /  /       \   \             .' .~       ~-. `.
   | |    /  /         )   )           /  /             `.`.
   \ \_ _/  /         /   /           /  /                `'
    \_ _ _.'         /   /           (  (
                    /   /             \  \\
                   /   /               \  \\
                  /   /                 )  )
                 (   (                 /  /
                  `.  `.             .'  /
                    `.   ~ - - - - ~   .'
                       ~ . _ _ _ _ . ~
'''
  )
  print('Welcome to the serpentine encourager!\n\n')
  
  while True:
    print('a) Print encouragement')
    print('b) Print flag')
    print('c) Quit\n')
    choice = input('What would you like to do? (a/b/c) ')
    
    if choice == 'a':
      print_encouragement()
      
    elif choice == 'b':
      print('\nOops! I must have misplaced the print_flag function! Check my source code!\n\n')
      
    elif choice == 'c':
      sys.exit(0)
      
    else:
      print('\nI did not understand "' + choice + '", input only "a", "b" or "c"\n\n')



if __name__ == "__main__":
  main()

PerfectBlack-picoctf@webshell:~$ nano decrypt_flag.py
PerfectBlack-picoctf@webshell:~$ python3 decrypt_flag.py
picoCTF{7h3_r04d_l355_7r4v3l3d_ae0b80bd}







