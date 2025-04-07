# based 

```python
PerfectBlack-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 29221 
Let us see how data is stored
map
Please give the 01101101 01100001 01110000 as a word.
...
you have 45 seconds.....

Input:
map
Please give me the  143 157 155 160 165 164 145 162 as a word.
Input:
computer
Please give me the 737472656574 as a word.
Input:
street
You've beaten the challenge
Flag: picoCTF{learning_about_converting_values_00a975ff}
```

# strings it

# solucion 1
```python
PerfectBlack-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/94d00153b0057d37da225ee79a846c62/strings
--2025-02-17 18:19:08--  https://jupiter.challenges.picoctf.org/static/94d00153b0057d37da225ee79a846c62/strings
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 776032 (758K) [application/octet-stream]
Saving to: 'strings.1'

strings.1                                       100%[====================================================================================================>] 757.84K  1.85MB/s    in 0.4s    

2025-02-17 18:19:08 (1.85 MB/s) - 'strings.1' saved [776032/776032]

PerfectBlack-picoctf@webshell:~$ 
PerfectBlack-picoctf@webshell:~$ strings -n 10 strings | grep pico
picoCTF{5tRIng5_1T_d66c7bb7}
```
#  Wave a flag

#  Description

Can you invoke help flags for a tool or binary? [This program](https://mercury.picoctf.net/static/fc1d77192c544314efece5dd309092e3/warm) has extraordinarily helpful information...

# solucion 1

```python
PerfectBlack-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/fc1d77192c544314efece5dd309092e3/warm
--2025-02-17 18:21:16--  https://mercury.picoctf.net/static/fc1d77192c544314efece5dd309092e3/warm
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10936 (11K) [application/octet-stream]
Saving to: 'warm'

warm                                            100%[====================================================================================================>]  10.68K  --.-KB/s    in 0s      

2025-02-17 18:21:16 (304 MB/s) - 'warm' saved [10936/10936]

PerfectBlack-picoctf@webshell:~$ ls       
README.txt  file  flag  salida  strings  strings.1  warm
PerfectBlack-picoctf@webshell:~$ chmod +x warm
PerfectBlack-picoctf@webshell:~$ ./warm
Hello user! Pass me a -h to learn what I can do!
PerfectBlack-picoctf@webshell:~$ ./warm -h
Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_6635aa47}
PerfectBlack-picoctf@webshell:~$ 
```

# Static ain't always noise
#### Description

Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/0f6ea599582dcce7b4f1ba94e3617baf/static)? This [BASH script](https://mercury.picoctf.net/static/0f6ea599582dcce7b4f1ba94e3617baf/ltdis.sh) might help!

# solucion 

descragamos los 2 archivos
```python
PerfectBlack-picoctf@webshell:~$ 
PerfectBlack-picoctf@webshell:~$ ls
README.txt  file  flag  ltdis.sh  salida  static  strings  strings.1  warm
PerfectBlack-picoctf@webshell:~$ chmod +x static
PerfectBlack-picoctf@webshell:~$ ./static       
Oh hai! Wait what? A flag? Yes, it's around here somewhere!
PerfectBlack-picoctf@webshell:~$ cat ltdis.sh

PerfectBlack-picoctf@webshell:~$ bash ltdis.sh static
Attempting disassembly of static ...
Disassembly successful! Available at: static.ltdis.x86_64.txt
Ripping strings from binary with file offsets...
Any strings found in static have been written to static.ltdis.strings.txt with file offset
PerfectBlack-picoctf@webshell:~$ cat static.ltdis.strings.txt | grep pico ^C
PerfectBlack-picoctf@webshell:~$ ls                    
README.txt  file  flag  ltdis.sh  salida  static  static.ltdis.strings.txt  static.ltdis.x86_64.txt  strings  strings.1  warm
PerfectBlack-picoctf@webshell:~$ cat static.ltdis.strings.txt | grep pico
   1020 picoCTF{d15a5m_t34s3r_6f8c8200}
```


# useless

#### Description

There's an interesting script in the user's home directory

Additional details will be available after launching your challenge instance.
# solucion 1


```python
PerfectBlack-picoctf@webshell:~$ ssh picoplayer@saturn.picoctf.net -p 64739
The authenticity of host '[saturn.picoctf.net]:64739 ([13.59.203.175]:64739)' can't be established.
ED25519 key fingerprint is SHA256:DiJcS90U9QussLS8HLR6l6BGJb5eCA0vRmA18IvDvw8.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:64739' (ED25519) to the list of known hosts.
picoplayer@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.6 LTS (GNU/Linux 6.5.0-1023-aws x86_64)
picoplayer@challenge:~$ man useless 
useless
     useless, -- This is a simple calculator script

SYNOPSIS
     useless, [add sub mul div] number1 number2

DESCRIPTION
     Use the useless, macro to make simple calulations like addition,subtraction, multiplication and division.

Examples
     ./useless add 1 2
       This will add 1 and 2 and return 3

     ./useless mul 2 3
       This will return 6 as a product of 2 and 3

     ./useless div 6 3
       This will return 2 as a quotient of 6 and 3

     ./useless sub 6 5
       This will return 1 as a remainder of substraction of 5 from 6

Authors
     This script was designed and developed by Cylab Africa

     picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_3823}

picoplayer@challenge:~$ Connection to saturn.picoctf.net closed by remote host.
Connection to saturn.picoctf.net closed.
PerfectBlack-picoctf@webshell:~$ 
```

# Tab, Tab, Attack
#### Description

Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames: [Addadshashanammu.zip](https://mercury.picoctf.net/static/72712e82413e78cc8aa8d553ffea42b0/Addadshashanammu.zip)
# solucion 

```python
PerfectBlack-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku$ cd
PerfectBlack-picoctf@webshell:~$ strings Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku$
strings: 'Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku$': No such file
PerfectBlack-picoctf@webshell:~$ strings Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku 
strings: Warning: 'Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku' is a directory
PerfectBlack-picoctf@webshell:~$ cd Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/
PerfectBlack-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku$ LS
-bash: LS: command not found
PerfectBlack-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku$ ls
fang-of-haynekhtnamet
PerfectBlack-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku$ ./fang-of-haynekhtnamet
*ZAP!* picoCTF{l3v3l_up!_t4k3_4_r35t!_6f332f10}
PerfectBlack-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku$ 
```

# Magikarp Ground Mission

#### Description

Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin. Login via `ssh` as `ctf-player` with the password, `a13b7f9d`

Additional details will be available after launching your challenge instance.


# solicion 

```python 

PerfectBlack-picoctf@webshell:~$ ssh ctf-player@venus.picoctf.net -p 52949
The authenticity of host '[venus.picoctf.net]:52949 ([3.131.124.143]:52949)' can't be established.
ED25519 key fingerprint is SHA256:P1f6h95BrSVnJbm2AKhphfHHGEyAeThib/rN/AwKs24.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[venus.picoctf.net]:52949' (ED25519) to the list of known hosts.
ctf-player@venus.picoctf.net's password: 
Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 5.4.0-1041-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage
This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ctf-player@pico-chall$ ls
1of3.flag.txt  instructions-to-2of3.txt
ctf-player@pico-chall$ cat 1of3.flag.txt
picoCTF{xxsh_0ut_0f_\/\/4t3r_71be5264}
ctf-player@pico-chall$ cat instructions-to-2of3.txt
Next, go to the root of all things, more succinctly `/`
ctf-player@pico-chall$ 
ctf-player@pico-chall$ cd /
ctf-player@pico-chall$ ls
2of3.flag.txt  bin  boot  dev  etc  home  instructions-to-3of3.txt  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
ctf-player@pico-chall$ cat 2of3.flag.txt
0ut_0f_\/\/4t3r_
ctf-player@pico-chall$ 
ctf-player@pico-chall$ cat instructions-to-3of3.txt
Lastly, ctf-player, go home... more succinctly `~`
ctf-player@pico-chall$ 
ctf-player@pico-chall$ cd $HOME
ctf-player@pico-chall$ LS
-bash: LS: command not found
ctf-player@pico-chall$ ls
3of3.flag.txt  drop-in
ctf-player@pico-chall$ cat 3of3.flag.txt
71be5264}
ctf-player@pico-chall$ Connection to venus.picoctf.net closed by remote host.
Connection to venus.picoctf.net closed.
PerfectBlack-picoctf@webshell:~$ 


picoCTF{xxsh_0ut_0f_\/\/4t3r_71be5264}

```

# repetitions

#### Description

Can you make sense of this file?Download the file [here](https://artifacts.picoctf.net/c/474/enc_flag).

```python
PerfectBlack-picoctf@webshell:~$ 
PerfectBlack-picoctf@webshell:~$
wgethttps://artifacts.picoctf.net/c/474/enc_flag
PerfectBlack-picoctf@webshell:~$ cat enc_flag|base64 -d|base64 -d|base64 -d|base64 -d|base64 -d|base64 -d
picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_3f81f7be}
```

# Big Zip
#### Description

Unzip this archive and find the flag.

- [Download zip file](https://artifacts.picoctf.net/c/505/big-zip-files.zip)
# solucion 
```python
PerfectBlack-picoctf@webshell:~$ grep -R picoCTF
.python_history:'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
grep: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/fang-of-haynekhtnamet: binary file matches
big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode 
picoCTF{gr3p_15_m4g1c_ef8790dc}
```

# First Find
#### Description

Unzip this archive and find the file named 'uber-secret.txt'

- [Download zip file](https://artifacts.picoctf.net/c/502/files.zip)
# solucion 

```python
PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/502/files.zip
--2025-02-17 19:22:06--  https://artifacts.picoctf.net/c/502/files.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.16, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3995553 (3.8M) [application/octet-stream]
Saving to: 'files.zip'

files.zip                                       100%[======================================================================================================>]   3.81M  1.82MB/s    in 2.1s    

2025-02-17 19:22:08 (1.82 MB/s) - 'files.zip' saved [3995553/3995553]

PerfectBlack-picoctf@webshell:~$ ls
files.zip
PerfectBlack-picoctf@webshell:~$ unzip files.zip
Archive:  files.zip
   creating: files/
   creating: files/satisfactory_books/
   creating: files/satisfactory_books/more_books/
  inflating: files/satisfactory_books/more_books/37121.txt.utf-8  
  inflating: files/satisfactory_books/23765.txt.utf-8  
  inflating: files/satisfactory_books/16021.txt.utf-8  
  inflating: files/13771.txt.utf-8   
   creating: files/adequate_books/
   creating: files/adequate_books/more_books/
   creating: files/adequate_books/more_books/.secret/
   creating: files/adequate_books/more_books/.secret/deeper_secrets/
   creating: files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/
 extracting: files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt  
  inflating: files/adequate_books/more_books/1023.txt.utf-8  
  inflating: files/adequate_books/46804-0.txt  
  inflating: files/adequate_books/44578.txt.utf-8  
   creating: files/acceptable_books/
   creating: files/acceptable_books/more_books/
  inflating: files/acceptable_books/more_books/40723.txt.utf-8  
  inflating: files/acceptable_books/17880.txt.utf-8  
  inflating: files/acceptable_books/17879.txt.utf-8  
  inflating: files/14789.txt.utf-8   
PerfectBlack-picoctf@webshell:~$ cat files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
picoCTF{f1nd_15_f457_ab443fd1}
PerfectBlack-picoctf@webshell:~$ 

```

