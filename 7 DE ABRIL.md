# 01 Glory of the Garden
# DESC
This [garden](https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg) contains more than it seems.

# SOLUCION

````` python
	lixin@DELTUS:/mnt/c/Users/39204$ wget https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg
--2025-04-07 12:15:55--  https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2295192 (2.2M) [application/octet-stream]
Saving to: ‘garden.jpg’

garden.jpg                    100%[=================================================>]   2.19M   940KB/s    in 2.4s

2025-04-07 12:16:01 (940 KB/s) - ‘garden.jpg’ saved [2295192/2295192]

lixin@DELTUS:/mnt/c/Users/39204$ strings -n 18 garden.jpg
Copyright (c) 1998 Hewlett-Packard Company
IEC http://www.iec.ch
IEC http://www.iec.ch
.IEC 61966-2.1 Default RGB colour space - sRGB
.IEC 61966-2.1 Default RGB colour space - sRGB
,Reference Viewing Condition in IEC61966-2.1
,Reference Viewing Condition in IEC61966-2.1
%&'()*456789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
&'()*56789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
Here is a flag "picoCTF{more_than_m33ts_the_3y3eBdBd2cc}"
lixin@DELTUS:/mnt/c/Users/39204$
````` 




# 02 So Meta

Find the flag in this [picture](https://jupiter.challenges.picoctf.org/static/916b07b4c87062c165ace1d3d31ef655/pico_img.png).
# SOLUCION

````` python
lixin@DELTUS:/mnt/c/Users/39204$ wget https://jupiter.challenges.picoctf.org/static/916b07b4c87062c165ace1d3d31ef655/pico_img.png
--2025-04-07 12:19:45--  https://jupiter.challenges.picoctf.org/static/916b07b4c87062c165ace1d3d31ef655/pico_img.png
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 108795 (106K) [application/octet-stream]
Saving to: ‘pico_img.png’

pico_img.png                  100%[=================================================>] 106.25K   285KB/s    in 0.4s

2025-04-07 12:19:47 (285 KB/s) - ‘pico_img.png’ saved [108795/108795]

lixin@DELTUS:/mnt/c/Users/39204$ strings -n 18 pico_img.png
"iTXtXML:com.adobe.xmp
" id="W5M0MpCehiHzreSzNTczkc9d"?> <x:xmpmeta xmlns:x="adobe:ns:meta/" x:xmptk="Adobe XMP Core 5.3-c011 66.145661, 2012/02/06-14:56:27        "> <rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"> <rdf:Description rdf:about="" xmlns:xmp="http://ns.adobe.com/xap/1.0/" xmlns:xmpMM="http://ns.adobe.com/xap/1.0/mm/" xmlns:stRef="http://ns.adobe.com/xap/1.0/sType/ResourceRef#" xmp:CreatorTool="Adobe Photoshop CS6 (Windows)" xmpMM:InstanceID="xmp.iid:A5566E73B2B811E8BC7F9A4303DF1F9B" xmpMM:DocumentID="xmp.did:A5566E74B2B811E8BC7F9A4303DF1F9B"> <xmpMM:DerivedFrom stRef:instanceID="xmp.iid:A5566E71B2B811E8BC7F9A4303DF1F9B" stRef:documentID="xmp.did:A5566E72B2B811E8BC7F9A4303DF1F9B"/> </rdf:Description> </rdf:RDF> </x:xmpmeta> <?xpacket end="r"?>
picoCTF{s0_m3ta_d8944929}K
lixin@DELTUS:/mnt/c/Users/39204$
````` 


#  03 shark on wire 1
# DESC

We found this [packet capture](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap). Recover the flag.
# SOLUCION

INSTALE WIRESHARCK 
DESCARGE EL ARCHIVO 
LO ABRI CON  wireshark capture.pcap
BUSQUE UN ARCHIVO UDP 
LO FILTRE POR PACKETES Y ME DIO LA BANDERA
````` python
picoCTF{StaT31355_636f6e6e}
````` 


# 04 extensions
# DESC

This is a really weird text file [TXT](https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt)? Can you find the flag?
# SOLUCION

DESCARGE EL ARCHIVO 
LE CAMVIE LA EXTENCION DE .TXT A .PNG
ABRI LA IMAGEN Y AHY VENIA EL TXT

````` python


picoCTF{now_you_know_about_extensions}
````` 

#   05 What Lies Within
# DESC
There's something in the [building](https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png). Can you retrieve the flag?

# SOLUCION

ME FUI A LA PAGINA https://stylesuxx.github.io/steganography/
DESCARGE LA IMAGEN
LA PEGE EN LA PAGINA Y LE DI DECODIFICAR 
Y LISTO
````` python

picoCTF{h1d1ng_1n_th3_b1t5}

````` 








