#  0 - Milkslap
# DESC

[🥛](http://mercury.picoctf.net:48380/)
# SOLUCION

````` python
Interesting, there is no file to download!? But there is a link in description if you click on the image.

![](https://miro.medium.com/v2/resize:fit:875/1*BrPYyuIEzNz9X9tN0J_IIg.png)

There is a PNG file, which works as a “GIF” when you move your mouse. Basically you give a milkslap to the person on the image.

Using curl to get more info, returns me nothing usefull.

![](https://miro.medium.com/v2/resize:fit:875/1*Ks-ikUMZFIZohqgy8_hLSw.png)

Then I copied the image link from the website and downloaded the only image there is.

![](https://miro.medium.com/v2/resize:fit:681/1*pUefBQf10n_IkN3KsNRFsA.png)

And runned few most common tools for steganography. As it is a PNG file, I used the **zsteg** command (steghide = only JPG, zsteg = only PNG) to try and find the flag.

Note: If you never used zsteg you can install it with command

> gem install zsteg

![](https://miro.medium.com/v2/resize:fit:875/1*zf-qvyfu2HI_Y0gfkTscGg.png)

Now I can read the flag, which is embedded inside the png file. Of course without ‘\n’. Which is new line feed.

**Ans**: picoCTF{imag3_m4n1pul4t10n_sl4p5}
````` 

#  02  Disk, disk, sleuth!
# DESC

Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image: [dds1-alpine.flag.img.gz](https://mercury.picoctf.net/static/f63e4eba644c99e92324b65cbd875db6/dds1-alpine.flag.img.gz)
# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Users/39204$
lixin@DELTUS:/mnt/c/Users/39204$ wget https://mercury.picoctf.net/static/f63e4eba644c99e92324b65cbd875db6/dds1-alpine.flag.img.gz
--2025-05-07 12:45:02--  https://mercury.picoctf.net/static/f63e4eba644c99e92324b65cbd875db6/dds1-alpine.flag.img.gz
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29768910 (28M) [application/octet-stream]
Saving to: ‘dds1-alpine.flag.img.gz’

dds1-alpine.flag.img.gz       100%[=================================================>]  28.39M  7.73MB/s    in 4.2s

2025-05-07 12:45:07 (6.83 MB/s) - ‘dds1-alpine.flag.img.gz’ saved [29768910/29768910]

lixin@DELTUS:/mnt/c/Users/39204$ gunzip dds1-alpine.flag.img.gz
lixin@DELTUS:/mnt/c/Users/39204$ sudo apt update
sudo apt install sleuthkit
[sudo] password for lixin:
Get:1 http://security.ubuntu.com/ubuntu noble-security InRelease [126 kB]
Hit:2 http://archive.ubuntu.com/ubuntu noble InRelease
Get:3 http://archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
Get:4 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages [820 kB]
Get:5 http://archive.ubuntu.com/ubuntu noble-backports InRelease [126 kB]
Get:6 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages [1066 kB]
Get:7 http://security.ubuntu.com/ubuntu noble-security/main Translation-en [152 kB]
Get:8 http://security.ubuntu.com/ubuntu noble-security/main amd64 Components [21.5 kB]
Get:9 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Packages [836 kB]
Get:10 http://security.ubuntu.com/ubuntu noble-security/universe Translation-en [182 kB]
Get:11 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Components [52.3 kB]
Get:12 http://security.ubuntu.com/ubuntu noble-security/restricted amd64 Packages [1041 kB]
Get:13 http://security.ubuntu.com/ubuntu noble-security/restricted Translation-en [215 kB]
Get:14 http://security.ubuntu.com/ubuntu noble-security/restricted amd64 Components [208 B]
Get:15 http://security.ubuntu.com/ubuntu noble-security/multiverse amd64 Packages [17.7 kB]
Get:16 http://security.ubuntu.com/ubuntu noble-security/multiverse amd64 Components [208 B]
Get:17 http://archive.ubuntu.com/ubuntu noble-updates/main Translation-en [229 kB]
Get:18 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Components [162 kB]
Get:19 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages [1061 kB]
Get:20 http://archive.ubuntu.com/ubuntu noble-updates/universe Translation-en [268 kB]
Get:21 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Components [376 kB]
Get:22 http://archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Packages [1073 kB]
Get:23 http://archive.ubuntu.com/ubuntu noble-updates/restricted Translation-en [221 kB]
Get:24 http://archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Components [212 B]
Get:25 http://archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Packages [21.7 kB]
Get:26 http://archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Components [940 B]
Get:27 http://archive.ubuntu.com/ubuntu noble-backports/main amd64 Components [7076 B]
Get:28 http://archive.ubuntu.com/ubuntu noble-backports/universe amd64 Packages [27.0 kB]
Get:29 http://archive.ubuntu.com/ubuntu noble-backports/universe Translation-en [16.5 kB]
Get:30 http://archive.ubuntu.com/ubuntu noble-backports/universe amd64 Components [16.4 kB]
Get:31 http://archive.ubuntu.com/ubuntu noble-backports/restricted amd64 Components [216 B]
Get:32 http://archive.ubuntu.com/ubuntu noble-backports/multiverse amd64 Components [212 B]
Fetched 8263 kB in 3s (2412 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
46 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
sleuthkit is already the newest version (4.12.1+dfsg-1.1ubuntu2).
sleuthkit set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 46 not upgraded.
lixin@DELTUS:/mnt/c/Users/39204$ srch_strings dds1-alpine.flag.img | grep pico
ffffffff81399ccf t pirq_pico_get
ffffffff81399cee t pirq_pico_set
ffffffff820adb46 t pico_router_probe
  SAY picoCTF{f0r3ns1c4t0r_n30phyt3_ad5c96c0}
lixin@DELTUS:/mnt/c/Users/39204$ srch_strings dds1-alpine.flag.img | grep picoCTF
  SAY picoCTF{f0r3ns1c4t0r_n30phyt3_ad5c96
````` 

#  03  Operation Orchid
# DESC

Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/213/disk.flag.img.gz)
# SOLUCION

````` python
This will be a place for me to write some writeups for my solutions for problems by the PicoCTF. Bear in mind this is my first day doing these problems, but I want to document it so I can remember stuff too. Here goes.

**Terminal used:** PicoCTF Webshell

**Year Solved:** 2024

# Operation Orchid

**Link:** [https://play.picoctf.org/practice/challenge/285](https://play.picoctf.org/practice/challenge/285)

We first `cd` to the `/tmp` directory in our shell, as recommended by PicoCTF. (I found that if we don’t use the `/tmp` directory, the files stay in our shell when we start our next session. Because the storage is limited, it’s better to use this `/tmp` folder.) Then, we download the file as given by the challenge using the `wget` command.

![](https://miro.medium.com/v2/resize:fit:875/1*Q2I8uKTjUx6CaWiuzCiqHw.png)

We’ll find out what the file is from the metadata using the `file <file_name>` command.

file disk.flag.img.gz

![](https://miro.medium.com/v2/resize:fit:875/1*DBO5G2gcxlcmapeOfnG90Q.png)

It’s a disk image, so we’ll unzip it using the `gunzip <file_name>` command. It’ll take a while, but once it’s done, type in `ls` to check the file contents in the directory you’re in. There will be the `disk.flag.img` file we just unzipped.

![](https://miro.medium.com/v2/resize:fit:680/1*CMxKpPxalzFETE-iytQr0w.png)

Next, we will use the `mmls` command to find out the contents of a disk. From the SleuthWiki’s page:

> mmls displays the contents of a volume system (media management). In general, this is used to list the partition table contents so that you can determine where each partition starts. The output identifies the type of partition and its length, which makes it easy to use ‘dd’ to extract the partitions. The output is sorted based on the starting sector so it is easy to identify gaps in the layout.

Basically, it shows the offset or the starting point of a partition in byte unites (if my Computer Architecture knowledge is still correct). We will use the command with our disk image.

mmls disk.flag.img

![](https://miro.medium.com/v2/resize:fit:875/1*QMekobSnYdEh1RZzlPaPTw.png)

We’ll find out that there’s **two** Linux (0x83) partitions. My guess is that it’s in the fifth partition (index 004) since it has the **largest** length, but we’ll find out what’s in the third partition (index 002).

Now, we’ll find out the contents of a partition using the `fls -o <starting offset>` command.

fls -o 2048

![](https://miro.medium.com/v2/resize:fit:703/1*FAM5W0Xm3UvlAIQ9GDQG4w.png)

This looks like OS mumbo-jumbo that I don’t understand, so I’ll just check out the other partition which starts at 411648.

![](https://miro.medium.com/v2/resize:fit:724/1*6UX5mF9n8W8AFrwzgHsmGw.png)

Inode number 472 has the folder `root` , which looks like a promising start. Hence, seek what’s inside there using the `fls` command once more, but now, we’re using the inode number as well, so the command looks like `fls -o <offset> <disk_name> <inode number>` .

![](https://miro.medium.com/v2/resize:fit:773/1*GistVa9-_szsP2WjbtXL0Q.png)

Woo, we’ve found flag.txt.enc on inode 1782! On inode 1876, there’s also a flag.txt, but since it has an asterisk, it’s already deleted. Now, since the `.enc` extension file means that the file is encrypted, we must find a way to decrypt it as well. But first, we have to know what the encryption method that is used and what the key is to decrypt it.

Let’s see what the `flag.txt.enc` file looks like inside using the `icat` command, to extract the data inside.

![](https://miro.medium.com/v2/resize:fit:790/1*ZWLMuJF0BCDBZvS9izgXaQ.png)

Salted__… hmm, looks like an AES encryption to me.

To find the key, we will find it using `strings -t d disk.flag.img | grep flag.txt` . Let’s break the command down:

1. `strings` is used to see the text or binary data inside a file. The `-t d` argument prints the offset of every string in the file.
2. The pipe operator `|` passes the output of `strings -t d` to `grep flag.txt` .
3. `grep` finds the line `flag.txt` so we can see what encryption method is used.

![](https://miro.medium.com/v2/resize:fit:875/1*l1fHqV471T9yIpca5s34wQ.png)

We get a bunch of output in some lines which look like `<number> <string>` . The numbers represent the byte offsets (in decimal) within the disk image where the strings were found. The strings show actions performed on a file named flag.txt.

We find that an OpenSSL AES-256 encryption was used (as we thought), with salt options, with the key `unbreakablepassword1234567` . All that’s left is to decrypt it. But first, we’re going to extract what’s inside using the `icat` method so we can decrypt the contents to the `/tmp` folder.

![](https://miro.medium.com/v2/resize:fit:875/1*VtgQU81q1mmViXD_R4dkrA.png)

Now the `flag.txt.enc` is in our `/tmp` folder so that we can do some commands to it. Here, we’re going to decrypt it using the `unbreakablepassword1234567` .

![](https://miro.medium.com/v2/resize:fit:875/1*H8Cnt3Hz4Ttb-3lm3ToR7Q.png)

**Flag found!** It’s `picoCTF{h4un71ng_p457_5113beab}`
````` 

#  04  Sleuthkit Apprentice
# DESC

Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/137/disk.flag.img.gz)
# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Users/39204$ gunzip disk.flag.img.gz
gzip: disk.flag.img.gz: No such file or directory
lixin@DELTUS:/mnt/c/Users/39204$ mmls disk.flag.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000360447   0000153600   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000360448   0000614399   0000253952   Linux (0x83)
lixin@DELTUS:/mnt/c/Users/39204$ fsstat -o 2048 disk.flag.img
FILE SYSTEM INFORMATION
--------------------------------------------
File System Type: Ext4
Volume Name:
Volume ID: 8e023955b4e7dab7e04b7643076ccf0f

Last Written at: 2021-09-29 13:10:02 (CDT)
Last Checked at: 2021-09-29 10:57:16 (CDT)

Last Mounted at: 2021-09-29 13:06:00 (CDT)
Unmounted properly
Last mounted on: /mnt/boot

Source OS: Linux
Dynamic Structure
Compat Features: Journal, Ext Attributes, Resize Inode, Dir Index
InCompat Features: Filetype, Extents, Flexible Block Groups,
Read Only Compat Features: Sparse Super, Large File, Huge File, Extra Inode Size

Journal ID: 00
Journal Inode: 8

METADATA INFORMATION
--------------------------------------------
Inode Range: 1 - 25585
Root Directory: 2
Free Inodes: 25560
Inode Size: 256

CONTENT INFORMATION
--------------------------------------------
Block Groups Per Flex Group: 16
Block Range: 0 - 102399
Block Size: 1024
Reserved Blocks Before Block Groups: 1
Free Blocks: 74579

BLOCK GROUP INFORMATION
--------------------------------------------
Number of Block Groups: 13
Inodes per group: 1968
Blocks per group: 8192

Group: 0:
  Inode Range: 1 - 1968
  Block Range: 1 - 8192
  Layout:
    Super Block: 1 - 1
    Group Descriptor Table: 2 - 2
    Group Descriptor Growth Blocks: 3 - 258
    Data bitmap: 259 - 259
    Inode bitmap: 272 - 272
    Inode Table: 285 - 776
    Data Blocks: 777 - 8192
  Free Inodes: 1944 (98%)
  Free Blocks: 1498 (18%)
  Total Directories: 2

Group: 1:
  Inode Range: 1969 - 3936
  Block Range: 8193 - 16384
  Layout:
    Super Block: 8193 - 8193
    Group Descriptor Table: 8194 - 8194
    Group Descriptor Growth Blocks: 8195 - 8450
    Data bitmap: 260 - 260
    Inode bitmap: 273 - 273
    Inode Table: 777 - 1268
    Data Blocks: 1269 - 16384
  Free Inodes: 1968 (100%)
  Free Blocks: 7548 (92%)
  Total Directories: 0

Group: 2:
  Inode Range: 3937 - 5904
  Block Range: 16385 - 24576
  Layout:
    Data bitmap: 261 - 261
    Inode bitmap: 274 - 274
    Inode Table: 1269 - 1760
    Data Blocks: 1761 - 24576
  Free Inodes: 1968 (100%)
  Free Blocks: 4644 (56%)
  Total Directories: 0

Group: 3:
  Inode Range: 5905 - 7872
  Block Range: 24577 - 32768
  Layout:
    Super Block: 24577 - 24577
    Group Descriptor Table: 24578 - 24578
    Group Descriptor Growth Blocks: 24579 - 24834
    Data bitmap: 262 - 262
    Inode bitmap: 275 - 275
    Inode Table: 1761 - 2252
    Data Blocks: 2253 - 32768
  Free Inodes: 1968 (100%)
  Free Blocks: 1884 (22%)
  Total Directories: 0

Group: 4:
  Inode Range: 7873 - 9840
  Block Range: 32769 - 40960
  Layout:
    Data bitmap: 263 - 263
    Inode bitmap: 276 - 276
    Inode Table: 2253 - 2744
    Data Blocks: 2745 - 40960
  Free Inodes: 1968 (100%)
  Free Blocks: 2436 (29%)
  Total Directories: 0

Group: 5:
  Inode Range: 9841 - 11808
  Block Range: 40961 - 49152
  Layout:
    Super Block: 40961 - 40961
    Group Descriptor Table: 40962 - 40962
    Group Descriptor Growth Blocks: 40963 - 41218
    Data bitmap: 264 - 264
    Inode bitmap: 277 - 277
    Inode Table: 2745 - 3236
    Data Blocks: 3237 - 49152
  Free Inodes: 1968 (100%)
  Free Blocks: 7934 (96%)
  Total Directories: 0

Group: 6:
  Inode Range: 11809 - 13776
  Block Range: 49153 - 57344
  Layout:
    Data bitmap: 265 - 265
    Inode bitmap: 278 - 278
    Inode Table: 3237 - 3728
    Data Blocks: 3729 - 57344
  Free Inodes: 1968 (100%)
  Free Blocks: 4096 (50%)
  Total Directories: 0

Group: 7:
  Inode Range: 13777 - 15744
  Block Range: 57345 - 65536
  Layout:
    Super Block: 57345 - 57345
    Group Descriptor Table: 57346 - 57346
    Group Descriptor Growth Blocks: 57347 - 57602
    Data bitmap: 266 - 266
    Inode bitmap: 279 - 279
    Inode Table: 3729 - 4220
    Data Blocks: 4221 - 65536
  Free Inodes: 1968 (100%)
  Free Blocks: 7934 (96%)
  Total Directories: 0

Group: 8:
  Inode Range: 15745 - 17712
  Block Range: 65537 - 73728
  Layout:
    Data bitmap: 267 - 267
    Inode bitmap: 280 - 280
    Inode Table: 4221 - 4712
    Data Blocks: 4713 - 73728
  Free Inodes: 1968 (100%)
  Free Blocks: 8192 (100%)
  Total Directories: 0

Group: 9:
  Inode Range: 17713 - 19680
  Block Range: 73729 - 81920
  Layout:
    Super Block: 73729 - 73729
    Group Descriptor Table: 73730 - 73730
    Group Descriptor Growth Blocks: 73731 - 73986
    Data bitmap: 268 - 268
    Inode bitmap: 281 - 281
    Inode Table: 4713 - 5204
    Data Blocks: 5205 - 81920
  Free Inodes: 1968 (100%)
  Free Blocks: 7934 (96%)
  Total Directories: 0

Group: 10:
  Inode Range: 19681 - 21648
  Block Range: 81921 - 90112
  Layout:
    Data bitmap: 269 - 269
    Inode bitmap: 282 - 282
    Inode Table: 5205 - 5696
    Data Blocks: 5697 - 90112
  Free Inodes: 1968 (100%)
  Free Blocks: 8192 (100%)
  Total Directories: 0

Group: 11:
  Inode Range: 21649 - 23616
  Block Range: 90113 - 98304
  Layout:
    Data bitmap: 270 - 270
    Inode bitmap: 283 - 283
    Inode Table: 5697 - 6188
    Data Blocks: 6189 - 98304
  Free Inodes: 1968 (100%)
  Free Blocks: 8192 (100%)
  Total Directories: 0

Group: 12:
  Inode Range: 23617 - 25584
  Block Range: 98305 - 102399
  Layout:
    Data bitmap: 271 - 271
    Inode bitmap: 284 - 284
    Inode Table: 6189 - 6680
    Data Blocks: 6681 - 102399
  Free Inodes: 1968 (100%)
  Free Blocks: 4095 (99%)
  Total Directories: 0
lixin@DELTUS:/mnt/c/Users/39204$ fls -o 2048 -f ext4 -r disk.flag.img | grep flag
lixin@DELTUS:/mnt/c/Users/39204$ icat -o 2048 -f ext4 disk.flag.img 67890
Metadata address too large for image (25585)
lixin@DELTUS:/mnt/c/Users/39204$ fls -o 360448 -f ext4 -r disk.flag.img | grep flag
++ r/r * 2082(realloc): flag.txt
++ r/r 2371:    flag.uni.txt
lixin@DELTUS:/mnt/c/Users/39204$ icat -o 360448 -f ext4 disk.flag.img 2371
picoCTF{by73_5urf3r_adac6cb4}
lixin@DELTUS:/mnt/c/Users/39204$
````` 

#  0- Operation Oni 
# DESC
 #### Description

Download this disk image, find the key and log into the remote machine.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

Additional details will be available after launching your challenge instance.

# SOLUCION

````` python
After downloading the file using **wget** decompressed the file using **gunzip** and then checked the file type

![](https://miro.medium.com/v2/resize:fit:875/1*kwJZWiC-7X61wGT66hfujA.png)

Then checked for file partitions using **mmls** command found three partitions out of one is unallocated.

![](https://miro.medium.com/v2/resize:fit:875/1*I9xvFgj5WLgouPHbkDR4gQ.png)

Then looked for file system of the partition number 2 **(Linux 0x83)** using **fsstat** command

![](https://miro.medium.com/v2/resize:fit:875/1*pz7CA3Au0byt7Vrs1VCNjA.png)

The first partitions is linux based partition so then I looked for files and directories of this partition using **fls** command..

![](https://miro.medium.com/v2/resize:fit:875/1*_WQpU2Iwe2TQa0Yna-iQ5g.png)

Some info about the partition

Nothing interesting here.

Then I checked for the file system of partition number 3 (**Linux 0x83**)using **fsstat** command then found that this is also a Linux partition

![](https://miro.medium.com/v2/resize:fit:875/1*iSVFO-NQdRPXROG174JQng.png)

Some info about the partition

Then looked for the directores and files using **fls** command

![](https://miro.medium.com/v2/resize:fit:875/1*B7-Y1TsLaL2IhFEDAmxyMw.png)

Found some interesting directories in this partition here

Then after searching in root directory I found…

![](https://miro.medium.com/v2/resize:fit:875/1*IssplDaTgzf82mFJ4S_oXw.png)

Then after looking in ssh directory..

![](https://miro.medium.com/v2/resize:fit:875/1*ejQAVCBErBlIQWog0SLtQQ.png)

Found public and private key

Reading every file one by one

![](https://miro.medium.com/v2/resize:fit:875/1*8enLWtZrHTs8cqfUgy73hg.png)

Found the private key for login into ssh

Then I exported the file to my local machine using **icat**

![](https://miro.medium.com/v2/resize:fit:875/1*Apz4MH94tvUeaLKXHMBtpg.png)

Checked the permission of the private key using **ls -l**

![](https://miro.medium.com/v2/resize:fit:875/1*6kfMwHJMmCkJ1bht0lomlA.png)

Then changing the permissions of the private key.

**NOTE: If the permissions are too open, SSH will refuse to use the key and instead prompt for a password or another form of authentication.**

So after changing the permission of the private key using **chmod** command

![](https://miro.medium.com/v2/resize:fit:875/1*NQpIzY5GN2BQkIuFB_BZCQ.png)

Permissions Changed

Now login to ssh using private key through `ssh -i keyfile -p portnumber username@ipofmachine.`

![](https://miro.medium.com/v2/resize:fit:875/1*sSkBVu-PBe8ZJxPlDajMXQ.png)

Login Successful

Then after looking in the directories found the flag

![](https://miro.medium.com/v2/resize:fit:875/1*d0ItQWjg7EWNvxIQXsxmaQ.png)

GOTCHA

picoCTF{k3y_5l3u7h_af277f77}
````` 


#  06 - Sleuthkit Intro
# DESC

Download the disk image and use `mmls` on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.[Download disk image](https://artifacts.picoctf.net/c/164/disk.img.gz)

Additional details will be available after launching your challenge instance.
# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Users/39204$ mmls disk.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000204799   0000202752   Linux (0x83)
lixin@DELTUS:/mnt/c/Users/39204$ nc saturn.picoctf.net 52248
What is the size of the Linux partition in the given disk image?
Length in sectors: 204800
204800
That is not correct. Feel free to try again.
lixin@DELTUS:/mnt/c/Users/39204$ nc saturn.picoctf.net 51405
What is the size of the Linux partition in the given disk image?
Length in sectors: 202752
202752
Great work!
picoCTF{mm15_f7w!}
lixin@DELTUS:/mnt/c/Users/39204$
````` 

