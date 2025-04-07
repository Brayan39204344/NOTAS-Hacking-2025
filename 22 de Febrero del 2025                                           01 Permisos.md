Can you read files in the root file?The system admin has provisioned an account for you on the main server:`ssh -p 50427 picoplayer@saturn.picoctf.net`Password: `UYiOazkqY2`Can you login and read the root file?
# solucion  

`ssh -p 53034 picoplayer@saturn.picoctf.net`
Password: `UYiOazkqY2`
```
picoplayer@challenge:~$ sudo -l
```
[sudo] password for picoplayer: 
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
``````
sudo vi /root

" ============================================================================
" Netrw Directory Listing                                        (netrw v165)
"   /root
"   Sorted by      name
"   Sort sequence: [\/]$,\<core\%(\.\d\+\)\=\>,\.h$,\.c$,\.cpp$,\~\=\*$,*,\.o$,\.obj$,\.info$,\.swp$
"   Quick Help: <F1>:help  -:go up dir  D:delete  R:rename  s:sort-by  x:special
" ==============================================================================
../                                                                                                 
./
.vim/
.bashrc
.flag.txt
.profile
.viminfo
`````
``````
# 02 chrono

#### Description

How to automate tasks to run at intervals on linux servers?Use ssh to connect to this server:

```
Server: saturn.picoctf.net
Port: 56656
Username: picoplayer 
Password: bLgSMmbY6X
```

# solucion 
````` python
PerfectBlack-picoctf@webshell:~$ ssh picoplayer@saturn.picoctf.net -p 55500
ssh: connect to host saturn.picoctf.net port 55500: Connection refused
PerfectBlack-picoctf@webshell:~$ ssh picoplayer@saturn.picoctf.net -p 56656
The authenticity of host '[saturn.picoctf.net]:56656 ([13.59.203.175]:56656)' can't be established.
ED25519 key fingerprint is SHA256:dMTscRrUiURy7uMu5eGWwEKdd2FzqLzx6LfWhssWnNQ.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:13: [hashed name]
    ~/.ssh/known_hosts:15: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:56656' (ED25519) to the list of known hosts.
picoplayer@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

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

picoplayer@challenge:~$ cat /etc/crontab
# picoCTF{Sch3DUL7NG_T45K3_L1NUX_1b4d8744}
picoplayer@challenge:~$ 

`````

# 03 Binary Search
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



# 04Special

#### Description

Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM)Start your instance to see connection details.`ssh -p 54798 ctf-player@saturn.picoctf.net`The password is `af86add3`

# SOLUCION 


````` python
PerfectBlack-picoctf@webshell:~$ ssh -p 54798 ctf-player@saturn.picoctf.net
ctf-player@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.
Last login: Sun Feb 23 05:07:05 2025 from 127.0.0.1
Special$ IFS=];b=cat]/etc/passwd;$b
IFS=];b=cat]/etc/passwd;$b 
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
_apt:x:100:65534::/nonexistent:/usr/sbin/nologin
systemd-timesync:x:101:101:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
systemd-network:x:102:103:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin
systemd-resolve:x:103:104:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin
messagebus:x:104:105::/nonexistent:/usr/sbin/nologin
sshd:x:105:65534::/run/sshd:/usr/sbin/nologin
ctf-player:x:1000:1000::/home/ctf-player:/usr/local/Special.py
Special$ $b$(IFS=];b=cat]blargh/flag.txt;$b)
$b$(IFS=];b=cat]blargh/flag.txt;$b) 
sh: 1: picoCTF{5p311ch3ck_15_7h3_w0r57_6a2763f6}: not found
Special$ 





````` 

- # 05 committee issue

#### Description

I accidentally wrote the flag down. Good thing I deleted it!You download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/77/challenge.zip)

````` python 
PerfectBlack-picoctf@webshell:~/drop-in$ 
PerfectBlack-picoctf@webshell:~/drop-in$ git checkout 3d5ec8a
Note: switching to '3d5ec8a'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 3d5ec8a create flag
PerfectBlack-picoctf@webshell:~/drop-in$ ls
message.txt
PerfectBlack-picoctf@webshell:~/drop-in$ cat message.txt
picoCTF{s@n1t1z3_30e86d36}
PerfectBlack-picoctf@webshell:~/drop-in$ 

