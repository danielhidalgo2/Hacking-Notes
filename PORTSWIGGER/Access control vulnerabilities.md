
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

