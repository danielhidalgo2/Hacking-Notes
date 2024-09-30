

### 1\. **Prueba de Manipulación del Algoritmo (CVE-2015-2951)**

Esta prueba busca explotar implementaciones incorrectas del algoritmo `alg`, en particular el uso de `none`, que podría permitir la creación de un token sin firma válida.

**Comando:**

bash

Copiar código

`python3 jwt_tool.py <JWT> -X a`

Esto intentará cambiar el algoritmo a `none` y probar si la aplicación acepta el token sin validación de firma.

### 2\. **Vulnerabilidad RS/HS256 Public Key Mismatch (CVE-2016-10555)**

Esta vulnerabilidad surge cuando una aplicación acepta la clave pública como si fuera una clave secreta HMAC, permitiendo firmar un token con una clave pública conocida.

**Comando:**

bash

Copiar código

`python3 jwt_tool.py <JWT> -X c`

Esto intentará aprovechar la mala configuración usando la clave pública para firmar un token.

### 3\. **Inyección de Clave Pública a través de `kid` (Key ID) (CVE-2018-0114)**

Si la aplicación usa `kid` para seleccionar la clave para la verificación de la firma, y el valor de `kid` es controlable por el usuario, es posible que se pueda inyectar una clave pública personalizada.

**Comando:**

bash

Copiar código

`python3 jwt_tool.py <JWT> -I -hc kid -hv "<your_kid_value>" -X i`

Prueba inyectar un `kid` que apunte a una clave pública que tú controles.

### 4\. **Ataque de Claves Débiles (Brute Force de Secretos)**

Este ataque intenta descubrir claves débiles usando un ataque de diccionario. Es útil cuando el JWT usa HMAC con una clave secreta predecible.

**Comando:**

bash

Copiar código

`python3 jwt_tool.py <JWT> -S -d /ruta/del/diccionario.txt`

Esto ejecutará un ataque de fuerza bruta para intentar adivinar el secreto usado para firmar el token.

### 5\. **Fuzzing de Valores de Claves**

Puedes realizar fuzzing sobre diferentes claves del payload para detectar comportamientos inesperados o errores en la lógica de la aplicación.

**Comando:**

bash

Copiar código

`python3 jwt_tool.py <JWT> -I -hc <claim_name> -hf <fuzzing_file.txt>`

Este comando realizará fuzzing en la clave `claim_name` usando los valores especificados en `fuzzing_file.txt`.

### 6\. **Timestamp Tampering (Manipulación de Tiempos)**

Puedes manipular las marcas de tiempo (`iat`, `exp`, `nbf`) para probar si la aplicación maneja correctamente la validación de tiempo.

**Comando:**

bash

Copiar código

`python3 jwt_tool.py <JWT> -I -hc iat -hv <new_iat_value>`

Modifica `iat`, `exp`, o `nbf` para ver si la aplicación sigue aceptando el token.

### 7\. **Escaneo Automático con el Playbook Scan**

Utiliza el modo de escaneo del playbook para realizar una evaluación automática de las vulnerabilidades conocidas.

**Comando:**

bash

Copiar código

`python3 jwt_tool.py -t https://example.com -rc "jwt=<JWT>" -M pb`

Esto ejecutará una serie de pruebas automáticas en el JWT proporcionado.

### 8\. **Prueba de Verificación de Firma**

Si tienes acceso a una clave pública o un secreto compartido, puedes intentar verificar la firma del JWT para asegurar que esté correctamente configurada.

**Comando:**

bash

Copiar código

`python3 jwt_tool.py <JWT> -V -pk /ruta/a/clave_publica.pem`

Esto verificará si la firma del JWT es válida usando la clave pública proporcionada.

### 9\. **Creación y Firma de Tokens Personalizados**

Puedes generar tu propio token personalizado y firmarlo usando una clave privada conocida.

**Comando:**

bash

Copiar código

`python3 jwt_tool.py -C -pk /ruta/a/clave_privada.pem -P '{"sub":"admin"}'`

Esto crea un nuevo JWT con el payload especificado y lo firma usando la clave privada.

