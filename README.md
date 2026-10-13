# Web pública de Bertha (bertha.uy)

Sitio estático: HTML + CSS, sin build. Se publica como **Worker de Cloudflare** (solo archivos estáticos), llamado `bertha`.

```
public/              lo que se publica
  index.html         página única (inicio, qué hacemos, menú, mayoristas, visitanos)
  estilos.css        estilos (paleta oliva, Poppins)
  404.html           página de error
  img/               fotos, logo e íconos (optimizados para web)
  _headers           cabeceras de seguridad y caché
  robots.txt, sitemap.xml, site.webmanifest, favicon.*
wrangler.jsonc       configuración del Worker (carpeta public/, página 404 propia)
```

## Publicación

El Worker `bertha` está conectado a este repo: cada push a `main` se publica solo, sin pasos manuales.

Dominio (pendiente):
1. Agregar `bertha.uy` a Cloudflare y cambiar los DNS en el registrador. **Antes**, verificar que estén copiados los registros de correo de Zoho (MX, SPF, DKIM, DMARC).
2. En el Worker `bertha` → **Settings → Domains & Routes → Add → Custom domain**: `bertha.uy` y `www.bertha.uy`.
3. `bertha.com.uy`: agregarlo a Cloudflare y crear una regla de redirección 301 a `https://bertha.uy`.

## Cómo actualizar

- **Precios y productos del menú:** en `public/index.html`, sección `id="menu"`; cada producto es una línea `<li>`. Las pestañas son Café, Otras bebidas, Salado y Dulce.
- **Horarios:** en `public/index.html` están en cuatro lugares: la tabla de Visitanos, el pie, el bloque `application/ld+json` y la constante `HORARIO` del script del final (la que maneja el cartel "Abierto / Cerrado").
- **Fotos nuevas:** guardar en `public/img/` en `.webp` y `.jpg`, de 800 y 1200 px de ancho.

## Pendiente

- Número de WhatsApp para mayoristas (hoy el botón abre un mensaje por Instagram).
- Domingos: confirmar si abren (hoy el cartel dice "Cerrado" los domingos).
- Más fotos (local, café, buns).
