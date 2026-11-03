# Rufián Coffee Room · sitio web

Sitio de una sola página: `index.html` + carpeta `assets/` (fotos, videos y logos). No necesita servidor especial, base de datos ni instalación.

## 1. Publicar el sitio (Netlify, gratis)

1. Entra a https://app.netlify.com/drop.
2. Arrastra la carpeta `rufian-sitio` completa a la página.
3. Netlify te da una dirección del tipo `algo.netlify.app`. Ahí ya funciona.
4. Para usar un dominio propio (por ejemplo `rufiancoffeeroom.com`): en Netlify → *Domain management* → *Add a domain*, y sigue los pasos para apuntar el dominio.

Para actualizar fotos o textos fijos más adelante, edita los archivos y vuelve a arrastrar la carpeta en *Deploys*.

## 2. Conectar el menú con Google Sheets

1. En Google Drive: **Nuevo → Subir archivo** y sube `rufian-menu.xlsx`. Ábrelo y elige **Abrir con Hojas de cálculo de Google** (o *Archivo → Guardar como Hojas de cálculo de Google*).
2. En la hoja de Google: **Archivo → Compartir → Publicar en la web**.
3. En "Vínculo", elige la pestaña **Menu** y el formato **Valores separados por comas (.csv)**. Pulsa **Publicar** y copia el enlace.
4. Abre `index.html` con un editor de texto, busca esta línea y pega el enlace entre las comillas:

   ```js
   const MENU_SHEET_CSV = "";
   ```

   Queda así:

   ```js
   const MENU_SHEET_CSV = "https://docs.google.com/spreadsheets/d/e/XXXX/pub?gid=0&single=true&output=csv";
   ```

5. Guarda y vuelve a subir la carpeta a Netlify. Desde ahí, los cambios en la hoja aparecen en el sitio sin volver a publicar.

**Comparte la hoja con el cliente** (botón *Compartir*, permiso de *Editor*). La pestaña **Instrucciones** le explica qué hace cada columna.

### Cosas que conviene saber
- Google tarda unos **5 minutos** en reflejar los cambios de una hoja publicada.
- Si la hoja no responde o queda casi vacía, el sitio muestra la copia del menú que trae dentro (`const MENU` en `index.html`). Nunca queda en blanco. Conviene actualizar esa copia de vez en cuando.
- La sección **Métodos**, las fotos y los videos no están en la hoja.
- Las 4 bebidas destacadas toman precio y descripción de la hoja. Si se cambia el nombre de una, su tarjeta se oculta.

## 3. Dónde cambiar otras cosas (en `index.html`)

| Qué | Busca |
|---|---|
| Horario, teléfono, dirección | `const LOCATION` |
| Instagram | `const BRAND` |
| Fotos y videos de cada sección | `const PHOTOS` |
| Bebidas destacadas | `const FEATURED` |
| Colores | `:root {` al inicio del `<style>` |

## Datos por confirmar con el negocio
- Horario de fin de semana: Google dice sábado y domingo desde las 7:30; la bio de Instagram dice 6:30 todos los días.
- Precio de Pink Chai Betabel ($80–90), temperaturas "80–90F" y texto de la tisana y de los granos (marcados con * en el sitio).

## Créditos de contenido
Fotos y videos tomados del Instagram oficial @rufiancoffeeroom (cada uno indica su publicación de origen en `const PHOTOS`). Logo proporcionado por el negocio; versiones sin fondo derivadas del original.