````` 
# 06time machine


#### Description

What was I last working on? I remember writing a note to help me remember...You can download the challenge files here:

# solucion

````` python 
PerfectBlack-picoctf@webshell:~$  wget https://artifacts.picoctf.net/c_titan/77/challenge.zip
--2025-02-23 05:37:18--  https://artifacts.picoctf.net/c_titan/77/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.42, 3.160.5.18, 3.160.5.71, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.42|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19199 (19K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                                   100%[======================================================================================================>]  18.75K  --.-KB/s    in 0.008s  

2025-02-23 05:37:18 (2.40 MB/s) - 'challenge.zip' saved [19199/19199]

PerfectBlack-picoctf@webshell:~$ ls
challenge.zip
PerfectBlack-picoctf@webshell:~$ unzip challenge.zip
Archive:  challenge.zip
   creating: drop-in/
   creating: drop-in/.git/
   creating: drop-in/.git/branches/
  inflating: drop-in/.git/description  
   creating: drop-in/.git/hooks/
  inflating: drop-in/.git/hooks/applypatch-msg.sample  
  inflating: drop-in/.git/hooks/commit-msg.sample  
  inflating: drop-in/.git/hooks/fsmonitor-watchman.sample  
  inflating: drop-in/.git/hooks/post-update.sample  
  inflating: drop-in/.git/hooks/pre-applypatch.sample  
  inflating: drop-in/.git/hooks/pre-commit.sample  
  inflating: drop-in/.git/hooks/pre-merge-commit.sample  
  inflating: drop-in/.git/hooks/pre-push.sample  
  inflating: drop-in/.git/hooks/pre-rebase.sample  
  inflating: drop-in/.git/hooks/pre-receive.sample  
  inflating: drop-in/.git/hooks/prepare-commit-msg.sample  
  inflating: drop-in/.git/hooks/update.sample  
   creating: drop-in/.git/info/
  inflating: drop-in/.git/info/exclude  
   creating: drop-in/.git/refs/
   creating: drop-in/.git/refs/heads/
 extracting: drop-in/.git/refs/heads/master  
   creating: drop-in/.git/refs/tags/
 extracting: drop-in/.git/HEAD       
  inflating: drop-in/.git/config     
   creating: drop-in/.git/objects/
   creating: drop-in/.git/objects/pack/
   creating: drop-in/.git/objects/info/
   creating: drop-in/.git/objects/96/
 extracting: drop-in/.git/objects/96/f7309de67d785ec0b93b8766ff2882bef5c3ef  
   creating: drop-in/.git/objects/8c/
 extracting: drop-in/.git/objects/8c/1d254e2da6713e33acd6d622fc1dae357ec3c6  
   creating: drop-in/.git/objects/3d/
 extracting: drop-in/.git/objects/3d/5ec8a26ee7b092a1760fea18f384c35e435139  
   creating: drop-in/.git/objects/d5/
 extracting: drop-in/.git/objects/d5/52d1ecd2d83fa2e65b6724d1ff73b45a7d59b7  
   creating: drop-in/.git/objects/0c/
 extracting: drop-in/.git/objects/0c/1ab266b7a3a1cd099bb509f82b7a2d03aecd03  
   creating: drop-in/.git/objects/e1/
 extracting: drop-in/.git/objects/e1/237df82d2e69f62dd53279abc1c8aeb66f6d64  
  inflating: drop-in/.git/index      
 extracting: drop-in/.git/COMMIT_EDITMSG  
   creating: drop-in/.git/logs/
  inflating: drop-in/.git/logs/HEAD  
   creating: drop-in/.git/logs/refs/
   creating: drop-in/.git/logs/refs/heads/
  inflating: drop-in/.git/logs/refs/heads/master  
 extracting: drop-in/message.txt     
