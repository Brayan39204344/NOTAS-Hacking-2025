# 01 m00nwalk

# DESC

Decode this [message](https://jupiter.challenges.picoctf.org/static/fc1edf07742e98a480c6aff7d2546107/message.wav) from the moon.
# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Windows/system32$ wget https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery
--2025-04-28 12:43:11--  https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 202940 (198K) [application/octet-stream]
Saving to: ‘mystery’

mystery                       100%[=================================================>] 198.18K   153KB/s    in 1.3s

2025-04-28 12:43:14 (153 KB/s) - ‘mystery’ saved [202940/202940]

lixin@DELTUS:/mnt/c/Windows/system32$ qsstv
ALSA lib confmisc.c:855:(parse_card) cannot find card '0'
ALSA lib conf.c:5204:(_snd_config_evaluate) function snd_func_card_inum returned error: No such file or directory
ALSA lib confmisc.c:422:(snd_func_concat) error evaluating strings
ALSA lib conf.c:5204:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1342:(snd_func_refer) error evaluating name
ALSA lib conf.c:5204:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:5727:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2721:(snd_pcm_open_noupdate) Unknown PCM default
pavucontrol
^C
lixin@DELTUS:/mnt/c/Windows/system32$ qsstv
ALSA lib confmisc.c:855:(parse_card) cannot find card '0'
ALSA lib conf.c:5204:(_snd_config_evaluate) function snd_func_card_inum returned error: No such file or directory
ALSA lib confmisc.c:422:(snd_func_concat) error evaluating strings
ALSA lib conf.c:5204:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1342:(snd_func_refer) error evaluating name
ALSA lib conf.c:5204:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:5727:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2721:(snd_pcm_open_noupdate) Unknown PCM default
^C
lixin@DELTUS:/mnt/c/Windows/system32$ pactl load-module module-null-sink sink_name=virtual-cable
Command 'pactl' not found, but can be installed with:
sudo apt install pulseaudio-utils
lixin@DELTUS:/mnt/c/Windows/system32$ paplay -d virtual-cable message.wav
Command 'paplay' not found, but can be installed with:
sudo apt install pulseaudio-utils
lixin@DELTUS:/mnt/c/Windows/system32$ sudo apt install pulseaudio-utils
[sudo] password for lixin:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Suggested packages:
  avahi-daemon pulseaudio
The following NEW packages will be installed:
  pulseaudio-utils
0 upgraded, 1 newly installed, 0 to remove and 89 not upgraded.
Need to get 73.5 kB of archives.
After this operation, 340 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 pulseaudio-utils amd64 1:16.1+dfsg1-2ubuntu10.1 [73.5 kB]
Fetched 73.5 kB in 2s (33.5 kB/s)
Selecting previously unselected package pulseaudio-utils.
(Reading database ... 51985 files and directories currently installed.)
Preparing to unpack .../pulseaudio-utils_1%3a16.1+dfsg1-2ubuntu10.1_amd64.deb ...
Unpacking pulseaudio-utils (1:16.1+dfsg1-2ubuntu10.1) ...
Setting up pulseaudio-utils (1:16.1+dfsg1-2ubuntu10.1) ...
Processing triggers for man-db (2.12.0-4build2) ...
lixin@DELTUS:/mnt/c/Windows/system32$ paplay -d virtual-cable message.wav
open(): No such file or directory
lixin@DELTUS:/mnt/c/Windows/system32$ wget https://jupiter.challenges.picoctf.org/static/fc1edf07742e98a480c6aff7d2546107/message.wav
--2025-04-28 12:50:02--  https://jupiter.challenges.picoctf.org/static/fc1edf07742e98a480c6aff7d2546107/message.wav
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11066998 (11M) [application/octet-stream]
Saving to: ‘message.wav’

message.wav                                          100%[=====================================================================================================================>]  10.55M   305KB/s    in 61s

2025-04-28 12:51:06 (177 KB/s) - ‘message.wav’ saved [11066998/11066998]

lixin@DELTUS:/mnt/c/Windows/system32$ paplay -d virtual-cable message.wav
Stream error: No such entity
lixin@DELTUS:/mnt/c/Windows/system32$ sudo apt install pngcheck
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  pngcheck
0 upgraded, 1 newly installed, 0 to remove and 89 not upgraded.
Need to get 66.1 kB of archives.
After this operation, 202 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble/universe amd64 pngcheck amd64 3.0.3-3 [66.1 kB]
Fetched 66.1 kB in 1s (68.3 kB/s)
Selecting previously unselected package pngcheck.
(Reading database ... 52020 files and directories currently installed.)
Preparing to unpack .../pngcheck_3.0.3-3_amd64.deb ...
Unpacking pngcheck (3.0.3-3) ...
Setting up pngcheck (3.0.3-3) ...
Processing triggers for man-db (2.12.0-4build2) ...
lixin@DELTUS:/mnt/c/Windows/system32$ sstv -d message.wav -o result.png
Traceback (most recent call last):
  File "/usr/local/bin/sstv", line 33, in <module>
    sys.exit(load_entry_point('sstv==0.1', 'console_scripts', 'sstv')())
             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/bin/sstv", line 25, in importlib_load_entry_point
    return next(matches).load()
           ^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.12/importlib/metadata/__init__.py", line 205, in load
    module = import_module(match.group('module'))
             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.12/importlib/__init__.py", line 90, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "<frozen importlib._bootstrap>", line 1387, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1360, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1310, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 488, in _call_with_frames_removed
  File "<frozen importlib._bootstrap>", line 1387, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1360, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1331, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 935, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 995, in exec_module
  File "<frozen importlib._bootstrap>", line 488, in _call_with_frames_removed
  File "/usr/local/lib/python3.12/dist-packages/sstv-0.1-py3.12.egg/sstv/__init__.py", line 3, in <module>
  File "/usr/local/lib/python3.12/dist-packages/sstv-0.1-py3.12.egg/sstv/command.py", line 6, in <module>
ModuleNotFoundError: No module named 'PIL'
lixin@DELTUS:/mnt/c/Windows/system32$ python -m sstv -d message.wav -o result.png
Command 'python' not found, did you mean:
  command 'python3' from deb python3
  command 'python' from deb python-is-python3
lixin@DELTUS:/mnt/c/Windows/system32$ cd /mnt/c/Users/39204/sstv
source myenv/bin/activate
pip install sstv pillow  # por si acaso
python -m sstv -d message.wav -o result.png
ERROR: Could not find a version that satisfies the requirement sstv (from versions: none)
ERROR: No matching distribution found for sstv
Traceback (most recent call last):
  File "<frozen runpy>", line 189, in _run_module_as_main
  File "<frozen runpy>", line 148, in _get_module_details
  File "<frozen runpy>", line 112, in _get_module_details
  File "/mnt/c/Users/39204/sstv/sstv/__init__.py", line 3, in <module>
    from .command import SSTVCommand
  File "/mnt/c/Users/39204/sstv/sstv/command.py", line 7, in <module>
    from soundfile import available_formats as available_audio_formats
ModuleNotFoundError: No module named 'soundfile'
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ pip install soundfile
Collecting soundfile
  Downloading soundfile-0.13.1-py2.py3-none-manylinux_2_28_x86_64.whl.metadata (16 kB)
Collecting cffi>=1.0 (from soundfile)
  Downloading cffi-1.17.1-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (1.5 kB)
Collecting numpy (from soundfile)
  Downloading numpy-2.2.5-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (62 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 62.0/62.0 kB 865.9 kB/s eta 0:00:00
Collecting pycparser (from cffi>=1.0->soundfile)
  Downloading pycparser-2.22-py3-none-any.whl.metadata (943 bytes)
Downloading soundfile-0.13.1-py2.py3-none-manylinux_2_28_x86_64.whl (1.3 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.3/1.3 MB 360.2 kB/s eta 0:00:00
Downloading cffi-1.17.1-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (479 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 479.4/479.4 kB 148.1 kB/s eta 0:00:00
Downloading numpy-2.2.5-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (16.1 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 16.1/16.1 MB 207.9 kB/s eta 0:00:00
Downloading pycparser-2.22-py3-none-any.whl (117 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 117.6/117.6 kB 393.1 kB/s eta 0:00:00
Installing collected packages: pycparser, numpy, cffi, soundfile


Successfully installed cffi-1.17.1 numpy-2.2.5 pycparser-2.22 soundfile-0.13.1
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ python -m sstv -d message.wav -o result.png
Traceback (most recent call last):
  File "<frozen runpy>", line 189, in _run_module_as_main
  File "<frozen runpy>", line 148, in _get_module_details
  File "<frozen runpy>", line 112, in _get_module_details
  File "/mnt/c/Users/39204/sstv/sstv/__init__.py", line 3, in <module>
    from .command import SSTVCommand
  File "/mnt/c/Users/39204/sstv/sstv/command.py", line 10, in <module>
    from .decode import SSTVDecoder
  File "/mnt/c/Users/39204/sstv/sstv/decode.py", line 6, in <module>
    from scipy.signal.windows import hann
ModuleNotFoundError: No module named 'scipy'
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ pip install scipy
Collecting scipy
  Downloading scipy-1.15.2-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (61 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 62.0/62.0 kB 206.3 kB/s eta 0:00:00
Requirement already satisfied: numpy<2.5,>=1.23.5 in ./myenv/lib/python3.12/site-packages (from scipy) (2.2.5)
Downloading scipy-1.15.2-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (37.3 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 37.3/37.3 MB 559.1 kB/s eta 0:00:00
Installing collected packages: scipy
Successfully installed scipy-1.15.2
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ python -m sstv -d message.wav -o result.png
usage: sstv [-h] [-d AUDIO_FILE] [-o OUTPUT_FILE] [-s SKIP] [-V] [--list-modes] [--list-audio-formats] [--list-image-formats]
sstv: error: argument -d/--decode: can't open 'message.wav': [Errno 2] No such file or directory: 'message.wav'
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ python -m sstv -d /mnt/c/Windows/System32/message.wav -o result.png
[sstv] Searching for calibration header... Found!
[sstv] Detected SSTV mode Scottie 1
[sstv] Decoding image...                                                                                [####################################################################################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ ^[[200~C:\Users\39204\sstv\result.png
^[[201~C:Users39204sstvresult.png: command not found
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ C:\Users\39204\sstv\result.png
C:Users39204sstvresult.png: command not found
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ cp result.png /mnt/c/Users/39204/Desktop/
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$



picoCTF{beep_boop_im_in_space}
````` 
#  02 WhitePages
# DESC

I stopped using YellowPages and moved onto WhitePages... but [the page they gave me](https://jupiter.challenges.picoctf.org/static/fa4a277cfa846e07a5981d8a19288a2e/whitepages.txt) is all blank!
# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Windows/system32$ wget https://jupiter.challenges.picoctf.org/static/fa4a277cfa846e07a5981d8a19288a2e/whitepages.txt
--2025-04-28 12:35:10--  https://jupiter.challenges.picoctf.org/static/fa4a277cfa846e07a5981d8a19288a2e/whitepages.txt
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2982 (2.9K) [application/octet-stream]
Saving to: ‘whitepages.txt’

whitepages.txt                100%[=================================================>]   2.91K  --.-KB/s    in 0s

2025-04-28 12:35:18 (381 MB/s) - ‘whitepages.txt’ saved [2982/2982]

lixin@DELTUS:/mnt/c/Windows/system32$ sed 's/\xe2\x83/0/g' whitepages.txt|sed 's/ /1/g'
    1 1     1  1    1  1 111     11 1  1 11   11 11 1111 1    11 1 1 1   1   11     1 1     1 1     1  1    1  1 1 1  11 1   1 1 1   1 1  1      1 1     1 1 1 1 1    1  1  11   1  1  1 1    11  1      1 1  1  1   1 1 1    11 1  1111 1 1  1  1   1   1 1  11  1       1  11   1      1    1  1     1 1    11 1  1 11 1   111 1 1  1  1  1111 1 1 1 1 1  111  1   1    1      1 1  1  1   1 1 1 1     1  1111 1 1  1  1 1 1      1 1     1  1    1  1  11 1 1  11      11      11      1      1   11  11 1111 111  1  11   1  11  1 1 111  11  1      1     1 111 11  11  1 1  1 11    1      1 1     11 1  1 111 1   111 1   111  11 11   1  111 1 1 111  1  11  111 11 1     1 11    1      1 1     1     1  1       11   1  11 1 1  11  1   11   1  11  11    1 1     1  1    1  1 111     11 1  1 11   11 11 1111 1    11 1 1 1   1   11  1111 11 11 111  11 1111 111 1   1 11111 11    1 11 11   11 11   1 11111 111  11 111     11    1 11   11 11  1 1 111  11 1 11111 11    1 111  1  11  1 1 1 11111 11   11 111  1  11  1 1 11    1 111 1   11  1 1 11  1   1 11111 11  1 1 111   1 111 1 1 11    1 11 11   1 11111  11  11 11  1 1  11  1   11 1    11  1   11  11  11      111     11   1 11  1   11  11   111  1 11    1 11  1   11    1 11   1   11  1  11    1  111  1 11  1    111  1  11 11  11    1 11  11  11  1   11    1  11 1   11   11 11  11  11    1 11  1    11 11  11111 1    1 1     1  1    1  1lixin@DELTUS:/mnt/c/Windows/system32$ sed 's/\xe2\x80\x83/0/g' whitepages.txt|sed 's/ /1/g'           sed 's/\xe2\x80\x83/0/g' whitepages.txt|sed 's/ /1/g'
0000101000001001000010010111000001101001011000110110111101000011010101000100011000001010000010100000100100001001010100110100010101000101001000000101000001010101010000100100110001001001010000110010000001010010010001010100001101001111010100100100010001010011001000000010011000100000010000100100000101000011010010110100011101010010010011110101010101001110010001000010000001010010010001010101000001001111010100100101010000001010000010010000100100110101001100000011000000110000001000000100011001101111011100100110001001100101011100110010000001000001011101100110010100101100001000000101000001101001011101000111010001110011011000100111010101110010011001110110100000101100001000000101000001000001001000000011000100110101001100100011000100110011000010100000100100001001011100000110100101100011011011110100001101010100010001100111101101101110011011110111010001011111011000010110110001101100010111110111001101110000011000010110001101100101011100110101111101100001011100100110010101011111011000110111001001100101011000010111010001100101011001000101111101100101011100010111010101100001011011000101111100110011011001010011001000110100001100100011001100110000001110000011000101100100011001100011100101100001011001000110000101100010001100100110000100111001011001000011100100110110011000ve0101100110011001000110000100110100011000110110011001100001011001000011011001111101000010100000100100001001lixin@DELTUS:/mnt/c/Windows/system32$ lo lleve al ciberchef y listo 
		picoCTF

		SEE PUBLIC RECORDS & BACKGROUND REPORT
		5000 Forbes Ave, Pittsburgh, PA 15213
		picoCTF{not_all_spaces_are_created_equal_3e2423081df9adab2a9d96afda4cfad6}
		
````` 
#  03  c0rrupt
# DESC
We found this [file](https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery). Recover the flag.

# SOLUCION

````` python
picoCTF{c0rrupt10n_1847995}
````` 
#  04  like1000
# DESC

This [.tar file](https://jupiter.challenges.picoctf.org/static/52084b5ad360b25f9af83933114324e0/1000.tar) got tarred a lot.
# SOLUCION

````` python
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ wget https://jupiter.challenges.picoctf.org/static/52084b5ad360b25f9af83933114324e0/1000.tar
--2025-04-28 13:09:22--  https://jupiter.challenges.picoctf.org/static/52084b5ad360b25f9af83933114324e0/1000.tar
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10250240 (9.8M) [application/octet-stream]
Saving to: ‘1000.tar’

1000.tar                                             100%[=====================================================================================================================>]   9.78M   249KB/s    in 24s

2025-04-28 13:09:47 (418 KB/s) - ‘1000.tar’ saved [10250240/10250240]
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ for i in {1000..1} ; do tar -xvf $i.tar && rm $i.tar ; done

picoCTF{l0t5_0f_TAR5}
````` 
#  05  shark on wire 2
# DESC

We found this [packet capture](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap). Recover the flag that was pilfered from the network.
# SOLUCION

````` python
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ wget https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap
--2025-04-28 13:19:11--  https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 112318 (110K) [application/octet-stream]
Saving to: ‘capture.pcap’

capture.pcap                                         100%[=====================================================================================================================>] 109.69K   333KB/s    in 0.3s

2025-04-28 13:19:13 (333 KB/s) - ‘capture.pcap’ saved [112318/112318]

(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ wireshark capture.pcap
 ** (wireshark:2010) 13:19:42.023997 [GUI CRITICAL] -- Failed to create wl_display (No such file or directory)
nl80211 not found.
^X^C
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ nano exploy.py
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$  exploy.py
exploy.py: command not found
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ nano exploy.py
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ nano exploy.py
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ python exploy.py
Traceback (most recent call last):
  File "/mnt/c/Users/39204/sstv/exploy.py", line 1, in <module>
    from scapy.all import *
ModuleNotFoundError: No module named 'scapy'
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ pip install scapy
Collecting scapy
  Downloading scapy-2.6.1-py3-none-any.whl.metadata (5.6 kB)
Downloading scapy-2.6.1-py3-none-any.whl (2.4 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 2.4/2.4 MB 2.2 MB/s eta 0:00:00
Installing collected packages: scapy
Successfully installed scapy-2.6.1
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$ python exploy.py
picoCTF{p1LLf3r3d_data_v1a_st3g0}
(myenv) lixin@DELTUS:/mnt/c/Users/39204/sstv$

````` 
