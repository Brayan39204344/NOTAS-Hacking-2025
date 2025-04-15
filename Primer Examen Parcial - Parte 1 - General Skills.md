# 01 FANTASY CTF
# DESC
Play this short game to get familiar with terminal applications and some of the most important rules in scope for picoCTF.Connect to the program with netcat:`$ nc verbal-sleep.picoctf.net 63285`

# SOLUCION
ingrese a la pagina le dia enter asta que me arrojo la bandera 
````` python
PerfectBlack-picoctf@webshell:~$ nc verbal-sleep.picoctf.net 63285
FANTASY CTF SIMULATION
picoCTF{m1113n1um_3d1710n_e41acbee}
````` 


# 02   HashingJobApp
# DESC
If you want to hash with the best, beat this test!`nc saturn.picoctf.net 53805`

# SOLUCION

````` python
PerfectBlack-picoctf@webshell:~$ nc saturn.picoctf.net 53805
Please md5 hash the text between quotes, excluding the quotes: 'clowns'
Answer: 
f9b12092c70ec2d9ae6d9ff68b061b27
f9b12092c70ec2d9ae6d9ff68b061b27
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'a full moon'
Answer: 
3dbbee596fa3666609f8bcff87bb3df4
3dbbee596fa3666609f8bcff87bb3df4
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'Atlantis'
Answer: 
a425a3c39e1eaba4a378b0a08d80db9b
a425a3c39e1eaba4a378b0a08d80db9b
Correct.
picoCTF{4ppl1c4710n_r3c31v3d_674c1de2}
````` 



# 03  Python Wrangling
# DESC
Python scripts are invoked kind of like programs in the Terminal... Can you run [this Python script](https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/ende.py) using [this password](https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/pw.txt) to get [the flag](https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/flag.txt.en)?

# SOLUCION

````` python
PerfectBlack-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/ende.py
--2025-04-15 15:50:42--  https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/ende.py
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1328 (1.3K) [application/octet-stream]
Saving to: 'ende.py'

ende.py                                                    100%[========================================================================================================================================>]   1.30K  --.-KB/s    in 0s      

2025-04-15 15:50:42 (1.13 GB/s) - 'ende.py' saved [1328/1328]

PerfectBlack-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/pw.txt
--2025-04-15 15:51:07--  https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/pw.txt
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33 [application/octet-stream]
Saving to: 'pw.txt'

pw.txt                                                     100%[========================================================================================================================================>]      33  --.-KB/s    in 0s      

2025-04-15 15:51:07 (16.6 MB/s) - 'pw.txt' saved [33/33]

PerfectBlack-picoctf@webshell:~$ https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/flag.txt.en
-bash: https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/flag.txt.en: No such file or directory
PerfectBlack-picoctf@webshell:~$ 
PerfectBlack-picoctf@webshell:~$ wgwt https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/flag.txt.en
-bash: wgwt: command not found
PerfectBlack-picoctf@webshell:~$ wgwt https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/flag.txt.en^C
PerfectBlack-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/flag.txt.en
--2025-04-15 15:52:20--  https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/flag.txt.en
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 140 [application/octet-stream]
Saving to: 'flag.txt.en'

flag.txt.en                                                100%[========================================================================================================================================>]     140  --.-KB/s    in 0s      

2025-04-15 15:52:20 (64.8 MB/s) - 'flag.txt.en' saved [140/140]

PerfectBlack-picoctf@webshell:~$ ls
README.txt  challenge.zip  drop-in  ende.py  flag.txt.en  pw.txt
PerfectBlack-picoctf@webshell:~$ ende.py -d flag.txt.en
-bash: ende.py: command not found
PerfectBlack-picoctf@webshell:~$ python3 ende.py -d flag.txt.en
Please enter the password:192ee2db192ee2db192ee2db192ee2db
picoCTF{4p0110_1n_7h3_h0us3_192ee2db}
````` 





# 04  Rust fixme 1
# DESC

Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz).
# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Windows/system32$ wget https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz
tar -xvzf fixme1.tar.gz
cd fixme1
cargo build
--2025-04-15 10:55:10--  https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 18.238.132.115, 18.238.132.26, 18.238.132.88, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|18.238.132.115|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1415 (1.4K) [application/octet-stream]
Saving to: ‘fixme1.tar.gz’

fixme1.tar.gz                 100%[=================================================>]   1.38K  --.-KB/s    in 0s

2025-04-15 10:55:14 (191 MB/s) - ‘fixme1.tar.gz’ saved [1415/1415]

fixme1/
fixme1/Cargo.toml
fixme1/Cargo.lock
fixme1/src/
fixme1/src/main.rs
Command 'cargo' not found, but can be installed with:
sudo snap install rustup  # version 1.27.1, or
sudo apt  install cargo   # version 1.75.0+dfsg0ubuntu1-0ubuntu7.1
sudo apt  install rustup  # version 1.26.0-3
See 'snap info rustup' for additional versions.
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
info: downloading installer








^X
Welcome to Rust!

This will download and install the official compiler for the Rust
programming language, and its package manager, Cargo.

Rustup metadata and toolchains will be installed into the Rustup
home directory, located at:

  /home/lixin/.rustup

This can be modified with the RUSTUP_HOME environment variable.

The Cargo home directory is located at:

  /home/lixin/.cargo

This can be modified with the CARGO_HOME environment variable.

The cargo, rustc, rustup and other commands will be added to
Cargo's bin directory, located at:

  /home/lixin/.cargo/bin

This path will then be added to your PATH environment variable by
modifying the profile files located at:

  /home/lixin/.profile
  /home/lixin/.bashrc

You can uninstall at any time with rustup self uninstall and
these changes will be reverted.

Current installation options:


   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable (default)
               profile: default
  modify PATH variable: yes

1) Proceed with standard installation (default - just press enter)
2) Customize installation
3) Cancel installation
>
info: profile set to 'default'
info: default host triple is x86_64-unknown-linux-gnu
info: syncing channel updates for 'stable-x86_64-unknown-linux-gnu'
872.8 KiB / 872.8 KiB (100 %) 603.0 KiB/s in  1s
info: latest update on 2025-04-03, rust version 1.86.0 (05f9846f8 2025-03-31)
info: downloading component 'cargo'
427.8 KiB /   8.8 MiB (  5 %)   0 B/s in  1s ETA: Unknown
763.8 KiB /   8.8 MiB (  8 %) 427.8 KiB/s in  4s ETA: 19s
  8.8 MiB /   8.8 MiB (100 %) 324.2 KiB/s in 47s
info: downloading component 'clippy'
  2.8 MiB /   2.8 MiB (100 %) 955.1 KiB/s in  3s
info: downloading component 'rust-docs'
 21.2 MiB /  21.2 MiB (100 %) 500.7 KiB/s in  1m 19s
info: downloading component 'rust-std'
 27.1 MiB /  27.1 MiB (100 %) 143.0 KiB/s in  2m  3s
