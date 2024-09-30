
Un **subdomain takeover** ocurre cuando un subdominio de un sitio web apunta a un servicio externo (como AWS, GitHub, Heroku, etc.), pero ese servicio ya no está activo o en uso. Esto permite a un atacante reclamar el servicio huérfano y tomar control del subdominio, lo que puede llevar a la inyección de contenido malicioso, phishing, o simplemente desacreditar el dominio principal.

### Ejemplo 1: GitHub Pages

Imagina que una empresa tiene un subdominio llamado `blog.ejemplo.com` que está configurado para apuntar a una página de GitHub Pages. Si la empresa elimina el repositorio de GitHub pero no elimina la entrada DNS que apunta al subdominio, un atacante podría crear un repositorio en su propia cuenta de GitHub llamado `blog` y reclamar el subdominio. Esto permitiría al atacante cargar contenido que aparecería en `blog.ejemplo.com`.

### Ejemplo 2: AWS S3

Supongamos que un subdominio como `media.ejemplo.com` apunta a un bucket de Amazon S3 para almacenar imágenes. Si el bucket es eliminado pero la entrada DNS aún apunta a S3, un atacante podría crear un bucket con el mismo nombre (`media`) en su propia cuenta de S3 y hacerse con el control del subdominio, permitiendo cargar archivos o scripts maliciosos.

### Cómo ocurre:

1. La empresa configura un subdominio para apuntar a un servicio externo.
2. El servicio externo es eliminado o dejado de usar.
3. El registro DNS aún apunta al servicio externo, pero este ya no está en uso.
4. Un atacante detecta el subdominio huérfano y reclama el control del servicio.

### Herramientas para detectar subdomain takeover:

- **Subjack** y **Subfinder**: Para escanear y detectar subdominios susceptibles a ser tomados.

El proceso de detección es similar a otras técnicas de bug bounty hunting, con el uso de herramientas automatizadas y una buena comprensión de los registros DNS.

```bash
subfinder -dL domains.txt -all -recursive -o subs.txt

subfinder -d example.com -all -recursive -o subs.txt

cat subs.txt | sort -u | tee -a all-subs.txt 

cat all-subs.txt | httpx | tee -a live-subs.txt 

subjack -w live-subs.txt -t 100 -timeout 30 -o potential_takeovers.txt -ssl -v

```