PerfectBlack-picoctf@webshell:~$ ls
challenge.zip  drop-in
PerfectBlack-picoctf@webshell:~$ 
PerfectBlack-picoctf@webshell:~$ 
PerfectBlack-picoctf@webshell:~$ cd drop-in/
PerfectBlack-picoctf@webshell:~/drop-in$ ls
message.txt
PerfectBlack-picoctf@webshell:~/drop-in$ cat message.txt
TOP SECRET
PerfectBlack-picoctf@webshell:~/drop-in$ git reflog
712314f (HEAD -> master) HEAD@{0}: commit (initial): picoCTF{t1m3m@ch1n3_e8c98b3a}
````` 

# 07 blame game

#### Description

Someone's commits seems to be preventing the program from working. Who is it?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/158/challenge.zip)
````` python
PerfectBlack-picoctf@webshell:~$ rm -rf *
PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/158/challenge.zip
--2025-02-23 05:52:47--  https://artifacts.picoctf.net/c_titan/158/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.71, 3.160.5.18, 3.160.5.93, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.71|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 294455 (288K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                                   100%[======================================================================================================>] 287.55K  1.84MB/s    in 0.2s    



2025-02-23 05:52:47 (1.84 MB/s) - 'challenge.zip' saved [294455/294455]

PerfectBlack-picoctf@webshell:~$ unzip challenge.zip
PerfectBlack-picoctf@webshell:~$ cd drop-in/
commit 8c83358c32daee3f8b597d2b853c1d1966b23f0a (HEAD)
Author: picoCTF{@sk_th3_1nt3rn_2c6bf174} <ops@picoctf.com>
Date:   Tue Mar 12 00:07:11 2024 +0000

    optimize file size of prod code

commit caa945839a2fc0fb52584b559b4e89ac7c46bf54
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:11 2024 +0000

    create top secret project

commit 8c83358c32daee3f8b597d2b853c1d1966b23f0a (HEAD)
Author: picoCTF{@sk_th3_1nt3rn_2c6bf174} <ops@picoctf.com>
Date:   Tue Mar 12 00:07:11 2024 +0000

    optimize file size of prod code

commit caa945839a2fc0fb52584b559b4e89ac7c46bf54
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:11 2024 +0000

    create top secret project

````` 
# 08 collaborative development
#### Description

My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?You can download the challenge files here:
# solucion


````` python
PerfectBlack-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/178/challenge.zip
--2025-02-23 06:00:33--  https://artifacts.picoctf.net/c_titan/178/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.71, 3.160.5.18, 3.160.5.93, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.71|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 24640 (24K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                                   100%[======================================================================================================>]  24.06K  --.-KB/s    in 0.008s  

2025-02-23 06:00:33 (2.78 MB/s) - 'challenge.zip' saved [24640/24640]

PerfectBlack-picoctf@webshell:~$ unzip challenge.zip




PerfectBlack-picoctf@webshell:~$ cd drop-in/
PerfectBlack-picoctf@webshell:~/drop-in$ cat flag.py 
print("Printing the flag...")
PerfectBlack-picoctf@webshell:~/drop-in$ git reflog

[8]+  Stopped                 git reflog
PerfectBlack-picoctf@webshell:~/drop-in$ git branch

[9]+  Stopped                 git branch
PerfectBlack-picoctf@webshell:~/drop-in$ 
PerfectBlack-picoctf@webshell:~/drop-in$ git marge feature/part-1
git: 'marge' is not a git command. See 'git --help'.

The most similar command is
        merge
PerfectBlack-picoctf@webshell:~/drop-in$ git merge feature/part-1
Updating 2258a0f..8eea062
Fast-forward
 flag.py | 1 +
 1 file changed, 1 insertion(+)