info: downloading component 'rustc'
 72.8 MiB /  72.8 MiB (100 %) 123.8 KiB/s in  4m 33s
info: downloading component 'rustfmt'
  2.4 MiB /   2.4 MiB (100 %) 224.8 KiB/s in 11s
info: installing component 'cargo'
info: installing component 'clippy'
info: installing component 'rust-docs'
 21.2 MiB /  21.2 MiB (100 %)   8.3 MiB/s in  2s
info: installing component 'rust-std'
 27.1 MiB /  27.1 MiB (100 %)  16.7 MiB/s in  1s
info: installing component 'rustc'
 72.8 MiB /  72.8 MiB (100 %)  16.7 MiB/s in  4s
info: installing component 'rustfmt'
info: default toolchain set to 'stable-x86_64-unknown-linux-gnu'

  stable-x86_64-unknown-linux-gnu installed - rustc 1.86.0 (05f9846f8 2025-03-31)


Rust is installed now. Great!

To get started you may need to restart your current shell.
This would reload your PATH environment variable to include
Cargo's bin directory ($HOME/.cargo/bin).

To configure your current shell, you need to source
the corresponding env file under $HOME/.cargo.

This is usually done by running one of the following (note the leading DOT):
. "$HOME/.cargo/env"            # For sh/bash/zsh/ash/dash/pdksh
source "$HOME/.cargo/env.fish"  # For fish
source "$HOME/.cargo/env.nu"    # For nushell
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$ cargo build
Command 'cargo' not found, but can be installed with:
sudo snap install rustup  # version 1.27.1, or
sudo apt  install cargo   # version 1.75.0+dfsg0ubuntu1-0ubuntu7.1
sudo apt  install rustup  # version 1.26.0-3
See 'snap info rustup' for additional versions.
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$ . "$HOME/.cargo/env"
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$ cargo --version
cargo 1.86.0 (adf9b6ad1 2025-02-28)
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$ cargo build
    Updating crates.io index
  Downloaded crossbeam-deque v0.8.5
  Downloaded xor_cryptor v1.2.3
  Downloaded crossbeam-utils v0.8.20
  Downloaded crossbeam-epoch v0.9.18
  Downloaded either v1.13.0
  Downloaded rayon-core v1.12.1
  Downloaded rayon v1.10.0
  Downloaded 7 crates (388.2 KB) in 2.32s
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling either v1.13.0
error: linker `cc` not found
  |
  = note: No such file or directory (os error 2)

error: could not compile `rayon-core` (build script) due to 1 previous error
warning: build failed, waiting for other jobs to finish...
error: could not compile `crossbeam-utils` (build script) due to 1 previous error
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$ cd srs
-bash: cd: srs: No such file or directory
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$  tar -xvzf fixme1.tar.gz
tar (child): fixme1.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
lixin@DELTUS:/mnt/c/Windows/system32/fixme1$ cd src
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$ nano main.rs
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$ cargo build
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
error: linker `cc` not found
  |
  = note: No such file or directory (os error 2)

