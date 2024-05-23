#### CrackMapExec Usage

The general format for using CrackMapExec is as follows:

  Network Services

```shell-session
hidalg0dd@htb[/htb]$ crackmapexec <proto> <target-IP> -u <user or userlist> -p <password or passwordlist>
```

  Network Services

```shell-session
hidalg0dd@htb[/htb]$ crackmapexec winrm 10.129.42.197 -u user.list -p password.list
```