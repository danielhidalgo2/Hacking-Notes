Cuando obtenemos un pem y un txt de la maquina victima con ssl podemos:
┌──(kali㉿kali)-[~/strange]

└─$ openssl rsautl -decrypt -in private.txt -out privateOUT.txt -inkey private_key.pem

The command rsautl was deprecated in version 3.0. Use 'pkeyutl' instead.

┌──(kali㉿kali)-[~/strange]

└─$ cat privateOUT.txt

demogorgon