error: could not compile `rayon-core` (build script) due to 1 previous error
warning: build failed, waiting for other jobs to finish...
error: could not compile `crossbeam-utils` (build script) due to 1 previous error
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$ sudo apt update && sudo apt install build-essential
[sudo] password for lixin:
Hit:1 http://archive.ubuntu.com/ubuntu noble InRelease
Get:2 http://security.ubuntu.com/ubuntu noble-security InRelease [126 kB]
Get:3 http://archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
Get:4 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages [748 kB]
Get:5 http://archive.ubuntu.com/ubuntu noble-backports InRelease [126 kB]
Get:6 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages [992 kB]
Get:7 http://security.ubuntu.com/ubuntu noble-security/main Translation-en [143 kB]
Get:8 http://security.ubuntu.com/ubuntu noble-security/main amd64 Components [8956 B]
Get:9 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Packages [830 kB]
Get:10 http://archive.ubuntu.com/ubuntu noble-updates/main Translation-en [219 kB]
Get:11 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Components [151 kB]
Get:12 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages [1054 kB]
Get:13 http://security.ubuntu.com/ubuntu noble-security/universe Translation-en [181 kB]
Get:14 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Components [52.2 kB]
Get:15 http://security.ubuntu.com/ubuntu noble-security/restricted amd64 Packages [859 kB]
Get:16 http://security.ubuntu.com/ubuntu noble-security/restricted Translation-en [175 kB]
Get:17 http://security.ubuntu.com/ubuntu noble-security/restricted amd64 Components [212 B]
Get:18 http://security.ubuntu.com/ubuntu noble-security/multiverse amd64 Components [208 B]
Get:19 http://archive.ubuntu.com/ubuntu noble-updates/universe Translation-en [266 kB]
Get:20 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Components [367 kB]
Get:21 http://archive.ubuntu.com/ubuntu noble-updates/restricted Translation-en [182 kB]
Get:22 http://archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Components [212 B]
Get:23 http://archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Components [940 B]
Get:24 http://archive.ubuntu.com/ubuntu noble-backports/main amd64 Components [7064 B]
Get:25 http://archive.ubuntu.com/ubuntu noble-backports/universe amd64 Components [15.8 kB]
Get:26 http://archive.ubuntu.com/ubuntu noble-backports/restricted amd64 Components [216 B]
Get:27 http://archive.ubuntu.com/ubuntu noble-backports/multiverse amd64 Components [212 B]
Fetched 6632 kB in 32s (205 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
90 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  bzip2 cpp cpp-13 cpp-13-x86-64-linux-gnu cpp-x86-64-linux-gnu dpkg-dev fakeroot g++ g++-13 g++-13-x86-64-linux-gnu
  g++-x86-64-linux-gnu gcc gcc-13 gcc-13-base gcc-13-x86-64-linux-gnu gcc-x86-64-linux-gnu libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan8 libatomic1 libc-dev-bin libc-devtools libc6-dev libcc1-0
  libcrypt-dev libde265-0 libdpkg-perl libfakeroot libfile-fcntllock-perl libgcc-13-dev libgd3 libheif-plugin-aomdec
  libheif-plugin-aomenc libheif-plugin-libde265 libheif1 libhwasan0 libisl23 libitm1 liblsan0 libmpc3 libquadmath0
  libstdc++-13-dev libtsan2 libubsan1 libxpm4 linux-libc-dev lto-disabled-list make manpages-dev rpcsvc-proto
Suggested packages:
  bzip2-doc cpp-doc gcc-13-locales cpp-13-doc debian-keyring g++-multilib g++-13-multilib gcc-13-doc gcc-multilib
  autoconf automake libtool flex bison gdb gcc-doc gcc-13-multilib gdb-x86-64-linux-gnu glibc-doc bzr libgd-tools
  libheif-plugin-x265 libheif-plugin-ffmpegdec libheif-plugin-jpegdec libheif-plugin-jpegenc libheif-plugin-j2kdec
  libheif-plugin-j2kenc libheif-plugin-rav1e libheif-plugin-svtenc libstdc++-13-doc make-doc
The following NEW packages will be installed:
  build-essential bzip2 cpp cpp-13 cpp-13-x86-64-linux-gnu cpp-x86-64-linux-gnu dpkg-dev fakeroot g++ g++-13
  g++-13-x86-64-linux-gnu g++-x86-64-linux-gnu gcc gcc-13 gcc-13-base gcc-13-x86-64-linux-gnu gcc-x86-64-linux-gnu
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan8 libatomic1 libc-dev-bin
  libc-devtools libc6-dev libcc1-0 libcrypt-dev libde265-0 libdpkg-perl libfakeroot libfile-fcntllock-perl
  libgcc-13-dev libgd3 libheif-plugin-aomdec libheif-plugin-aomenc libheif-plugin-libde265 libheif1 libhwasan0
  libisl23 libitm1 liblsan0 libmpc3 libquadmath0 libstdc++-13-dev libtsan2 libubsan1 libxpm4 linux-libc-dev
  lto-disabled-list make manpages-dev rpcsvc-proto
0 upgraded, 52 newly installed, 0 to remove and 90 not upgraded.
Need to get 69.2 MB/69.2 MB of archives.
After this operation, 236 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libc-dev-bin amd64 2.39-0ubuntu8.4 [20.4 kB]
Get:2 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 linux-libc-dev amd64 6.8.0-57.59 [1807 kB]
Get:3 http://archive.ubuntu.com/ubuntu noble/main amd64 libcrypt-dev amd64 1:4.4.36-4build1 [112 kB]
Get:4 http://archive.ubuntu.com/ubuntu noble/main amd64 rpcsvc-proto amd64 1.4.2-0ubuntu7 [67.4 kB]
Get:5 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libc6-dev amd64 2.39-0ubuntu8.4 [2124 kB]
Get:6 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 gcc-13-base amd64 13.3.0-6ubuntu2~24.04 [51.5 kB]
Get:7 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libisl23 amd64 0.26-3build1.1 [680 kB]
Get:8 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libmpc3 amd64 1.3.1-1build1.1 [54.6 kB]
Get:9 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 cpp-13-x86-64-linux-gnu amd64 13.3.0-6ubuntu2~24.04 [10.7 MB]
Get:10 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 cpp-13 amd64 13.3.0-6ubuntu2~24.04 [1038 B]
Get:11 http://archive.ubuntu.com/ubuntu noble/main amd64 cpp-x86-64-linux-gnu amd64 4:13.2.0-7ubuntu1 [5326 B]
Get:12 http://archive.ubuntu.com/ubuntu noble/main amd64 cpp amd64 4:13.2.0-7ubuntu1 [22.4 kB]
Get:13 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libcc1-0 amd64 14.2.0-4ubuntu2~24.04 [48.0 kB]
Get:14 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libitm1 amd64 14.2.0-4ubuntu2~24.04 [29.7 kB]
Get:15 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libasan8 amd64 14.2.0-4ubuntu2~24.04 [3031 kB]
Get:16 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 liblsan0 amd64 14.2.0-4ubuntu2~24.04 [1322 kB]
Get:17 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libtsan2 amd64 14.2.0-4ubuntu2~24.04 [2772 kB]
Get:18 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libubsan1 amd64 14.2.0-4ubuntu2~24.04 [1184 kB]
Get:19 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libhwasan0 amd64 14.2.0-4ubuntu2~24.04 [1641 kB]
Get:20 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libquadmath0 amd64 14.2.0-4ubuntu2~24.04 [153 kB]
Get:21 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libgcc-13-dev amd64 13.3.0-6ubuntu2~24.04 [2681 kB]
Get:22 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 gcc-13-x86-64-linux-gnu amd64 13.3.0-6ubuntu2~24.04 [21.1 MB]
Get:23 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 gcc-13 amd64 13.3.0-6ubuntu2~24.04 [494 kB]
Get:24 http://archive.ubuntu.com/ubuntu noble/main amd64 gcc-x86-64-linux-gnu amd64 4:13.2.0-7ubuntu1 [1212 B]
Get:25 http://archive.ubuntu.com/ubuntu noble/main amd64 gcc amd64 4:13.2.0-7ubuntu1 [5018 B]
Get:26 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libstdc++-13-dev amd64 13.3.0-6ubuntu2~24.04 [2420 kB]
Get:27 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 g++-13-x86-64-linux-gnu amd64 13.3.0-6ubuntu2~24.04 [12.2 MB]
Get:28 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 g++-13 amd64 13.3.0-6ubuntu2~24.04 [16.1 kB]
Get:29 http://archive.ubuntu.com/ubuntu noble/main amd64 g++-x86-64-linux-gnu amd64 4:13.2.0-7ubuntu1 [964 B]
Get:30 http://archive.ubuntu.com/ubuntu noble/main amd64 g++ amd64 4:13.2.0-7ubuntu1 [1100 B]
Get:31 http://archive.ubuntu.com/ubuntu noble/main amd64 make amd64 4.3-4.1build2 [180 kB]
Get:32 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libdpkg-perl all 1.22.6ubuntu6.1 [269 kB]
Get:33 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 bzip2 amd64 1.0.8-5.1build0.1 [34.5 kB]
Get:34 http://archive.ubuntu.com/ubuntu noble/main amd64 lto-disabled-list all 47 [12.4 kB]
Get:35 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 dpkg-dev all 1.22.6ubuntu6.1 [1074 kB]
Get:36 http://archive.ubuntu.com/ubuntu noble/main amd64 build-essential amd64 12.10ubuntu1 [4928 B]
Get:37 http://archive.ubuntu.com/ubuntu noble/main amd64 libfakeroot amd64 1.33-1 [32.4 kB]
Get:38 http://archive.ubuntu.com/ubuntu noble/main amd64 fakeroot amd64 1.33-1 [67.2 kB]
Get:39 http://archive.ubuntu.com/ubuntu noble/main amd64 libalgorithm-diff-perl all 1.201-1 [41.8 kB]
Get:40 http://archive.ubuntu.com/ubuntu noble/main amd64 libalgorithm-diff-xs-perl amd64 0.04-8build3 [11.2 kB]
Get:41 http://archive.ubuntu.com/ubuntu noble/main amd64 libalgorithm-merge-perl all 0.08-5 [11.4 kB]
Get:42 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libheif-plugin-aomdec amd64 1.17.6-1ubuntu4.1 [10.4 kB]
Get:43 http://archive.ubuntu.com/ubuntu noble/main amd64 libde265-0 amd64 1.0.15-1build3 [166 kB]
Get:44 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libheif-plugin-libde265 amd64 1.17.6-1ubuntu4.1 [8176 B]
Get:45 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libheif1 amd64 1.17.6-1ubuntu4.1 [275 kB]
Get:46 http://archive.ubuntu.com/ubuntu noble/main amd64 libxpm4 amd64 1:3.5.17-1build2 [36.5 kB]
Get:47 http://archive.ubuntu.com/ubuntu noble/main amd64 libgd3 amd64 2.3.3-9ubuntu5 [128 kB]
Get:48 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libc-devtools amd64 2.39-0ubuntu8.4 [29.3 kB]
Get:49 http://archive.ubuntu.com/ubuntu noble/main amd64 libfile-fcntllock-perl amd64 0.22-4ubuntu5 [30.7 kB]
Get:50 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libheif-plugin-aomenc amd64 1.17.6-1ubuntu4.1 [14.7 kB]
Get:51 http://archive.ubuntu.com/ubuntu noble/main amd64 manpages-dev all 6.7-2 [2013 kB]
Fetched 69.2 MB in 7min 31s (153 kB/s)
Extracting templates from packages: 100%
Selecting previously unselected package libc-dev-bin.
(Reading database ... 43079 files and directories currently installed.)
Preparing to unpack .../00-libc-dev-bin_2.39-0ubuntu8.4_amd64.deb ...
Unpacking libc-dev-bin (2.39-0ubuntu8.4) ...
Selecting previously unselected package linux-libc-dev:amd64.
Preparing to unpack .../01-linux-libc-dev_6.8.0-57.59_amd64.deb ...
Unpacking linux-libc-dev:amd64 (6.8.0-57.59) ...
Selecting previously unselected package libcrypt-dev:amd64.
Preparing to unpack .../02-libcrypt-dev_1%3a4.4.36-4build1_amd64.deb ...
Unpacking libcrypt-dev:amd64 (1:4.4.36-4build1) ...
Selecting previously unselected package rpcsvc-proto.
Preparing to unpack .../03-rpcsvc-proto_1.4.2-0ubuntu7_amd64.deb ...
Unpacking rpcsvc-proto (1.4.2-0ubuntu7) ...
Selecting previously unselected package libc6-dev:amd64.
Preparing to unpack .../04-libc6-dev_2.39-0ubuntu8.4_amd64.deb ...
Unpacking libc6-dev:amd64 (2.39-0ubuntu8.4) ...
Selecting previously unselected package gcc-13-base:amd64.
Preparing to unpack .../05-gcc-13-base_13.3.0-6ubuntu2~24.04_amd64.deb ...
Unpacking gcc-13-base:amd64 (13.3.0-6ubuntu2~24.04) ...
Selecting previously unselected package libisl23:amd64.
Preparing to unpack .../06-libisl23_0.26-3build1.1_amd64.deb ...
Unpacking libisl23:amd64 (0.26-3build1.1) ...
Selecting previously unselected package libmpc3:amd64.
Preparing to unpack .../07-libmpc3_1.3.1-1build1.1_amd64.deb ...
Unpacking libmpc3:amd64 (1.3.1-1build1.1) ...
Selecting previously unselected package cpp-13-x86-64-linux-gnu.
Preparing to unpack .../08-cpp-13-x86-64-linux-gnu_13.3.0-6ubuntu2~24.04_amd64.deb ...
Unpacking cpp-13-x86-64-linux-gnu (13.3.0-6ubuntu2~24.04) ...
Selecting previously unselected package cpp-13.
Preparing to unpack .../09-cpp-13_13.3.0-6ubuntu2~24.04_amd64.deb ...
Unpacking cpp-13 (13.3.0-6ubuntu2~24.04) ...
Selecting previously unselected package cpp-x86-64-linux-gnu.
Preparing to unpack .../10-cpp-x86-64-linux-gnu_4%3a13.2.0-7ubuntu1_amd64.deb ...
Unpacking cpp-x86-64-linux-gnu (4:13.2.0-7ubuntu1) ...
Selecting previously unselected package cpp.
Preparing to unpack .../11-cpp_4%3a13.2.0-7ubuntu1_amd64.deb ...
Unpacking cpp (4:13.2.0-7ubuntu1) ...
Selecting previously unselected package libcc1-0:amd64.
Preparing to unpack .../12-libcc1-0_14.2.0-4ubuntu2~24.04_amd64.deb ...
Unpacking libcc1-0:amd64 (14.2.0-4ubuntu2~24.04) ...
Selecting previously unselected package libitm1:amd64.
Preparing to unpack .../13-libitm1_14.2.0-4ubuntu2~24.04_amd64.deb ...
Unpacking libitm1:amd64 (14.2.0-4ubuntu2~24.04) ...
Selecting previously unselected package libatomic1:amd64.
Preparing to unpack .../14-libatomic1_14.2.0-4ubuntu2~24.04_amd64.deb ...
Unpacking libatomic1:amd64 (14.2.0-4ubuntu2~24.04) ...
Selecting previously unselected package libasan8:amd64.
Preparing to unpack .../15-libasan8_14.2.0-4ubuntu2~24.04_amd64.deb ...
Unpacking libasan8:amd64 (14.2.0-4ubuntu2~24.04) ...
Selecting previously unselected package liblsan0:amd64.
Preparing to unpack .../16-liblsan0_14.2.0-4ubuntu2~24.04_amd64.deb ...
Unpacking liblsan0:amd64 (14.2.0-4ubuntu2~24.04) ...
Selecting previously unselected package libtsan2:amd64.
Preparing to unpack .../17-libtsan2_14.2.0-4ubuntu2~24.04_amd64.deb ...
Unpacking libtsan2:amd64 (14.2.0-4ubuntu2~24.04) ...
Selecting previously unselected package libubsan1:amd64.
Preparing to unpack .../18-libubsan1_14.2.0-4ubuntu2~24.04_amd64.deb ...
Unpacking libubsan1:amd64 (14.2.0-4ubuntu2~24.04) ...
Selecting previously unselected package libhwasan0:amd64.
Preparing to unpack .../19-libhwasan0_14.2.0-4ubuntu2~24.04_amd64.deb ...
Unpacking libhwasan0:amd64 (14.2.0-4ubuntu2~24.04) ...
Selecting previously unselected package libquadmath0:amd64.
Preparing to unpack .../20-libquadmath0_14.2.0-4ubuntu2~24.04_amd64.deb ...
Unpacking libquadmath0:amd64 (14.2.0-4ubuntu2~24.04) ...
Selecting previously unselected package libgcc-13-dev:amd64.
Preparing to unpack .../21-libgcc-13-dev_13.3.0-6ubuntu2~24.04_amd64.deb ...
Unpacking libgcc-13-dev:amd64 (13.3.0-6ubuntu2~24.04) ...
Selecting previously unselected package gcc-13-x86-64-linux-gnu.
Preparing to unpack .../22-gcc-13-x86-64-linux-gnu_13.3.0-6ubuntu2~24.04_amd64.deb ...
Unpacking gcc-13-x86-64-linux-gnu (13.3.0-6ubuntu2~24.04) ...
Selecting previously unselected package gcc-13.
Preparing to unpack .../23-gcc-13_13.3.0-6ubuntu2~24.04_amd64.deb ...
Unpacking gcc-13 (13.3.0-6ubuntu2~24.04) ...
Selecting previously unselected package gcc-x86-64-linux-gnu.
Preparing to unpack .../24-gcc-x86-64-linux-gnu_4%3a13.2.0-7ubuntu1_amd64.deb ...
Unpacking gcc-x86-64-linux-gnu (4:13.2.0-7ubuntu1) ...
Selecting previously unselected package gcc.
Preparing to unpack .../25-gcc_4%3a13.2.0-7ubuntu1_amd64.deb ...
Unpacking gcc (4:13.2.0-7ubuntu1) ...
Selecting previously unselected package libstdc++-13-dev:amd64.
Preparing to unpack .../26-libstdc++-13-dev_13.3.0-6ubuntu2~24.04_amd64.deb ...
Unpacking libstdc++-13-dev:amd64 (13.3.0-6ubuntu2~24.04) ...
Selecting previously unselected package g++-13-x86-64-linux-gnu.
Preparing to unpack .../27-g++-13-x86-64-linux-gnu_13.3.0-6ubuntu2~24.04_amd64.deb ...
Unpacking g++-13-x86-64-linux-gnu (13.3.0-6ubuntu2~24.04) ...
Selecting previously unselected package g++-13.
Preparing to unpack .../28-g++-13_13.3.0-6ubuntu2~24.04_amd64.deb ...
Unpacking g++-13 (13.3.0-6ubuntu2~24.04) ...
Selecting previously unselected package g++-x86-64-linux-gnu.
Preparing to unpack .../29-g++-x86-64-linux-gnu_4%3a13.2.0-7ubuntu1_amd64.deb ...
Unpacking g++-x86-64-linux-gnu (4:13.2.0-7ubuntu1) ...
Selecting previously unselected package g++.
Preparing to unpack .../30-g++_4%3a13.2.0-7ubuntu1_amd64.deb ...
Unpacking g++ (4:13.2.0-7ubuntu1) ...
Selecting previously unselected package make.
Preparing to unpack .../31-make_4.3-4.1build2_amd64.deb ...
Unpacking make (4.3-4.1build2) ...
Selecting previously unselected package libdpkg-perl.
Preparing to unpack .../32-libdpkg-perl_1.22.6ubuntu6.1_all.deb ...
Unpacking libdpkg-perl (1.22.6ubuntu6.1) ...
Selecting previously unselected package bzip2.
Preparing to unpack .../33-bzip2_1.0.8-5.1build0.1_amd64.deb ...
Unpacking bzip2 (1.0.8-5.1build0.1) ...
Selecting previously unselected package lto-disabled-list.
Preparing to unpack .../34-lto-disabled-list_47_all.deb ...
Unpacking lto-disabled-list (47) ...
Selecting previously unselected package dpkg-dev.
Preparing to unpack .../35-dpkg-dev_1.22.6ubuntu6.1_all.deb ...
Unpacking dpkg-dev (1.22.6ubuntu6.1) ...
Selecting previously unselected package build-essential.
Preparing to unpack .../36-build-essential_12.10ubuntu1_amd64.deb ...
Unpacking build-essential (12.10ubuntu1) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../37-libfakeroot_1.33-1_amd64.deb ...
Unpacking libfakeroot:amd64 (1.33-1) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../38-fakeroot_1.33-1_amd64.deb ...
Unpacking fakeroot (1.33-1) ...
Selecting previously unselected package libalgorithm-diff-perl.
Preparing to unpack .../39-libalgorithm-diff-perl_1.201-1_all.deb ...
Unpacking libalgorithm-diff-perl (1.201-1) ...
Selecting previously unselected package libalgorithm-diff-xs-perl:amd64.
Preparing to unpack .../40-libalgorithm-diff-xs-perl_0.04-8build3_amd64.deb ...
Unpacking libalgorithm-diff-xs-perl:amd64 (0.04-8build3) ...
Selecting previously unselected package libalgorithm-merge-perl.
Preparing to unpack .../41-libalgorithm-merge-perl_0.08-5_all.deb ...
Unpacking libalgorithm-merge-perl (0.08-5) ...
Selecting previously unselected package libheif-plugin-aomdec:amd64.
Preparing to unpack .../42-libheif-plugin-aomdec_1.17.6-1ubuntu4.1_amd64.deb ...
Unpacking libheif-plugin-aomdec:amd64 (1.17.6-1ubuntu4.1) ...
Selecting previously unselected package libde265-0:amd64.
Preparing to unpack .../43-libde265-0_1.0.15-1build3_amd64.deb ...
Unpacking libde265-0:amd64 (1.0.15-1build3) ...
Selecting previously unselected package libheif-plugin-libde265:amd64.
Preparing to unpack .../44-libheif-plugin-libde265_1.17.6-1ubuntu4.1_amd64.deb ...
Unpacking libheif-plugin-libde265:amd64 (1.17.6-1ubuntu4.1) ...
Selecting previously unselected package libheif1:amd64.
Preparing to unpack .../45-libheif1_1.17.6-1ubuntu4.1_amd64.deb ...
Unpacking libheif1:amd64 (1.17.6-1ubuntu4.1) ...
Selecting previously unselected package libxpm4:amd64.
Preparing to unpack .../46-libxpm4_1%3a3.5.17-1build2_amd64.deb ...
Unpacking libxpm4:amd64 (1:3.5.17-1build2) ...
Selecting previously unselected package libgd3:amd64.
Preparing to unpack .../47-libgd3_2.3.3-9ubuntu5_amd64.deb ...
Unpacking libgd3:amd64 (2.3.3-9ubuntu5) ...
Selecting previously unselected package libc-devtools.
Preparing to unpack .../48-libc-devtools_2.39-0ubuntu8.4_amd64.deb ...
Unpacking libc-devtools (2.39-0ubuntu8.4) ...
Selecting previously unselected package libfile-fcntllock-perl.
Preparing to unpack .../49-libfile-fcntllock-perl_0.22-4ubuntu5_amd64.deb ...
Unpacking libfile-fcntllock-perl (0.22-4ubuntu5) ...
Selecting previously unselected package libheif-plugin-aomenc:amd64.
Preparing to unpack .../50-libheif-plugin-aomenc_1.17.6-1ubuntu4.1_amd64.deb ...
Unpacking libheif-plugin-aomenc:amd64 (1.17.6-1ubuntu4.1) ...
Selecting previously unselected package manpages-dev.
Preparing to unpack .../51-manpages-dev_6.7-2_all.deb ...
Unpacking manpages-dev (6.7-2) ...
Setting up manpages-dev (6.7-2) ...
Setting up lto-disabled-list (47) ...
Setting up libxpm4:amd64 (1:3.5.17-1build2) ...
Setting up libfile-fcntllock-perl (0.22-4ubuntu5) ...
Setting up libalgorithm-diff-perl (1.201-1) ...
Setting up linux-libc-dev:amd64 (6.8.0-57.59) ...
Setting up bzip2 (1.0.8-5.1build0.1) ...
Setting up libfakeroot:amd64 (1.33-1) ...
Setting up fakeroot (1.33-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up rpcsvc-proto (1.4.2-0ubuntu7) ...
Setting up gcc-13-base:amd64 (13.3.0-6ubuntu2~24.04) ...
Setting up make (4.3-4.1build2) ...
Setting up libquadmath0:amd64 (14.2.0-4ubuntu2~24.04) ...
Setting up libmpc3:amd64 (1.3.1-1build1.1) ...
Setting up libatomic1:amd64 (14.2.0-4ubuntu2~24.04) ...
Setting up libdpkg-perl (1.22.6ubuntu6.1) ...
Setting up libubsan1:amd64 (14.2.0-4ubuntu2~24.04) ...
Setting up libhwasan0:amd64 (14.2.0-4ubuntu2~24.04) ...
Setting up libcrypt-dev:amd64 (1:4.4.36-4build1) ...
Setting up libasan8:amd64 (14.2.0-4ubuntu2~24.04) ...
Setting up libtsan2:amd64 (14.2.0-4ubuntu2~24.04) ...
Setting up libisl23:amd64 (0.26-3build1.1) ...
Setting up libde265-0:amd64 (1.0.15-1build3) ...
Setting up libc-dev-bin (2.39-0ubuntu8.4) ...
Setting up libalgorithm-diff-xs-perl:amd64 (0.04-8build3) ...
Setting up libcc1-0:amd64 (14.2.0-4ubuntu2~24.04) ...
Setting up liblsan0:amd64 (14.2.0-4ubuntu2~24.04) ...
Setting up libitm1:amd64 (14.2.0-4ubuntu2~24.04) ...
Setting up libalgorithm-merge-perl (0.08-5) ...
Setting up cpp-13-x86-64-linux-gnu (13.3.0-6ubuntu2~24.04) ...
Setting up dpkg-dev (1.22.6ubuntu6.1) ...
Setting up libgcc-13-dev:amd64 (13.3.0-6ubuntu2~24.04) ...
Setting up libc6-dev:amd64 (2.39-0ubuntu8.4) ...
Setting up libstdc++-13-dev:amd64 (13.3.0-6ubuntu2~24.04) ...
Setting up cpp-x86-64-linux-gnu (4:13.2.0-7ubuntu1) ...
Setting up cpp-13 (13.3.0-6ubuntu2~24.04) ...
Setting up gcc-13-x86-64-linux-gnu (13.3.0-6ubuntu2~24.04) ...
Setting up gcc-13 (13.3.0-6ubuntu2~24.04) ...
Setting up cpp (4:13.2.0-7ubuntu1) ...
Setting up g++-13-x86-64-linux-gnu (13.3.0-6ubuntu2~24.04) ...
Setting up gcc-x86-64-linux-gnu (4:13.2.0-7ubuntu1) ...
Setting up gcc (4:13.2.0-7ubuntu1) ...
Setting up g++-x86-64-linux-gnu (4:13.2.0-7ubuntu1) ...
Setting up g++-13 (13.3.0-6ubuntu2~24.04) ...
Setting up g++ (4:13.2.0-7ubuntu1) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up build-essential (12.10ubuntu1) ...
Setting up libheif1:amd64 (1.17.6-1ubuntu4.1) ...
Setting up libgd3:amd64 (2.3.3-9ubuntu5) ...
Setting up libc-devtools (2.39-0ubuntu8.4) ...
Setting up libheif-plugin-aomdec:amd64 (1.17.6-1ubuntu4.1) ...
Setting up libheif-plugin-libde265:amd64 (1.17.6-1ubuntu4.1) ...
Setting up libheif-plugin-aomenc:amd64 (1.17.6-1ubuntu4.1) ...
Processing triggers for libc-bin (2.39-0ubuntu8.4) ...
Processing triggers for man-db (2.12.0-4build2) ...
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$ cargo build
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling crossbeam-epoch v0.9.18
   Compiling crossbeam-deque v0.8.5
   Compiling rayon v1.10.0
   Compiling xor_cryptor v1.2.3
   Compiling rust_proj v0.1.0 (/mnt/c/Windows/system32/fixme1)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 7.43s
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$ cargo run
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling crossbeam-epoch v0.9.18
   Compiling crossbeam-deque v0.8.5
   Compiling rayon v1.10.0
   Compiling xor_cryptor v1.2.3
   Compiling rust_proj v0.1.0 (/mnt/c/Windows/system32/fixme1)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 5.95s
     Running `/mnt/c/Windows/system32/fixme1/target/debug/rust_proj`
picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}:?
````` 








# 05  Rust fixme 2
# DESC

The Rust saga continues? I ask you, can I borrow that, pleeeeeaaaasseeeee?Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/babfbee79718a6363826ba86300173ffde6d81577e9dd07d4130c53a7eecf6c3/fixme2.tar.gz).
# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$ wget https://challenge-files.picoctf.net/c_verbal_sleep/babfbee79718a6363826ba86300173ffde6d81577e9dd07d4130c53a7eecf6c3/fixme2.tar.gz
--2025-04-15 11:27:01--  https://challenge-files.picoctf.net/c_verbal_sleep/babfbee79718a6363826ba86300173ffde6d81577e9dd07d4130c53a7eecf6c3/fixme2.tar.gz
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 18.238.132.88, 18.238.132.49, 18.238.132.115, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|18.238.132.88|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1585 (1.5K) [application/octet-stream]
Saving to: ‘fixme2.tar.gz’

fixme2.tar.gz                 100%[=================================================>]   1.55K  --.-KB/s    in 0s

2025-04-15 11:27:02 (175 MB/s) - ‘fixme2.tar.gz’ saved [1585/1585]

lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$ ls
fixme2.tar.gz  main.rs
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$  cd fixme2
-bash: cd: fixme2: No such file or directory
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$ cd fixme2.tar.gz
-bash: cd: fixme2.tar.gz: Not a directory
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$ cd fixme2.tar.gz
-bash: cd: fixme2.tar.gz: Not a directory
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$ tar -xvzf fixme2.tar.gz
fixme2/
fixme2/Cargo.toml
fixme2/Cargo.lock
fixme2/src/
fixme2/src/main.rs
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$ cd fixme2.tar.gz
-bash: cd: fixme2.tar.gz: Not a directory
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src$ cd fixme2
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2$ cargo build
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling either v1.13.0
   Compiling crossbeam-epoch v0.9.18
   Compiling crossbeam-deque v0.8.5
   Compiling rayon v1.10.0
   Compiling xor_cryptor v1.2.3
   Compiling rust_proj v0.1.0 (/mnt/c/Windows/system32/fixme1/src/fixme2)
error[E0596]: cannot borrow `*borrowed_string` as mutable, as it is behind a `&` reference
 --> src/main.rs:9:5
  |
9 |     borrowed_string.push_str("PARTY FOUL! Here is your flag: ");
  |     ^^^^^^^^^^^^^^^ `borrowed_string` is a `&` reference, so the data it refers to cannot be borrowed as mutable
  |
help: consider changing this to be a mutable reference
  |
3 | fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &mut String){ // How do we pass values to a function that we want to change?
  |                                                        +++

error[E0596]: cannot borrow `*borrowed_string` as mutable, as it is behind a `&` reference
  --> src/main.rs:20:5
   |
20 |     borrowed_string.push_str(&String::from_utf8_lossy(&decrypted_buffer));
   |     ^^^^^^^^^^^^^^^ `borrowed_string` is a `&` reference, so the data it refers to cannot be borrowed as mutable
   |
help: consider changing this to be a mutable reference
   |
3  | fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &mut String){ // How do we pass values to a function that we want to change?
   |                                                        +++

For more information about this error, try `rustc --explain E0596`.
error: could not compile `rust_proj` (bin "rust_proj") due to 2 previous errors
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2$ cd src
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src$ nano main.rc
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src$ nano main.rs
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src$ cargo build
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling crossbeam-epoch v0.9.18
   Compiling crossbeam-deque v0.8.5
   Compiling rayon v1.10.0
   Compiling xor_cryptor v1.2.3
   Compiling rust_proj v0.1.0 (/mnt/c/Windows/system32/fixme1/src/fixme2)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 7.24s
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src$ cargo run
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.22s
     Running `/mnt/c/Windows/system32/fixme1/src/fixme2/target/debug/rust_proj`
Using memory unsafe languages is a: PARTY FOUL! Here is your flag: picoCTF{4r3_y0u_h4v1n5_fun_y31?}
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src$
````` 







# 0 Rust fixme 3
# DESC
#### Description

Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/dcdaf491b35c1d0f5075e9583edbbb7aaea1dffb6ad32bc000e4d87b5200ff7b/fixme3.tar.gz).

# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src$ wget https://challenge-files.picoctf.net/c_verbal_sleep/dcdaf491b35c1d0f5075e9583edbbb7aaea1dffb6ad32bc000e4d87b5200ff7b/fixme3.tar.gz
--2025-04-15 11:36:01--  https://challenge-files.picoctf.net/c_verbal_sleep/dcdaf491b35c1d0f5075e9583edbbb7aaea1dffb6ad32bc000e4d87b5200ff7b/fixme3.tar.gz
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 18.238.132.49, 18.238.132.115, 18.238.132.88, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|18.238.132.49|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1776 (1.7K) [application/octet-stream]
Saving to: ‘fixme3.tar.gz’

fixme3.tar.gz                 100%[=================================================>]   1.73K  --.-KB/s    in 0s

2025-04-15 11:36:03 (264 MB/s) - ‘fixme3.tar.gz’ saved [1776/1776]

lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src$ tar -xvzf fixme3.tar.gz
fixme3/
fixme3/Cargo.toml
fixme3/Cargo.lock
fixme3/src/
fixme3/src/main.rs
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src$ cd fixme3
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src/fixme3$ cargo build
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling either v1.13.0
   Compiling crossbeam-epoch v0.9.18
   Compiling crossbeam-deque v0.8.5
   Compiling rayon v1.10.0
   Compiling xor_cryptor v1.2.3
   Compiling rust_proj v0.1.0 (/mnt/c/Windows/system32/fixme1/src/fixme2/src/fixme3)
