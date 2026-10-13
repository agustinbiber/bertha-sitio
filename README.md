# Web pública de Bertha (bertha.uy)

Sitio estático: HTML + CSS, sin build. Se publica con **Cloudflare Pages**.

```
index.html       página única (inicio, qué hacemos, menú, mayoristas, visitanos)
estilos.css      estilos (paleta oliva, Poppins)
404.html         página de error
img/             fotos, logo e íconos (optimizados para web)
_headers         cabeceras de seguridad y caché (Cloudflare Pages)
robots.txt, sitemap.xml, site.webmanifest, favicon.*
```

## Publicar en Cloudflare Pages

1. Cloudflare → **Workers & Pages → Create → Pages → Connect to Git** → repo `bertha-sitio`.
2. Configuración del build:
   - Framework preset: **None**
   - Build command: *(vacío)*
   - Build output directory: *(vacío, es la raíz del repo)*
   - Rama de producción: `main`
3. Cada push a `main`  publica solo.
4. **Custom domains** → agregar `bertha.uy` y `www.bertha.uy`.
5. Dominio `bertha.com.uy`: agregarlo a Cloudflare y crear una regla de redirección 301 a `https://bertha.uy`.

Antes de cambiar los DNS a Cloudflare: verificar que estén copiados los registros de correo de Zoho (MX, SPF, DKIM, DMARC).

## Cómo actualizar

- **Precios y productos del menú:** en `index.html`, sección `id="menu"`; cada producto es una línea `<li>`. Las pestañas son Café, Otras bebidas, Salado y Dulce.
- **Horarios:** en `index.html` están en cuatro lugares: la tabla de Visitanos, el pie, el bloque `application/ld+json` y la constante `HORARIO` del script del final (la que maneja el cartel "Abierto / Cerrado").
- **Fotos nuevas:** guardar en `img/` en `.webp` y `.jpg`, de 800 y 1200 px de ancho.

## Pendiente

- Número de WhatsApp para mayoristas (hoy el botón abre un mensaje por Instagram).
- Domingos: confirmar si abren (hoy el cartel dice "Cerrado" los domingos).
- Más fotos (local, café, buns).
