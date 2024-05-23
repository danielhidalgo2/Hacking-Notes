wfuzz -c -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt --hc 400,404,403,302 -H "Host: FUZZ.hidden.lab" -u http://hidden.lab -t 100 