error[E0133]: call to unsafe function `std::slice::from_raw_parts` is unsafe and requires unsafe function or block
  --> src/main.rs:31:31
   |
31 |         let decrypted_slice = std::slice::from_raw_parts(decrypted_ptr, decrypted_len);
   |                               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ call to unsafe function
   |
   = note: consult the function's documentation for information on how to avoid undefined behavior

For more information about this error, try `rustc --explain E0133`.
error: could not compile `rust_proj` (bin "rust_proj") due to 1 previous error
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src/fixme3$ cd rsc
-bash: cd: rsc: No such file or directory
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src/fixme3$ cd src
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src/fixme3/src$ nano main.rs
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src/fixme3/src$ cargo build
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling crossbeam-epoch v0.9.18
   Compiling crossbeam-deque v0.8.5
   Compiling rayon v1.10.0
   Compiling xor_cryptor v1.2.3
   Compiling rust_proj v0.1.0 (/mnt/c/Windows/system32/fixme1/src/fixme2/src/fixme3)
error: unexpected closing delimiter: `}`
  --> src/main.rs:36:1
   |
3  | fn decrypt(encrypted_buffer: Vec<u8>, borrowed_string: &mut String) {
   |                                                                     - this delimiter might not be properly closed...
...
34 |      }
   |      - ...as it matches this but it has different indentation
