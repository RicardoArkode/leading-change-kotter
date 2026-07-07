# Adopción del Cambio en Odoo (Kotter) · Arkode

Página interactiva que aplica los 8 errores de John P. Kotter ("Leading Change: Why Transformation Efforts Fail", HBR 1995/2007) a una implementación de Odoo. Incluye un diagnóstico interactivo de sostenibilidad del cambio. Material genérico de Arkode, sin personalización por cliente.

## Estructura

- `index.html`: la página completa (formato dc: templating renderizado en el navegador por `support.js`).
- `support.js`: runtime que renderiza la página (carga React y Babel desde CDN).
- `_ds/`: design system de Arkode (tokens, CSS, bundle).
- `assets/`: logos e ícono.
- `uploads/Kotter_8_Errores_Documentacion.md`: fuente de contenido (síntesis fiel del artículo).
- `screenshots/`: capturas de referencia, no se usan en la página.

## Sitio estático, sin build

No hay paso de build ni dependencias que instalar. Cualquier hosting estático lo sirve tal cual.

### Correr local

```bash
python3 -m http.server 8000
# abrir http://localhost:8000
```

### Desplegar en Vercel

1. Crear el repo en GitHub y subir estos archivos.
2. En Vercel: Add New > Project > importar el repo.
3. Framework Preset: **Other**. Build Command y Output Directory: dejar vacíos (raíz).
4. Deploy. La página queda servida desde `index.html`.
