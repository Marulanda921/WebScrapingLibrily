# Web Scraper para Categorías y Productos de Buscalibre

Este script está diseñado para extraer información de productos desde la página web colombiana **Buscalibre**. Obtiene datos como nombres de productos, autores, precios, descuentos y disponibilidad de stock para cada categoría, y los almacena en una base de datos MySQL.

---

## Funcionalidades

- Extrae detalles de productos de múltiples categorías y páginas.
- Recopila la siguiente información:
  - Nombre del producto
  - Autor
  - Precio actual
  - Precio original
  - Descuento
  - Disponibilidad de stock
  - Detalles adicionales
  - URLs de producto e imagen
- Almacena los datos en una base de datos MySQL para su posterior análisis.
- Maneja errores de forma robusta y omite entradas problemáticas sin detener el proceso.

---

## Requisitos Previos

Antes de ejecutar el script, asegúrate de cumplir con lo siguiente:

1. **Módulos de Python**:
   - Instala los módulos necesarios ejecutando:
     ```bash
     pip install requests beautifulsoup4 pymysql
     ```

2. **Base de Datos MySQL**:
   - Crea una base de datos llamada `libreria`.
   - Agrega una tabla `productos` con la siguiente estructura:
     ```sql
     CREATE TABLE productos (
         id INT AUTO_INCREMENT PRIMARY KEY,
         categoria VARCHAR(255),
         nombre VARCHAR(255),
         autor VARCHAR(255),
         precio_actual FLOAT,
         precio_anterior FLOAT,
         descuento VARCHAR(50),
         url_producto TEXT,
         detalles_adicionales TEXT,
         unidades_disponibles VARCHAR(50),
         imagen_url TEXT
     );
     ```

3. **Configuración de la Conexión**:
   - Actualiza los detalles de conexión a la base de datos en el script:
     ```python
     db = pymysql.connect(
         host="localhost",
         user="tu_usuario",
         password="tu_contraseña",
         database="libreria",
         port=3306
     )
     ```

---

## Uso

1. **Ejecutar el Script**:
   Ejecuta el script en un entorno Python:
   ```bash
   python scraper.py
   ```

2. **Resultados**:
   - Los datos se almacenarán en la tabla `productos` de tu base de datos MySQL.

---

## Notas

- El script utiliza `BeautifulSoup` para analizar el HTML y extraer datos.
- Implementa un control básico de frecuencia con `time.sleep(0.5)` para evitar sobrecargar el servidor.
- El manejo de errores asegura robustez registrando problemas y omitiendo entradas problemáticas.

---

## Aviso Legal

Este script es solo para fines educativos. Asegúrate de cumplir con los **Términos de Servicio de Buscalibre** y respeta su propiedad intelectual. Úsalo de forma responsable.