35 |     println!("{}", borrowed_string);
36 | }
   | ^ unexpected closing delimiter

error: could not compile `rust_proj` (bin "rust_proj") due to 1 previous error
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src/fixme3/src$ nano main.rs
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src/fixme3/src$ cargo build
   Compiling rust_proj v0.1.0 (/mnt/c/Windows/system32/fixme1/src/fixme2/src/fixme3)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 3.77s
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src/fixme3/src$ cargo run
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.21s
     Running `/mnt/c/Windows/system32/fixme1/src/fixme2/src/fixme3/target/debug/rust_proj`
Using memory unsafe languages is a: PARTY FOUL! Here is your flag: picoCTF{n0w_y0uv3_f1x3d_1h3m_411}
lixin@DELTUS:/mnt/c/Windows/system32/fixme1/src/fixme2/src/fixme3/src$
````` 







# 07  dont-you-love-banners
# DESC


# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Windows/system32$ nc tethys.picoctf.net 55101
SSH-2.0-OpenSSH_7.6p1 My_Passw@rd_@1234
^Z
[1]+  Stopped                 nc tethys.picoctf.net 55101
lixin@DELTUS:/mnt/c/Windows/system32$  nc tethys.picoctf.net 57140
*************************************
**************WELCOME****************
*************************************

what is the password?
My_Passw@rd_@1234
What is the top cyber security conference in the world?
defcon
the first hacker ever was known for phreaking(making free phone calls), who was it?
jhon Draper
Lol, good try, try again and good luck

What is the top cyber security conference in the world?
defcon
the first hacker ever was known for phreaking(making free phone calls), who was it?
Jhon Draper
Lol, good try, try again and good luck

What is the top cyber security conference in the world?
defcon
the first hacker ever was known for phreaking(making free phone calls), who was it?
John Draper
player@challenge:~$ ls
ls
banner  text
player@challenge:~$ cat banner
cat banner
*************************************
**************WELCOME****************
*************************************
player@challenge:~$ cat text
cat text
keep digging
player@challenge:~$ pwd
pwd
/home/player
player@challenge:~$ cd /root
cd /root
player@challenge:/root$ ls
ls
flag.txt  script.py
player@challenge:/root$ cat flag.txt
cat flag.txt
cat: flag.txt: Permission denied
player@challenge:/root$ cat script.py
cat script.py

import os
import pty

incorrect_ans_reply = "Lol, good try, try again and good luck\n"

if __name__ == "__main__":
    try:
      with open("/home/player/banner", "r") as f:
        print(f.read())
    except:
      print("*********************************************")
      print("***************DEFAULT BANNER****************")
      print("*Please supply banner in /home/player/banner*")
      print("*********************************************")

try:
    request = input("what is the password? \n").upper()
    while request:
        if request == 'MY_PASSW@RD_@1234':
            text = input("What is the top cyber security conference in the world?\n").upper()
            if text == 'DEFCON' or text == 'DEF CON':
                output = input(
                    "the first hacker ever was known for phreaking(making free phone calls), who was it?\n").upper()
                if output == 'JOHN DRAPER' or output == 'JOHN THOMAS DRAPER' or output == 'JOHN' or output== 'DRAPER':
                    scmd = 'su - player'
                    pty.spawn(scmd.split(' '))

                else:
                    print(incorrect_ans_reply)
            else:
                print(incorrect_ans_reply)
        else:
            print(incorrect_ans_reply)
            break

except:
    KeyboardInterrupt

player@challenge:/root$ ls
ls
flag.txt  script.py
player@challenge:/root$ cd ..
cd ..
player@challenge:/$ ls
ls
bin   challenge  etc   lib    media  opt   root  sbin  sys  usr
boot  dev        home  lib64  mnt    proc  run   srv   tmp  var
player@challenge:/$ cd/home/player
cd/home/player
-su: cd/home/player: No such file or directory
player@challenge:/$ cd /home/player
cd /home/player
player@challenge:~$ ls
ls
banner  text
player@challenge:~$ rm banner
rm banner
player@challenge:~$ ls
ls
text
player@challenge:~$ ln -s /root/flag.txt
ln -s /root/flag.txt
player@challenge:~$ ln -s /root/flag.txt /home/player/banner
ln -s /root/flag.txt /home/player/banner
player@challenge:~$ ls
ls
cbanner  flag.txt  text
player@challenge:~$ at banner
cat banner
cat: banner: Permission denied
player@challenge:~$ ^Z
[2]+  Stopped                 nc tethys.picoctf.net 57140
lixin@DELTUS:/mnt/c/Windows/system32$ tethys.picoctf.net 57140
tethys.picoctf.net: command not found
lixin@DELTUS:/mnt/c/Windows/system32$ nc tethys.picoctf.net 57140
picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_a0e119d4}

what is the password?
````` 






