
## LAB 1

Ocurre cuando tratamos de enviar la petición a otro recurso que tiene la web en este caso localhost y borramos a Carlos

```
http://localhost/admin/delete?username=carlos
```


## LAB 2

A otros recursos que podemos acceder son otras ips que este conectadas la máquina, suponiendo esto:
http://192.168.0.1:8080/admin
Lo que podemos intentar hacer es con intruder( CTRL +i) tratar de descubrir otros hosts o IPs mandando un ataque desde el 0 a 254


## LAB 3

Para resolver este deberemos tener el burpsuite colaborator.
Se trata en la peticion modificar el referer para que nos redirija a otro sitio web como http://google.es

## LAB 4

En este tratamos de bypassear posibles whitelists, por un parte "localhost" no le gusta entonces tratamos de probar 127.0.0.1 o 127.0.8.2 etc, pero tampoco funciona. Otra forma es convertirlo en hexadecimal 7F000001 pero tampoco. En última instancia otra forma de representar esta ip es directamente poner 127.1 y esto si que funciona.
Por otra parte tenemos que bypassear la palabra admin que no le gusta, en este caso url encodeamos la a y después el % también que suele dar problemas:
```
http://127.1/%2561dmin/delete?username=carlos
```


## LAB 5

En este lab aprovechamos de un open redirect + SSRF. El Open redirect se acontece cuando en una petición encontramos lo siguiente:
/product/nextProduct?currentProductId=2&path=/product?productId=3
La variable path nos redirige a otros directorios de la web.
Nosotros podemos tratar de redirigir la petición a el sitio web que prefiramos en este caso google.es
/product/nextProduct?currentProductId=2&path=http://google.es
Sabiendo esto, en la otra peticion vulnerable a SSRF deberemos hacer lo mismo que hemos estado haciendo conociendo que nos va a redirigir a donde deseemos:

```
/product/nextProduct?currentProductId=2%26path=http://192.168.0.12:8080/admin/delete?username=carlos
```

Debemos tener en cuenta los & para urlencodearlos.

## LAB 6

En este caso cuenta con una proteccion anti SSRF nos dice que la peticion debe tener stock.weliketoshop.net, deberemos probar si la autenticación en la url existe http://user:password@stock.weliketoshop.net:8080/product/stock/check?productId=1%26storeId=1 
Vemos que si entonce probamos con localhost http://localhost@stock.weliketoshop.net:8080/product/stock/check?productId=1%26storeId=1 
Por último para bypassear esto obviamos el resto de la peticion con "#" este lo deberemos de urlencodear 2 veces y ya podremos acceder al recurso deseado:

```
http://localhost%2523@stock.weliketoshop.net:8080/admin/delete?username=carlos
```
