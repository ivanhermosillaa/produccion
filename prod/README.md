# Producción editorial · Meganoticias, Mega y Megatiempo

Interfaz de producción editorial con datos de octubre de 2026.

## Estructura

```
produccion_web/
├── index.html          # interfaz (HTML, CSS y JavaScript en un archivo)
└── data/v1/            # datos en JSON (contrato de la API)
    ├── meta.json
    ├── portals.json
    ├── articles-2026-10.json
    ├── summary-2026-10.json
    ├── daily-2026-10.json
    ├── hourly-2026-10.json
    ├── sections-2026-10.json
    ├── authors-2026-10.json
    └── topics-2026-10.json
```

La interfaz lee `meta.json`, `portals.json` y los `articles-YYYY-MM.json` de los meses indicados en `meta.json`. Los demás archivos corresponden a endpoints futuros de la API. Las métricas de la interfaz se calculan en el navegador a partir de los artículos.

## Cómo abrirla

Los navegadores bloquean la lectura de JSON cuando la página se abre con doble clic (`file://`). Hay que servir la carpeta:

```bash
cd produccion_web
python3 -m http.server 8000
```

Luego abre `http://localhost:8000` en el navegador.

## Requisitos

- Conexión a internet para cargar Roboto (Google Fonts) y Chart.js (cdnjs).
- Navegador moderno (Chrome, Edge, Firefox o Safari recientes).

## Actualizar datos

Reemplaza los archivos de `data/v1/` por una nueva generación del pipeline. Si agregas otro mes, añade su `articles-YYYY-MM.json` y su entrada en `meta.json > months`; el selector de periodo lo mostrará sin cambiar el HTML.