# 08  flag_shop
# DESC
There's a flag shop selling stuff, can you buy a flag? [Source](https://jupiter.challenges.picoctf.org/static/64e724ad327f83ad833d9c6baa072b1f/store.c). Connect with `nc jupiter.challenges.picoctf.org 4906`.

# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Windows/system32$  nc jupiter.challenges.picoctf.org 4906
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
1



 Balance: 1100


Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
2

The final cost is: 1800
Not enough funds to complete purchase
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one1

Not enough funds for transaction


Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one 100000000000000000000
Welcome to the flag exchange
We sell flags

3. Check Account Balance

4. Buy Flags

5. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
100000000000000000000
Welcome to the flag exchange
We sell flags

3. Check Account Balance

4. Buy Flags

5. Exit

 Enter a menu selection
2
lixin@DELTUS:/mnt/c/Windows/system32$ nc tethys.picoctf.net 57140
lixin@DELTUS:/mnt/c/Windows/system32$ cd ..
lixin@DELTUS:/mnt/c/Windows$ nc jupiter.challenges.picoctf.org 4906
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
1



 Balance: 1100


Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
2

The final cost is: 1800
Not enough funds to complete purchase
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
^Z
[4]+  Stopped                 nc jupiter.challenges.picoctf.org 4906
lixin@DELTUS:/mnt/c/Windows$ nc jupiter.challenges.picoctf.org 4906
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
1



 Balance: 1100


Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
1

