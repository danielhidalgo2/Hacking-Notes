#### HTTP Headers

  Active Infrastructure Identification

```shell-session
hidalg0dd@htb[/htb]$ curl -I "http://${TARGET}"

HTTP/1.1 200 OK
Date: Thu, 23 Sep 2021 15:10:42 GMT
Server: Apache/2.4.25 (Debian)
X-Powered-By: PHP/7.3.5
Link: <http://192.168.10.10/wp-json/>; rel="https://api.w.org/"
Content-Type: text/html; charset=UTF-8
```

#### WhatWeb

  Active Infrastructure Identification

```shell-session
hidalg0dd@htb[/htb]$ whatweb -a3 https://www.facebook.com -v

WhatWeb report for https://www.facebook.com
Status    : 200 OK
Title     : <None>
IP        : 31.13.92.36
Country   : IRELAND, IE

Summary   : Strict-Transport-Security[max-age=15552000; preload], PasswordField[pass], Script[text/javascript], X-XSS-Protection[0], HTML5, X-Frame-Options[DENY], Meta-Refresh-Redirect[/?_fb_noscript=1], UncommonHeaders[x-fb-rlafr,x-content-type-options,x-fb-debug,alt-svc]

Detected Plugins:
[ HTML5 ]
	HTML version 5, detected by the doctype declaration


[ Meta-Refresh-Redirect ]
	Meta refresh tag is a deprecated URL element that can be
	used to optionally wait x seconds before reloading the
	current page or loading a new page. More info:
	https://secure.wikimedia.org/wikipedia/en/wiki/Meta_refresh

	String       : /?_fb_noscript=1

[ PasswordField ]
	find password fields

	String       : pass (from field name)

[ Script ]
	This plugin detects instances of script HTML elements and
	returns the script language/type.

	String       : text/javascript

[ Strict-Transport-Security ]
	Strict-Transport-Security is an HTTP header that restricts
	a web browser from accessing a website without the security
	of the HTTPS protocol.

	String       : max-age=15552000; preload

[ UncommonHeaders ]
	Uncommon HTTP server headers. The blacklist includes all
	the standard headers and many non standard but common ones.
	Interesting but fairly common headers should have their own
	plugins, eg. x-powered-by, server and x-aspnet-version.
	Info about headers can be found at www.http-stats.com

	String       : x-fb-rlafr,x-content-type-options,x-fb-debug,alt-svc (from headers)

[ X-Frame-Options ]
	This plugin retrieves the X-Frame-Options value from the
	HTTP header. - More Info:
	http://msdn.microsoft.com/en-us/library/cc288472%28VS.85%29.
	aspx

	String       : DENY

[ X-XSS-Protection ]
	This plugin retrieves the X-XSS-Protection value from the
	HTTP header. - More Info:
	http://msdn.microsoft.com/en-us/library/cc288472%28VS.85%29.
	aspx

	String       : 0

HTTP Headers:
	HTTP/1.1 200 OK
	Vary: Accept-Encoding
	Content-Encoding: gzip
	x-fb-rlafr: 0
	Pragma: no-cache
	Cache-Control: private, no-cache, no-store, must-revalidate
	Expires: Sat, 01 Jan 2000 00:00:00 GMT
	X-Content-Type-Options: nosniff
	X-XSS-Protection: 0
	X-Frame-Options: DENY
	Strict-Transport-Security: max-age=15552000; preload
	Content-Type: text/html; charset="utf-8"
	X-FB-Debug: r2w+sMJ7lVrMjS/ETitC6cNpJXma0r3fbt0rIlnTPAfQqTc+U4PQopVL7sR/6YA/ZKRkqP1wMPoFdUfMBP1JSA==
	Date: Wed, 06 Oct 2021 09:04:27 GMT
	Alt-Svc: h3=":443"; ma=3600, h3-29=":443"; ma=3600,h3-27=":443"; ma=3600
	Connection: close

WhatWeb report for https://www.facebook.com/?_fb_noscript=1
Status    : 200 OK
Title     : <None>
IP        : 31.13.92.36
Country   : IRELAND, IE

Summary   : Cookies[noscript], Strict-Transport-Security[max-age=15552000; preload], PasswordField[pass], Script[text/javascript], X-XSS-Protection[0], HTML5, X-Frame-Options[DENY], UncommonHeaders[x-fb-rlafr,x-content-type-options,x-fb-debug,alt-svc]

Detected Plugins:
[ Cookies ]
	Display the names of cookies in the HTTP headers. The
	values are not returned to save on space.

	String       : noscript

[ HTML5 ]
	HTML version 5, detected by the doctype declaration


[ PasswordField ]
	find password fields

	String       : pass (from field name)

[ Script ]
	This plugin detects instances of script HTML elements and
	returns the script language/type.

	String       : text/javascript

[ Strict-Transport-Security ]
	Strict-Transport-Security is an HTTP header that restricts
	a web browser from accessing a website without the security
	of the HTTPS protocol.

	String       : max-age=15552000; preload

[ UncommonHeaders ]
	Uncommon HTTP server headers. The blacklist includes all
	the standard headers and many non standard but common ones.
	Interesting but fairly common headers should have their own
	plugins, eg. x-powered-by, server and x-aspnet-version.
	Info about headers can be found at www.http-stats.com

	String       : x-fb-rlafr,x-content-type-options,x-fb-debug,alt-svc (from headers)

[ X-Frame-Options ]
	This plugin retrieves the X-Frame-Options value from the
	HTTP header. - More Info:
	http://msdn.microsoft.com/en-us/library/cc288472%28VS.85%29.
	aspx

	String       : DENY

[ X-XSS-Protection ]
	This plugin retrieves the X-XSS-Protection value from the
	HTTP header. - More Info:
	http://msdn.microsoft.com/en-us/library/cc288472%28VS.85%29.
	aspx

	String       : 0

HTTP Headers:
	HTTP/1.1 200 OK
	Vary: Accept-Encoding
	Content-Encoding: gzip
	Set-Cookie: noscript=1; path=/; domain=.facebook.com; secure
	x-fb-rlafr: 0
	Pragma: no-cache
	Cache-Control: private, no-cache, no-store, must-revalidate
	Expires: Sat, 01 Jan 2000 00:00:00 GMT
	X-Content-Type-Options: nosniff
	X-XSS-Protection: 0
	X-Frame-Options: DENY
	Strict-Transport-Security: max-age=15552000; preload
	Content-Type: text/html; charset="utf-8"
	X-FB-Debug: 7bEryjJ3tsTb/ap562d5L6KUJyJJ3bJh9XoamIo2lCVrX4cK/VAGbLx7muaAwnyobVm9myC3fQ+CXJqkk0eacg==
	Date: Wed, 06 Oct 2021 09:04:31 GMT
	Alt-Svc: h3=":443"; ma=3600, h3-29=":443"; ma=3600,h3-27=":443"; ma=3600
	Connection: close
```

#### Installing WafW00f

  Active Infrastructure Identification

```shell-session
hidalg0dd@htb[/htb]$ sudo apt install wafw00f -y
```

We can use options like `-a` to check all possible WAFs in place instead of stopping scanning at the first match, read targets from an input file via the `-i` flag, or proxy the requests using the `-p` option.

  Active Infrastructure Identification

```shell-session
hidalg0dd@htb[/htb]$ wafw00f -v https://www.tesla.com

                   ______
                  /      \
                 (  Woof! )
                  \  ____/                      )
                  ,,                           ) (_
             .-. -    _______                 ( |__|
            ()``; |==|_______)                .)|__|
            / ('        /|\                  (  |__|
        (  /  )        / | \                  . |__|
         \(_)_))      /  |  \                   |__|

                    ~ WAFW00F : v2.1.0 ~
    The Web Application Firewall Fingerprinting Toolkit

[*] Checking https://www.tesla.com
[+] The site https://www.tesla.com is behind CacheWall (Varnish) WAF.
[~] Number of requests: 2
```

