Hacemos un escaneo básico con nmap:

![[Pasted image 20240425151629.png]]
Como el puerto smb esta abierto obtenemos el dominio:
![[Pasted image 20240425151843.png]]Ahora en etc/hosts hacemos nano y metemos el dominio
![[Pasted image 20240425151949.png]]
Con smbmap y smbclient conseguimos entrar:
![[Pasted image 20240425152150.png]]
Enumerando obtenemos este xml y con esta tool hacemos decrypt y obtenemos la password
![[Pasted image 20240425152451.png]]
Despues de esto obtenemos el user and password y con rpcclient podemos enumerar
![[Pasted image 20240425153129.png]]
Como el usuario es TGS con impacket hacemos esto:
![[Pasted image 20240425153700.png]]
![[Pasted image 20240425153729.png]]

Luego con john podemos crackear el hash:
![[Pasted image 20240425153840.png]]

Luego con impacket psexec obtenemos una cmd:

![[Pasted image 20240425154030.png]]

  