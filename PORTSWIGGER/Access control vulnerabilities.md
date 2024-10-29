
## LAB 1

Enumerando directorios encontramos el tipico robots.txt en el nos da la pista del directorio `/administrator-panel` en el accedemos a permisos que no deberiamos tener

## LAB 2

Capturamos con Burp Suite la petición, esto nos revela el codigo fuente con un posible directorio para ser admin
`/admin-1xgccv`

## LAB 3

Nos dicen que hay un panel de administrador en /admin, capturando la petición, vemos que hay un parámetro `Admin=false`  simplemente lo modificamos a true y enviamos la peticion.

## LAB 4

Esta vez para ser admin neccesitamos cambiar el roleid, el usuario normal tiene un roleid:1, con burp podemos modificar facilmente añadiendo al JSON roleid:2 y ya seremos admin.

## LAB 5

Nos piden que obtengamos el API Key de carlos para ello simplemente deberemos modificar el id que aparece en la URL:
`my-account?id=carlos`

## LAB 6

En este caso el id no es predecible, observando la web vemos que hay un post hecho por carlos que nos revela su id `id=17dee894-60bf-4eed-8e13-9bd182d9d4d3`

## LAB 7

Cambiando el id a carlos vemos que nos redirige al home, pero si lo capturamos con el repeater y miramos el código, nos revela el API Key.

## LAB 8

En este lab nos piden que averiguemos la constraseña de administrator, esto lo logramos cambiando el id a administrator y capturandolo con Burp, se nos leakea en el codigo fuente la contraseña.

# Lab: URL-based access control can be circumvented


1. Try to load `/admin` and observe that you get blocked. Notice that the response is very plain, suggesting it may originate from a front-end system.
2. Send the request to Burp Repeater. Change the URL in the request line to `/` and add the HTTP header `X-Original-URL: /invalid`. Observe that the application returns a "not found" response. This indicates that the back-end system is processing the URL from the `X-Original-URL` header.
3. Change the value of the `X-Original-URL` header to `/admin`. Observe that you can now access the admin page.
4. To delete `carlos`, add `?username=carlos` to the real query string, and change the `X-Original-URL` path to `/admin/delete`.