PerfectBlack-picoctf@webshell:~/drop-in$ git merge feature/part-2
Committer identity unknown

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'PerfectBlack-picoctf@webshell.(none)')
PerfectBlack-picoctf@webshell:~/drop-in$ git config --global user.name random 
PerfectBlack-picoctf@webshell:~/drop-in$ git config --global user.email random@gmail.com
PerfectBlack-picoctf@webshell:~/drop-in$ git merge feature/part-2
Auto-merging flag.py
CONFLICT (content): Merge conflict in flag.py
Automatic merge failed; fix conflicts and then commit the result.
PerfectBlack-picoctf@webshell:~/drop-in$ cat flag.py
print("Printing the flag...")
<<<<<<< HEAD
print("picoCTF{t3@mw0rk_", end='')
=======

print("m@k3s_th3_dr3@m_", end='')
>>>>>>> feature/part-2
PerfectBlack-picoctf@webshell:~/drop-in$ git add flag.py
PerfectBlack-picoctf@webshell:~/drop-in$ git commit -m mergeg
[main 8a76446] mergeg
PerfectBlack-picoctf@webshell:~/drop-in$ cat flag.py
print("Printing the flag...")
<<<<<<< HEAD
print("picoCTF{t3@mw0rk_", end='')
=======

print("m@k3s_th3_dr3@m_", end='')
>>>>>>> feature/part-2
PerfectBlack-picoctf@webshell:~/drop-in$ git merge feature/part-3
Auto-merging flag.py
CONFLICT (content): Merge conflict in flag.py
Automatic merge failed; fix conflicts and then commit the result.
PerfectBlack-picoctf@webshell:~/drop-in$ git add flag.py
PerfectBlack-picoctf@webshell:~/drop-in$ cat flag.py
print("Printing the flag...")
<<<<<<< HEAD
<<<<<<< HEAD
print("picoCTF{t3@mw0rk_", end='')
=======

print("m@k3s_th3_dr3@m_", end='')
>>>>>>> feature/part-2
=======

print("w0rk_6c06cec1}")
>>>>>>> feature/part-3
PerfectBlack-picoctf@webshell:~/drop-in$ git commit -m mergeg
[main 65a6970] mergeg
PerfectBlack-picoctf@webshell:~/drop-in$ cat flag.py
print("Printing the flag...")
<<<<<<< HEAD
<<<<<<< HEAD
print("picoCTF{t3@mw0rk_", end='')
=======

print("m@k3s_th3_dr3@m_", end='')
>>>>>>> feature/part-2
=======

print("w0rk_6c06cec1}")
>>>>>>> feature/part-3
PerfectBlack-picoctf@webshell:~/drop-in$ 
picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_6c06cec1}


````` 



# 09 binhexa

#### Description

How well can you perfom basic binary operations?

Additional details will be available after launching your challenge instance.
````` python 

PerfectBlack-picoctf@webshell:~$ nc titan.picoctf.net 65332

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 10111100
Binary Number 2: 11101101


Question 1/6:
Operation 1: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 10101100
Correct!

Question 2/6:
Operation 2: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 10111100000
Incorrect. Try again
Enter the binary result: 101111000
Correct!

Question 3/6:
Operation 3: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 11111101
Correct!

Question 4/6:
Operation 4: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 01110110
Correct!

Question 5/6:
Operation 5: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 1000101101100100
Incorrect. Try again
Enter the binary result: 1010111000001100
Correct!

Question 6/6:
Operation 6: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 110101001
Correct!
Enter the results of the last operation in hexadecimal: 0x1A9 

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_1367e2c6}


````` 

# 10 - ASCII Numbers
#### Description

Convert the following string of ASCII numbers into a readable string:
0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x35 0x63 0x31 0x31 0x5f 0x6e 0x30 0x5f 0x71 0x75 0x33 0x35 0x37 0x31 0x30 0x6e 0x35 0x5f 0x31 0x6c 0x6c 0x5f 0x74 0x33 0x31 0x31 0x5f 0x79 0x33 0x5f 0x6e 0x30 0x5f 0x6c 0x31 0x33 0x35 0x5f 0x34 0x34 0x35 0x64 0x34 0x31 0x38 0x30 0x7d

# solucion
![[Pasted image 20250223003649.png]]