The final cost is: 900

Your current balance after transaction: 200

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one1

Not enough funds for transaction


Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one10000000000000000
Welcome to the flag exchange
We sell flags

3. Check Account Balance

4. Buy Flags

5. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
10000000000000000

The final cost is: -494665728

Your current balance after transaction: 494665928

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
 2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one1
YOUR FLAG IS: picoCTF{m0n3y_bag5_9c5fac9b}
Welcome to the flag exchange
We sell flags

3. Check Account Balance

4. Buy Flags

5. Exit

 Enter a menu selection

````` 





# 09 SansAlpha
# DESC
The Multiverse is within your grasp! Unfortunately, the server that contains the secrets of the multiverse is in a universe where keyboards only have numbers and (most) symbols.`ssh -p 62894 ctf-player@mimas.picoctf.net`Use password: `84b12bae`


# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Windows$ ssh -p 62894 ctf-player@mimas.picoctf.net
ctf-player@mimas.picoctf.net's password:
Permission denied, please try again.
ctf-player@mimas.picoctf.net's password:
Permission denied, please try again.
ctf-player@mimas.picoctf.net's password:
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.5.0-1016-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.
Last login: Tue Apr 15 18:09:44 2025 from 127.0.0.1
SansAlpha$ /*/???[!_]64 */????.*
cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV9iMGQ1ZTg1NX0=

SansAlpha$ exit
Connection to mimas.picoctf.net closed.
lixin@DELTUS:/mnt/c/Windows$ echo cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV9iMGQ1ZTg1NX0=
cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV9iMGQ1ZTg1NX0=
lixin@DELTUS:/mnt/c/Windows$ echo cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV9iMGQ1ZTg1NX0= | base64 -d
return 0 picoCTF{7h15_mu171v3r53_15_m4dn355_b0d5e855}
````` 






# 10  Specialer
# DESC
Reception of Special has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer.`ssh -p 60922 ctf-player@saturn.picoctf.net`. The password is `af86add3`

# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Windows$ ssh -p 60922 ctf-player@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:60922 ([13.59.203.175]:60922)' can't be established.
ED25519 key fingerprint is SHA256:lMXKIC17ONzyUJx7ZYBY5VSwoxCz20uq5/Nm+IhXKew.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? y
Please type 'yes', 'no' or the fingerprint: y
Please type 'yes', 'no' or the fingerprint: yes
Warning: Permanently added '[saturn.picoctf.net]:60922' (ED25519) to the list of known hosts.
ctf-player@saturn.picoctf.net's password:
Specialer$ echo "$(<kazam.txt)"
-bash: kazam.txt: No such file or directory

Specialer$ cd abra
Specialer$ pwd
/home/ctf-player/abra
Specialer$ echo *
cadabra.txt cadaniel.txt
Specialer$ "$(<cadabra.txt)"
-bash: Nothing up my sleeve!: command not found
Specialer$ "$(<cadaniel.txt)"
-bash: Yes, I did it! I really did it! I'm a true wizard!: command not found
Specialer$ cd ..
Specialer$ cd ala
Specialer$ echo *
kazam.txt mode.txt
Specialer$ "$(<kazam.txt)"
-bash: return 0 picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_a8567b6f}: command not found
Specialer$ Connection to saturn.picoctf.net closed by remote host.
Connection to saturn.picoctf.net closed.
lixin@DELTUS:/mnt/c/Windows$
````` 






