# prometeo-web

Sitio institucional de **Prometeo** — [prometeo.com.ar](https://prometeo.com.ar). Presenta las soluciones de la empresa (Odoo, software a medida, campañas de marketing, automatizaciones, tableros, integraciones, soporte) y el producto **CobraYa**.

Sitio estático: HTML + CSS + JS sin build ni dependencias.

## Estructura

| Ruta | Contenido |
|---|---|
| `index.html` | Página única con todas las secciones |
| `css/base.css` | Tokens de marca, tipografía, botones, nav y hero |
| `css/sections.css` | Secciones, responsive y animaciones |
| `js/site.js` | Nav, menú móvil, aparición al scroll, carrusel de clientes, formulario |
| `assets/` | Logo (`prometeo-mark.svg`) y logos de clientes |

## Correr en local

```bash
python3 -m http.server 8000
# abrir http://localhost:8000
```

El formulario necesita la access key de Web3Forms. En local se toma de `localStorage`:

```js
localStorage.setItem('w3fkey', 'TU_KEY')
```

## Deploy

Cada push a `main` publica en GitHub Pages (`.github/workflows/deploy.yml`). El dominio `prometeo.com.ar` apunta al sitio vía Cloudflare.

- El workflow reemplaza `__WEB3FORMS_KEY__` en `index.html` por el secret **`WEB3FORMS_KEY`** del repo. Sin ese secret el deploy falla a propósito.
- La key queda visible en el HTML publicado (inevitable en un sitio estático); el secret solo evita que figure en el repo.

## Agregar un cliente

1. Subir el logo a `assets/` (cuadrado, ~900 px).
2. Copiar un `<article class="case">` dentro de `#clientsMarquee` en `index.html` y cambiar logo, rubro, nombre e Instagram.

## Agregar un interés al formulario

Sumar un `<option>` en `#f-interes`. Si un botón debe preseleccionarlo, ponerle `data-interes="<texto exacto de la opción>"`.
