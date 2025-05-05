#  01  WebNet0
# DESC

We found this [packet capture](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/picopico.key). Recover the flag.
# SOLUCION
Por el nombre del desafío estoy casi seguro de que este pcap es una conexión [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security) con datos encriptados, a estas alturas la mayoría de los protocolos y conjuntos de cifrado TLS están bien encriptados y sin la clave privada no podemos desencriptar los datos, pero en este desafío ¡tenemos la clave!

Así que Google es nuestro mejor amigo:

> descifrado de pcap tls

Encontré este [sitio](https://packetpushers.net/using-ssldump-decode-ssltls-packets/) que habla de la herramienta "ssldump". Parece justo lo que necesitamos. Pero necesitamos descifrar el archivo pcap, no rastrearlo, así que busqué de nuevo:

```
ssldump pcap file And found this [site](https://support.citrix.com/article/CTX116978)
```

![Dominio](https://i.imgur.com/is7KfqF.png)¡Este es el comando que necesitamos! Instalé ssldump y usé el comando:

```
ssldump -r capture.pcap -k picopico.key -d
```

![Utilice el comando](https://i.imgur.com/mugHZJP.png)Luego me desplacé un poco hacia abajo y esto me llamó la atención:![¡La bandera!](https://i.imgur.com/kbABnxs.png)¡Y encontramos la bandera!

picoCTF{nongshim.shrimp.crackers}


# 02  WebNet1

# DESC

We found this [packet capture](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key). Recover the flag.
# SOLUCION

````` python
This is the follow-up for [WebNet0](https://github.com/Dvd848/CTFs/blob/master/2019_picoCTF/WebNet0.md).

We receive a network capture file:

```shell
root@kali:/media/sf_CTFs/pico/WebNet1# tshark -r capture.pcap
Running as user "root" and group "root". This could be dangerous.
    1   0.000000 128.237.140.23 → 172.31.22.220 TCP 78 57930 → 443 [SYN] Seq=0 Win=65535 Len=0 MSS=1386 WS=64 TSval=133587575 TSecr=0 SACK_PERM=1 57930 443
    2   0.000031 172.31.22.220 → 128.237.140.23 TCP 74 443 → 57930 [SYN, ACK] Seq=0 Ack=1 Win=26847 [TCP CHECKSUM INCORRECT] Len=0 MSS=8961 SACK_PERM=1 TSval=570160341 TSecr=133587575 WS=128 443 57930
    3   0.024621 128.237.140.23 → 172.31.22.220 TCP 78 57940 → 443 [SYN] Seq=0 Win=65535 Len=0 MSS=1386 WS=64 TSval=133587599 TSecr=0 SACK_PERM=1 57940 443
    4   0.024650 172.31.22.220 → 128.237.140.23 TCP 74 443 → 57940 [SYN, ACK] Seq=0 Ack=1 Win=26847 [TCP CHECKSUM INCORRECT] Len=0 MSS=8961 SACK_PERM=1 TSval=570160366 TSecr=133587599 WS=128 443 57940
    5   0.025067 128.237.140.23 → 172.31.22.220 TCP 78 57941 → 443 [SYN] Seq=0 Win=65535 Len=0 MSS=1386 WS=64 TSval=133587599 TSecr=0 SACK_PERM=1 57941 443
    6   0.025073 172.31.22.220 → 128.237.140.23 TCP 74 443 → 57941 [SYN, ACK] Seq=0 Ack=1 Win=26847 [TCP CHECKSUM INCORRECT] Len=0 MSS=8961 SACK_PERM=1 TSval=570160366 TSecr=133587599 WS=128 443 57941
    7   0.029264 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1 Ack=1 Win=131904 Len=0 TSval=133587603 TSecr=570160341 57930 443
    8   0.029774 128.237.140.23 → 172.31.22.220 TLSv1 583 Client Hello 57930 443
    9   0.029794 172.31.22.220 → 128.237.140.23 TCP 66 443 → 57930 [ACK] Seq=1 Ack=518 Win=28032 [TCP CHECKSUM INCORRECT] Len=0 TSval=570160371 TSecr=133587603 443 57930
   10   0.030173 172.31.22.220 → 128.237.140.23 TLSv1.2 1073 Server Hello, Certificate, Server Hello Done 443 57930
   11   0.053963 128.237.140.23 → 172.31.22.220 TCP 66 57940 → 443 [ACK] Seq=1 Ack=1 Win=131904 Len=0 TSval=133587625 TSecr=570160366 57940 443
   12   0.054050 128.237.140.23 → 172.31.22.220 TCP 66 57941 → 443 [ACK] Seq=1 Ack=1 Win=131904 Len=0 TSval=133587625 TSecr=570160366 57941 443
   13   0.054463 128.237.140.23 → 172.31.22.220 TLSv1 583 Client Hello 57941 443
   14   0.054486 172.31.22.220 → 128.237.140.23 TCP 66 443 → 57941 [ACK] Seq=1 Ack=518 Win=28032 [TCP CHECKSUM INCORRECT] Len=0 TSval=570160395 TSecr=133587625 443 57941
   15   0.054500 128.237.140.23 → 172.31.22.220 TLSv1 583 Client Hello 57940 443
   16   0.054506 172.31.22.220 → 128.237.140.23 TCP 66 443 → 57940 [ACK] Seq=1 Ack=518 Win=28032 [TCP CHECKSUM INCORRECT] Len=0 TSval=570160395 TSecr=133587625 443 57940
   17   0.054815 172.31.22.220 → 128.237.140.23 TLSv1.2 1073 Server Hello, Certificate, Server Hello Done 443 57941
   18   0.054984 172.31.22.220 → 128.237.140.23 TLSv1.2 1073 Server Hello, Certificate, Server Hello Done 443 57940
   19   0.058931 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=518 Ack=1008 Win=130880 Len=0 TSval=133587629 TSecr=570160371 57930 443
   20   0.059631 128.237.140.23 → 172.31.22.220 TLSv1.2 384 Client Key Exchange, Change Cipher Spec, Encrypted Handshake Message 57930 443
   21   0.061312 172.31.22.220 → 128.237.140.23 TLSv1.2 324 New Session Ticket, Change Cipher Spec, Encrypted Handshake Message 443 57930
   22   0.071450 128.237.140.23 → 172.31.22.220 TCP 78 57944 → 443 [SYN] Seq=0 Win=65535 Len=0 MSS=1386 WS=64 TSval=133587639 TSecr=0 SACK_PERM=1 57944 443
   23   0.071468 172.31.22.220 → 128.237.140.23 TCP 74 443 → 57944 [SYN, ACK] Seq=0 Ack=1 Win=26847 [TCP CHECKSUM INCORRECT] Len=0 MSS=8961 SACK_PERM=1 TSval=570160412 TSecr=133587639 WS=128 443 57944
   24   0.084552 128.237.140.23 → 172.31.22.220 TCP 66 57941 → 443 [ACK] Seq=518 Ack=1008 Win=130880 Len=0 TSval=133587650 TSecr=570160396 57941 443
   25   0.084611 128.237.140.23 → 172.31.22.220 TCP 66 57940 → 443 [ACK] Seq=518 Ack=1008 Win=130880 Len=0 TSval=133587650 TSecr=570160396 57940 443
   26   0.085416 128.237.140.23 → 172.31.22.220 TLSv1.2 384 Client Key Exchange, Change Cipher Spec, Encrypted Handshake Message 57941 443
   27   0.085797 128.237.140.23 → 172.31.22.220 TLSv1.2 384 Client Key Exchange, Change Cipher Spec, Encrypted Handshake Message 57940 443
   28   0.086486 172.31.22.220 → 128.237.140.23 TLSv1.2 324 New Session Ticket, Change Cipher Spec, Encrypted Handshake Message 443 57941
   29   0.087455 172.31.22.220 → 128.237.140.23 TLSv1.2 324 New Session Ticket, Change Cipher Spec, Encrypted Handshake Message 443 57940
   30   0.092163 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=836 Ack=1266 Win=130752 Len=0 TSval=133587657 TSecr=570160402 57930 443
   31   0.101699 128.237.140.23 → 172.31.22.220 TCP 66 57944 → 443 [ACK] Seq=1 Ack=1 Win=131904 Len=0 TSval=133587666 TSecr=570160412 57944 443
   32   0.101871 128.237.140.23 → 172.31.22.220 TLSv1 583 Client Hello 57944 443
   33   0.101890 172.31.22.220 → 128.237.140.23 TCP 66 443 → 57944 [ACK] Seq=1 Ack=518 Win=28032 [TCP CHECKSUM INCORRECT] Len=0 TSval=570160443 TSecr=133587666 443 57944
   34   0.102246 172.31.22.220 → 128.237.140.23 TLSv1.2 1073 Server Hello, Certificate, Server Hello Done 443 57944
   35   0.120097 128.237.140.23 → 172.31.22.220 TCP 66 57940 → 443 [ACK] Seq=836 Ack=1266 Win=130752 Len=0 TSval=133587679 TSecr=570160428 57940 443
   36   0.120117 128.237.140.23 → 172.31.22.220 TCP 66 57941 → 443 [ACK] Seq=836 Ack=1266 Win=130752 Len=0 TSval=133587679 TSecr=570160427 57941 443
   37   0.133091 128.237.140.23 → 172.31.22.220 TCP 66 57944 → 443 [ACK] Seq=518 Ack=1008 Win=130880 Len=0 TSval=133587692 TSecr=570160443 57944 443
   38   0.133943 128.237.140.23 → 172.31.22.220 TLSv1.2 384 Client Key Exchange, Change Cipher Spec, Encrypted Handshake Message 57944 443
   39   0.135006 172.31.22.220 → 128.237.140.23 TLSv1.2 324 New Session Ticket, Change Cipher Spec, Encrypted Handshake Message 443 57944
   40   0.164185 128.237.140.23 → 172.31.22.220 TCP 66 57944 → 443 [ACK] Seq=836 Ack=1266 Win=130752 Len=0 TSval=133587722 TSecr=570160476 57944 443
   41   0.169256 128.237.140.23 → 172.31.22.220 TLSv1.2 517 Application Data 57944 443
   42   0.169756 172.31.22.220 → 128.237.140.23 TLSv1.2 1330 Application Data 443 57944
   43   0.218857 128.237.140.23 → 172.31.22.220 TCP 66 57944 → 443 [ACK] Seq=1287 Ack=2530 Win=129792 Len=0 TSval=133587775 TSecr=570160511 57944 443
   44   0.340614 128.237.140.23 → 172.31.22.220 TLSv1.2 532 Application Data 57930 443
   45   0.341085 172.31.22.220 → 128.237.140.23 TLSv1.2 581 Application Data 443 57930
   46   0.371530 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1302 Ack=1781 Win=130496 Len=0 TSval=133587922 TSecr=570160682 57930 443
   47   0.550456 128.237.140.23 → 172.31.22.220 TLSv1.2 519 Application Data 57930 443
   48   0.550792 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Application Data 443 57930
   49   0.550805 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   50   0.550809 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   51   0.550867 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   52   0.550900 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   53   0.580162 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=4529 Win=128320 Len=0 TSval=133588111 TSecr=570160892 57930 443
   54   0.580191 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   55   0.580203 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   56   0.580206 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=7277 Win=125888 Len=0 TSval=133588111 TSecr=570160892 57930 443
   57   0.580238 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   58   0.580272 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   59   0.580723 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=10025 Win=123136 Len=0 TSval=133588111 TSecr=570160892 57930 443
   60   0.580727 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   61   0.580733 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   62   0.580736 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=12773 Win=120448 Len=0 TSval=133588111 TSecr=570160892 57930 443
   63   0.580739 128.237.140.23 → 172.31.22.220 TCP 66 [TCP Window Update] 57930 → 443 [ACK] Seq=1755 Ack=12773 Win=131072 Len=0 TSval=133588111 TSecr=570160892 57930 443
   64   0.580764 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   65   0.580796 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   66   0.581035 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=15521 Win=129664 Len=0 TSval=133588112 TSecr=570160892 57930 443
   67   0.581039 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   68   0.581056 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   69   0.610313 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=18269 Win=128320 Len=0 TSval=133588139 TSecr=570160921 57930 443
   70   0.610340 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   71   0.610363 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   72   0.610366 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=21017 Win=125568 Len=0 TSval=133588139 TSecr=570160921 57930 443
   73   0.610404 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   74   0.610440 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   75   0.611355 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=23765 Win=122816 Len=0 TSval=133588139 TSecr=570160921 57930 443
   76   0.611358 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   77   0.611365 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   78   0.611367 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=26513 Win=120064 Len=0 TSval=133588139 TSecr=570160921 57930 443
   79   0.611371 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=29261 Win=117312 Len=0 TSval=133588139 TSecr=570160922 57930 443
   80   0.611373 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=34757 Win=111808 Len=0 TSval=133588139 TSecr=570160922 57930 443
   81   0.611376 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=32009 Win=114560 Len=0 TSval=133588139 TSecr=570160922 57930 443
   82   0.611378 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=37505 Win=109056 Len=0 TSval=133588139 TSecr=570160922 57930 443
   83   0.611382 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=40253 Win=106304 Len=0 TSval=133588140 TSecr=570160922 57930 443
   84   0.611384 128.237.140.23 → 172.31.22.220 TCP 66 [TCP Window Update] 57930 → 443 [ACK] Seq=1755 Ack=40253 Win=109376 Len=0 TSval=133588140 TSecr=570160922 57930 443
   85   0.611398 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   86   0.611429 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   87   0.611472 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   88   0.611545 172.31.22.220 → 128.237.140.23 TLSv1.2 2814 Ignored Unknown Record 443 57930
   89   0.611581 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=41627 Win=124416 Len=0 TSval=133588140 TSecr=570160922 57930 443
   90   0.611587 128.237.140.23 → 172.31.22.220 TCP 66 [TCP Window Update] 57930 → 443 [ACK] Seq=1755 Ack=41627 Win=131072 Len=0 TSval=133588140 TSecr=570160922 57930 443
   91   0.611591 172.31.22.220 → 128.237.140.23 TLSv1.2 2275 Ignored Unknown Record 443 57930
   92   0.639462 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=44375 Win=129664 Len=0 TSval=133588168 TSecr=570160922 57930 443
   93   0.639481 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=45749 Win=131072 Len=0 TSval=133588168 TSecr=570160951 57930 443
   94   0.640260 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=48497 Win=128320 Len=0 TSval=133588168 TSecr=570160951 57930 443
   95   0.640264 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=51245 Win=125568 Len=0 TSval=133588168 TSecr=570160951 57930 443
   96   0.640267 128.237.140.23 → 172.31.22.220 TCP 66 [TCP Window Update] 57930 → 443 [ACK] Seq=1755 Ack=51245 Win=131072 Len=0 TSval=133588168 TSecr=570160951 57930 443
   97   0.640944 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=53993 Win=128320 Len=0 TSval=133588169 TSecr=570160951 57930 443
   98   0.640948 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=56741 Win=125568 Len=0 TSval=133588169 TSecr=570160952 57930 443
   99   0.640950 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=59489 Win=122816 Len=0 TSval=133588169 TSecr=570160952 57930 443
  100   0.640953 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=62237 Win=120064 Len=0 TSval=133588169 TSecr=570160952 57930 443
  101   0.640955 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=64985 Win=117312 Len=0 TSval=133588169 TSecr=570160952 57930 443
  102   0.641830 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=67733 Win=128320 Len=0 TSval=133588169 TSecr=570160952 57930 443
  103   0.641834 128.237.140.23 → 172.31.22.220 TCP 66 [TCP Window Update] 57930 → 443 [ACK] Seq=1755 Ack=67733 Win=131072 Len=0 TSval=133588169 TSecr=570160952 57930 443
  104   0.641843 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=64985 Win=131072 Len=0 TSval=133588169 TSecr=570160952 57930 443
  105   0.641844 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=70481 Win=128320 Len=0 TSval=133588169 TSecr=570160953 57930 443
  106   0.641847 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=71855 Win=131072 Len=0 TSval=133588169 TSecr=570160953 57930 443
  107   0.642018 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=1755 Ack=72690 Win=130176 Len=0 TSval=133588170 TSecr=570160953 57930 443
  108   0.799152 128.237.140.23 → 172.31.22.220 TLSv1.2 438 Application Data 57930 443
  109   0.799455 172.31.22.220 → 128.237.140.23 TLSv1.2 637 Application Data 443 57930
  110   0.830330 128.237.140.23 → 172.31.22.220 TCP 66 57930 → 443 [ACK] Seq=2127 Ack=73261 Win=130496 Len=0 TSval=133588355 TSecr=570161140 57930 443
```

And a key file:

```shell
root@kali:/media/sf_CTFs/pico/WebNet1# openssl rsa -in picopico.key -text
RSA Private-Key: (2048 bit, 2 primes)
modulus:
    00:b0:2a:51:4f:34:a8:ec:78:91:79:a6:e0:89:53:
    9c:77:f1:77:13:d5:e4:20:7b:9c:ce:28:d6:a1:02:
    56:2e:76:f1:95:38:4b:3a:d5:39:c8:82:f7:04:47:
    89:28:f2:2d:ce:0b:06:a4:db:f6:ad:70:69:37:a3:
    3f:63:14:a7:a9:ed:71:44:60:d3:f7:d4:8c:30:0f:
    d8:ff:61:ac:e5:2b:2e:03:44:b1:8e:6c:ec:88:65:
    45:35:7f:65:91:03:b5:21:7f:43:ce:41:7b:03:4f:
    5a:14:5f:7d:a3:30:a6:64:41:24:83:5b:83:11:65:
    df:6d:ac:96:1d:3b:64:eb:70:43:cc:b0:18:99:42:
    51:65:be:09:cd:c2:5d:d0:95:ac:28:cd:31:cb:00:
    92:88:df:a8:f5:70:fc:12:30:c7:8d:71:ad:5e:d1:
    98:b5:b3:b4:79:23:17:e1:a4:d5:ce:04:5d:05:9b:
    18:96:be:67:8e:1d:b6:ac:a7:21:e0:f1:41:26:18:
    1a:e4:77:89:38:c1:74:8a:19:0b:eb:73:c4:23:c9:
    c3:f8:49:c1:1d:aa:ec:49:89:89:c3:4f:c8:84:6c:
    0a:bb:d3:fe:df:ff:93:48:37:50:c4:f5:8a:06:26:
    a2:98:8d:34:bd:9d:13:c1:e1:8b:e3:24:df:d2:26:
    78:6f
publicExponent: 65537 (0x10001)
privateExponent:
    08:29:dd:dc:ba:c6:fd:36:55:1f:7b:11:3a:ab:ea:
    3b:50:b0:40:f6:0f:7d:45:dd:2d:5c:8d:1d:a6:fb:
    11:6a:27:a5:cf:97:04:e1:ee:ac:91:0d:1b:60:a9:
    45:81:7b:87:e9:d0:e4:00:e1:7c:86:12:0a:27:01:
    7f:f8:ec:10:1e:d5:b9:e2:76:d0:2c:44:56:d1:d5:
    2f:78:7a:47:a0:69:a0:73:25:7b:41:26:f0:e7:28:
    7e:e3:29:74:bf:e4:3b:ea:26:dd:3f:01:91:54:b3:
    0a:f0:a5:e4:d3:13:52:e0:05:ee:24:66:7d:7e:e8:
    0c:b0:0b:c0:cd:08:cf:34:2f:da:e9:fe:d9:49:93:
    d7:9a:e0:01:97:e5:dc:82:f5:3c:6b:c9:85:b8:4b:
    c5:f7:9e:c8:f1:3d:30:1c:b5:4a:a0:63:43:da:cd:
    16:7f:2c:42:ff:79:f4:9e:81:1f:3e:1b:12:92:bf:
    fc:4a:ed:34:fd:b2:87:ba:22:54:10:60:28:44:35:
    80:4b:8e:8d:00:bf:e2:8c:68:a8:21:5f:65:a7:fd:
    5c:d4:42:c4:1f:f3:63:59:d4:a6:bb:c9:cb:3d:3d:
    34:c4:16:34:5d:84:9a:f9:81:54:67:e8:4f:19:ae:
    ba:de:4d:d0:66:d5:af:65:32:1f:15:8c:2a:6d:ac:
    39
prime1:
    00:e9:6f:6f:80:5a:05:a5:1a:d7:ad:b8:b2:89:7c:
    9b:3c:76:77:7a:2e:19:da:7d:b2:82:39:73:0e:4f:
    af:2a:30:14:68:4e:90:6d:55:32:d1:55:23:6f:58:
    29:bc:9b:84:d3:11:ac:d7:e3:e6:40:f9:b2:45:c1:
    41:70:68:04:c3:98:77:2b:ea:53:08:de:d3:4a:ad:
    cb:27:63:61:7b:a3:92:38:cf:a9:b0:b9:1b:92:7a:
    cc:ea:fe:77:71:66:a0:b3:c0:2b:b8:9c:a8:b1:87:
    77:33:9e:9e:e3:26:21:25:34:6d:1d:f0:bb:b9:79:
    08:26:54:02:b5:02:15:97:7d
prime2:
    00:c1:31:af:60:6b:b5:49:50:fe:29:cd:c1:e7:58:
    0a:22:df:83:a9:7e:3b:d0:61:e1:a5:20:a2:f7:00:
    a3:b8:39:e7:5a:1d:d1:fd:aa:27:78:d4:f4:07:9c:
    be:ce:df:1c:cd:eb:af:52:90:b6:79:b3:47:7c:f0:
    0f:cb:14:b9:38:a1:93:4c:29:d9:12:4d:02:10:f8:
    03:1b:5c:7d:35:1c:61:6f:9c:23:ae:3e:0f:c5:6c:
    da:75:c1:2e:f3:24:48:39:bb:91:c5:41:6c:8c:3c:
    d2:4b:af:f8:59:ea:0d:98:a7:e5:06:a4:07:06:4f:
    03:3f:44:23:d5:00:f8:4b:5b
exponent1:
    00:c0:07:43:9a:3a:73:da:56:32:86:5e:21:c0:a8:
    18:ab:ac:68:ac:c1:af:d2:e5:04:2b:cc:46:b1:c7:
    2b:39:71:43:d8:6a:88:b4:e8:19:5d:ca:c3:d3:9c:
    9a:f8:e4:96:67:6b:6a:dc:4e:45:e3:bd:84:c1:8d:
    30:df:df:31:cc:15:68:33:60:17:de:7c:2f:24:87:
    c3:4f:2b:99:cd:b3:c9:5d:a2:b6:dd:01:e9:84:9e:
    30:64:3f:e0:d2:10:b2:b2:2b:ab:cb:ba:53:ab:76:
    dc:c0:42:04:42:a7:e3:2c:4f:ec:53:6c:ed:80:ad:
    e7:de:5f:cd:ba:49:74:a9:a1
exponent2:
    2d:af:9c:33:87:05:05:e3:7b:57:53:6b:09:54:4e:
    81:54:ae:04:04:f0:0c:25:39:81:1d:28:ac:94:a0:
    22:ce:be:a1:16:f0:33:b6:6b:43:2d:c8:cf:8c:07:
    ab:50:23:b5:a6:88:7d:53:ef:72:f4:2c:71:a5:2b:
    76:f0:dd:a4:40:c1:5e:7f:7e:ef:ce:fa:30:1d:16:
    4f:00:1e:33:d3:14:4f:9a:72:ed:9f:8b:87:3a:68:
    a6:f4:1a:30:31:62:4b:14:ca:32:05:78:af:e9:2a:
    29:ef:e1:21:12:32:48:e9:5b:45:a8:c0:68:83:82:
    d7:11:3c:10:00:fc:b6:85
coefficient:
    7c:43:35:ad:f3:34:bf:75:26:07:b3:d2:ea:ed:26:
    3f:77:24:3f:60:85:09:d6:ab:c9:73:df:0b:9d:86:
    05:c2:77:43:8e:98:a6:c4:2f:2d:35:68:b4:cf:ad:
    78:7b:d3:8c:dc:36:8f:0c:19:c4:89:78:35:e9:c6:
    48:48:f7:28:38:50:a0:e8:90:0b:d0:6b:0c:3f:83:
    07:82:3d:f9:3f:67:c5:3d:e0:ed:1e:8c:ae:02:13:
    82:10:78:59:ee:d3:56:12:ff:3e:58:e7:25:3c:83:
    aa:98:cd:03:89:18:4e:f7:80:24:fb:fa:5e:ad:44:
    46:de:4f:52:d5:f7:06:a4
writing RSA key
-----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEAsCpRTzSo7HiReabgiVOcd/F3E9XkIHuczijWoQJWLnbxlThL
OtU5yIL3BEeJKPItzgsGpNv2rXBpN6M/YxSnqe1xRGDT99SMMA/Y/2Gs5SsuA0Sx
jmzsiGVFNX9lkQO1IX9DzkF7A09aFF99ozCmZEEkg1uDEWXfbayWHTtk63BDzLAY
mUJRZb4JzcJd0JWsKM0xywCSiN+o9XD8EjDHjXGtXtGYtbO0eSMX4aTVzgRdBZsY
lr5njh22rKch4PFBJhga5HeJOMF0ihkL63PEI8nD+EnBHarsSYmJw0/IhGwKu9P+
3/+TSDdQxPWKBiaimI00vZ0TweGL4yTf0iZ4bwIDAQABAoIBAAgp3dy6xv02VR97
ETqr6jtQsED2D31F3S1cjR2m+xFqJ6XPlwTh7qyRDRtgqUWBe4fp0OQA4XyGEgon
AX/47BAe1bnidtAsRFbR1S94ekegaaBzJXtBJvDnKH7jKXS/5DvqJt0/AZFUswrw
peTTE1LgBe4kZn1+6AywC8DNCM80L9rp/tlJk9ea4AGX5dyC9TxryYW4S8X3nsjx
PTActUqgY0PazRZ/LEL/efSegR8+GxKSv/xK7TT9soe6IlQQYChENYBLjo0Av+KM
aKghX2Wn/VzUQsQf82NZ1Ka7ycs9PTTEFjRdhJr5gVRn6E8ZrrreTdBm1a9lMh8V
jCptrDkCgYEA6W9vgFoFpRrXrbiyiXybPHZ3ei4Z2n2ygjlzDk+vKjAUaE6QbVUy
0VUjb1gpvJuE0xGs1+PmQPmyRcFBcGgEw5h3K+pTCN7TSq3LJ2Nhe6OSOM+psLkb
knrM6v53cWags8AruJyosYd3M56e4yYhJTRtHfC7uXkIJlQCtQIVl30CgYEAwTGv
YGu1SVD+Kc3B51gKIt+DqX470GHhpSCi9wCjuDnnWh3R/aoneNT0B5y+zt8czeuv
UpC2ebNHfPAPyxS5OKGTTCnZEk0CEPgDG1x9NRxhb5wjrj4PxWzadcEu8yRIObuR
xUFsjDzSS6/4WeoNmKflBqQHBk8DP0Qj1QD4S1sCgYEAwAdDmjpz2lYyhl4hwKgY
q6xorMGv0uUEK8xGsccrOXFD2GqItOgZXcrD05ya+OSWZ2tq3E5F472EwY0w398x
zBVoM2AX3nwvJIfDTyuZzbPJXaK23QHphJ4wZD/g0hCysiury7pTq3bcwEIEQqfj
LE/sU2ztgK3n3l/Nukl0qaECgYAtr5wzhwUF43tXU2sJVE6BVK4EBPAMJTmBHSis
lKAizr6hFvAztmtDLcjPjAerUCO1poh9U+9y9CxxpSt28N2kQMFef37vzvowHRZP
AB4z0xRPmnLtn4uHOmim9BowMWJLFMoyBXiv6Sop7+EhEjJI6VtFqMBog4LXETwQ
APy2hQKBgHxDNa3zNL91Jgez0urtJj93JD9ghQnWq8lz3wudhgXCd0OOmKbELy01
aLTPrXh704zcNo8MGcSJeDXpxkhI9yg4UKDokAvQaww/gweCPfk/Z8U94O0ejK4C
E4IQeFnu01YS/z5Y5yU8g6qYzQOJGE73gCT7+l6tREbeT1LV9wak
-----END RSA PRIVATE KEY-----
```

If we decrypt the capture using the provided key and follow the first stream, we get the following HTTP session:

```shell
root@kali:/media/sf_CTFs/pico/WebNet1# tshark -r capture.pcap  -o "ssl.debug_file:ssldebug.log" -o "ssl.desegment_ssl_records: TRUE" -o "ssl.desegment_ssl_application_data: TRUE" -o "ssl.keys_list:172.31.22.220,443,http,picopico.key" -qz follow,ssl,ascii,0
Running as user "root" and group "root". This could be dangerous.

===================================================================
Follow: ssl,ascii
Filter: tcp.stream eq 0
Node 0: 128.237.140.23:57930
Node 1: :0
437
GET /starter-template.css HTTP/1.1
Host: ec2-18-223-184-200.us-east-2.compute.amazonaws.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:68.0) Gecko/20100101 Firefox/68.0
Accept: text/css,*/*;q=0.1
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Referer: https://ec2-18-223-184-200.us-east-2.compute.amazonaws.com/second.html
Pragma: no-cache
Cache-Control: no-cache


        486
HTTP/1.1 200 OK
Date: Fri, 23 Aug 2019 16:27:04 GMT
Server: Apache/2.4.29 (Ubuntu)
Last-Modified: Mon, 12 Aug 2019 16:47:05 GMT
ETag: "62-58fee462bf227-gzip"
Accept-Ranges: bytes
Vary: Accept-Encoding
Content-Encoding: gzip
Pico-Flag: picoCTF{this.is.not.your.flag.anymore}
Content-Length: 100
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/css

..........K.O.T..RP(HLI..K.-./.R0-J......+.I,*I-.-I.-.I,IEVj.`.T.`..Q..P.ZQ......g.......2.. ...b...
424
GET /vulture.jpg HTTP/1.1
Host: ec2-18-223-184-200.us-east-2.compute.amazonaws.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:68.0) Gecko/20100101 Firefox/68.0
Accept: image/webp,*/*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Referer: https://ec2-18-223-184-200.us-east-2.compute.amazonaws.com/second.html
Pragma: no-cache
Cache-Control: no-cache


        340
HTTP/1.1 200 OK
Date: Fri, 23 Aug 2019 16:27:04 GMT
Server: Apache/2.4.29 (Ubuntu)
Last-Modified: Fri, 23 Aug 2019 16:26:33 GMT
ETag: "112fb-590cb44f2cbe6"
Accept-Ranges: bytes
Content-Length: 70395
Pico-Flag: picoCTF{this.is.not.your.flag.anymore}
Keep-Alive: timeout=5, max=99
Connection: Keep-Alive
Content-Type: image/jpeg


343
GET /favicon.ico HTTP/1.1
Host: ec2-18-223-184-200.us-east-2.compute.amazonaws.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:68.0) Gecko/20100101 Firefox/68.0
Accept: image/webp,*/*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Pragma: no-cache
Cache-Control: no-cache


===================================================================
```

The flag in the HTTP header was replaced with a red herring: `Pico-Flag: picoCTF{this.is.not.your.flag.anymore}`.

We can see that one of the HTTP requests was for an image:

```
GET /vulture.jpg HTTP/1.1
```

We can export the HTTP objects from the session using the following command:

```shell
root@kali:/media/sf_CTFs/pico/WebNet1# mkdir out
root@kali:/media/sf_CTFs/pico/WebNet1# tshark -r capture.pcap  -o "ssl.debug_file:ssldebug.log" -o "ssl.desegment_ssl_records: TRUE" -o "ssl.desegment_ssl_application_data: TRUE" -o "ssl.keys_list:172.31.22.220,443,http,picopico.key" -o "tcp.desegment_tcp_streams: TRUE" -o "tcp.no_subdissector_on_error: FALSE" --export-objects "http,out"
```

In the GUI, we need to make sure that the following options are configured (under Edit -> Preferences):

- TCP:
    - Allow subdissector to reassemble TCP streams: Checked
    - Do not call subdissecors for error packets: Unchecked
- SSL (/TLS):
    - Reassemble TLS records spanning multiple TCP segments: Checked
    - Reassemble TCL Application Data spanning multiple TLS records: Checked

Then, we can select File -> Export Objects -> HTTP.

We get the following files:

```shell
root@kali:/media/sf_CTFs/pico/WebNet1# ls out
favicon.ico  second.html  starter-template.css  vulture.jpg
root@kali:/media/sf_CTFs/pico/WebNet1# strings out/vulture.jpg | grep pico
picoCTF{honey.roasted.peanuts}
```
````` 

# 03  tunn3l v1s10n

# DESC

We found this [file](https://mercury.picoctf.net/static/7b2d7c26630e977197022d0af09e3aeb/tunn3l_v1s10n). Recover the flag.
# SOLUCION

````` python
## Intro

[](https://gist.github.com/nick3499/3c63d826f9156a2250bdc3acb2e5cbba#intro)

One surgical procedure for the ethical hacker is to use `scalpel` to fix **tunn3l v1s10n**.

## Tool: Scalpel

[](https://gist.github.com/nick3499/3c63d826f9156a2250bdc3acb2e5cbba#tool-scalpel)

In the `/etc/scalpel/scalpel.conf` configuration file of the `scalpel` tool, **uncomment** the following line:

```
#       bmp     y       100000  BM??\x00\x00\x00
```

- download `tunn3l_v1s10n` and rename it to `tunn3l_v1s10n.bmp` after confirming that the first two bytes are `42 4d` (`BM`), using a hex editor
- copy `tunn3l_v1s10n.bmp` to an empty sub-directory
- set first 7 bytes of `tunn3l_v1s10n.bmp` to **42 4d 3f 3f 00 00 00**, using a hex editor
- pass `tunn3l_v1s10n.bmp` as an argument to `scalpel` in `root` user mode

```shell
# scalpel tunn3l_v1s10n.bmp
Scalpel version 1.60
Written by Golden G. Richard III, based on Foremost 0.69.

Opening target "/home/kali/Desktop/tunn3l-v1s10n/bmp_file/tunn3l_v1s10n.bmp"

Image file pass 1/2.
tunn3l_v1s10n.bmp: 100.0% |****************************************************|    2.8 MB    00:00 ETAAllocating work queues...
Work queues allocation complete. Building carve lists...
Carve lists built.  Workload:
bmp with header "\x42\x4d\x3f\x3f\x00\x00\x00" and footer "" --> 1 files
Carving files from image.
Image file pass 2/2.
tunn3l_v1s10n.bmp: 100.0% |****************************************************|    2.8 MB    00:00 ETAProcessing of image file complete. Cleaning up...
Done.
Scalpel is done, files carved = 1, elapsed = 0 seconds.
```

### Before/After Scalpel

[](https://gist.github.com/nick3499/3c63d826f9156a2250bdc3acb2e5cbba#beforeafter-scalpel)

- `42 4d 8e 26 2c 00 00 00 00 00 ba d0 00 00 ba d0 00 00 6e 04 00 00 32 01 00 00 01 00 18 00 00 00` (corrupted bytes)
- `42 4d 3f 3f 00 00 00 00 00 00 36 00 00 00 28 00 00 00 6e 04 00 00 42 03 00 00 01 00 18 00 00 00` (after `scalpel`)

### Details

[](https://gist.github.com/nick3499/3c63d826f9156a2250bdc3acb2e5cbba#details)

- first bytes `ba d0` were changed to `36 00`
- second bytes `ba d0` were changed to `28 00`
- bytes `32 01` were changed to `42 03`
- hex `36` indicates that **54** bytes equals **14**-byte-long file header plus **40**-byte-long info header
- hex `28` indicates a **40** byte-long BMP info header
- `42` and `03` affect the offsets of the image, as I understand it.

## Flag

[](https://gist.github.com/nick3499/3c63d826f9156a2250bdc3acb2e5cbba#flag)

Thanks to the precise efficiency of `scalpel`, the picoCTF flag pops at the top of the image:

```
picoCTF{qu1t3_a_v13w_2020}
```
````` 



# 04  Matryoshka doll

# DESC

Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [this](https://mercury.picoctf.net/static/205adad23bf9d8303081a0e71c9beab8/dolls.jpg)
# SOLUCION

````` python
Windows PowerShell
Copyright (C) Microsoft Corporation. Todos los derechos reservados.

Instale la versión más reciente de PowerShell para obtener nuevas características y mejoras. https://aka.ms/PSWindows

PS C:\Users\39204> wsl
lixin@DELTUS:/mnt/c/Users/39204$  wget https://mercury.picoctf.net/static/205adad23bf9d8303081a0e71c9beab8/dolls.jpg
--2025-05-05 11:36:23--  https://mercury.picoctf.net/static/205adad23bf9d8303081a0e71c9beab8/dolls.jpg
--2025-05-05 11:37:49--  https://mercury.picoctf.net/static/205adad23bf9d8303081a0e71c9beab8/dolls.jpg
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 651632 (636K) [application/octet-stream]
Saving to: ‘dolls.jpg’

dolls.jpg                     100%[=================================================>] 636.36K   657KB/s    in 1.0s

2025-05-05 11:37:52 (657 KB/s) - ‘dolls.jpg’ saved [651632/651632]

--2025-05-05: command not found
lixin@DELTUS:/mnt/c/Users/39204$ binwalk -e dolls.png

General Error: Cannot open file dolls.png (CWD: /mnt/c/Users/39204) : [Errno 2] No such file or directory: 'dolls.png'

lixin@DELTUS:/mnt/c/Users/39204$ binwalk -e dolls.png

General Error: Cannot open file dolls.png (CWD: /mnt/c/Users/39204) : [Errno 2] No such file or directory: 'dolls.png'

lixin@DELTUS:/mnt/c/Users/39204$ ls
 AppData
'Configuración local'
 Contacts
 Cookies
'Datos de programa'
 Desktop
 Documents
 Downloads
'Entorno de red'
 Favorites
 Impresoras
 Links
'Menú Inicio'
'Mis documentos'
 Music
 NTUSER.DAT
 NTUSER.DAT{882bd01a-8d08-11ef-a5e1-c0bfbeed247b}.TM.blf
 NTUSER.DAT{882bd01a-8d08-11ef-a5e1-c0bfbeed247b}.TMContainer00000000000000000001.regtrans-ms
 NTUSER.DAT{882bd01a-8d08-11ef-a5e1-c0bfbeed247b}.TMContainer00000000000000000002.regtrans-ms
 OneDrive
 Oracle
 Packages
 Pictures
 Plantillas
 Reciente
'Saved Games'
 Searches
 SendTo
 Videos
'WPS Cloud Files'
 ansel
 capture.pcap
 dolls.jpg
 flag.png
 garden.jpg
 message.wav
 ntuser.dat.LOG1
 ntuser.dat.LOG2
 ntuser.ini
 output.txt
 pico_img.png
 sstv
 waterfall-20250428121341.jpg
 waterfall-20250428121457.jpg
lixin@DELTUS:/mnt/c/Users/39204$ binwalk -e dolls.png

General Error: Cannot open file dolls.png (CWD: /mnt/c/Users/39204) : [Errno 2] No such file or directory: 'dolls.png'

lixin@DELTUS:/mnt/c/Users/39204$ binwalk -e dolls.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 594 x 1104, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
272492        0x4286C         Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
651610        0x9F15A         End of Zip archive, footer length: 22

lixin@DELTUS:/mnt/c/Users/39204$ ls  base_images/2_c.jpg
ls: cannot access 'base_images/2_c.jpg': No such file or directory
lixin@DELTUS:/mnt/c/Users/39204$ cd _dolls.jpg.extracted
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ ls
4286C.zip  base_images
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ chmod +x matryoshka.sh
chmod: cannot access 'matryoshka.sh': No such file or directory
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ nano matryoshka.sh
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ chmod +x matryoshka.sh
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ ./matryoshka.sh

General Error: Cannot open file dolls.jpg (CWD: /mnt/c/Users/39204/_dolls.jpg.extracted) : [Errno 2] No such file or directory: 'dolls.jpg'

No se pudo extraer archivos de dolls.jpg
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
./matryoshka.sh
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
^C
No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
^XProcesando: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
^Z
[1]+  Stopped                 ./matryoshka.sh
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ nano matryoshka.sh
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ nano matryoshka2.sh
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ chmod +x matryoshka2.sh
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ ./matryoshka2.sh
Extrayendo archivos de: dolls.jpg

General Error: Cannot open file dolls.jpg (CWD: /mnt/c/Users/39204/_dolls.jpg.extracted) : [Errno 2] No such file or directory: 'dolls.jpg'

No se pudo extraer archivos de dolls.jpg
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip
^C
No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip
^X
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
^X0             0x0             Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
379118        0x5C8EE         End of Zip archive, footer length: 22

No se pudo extraer archivos de 4286C.zip
Procesando: 4286C.zip
Extrayendo archivos de: 4286C.zip
^Z
[2]+  Stopped                 ./matryoshka2.sh
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ [200~ls /mnt/c/Users/39204/_dolls.jpg.extracted/~
[200~ls: command not found
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ ls /mnt/c/Users/39204/_dolls.jpg.extracted/
4286C.zip                 _4286C.zip-146.extracted  _4286C.zip-195.extracted  _4286C.zip-57.extracted
_4286C.zip-0.extracted    _4286C.zip-147.extracted  _4286C.zip-196.extracted  _4286C.zip-58.extracted
_4286C.zip-1.extracted    _4286C.zip-148.extracted  _4286C.zip-197.extracted  _4286C.zip-59.extracted
_4286C.zip-10.extracted   _4286C.zip-149.extracted  _4286C.zip-198.extracted  _4286C.zip-6.extracted
_4286C.zip-100.extracted  _4286C.zip-15.extracted   _4286C.zip-199.extracted  _4286C.zip-60.extracted
_4286C.zip-101.extracted  _4286C.zip-150.extracted  _4286C.zip-2.extracted    _4286C.zip-61.extracted
_4286C.zip-102.extracted  _4286C.zip-151.extracted  _4286C.zip-20.extracted   _4286C.zip-62.extracted
_4286C.zip-103.extracted  _4286C.zip-152.extracted  _4286C.zip-200.extracted  _4286C.zip-63.extracted
_4286C.zip-104.extracted  _4286C.zip-153.extracted  _4286C.zip-201.extracted  _4286C.zip-64.extracted
_4286C.zip-105.extracted  _4286C.zip-154.extracted  _4286C.zip-202.extracted  _4286C.zip-65.extracted
_4286C.zip-106.extracted  _4286C.zip-155.extracted  _4286C.zip-203.extracted  _4286C.zip-66.extracted
_4286C.zip-107.extracted  _4286C.zip-156.extracted  _4286C.zip-204.extracted  _4286C.zip-67.extracted
_4286C.zip-108.extracted  _4286C.zip-157.extracted  _4286C.zip-205.extracted  _4286C.zip-68.extracted
_4286C.zip-109.extracted  _4286C.zip-158.extracted  _4286C.zip-206.extracted  _4286C.zip-69.extracted
_4286C.zip-11.extracted   _4286C.zip-159.extracted  _4286C.zip-207.extracted  _4286C.zip-7.extracted
_4286C.zip-110.extracted  _4286C.zip-16.extracted   _4286C.zip-21.extracted   _4286C.zip-70.extracted
_4286C.zip-111.extracted  _4286C.zip-160.extracted  _4286C.zip-22.extracted   _4286C.zip-71.extracted
_4286C.zip-112.extracted  _4286C.zip-161.extracted  _4286C.zip-23.extracted   _4286C.zip-72.extracted
_4286C.zip-113.extracted  _4286C.zip-162.extracted  _4286C.zip-24.extracted   _4286C.zip-73.extracted
_4286C.zip-114.extracted  _4286C.zip-163.extracted  _4286C.zip-25.extracted   _4286C.zip-74.extracted
_4286C.zip-115.extracted  _4286C.zip-164.extracted  _4286C.zip-26.extracted   _4286C.zip-75.extracted
_4286C.zip-116.extracted  _4286C.zip-165.extracted  _4286C.zip-27.extracted   _4286C.zip-76.extracted
_4286C.zip-117.extracted  _4286C.zip-166.extracted  _4286C.zip-28.extracted   _4286C.zip-77.extracted
_4286C.zip-118.extracted  _4286C.zip-167.extracted  _4286C.zip-29.extracted   _4286C.zip-78.extracted
_4286C.zip-119.extracted  _4286C.zip-168.extracted  _4286C.zip-3.extracted    _4286C.zip-79.extracted
_4286C.zip-12.extracted   _4286C.zip-169.extracted  _4286C.zip-30.extracted   _4286C.zip-8.extracted
_4286C.zip-120.extracted  _4286C.zip-17.extracted   _4286C.zip-31.extracted   _4286C.zip-80.extracted
_4286C.zip-121.extracted  _4286C.zip-170.extracted  _4286C.zip-32.extracted   _4286C.zip-81.extracted
_4286C.zip-122.extracted  _4286C.zip-171.extracted  _4286C.zip-33.extracted   _4286C.zip-82.extracted
_4286C.zip-123.extracted  _4286C.zip-172.extracted  _4286C.zip-34.extracted   _4286C.zip-83.extracted
_4286C.zip-124.extracted  _4286C.zip-173.extracted  _4286C.zip-35.extracted   _4286C.zip-84.extracted
_4286C.zip-125.extracted  _4286C.zip-174.extracted  _4286C.zip-36.extracted   _4286C.zip-85.extracted
_4286C.zip-126.extracted  _4286C.zip-175.extracted  _4286C.zip-37.extracted   _4286C.zip-86.extracted
_4286C.zip-127.extracted  _4286C.zip-176.extracted  _4286C.zip-38.extracted   _4286C.zip-87.extracted
_4286C.zip-128.extracted  _4286C.zip-177.extracted  _4286C.zip-39.extracted   _4286C.zip-88.extracted
_4286C.zip-129.extracted  _4286C.zip-178.extracted  _4286C.zip-4.extracted    _4286C.zip-89.extracted
_4286C.zip-13.extracted   _4286C.zip-179.extracted  _4286C.zip-40.extracted   _4286C.zip-9.extracted
_4286C.zip-130.extracted  _4286C.zip-18.extracted   _4286C.zip-41.extracted   _4286C.zip-90.extracted
_4286C.zip-131.extracted  _4286C.zip-180.extracted  _4286C.zip-42.extracted   _4286C.zip-91.extracted
_4286C.zip-132.extracted  _4286C.zip-181.extracted  _4286C.zip-43.extracted   _4286C.zip-92.extracted
_4286C.zip-133.extracted  _4286C.zip-182.extracted  _4286C.zip-44.extracted   _4286C.zip-93.extracted
_4286C.zip-134.extracted  _4286C.zip-183.extracted  _4286C.zip-45.extracted   _4286C.zip-94.extracted
_4286C.zip-135.extracted  _4286C.zip-184.extracted  _4286C.zip-46.extracted   _4286C.zip-95.extracted
_4286C.zip-136.extracted  _4286C.zip-185.extracted  _4286C.zip-47.extracted   _4286C.zip-96.extracted
_4286C.zip-137.extracted  _4286C.zip-186.extracted  _4286C.zip-48.extracted   _4286C.zip-97.extracted
_4286C.zip-138.extracted  _4286C.zip-187.extracted  _4286C.zip-49.extracted   _4286C.zip-98.extracted
_4286C.zip-139.extracted  _4286C.zip-188.extracted  _4286C.zip-5.extracted    _4286C.zip-99.extracted
_4286C.zip-14.extracted   _4286C.zip-189.extracted  _4286C.zip-50.extracted   _4286C.zip.extracted
_4286C.zip-140.extracted  _4286C.zip-19.extracted   _4286C.zip-51.extracted   base_images
_4286C.zip-141.extracted  _4286C.zip-190.extracted  _4286C.zip-52.extracted   matryoshka.sh
_4286C.zip-142.extracted  _4286C.zip-191.extracted  _4286C.zip-53.extracted   matryoshka2.sh
_4286C.zip-143.extracted  _4286C.zip-192.extracted  _4286C.zip-54.extracted
_4286C.zip-144.extracted  _4286C.zip-193.extracted  _4286C.zip-55.extracted
_4286C.zip-145.extracted  _4286C.zip-194.extracted  _4286C.zip-56.extracted
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ Matryoshka doll
Author: Susie/Pandu

Due in: 1 day, 12 hours
Assignment: Forensic 3 (2025 - Fundamentos de la Seguridad de la Informacion IC EJ25)
Description
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: this
Matryoshka: command not found
Author:: command not found
Command 'Due' not found, did you mean:
  command 'vue' from snap vue (3.3.0)
  command 'rue' from snap darkdimension-rue (1.0.7)
  command 'due' from deb due (3.0.0-1)
See 'snap info <snapname>' for additional versions.
-bash: syntax error near unexpected token `('
Description: command not found
>
>
>
> ^C
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ cd ..
lixin@DELTUS:/mnt/c/Users/39204$ binwalk -e dolls.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 594 x 1104, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
272492        0x4286C         Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
651610        0x9F15A         End of Zip archive, footer length: 22

lixin@DELTUS:/mnt/c/Users/39204$ cd _dolls.jpg.extracted
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ unzip 4286C.zip
Archive:  4286C.zip
replace base_images/2_c.jpg? [y]es, [n]o, [A]ll, [N]one, [r]ename: yes
  inflating: base_images/2_c.jpg
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted$ cd base_images
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images$ binwalk -e 2_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 526 x 1106, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
187707        0x2DD3B         Zip archive data, at least v2.0 to extract, compressed size: 196042, uncompressed size: 201444, name: base_images/3_c.jpg
383804        0x5DB3C         End of Zip archive, footer length: 22
383915        0x5DBAB         End of Zip archive, footer length: 22

lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images$ cd _2_c.jpg.extracted
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted$ ls
unzip [nombre_del_zip].zip
2DD3B.zip  base_images
unzip:  cannot find or open [nombre_del_zip].zip, [nombre_del_zip].zip.zip or [nombre_del_zip].zip.ZIP.

No zipfiles found.
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted$ ls
2DD3B.zip  base_images
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted$ binwalk -e 3_c.jpg
cd _3_c.jpg.extracted
ls
unzip [nombre_del_zip].zip

General Error: Cannot open file 3_c.jpg (CWD: /mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted) : [Errno 2] No such file or directory: '3_c.jpg'

-bash: cd: _3_c.jpg.extracted: No such file or directory
2DD3B.zip  base_images
unzip:  cannot find or open [nombre_del_zip].zip, [nombre_del_zip].zip.zip or [nombre_del_zip].zip.ZIP.

No zipfiles found.
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted$ ls
unzip [nombre_del_zip].zip
2DD3B.zip  base_images
unzip:  cannot find or open [nombre_del_zip].zip, [nombre_del_zip].zip.zip or [nombre_del_zip].zip.ZIP.

No zipfiles found.
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted$ ls
2DD3B.zip  base_images
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted$
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted$ unzip 2DD3B.zip
Archive:  2DD3B.zip
replace base_images/3_c.jpg? [y]es, [n]o, [A]ll, [N]one, [r]ename: yes
  inflating: base_images/3_c.jpg
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted$ cd base_images
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images$ ls
3_c.jpg
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images$ binwalk -e 3_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 428 x 1104, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
123606        0x1E2D6         Zip archive data, at least v2.0 to extract, compressed size: 77650, uncompressed size: 79807, name: base_images/4_c.jpg
201422        0x312CE         End of Zip archive, footer length: 22

lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images$ cd _3_c.jpg.extracted
ls
1E2D6.zip  base_images
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted$ unzip 1E2D6.zip
Archive:  1E2D6.zip
replace base_images/4_c.jpg? [y]es, [n]o, [A]ll, [N]one, [r]ename: yes
  inflating: base_images/4_c.jpg
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted$ unzip 1E2D6.zip
Archive:  1E2D6.zip
replace base_images/4_c.jpg? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: base_images/4_c.jpg
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted$ cd base_images
binwalk -e 4_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 320 x 768, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
79578         0x136DA         Zip archive data, at least v2.0 to extract, compressed size: 63, uncompressed size: 81, name: flag.txt
79785         0x137A9         End of Zip archive, footer length: 22

lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images$ unzip 136DA.zip
unzip:  cannot find or open 136DA.zip, 136DA.zip.zip or 136DA.zip.ZIP.
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images$ ls
4_c.jpg  _4_c.jpg.extracted
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images$ cat flag.txt
cat: flag.txt: No such file or directory
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images$ cd _4_c.jpg.extracted
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images/_4_c.jpg.extracted$ ls
136DA.zip  flag.txt
lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images/_4_c.jpg.extracted$ cat flag.txt
picoCTF{96fac089316e094d41ea046900197662}lixin@DELTUS:/mnt/c/Users/39204/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images/_4_c.jpg.extracted$

````` 




# 0  MacroHard WeakEdge

# DESC

I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm](https://mercury.picoctf.net/static/2e739f9e0dc9f4c1556ea6b033c3ec8e/Forensics%20is%20fun.pptm)
# SOLUCION

Usaré Linux (Kali Linux) porque estoy aprendiendo Linux, si usas Windows o Mac entonces está bien, solo consigue las herramientas alternativas para realizar el trabajo.

![](https://miro.medium.com/v2/resize:fit:875/1*kKdX8vXec1yhWmKw9PIbfg.png)

Objetivo: encontrar la bandera que está oculta dentro del archivo “Forensic is fun.pptm”.

Primero, necesito descargar el archivo a mi máquina local ejecutando el comando

> wget [https://mercury.picoctf.net/static/2e739f9e0dc9f4c1556ea6b033c3ec8e/La ciencia forense es divertida.pptm](https://mercury.picoctf.net/static/2e739f9e0dc9f4c1556ea6b033c3ec8e/Forensics%20is%20fun.pptm)

![](https://miro.medium.com/v2/resize:fit:875/1*r0SA7DgVeVBDannYJCeqxg.png)

Conseguir el archivo en la máquina local

Entonces, ¿qué es?

> archivo ./Forensics\is\fun.pptm

![](https://miro.medium.com/v2/resize:fit:875/1*7GlNSaNOlr1X-WXHGhCFYA.png)

Ejecutar el comando Archivo para inspeccionar el archivo

Busquemos en Google qué es un archivo .pptm.

![](https://miro.medium.com/v2/resize:fit:875/1*aJ4IUiVa-NoudT7NKEu-dg.png)

¡Ajá! Es simplemente un archivo de PowerPoint con macros habilitadas. Por si no sabes qué es una macro, es una función que te permite escribir código para automatizar tareas. Y eso también me impresionó; pensé que debía ser la clave, ya que el título también contiene la palabra "macro". Así que abramos el archivo con LibreOffice 7.2 y veamos qué contiene la macro.

![](https://miro.medium.com/v2/resize:fit:875/1*Xsalfo9OF267fbvuRiya6w.png)

Inspeccionar la macro de un archivo con LibreOffice 7.2

Sí, fui muy ingenuo y pensé que la bandera debería estar en el contenido de la macro, pero no había nada; simplemente el autor nos hizo creer que la bandera sí estaba en el contenido de la macro. Bueno, llegamos al final, ¿dónde podría estar la bandera?

Luego busqué en Google "macros oculta" del formato de archivo pptm, pero no pude encontrar lo que necesitábamos, así que investigué nuevamente sobre el formato de archivo pptm en sí, no sobre la "bandera oculta" que podría contener, sino sobre el formato de archivo en sí.

Tuve suerte y encontré este enlace sobre [el formato de archivo pptm;](https://docs.fileformat.com/presentation/pptm/) en resumen, el archivo ppt o pptm se puede descomprimir cambiando la extensión a .zip y usando herramientas para descomprimir el archivo.

![](https://miro.medium.com/v2/resize:fit:875/1*Qnis9gfALdbK45Qq-lNwDw.png)

formato de archivo pptm

Vamos a descomprimirlo

> descomprimir ./Forensics\is\fun.pptm

![](https://miro.medium.com/v2/resize:fit:875/1*LN_Ebw9FUU1yZ7qGmvIY5w.png)

Recibimos varios archivos; nuestro archivo de PowerPoint contiene principalmente archivos .xml y .rel. Así que busquemos todos los archivos que no sean .xlm ni .rel.

Aquí uso la herramienta Buscador difuso para buscar archivos.

![](https://miro.medium.com/v2/resize:fit:743/1*xISs-8R-uc61s9fzIsDmqg.png)

Tenemos ppt/vbaProject.bin y ppt/slideMasters/hidden que parecen realmente sospechosos, veamos qué contienen.

> gato ./ppt/vbaProject.bin

![](https://miro.medium.com/v2/resize:fit:875/1*Xfbgfdp2KhCgQGUWbZuvXw.png)

Mmm... El archivo .vba es en realidad la macro que revisamos antes. Podemos ver el "not_flag" que se mostró antes. No contiene el indicador.

¿Qué pasa con el archivo ppt/slideMasters/oculto?

> gato ./ppt/slideMasters/hidden

![](https://miro.medium.com/v2/resize:fit:875/1*YPQdwksmLBs-dSDuSEDaXw.png)

Esta es nuestra última esperanza, pero ¿qué es esto? ¿Un montón de caracteres aleatorios? Quizás sea la bandera, pero está codificada. Así que intenté decodificarla en base64 y obtuve la bandera.

Conseguimos la bandera: picoCTF{D1d_u_kn0w_ppts_r_z1p5}


# 0

# DESC


# SOLUCION

````` python

````` 


