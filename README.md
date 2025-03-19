# ninjaDorks

`ninjaDorks` es una herramienta de línea de comandos diseñada para automatizar la búsqueda de dorks en motores de búsqueda como Google y DuckDuckGo, así como realizar búsquedas inteligentes utilizando modelos de IA. También permite la generación de dorks mediante inteligencia artificial y la automatización de búsquedas con Selenium.

## Características

-   **Búsqueda en Google y DuckDuckGo:** Realiza búsquedas automatizadas utilizando dorks y exporta los resultados en formato JSON o HTML.
-   **Descarga de archivos:** Descarga archivos de los resultados de búsqueda basados en extensiones especificadas.
-   **Generación de dorks con IA:** Genera dorks automáticamente a partir de descripciones proporcionadas por el usuario, utilizando modelos de IA como GPT, GPT-4, Gemini y modelos locales.
-   **Búsqueda inteligente en archivos:** Realiza búsquedas inteligentes en archivos locales utilizando modelos de IA.
-   **Automatización con Selenium:** Automatiza la búsqueda en Google utilizando un navegador web a través de Selenium.
-   **Configuración fácil:** Configura las claves de API y otros parámetros a través de un archivo `.env`.

## Requisitos

-   Python 3.6+
-   Dependencias listadas en `requirements.txt` (instalar con `pip install -r requirements.txt`).
-   Claves de API de Google Custom Search, OpenAI, y/o Gemini (opcional, dependiendo de las funcionalidades que desees utilizar).
-   GPT4All (opcional, para generación de dorks local).
-   Selenium (opcional, para la funcionalidad de automatización con navegador).
-   Un navegador compatible con Selenium (Chrome, Firefox, etc.).

## Instalación

1.  Clona el repositorio:

    ```bash
    git clone https://github.com/DanielRodZa/GoogleDorksIA.git
    cd ninjaDorks
    ```

2.  Crea un entorno virtual (recomendado):

    ```bash
    python3 -m venv venv
    source venv/bin/activate  # En Linux/macOS
    venv\Scripts\activate  # En Windows
    ```

3.  Instala las dependencias:

    ```bash
    pip install -r requirements.txt
    ```

4.  Configura las claves de API:

    Ejecuta el script con la opción `-c` o `--configure` para configurar las claves de API necesarias:

    ```bash
    python ninjaDorks.py -c
    ```

    Opcionalmente, puedes configurar manualmente el archivo `.env` con las siguientes variables:

    ```
    API_KEY_GOOGLE=<tu_clave_de_api_de_google>
    SEARCH_ENGINE_ID=<tu_id_de_motor_de_búsqueda>
    OPENAI_API_KEY=<tu_clave_de_api_de_openai>
    GEMINI_API_KEY=<tu_clave_de_api_gemini>
    ```

## Uso

### Búsqueda en Google

```bash
python ninjaDorks.py -g -q "filetype:sql \"MySQL dump\" (pass|password|psswd|pwd)" --json resultados.json --html resultados.html --download pdf,doc
```

### Búsqueda en DuckDuckGo

```bash
python ninjaDorks.py -d -q "términos de búsqueda" --json resultados.json --html resultados.html --download pdf
```

### Generación de dorks con IA

```bash
python ninjaDorks.py -gd "Listado de usuarios y passwords en ficheros de texto"
```

### Búsqueda inteligente en archivos

```bash
python ninjaDorks.py --smart_search "Dime los 5 puntos más importantes" --dir_path /ruta/a/tu/directorio --model_name gpt-4 --max_tokens 200
```

### Búsqueda con Selenium

```bash
python ninjaDorks.py --selenium -q "términos de búsqueda" --json resultados.json --html resultados.html
```

## Opciones

-   `-q` o `--query`
    -   Especifica la consulta de búsqueda.
    -   Ejemplo: `-q "filetype:pdf contraseña"`
-   `-c` o `--configure`
    -   Inicia el proceso de configuración del archivo `.env`.
    -   Ejemplo: `python ninjaDorks.py -c`
-   `--start_page`
    -   Define la página de inicio de la búsqueda.
    -   Ejemplo: `--start_page 2`
-   `--pages`
    -   Número de páginas de resultados de búsqueda.
    -   Ejemplo: `--pages 5`
-   `--lang`
    -   Código de idioma para los resultados.
    -   Ejemplo: `--lang lang_en`
-   `-g` o `--google`
    -   Utiliza Google como motor de búsqueda.
    -   Ejemplo: `python ninjaDorks.py -g -q "términos"`
-   `-d` o `--duck`
    -   Utiliza DuckDuckGo como motor de búsqueda.
    -   Ejemplo: `python ninjaDorks.py -d -q "términos"`
-   `--json`
    -   Exporta los resultados en formato JSON.
    -   Ejemplo: `--json resultados.json`
-   `--html`
    -   Exporta los resultados en formato HTML.
    -   Ejemplo: `--html resultados.html`
-   `--download`
    -   Especifica las extensiones de los archivos a descargar, separadas por comas.
    -   Ejemplo: `--download pdf,doc,txt`
-   `-gd` o `--generate_dork`
    -   Genera un dork a partir de una descripción.
    -   Ejemplo: `-gd "encontrar contraseñas en archivos de texto"`
-   `--smart_search`
    -   Realiza una búsqueda inteligente en archivos.
    -   Ejemplo: `--smart_search "resumen de vulnerabilidades"`
-   `--dir_path`
    -   Ruta al directorio para la búsqueda inteligente.
    -   Ejemplo: `--dir_path /ruta/a/mis/archivos`
-   `--model_name`
    -   Nombre del modelo de OpenAI para la búsqueda inteligente.
    -   Ejemplo: `--model_name gpt-4`
-   `--max_tokens`
    -   Número máximo de tokens para la predicción/generación de la IA.
    -   Ejemplo: `--max_tokens 200`
-   `--selenium`
    -   Utiliza Selenium para la búsqueda automatizada en un navegador.
    -   Ejemplo: `--selenium -q "términos"`
