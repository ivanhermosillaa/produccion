# Producción editorial · Meganoticias, Mega y Megatiempo

Interfaz de producción editorial con datos de octubre de 2026.

## Estructura

```
produccion_web/
├── index.html            # interfaz (HTML, CSS y JavaScript en un archivo)
└── data/
    └── produccion.json   # metadatos, portales y artículos
```

`produccion.json` contiene tres bloques:

- `meta`: versión del esquema, fecha de generación, zona horaria y meses incluidos.
- `portals`: id, nombre, color y dominio de cada portal.
- `articles`: artículos con portal, fecha y hora de publicación, sección, formato, título, autor, estado y tipo de contenido.

Todas las métricas (tarjetas, mapa de calor, periodistas y temas) se calculan en el navegador a partir de `articles`.

## Cómo publicar

Sube la carpeta `produccion_web` completa al servidor, manteniendo `index.html` y `data/produccion.json` en el mismo nivel. Para probar en local, sirve la carpeta con un servidor:

```bash
cd produccion_web
python3 -m http.server 8000
```

Luego abre `http://localhost:8000`. No funciona con doble clic porque el navegador bloquea la lectura de JSON desde archivos locales.

## Actualizar datos

Reemplaza `data/produccion.json` por una nueva generación con el mismo formato. Si el periodo incluye más meses, agrégalos al mismo arreglo `articles` y actualiza `meta.months`.

## Requisitos

- Conexión a internet para Roboto (Google Fonts) y Chart.js (cdnjs).
- Navegador moderno.

## Panel de calidad de datos

Debajo de la cabecera aparece el panel de calidad. Evalúa el sitio y el periodo seleccionados con once controles:

- Títulos repetidos en URLs distintas.
- Fecha en la URL distinta a la fecha de publicación.
- Títulos muy cortos.
- Antigüedad de la última carga (atención después de 48 horas).
- Firmas institucionales y patrocinados publicados (informativos).
- Artículos sin periodista, caracteres de escape, fechas futuras, tasa de no publicadas y días sin publicaciones editoriales.

Cada control muestra su estado (Correcto, Atención, Crítico o Informativo) y permite revisar los casos concretos con enlace a la nota. Los umbrales están en la función `qualityChecks` de `index.html`.
