# JB's Gastos

Control de gastos multi-moneda para viajes y vida diaria. App de una sola página (HTML+CSS+JS), sin servidor, con soporte para instalarse como aplicación (PWA) en el móvil.

## 📁 Qué contiene esta carpeta

```
index.html              → la app completa
manifest.json           → datos de la app para poder "instalarla" (nombre, iconos, colores)
service-worker.js       → permite que la app abra aunque no haya conexión
icons/                  → icono en varios tamaños (moderno, degradado mint)
README.md               → este archivo
```

Todos los datos (viajes, gastos, presupuestos...) se guardan en el propio móvil (localStorage), no en ningún servidor. GitHub solo aloja los archivos.

## 🚀 Subir a GitHub Pages (una vez)

1. Entra en [github.com](https://github.com) y pulsa **New repository**.
   - Nombre sugerido: `jb-gastos` (puede ser el que quieras).
   - Puede ser público o privado — con Pages funciona igual, aunque en repos privados Pages requiere plan de pago; si quieres mantenerlo privado y gratis, usa **público** (los datos de gastos no se suben a ningún sitio, solo el código de la app).
2. Sube **todos los archivos de esta carpeta** manteniendo la subcarpeta `icons/` tal cual (arrastra y suelta desde la web de GitHub, o usa el método con git más abajo).
3. Ve a **Settings → Pages** (menú lateral izquierdo del repositorio).
4. En "Build and deployment" → "Source", elige **Deploy from a branch**.
5. En "Branch" elige `main` (o `master`) y la carpeta `/ (root)`. Guarda.
6. Espera 1–2 minutos. GitHub te dará una URL parecida a:
   `https://TU-USUARIO.github.io/jb-gastos/`
7. Abre esa URL en el móvil (Chrome en Android). Ya puedes usarla directamente desde el navegador.

### Subir con git (alternativa desde terminal/ordenador)
```bash
cd jb-gastos          # la carpeta con estos archivos
git init
git add .
git commit -m "JB's Gastos"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/jb-gastos.git
git push -u origin main
```
Luego repite los pasos 3–6 de arriba.

## 📲 Instalarla en el móvil (icono en pantalla de inicio)

**Android (Chrome):**
1. Abre la URL de GitHub Pages.
2. Toca los tres puntos (⋮) arriba a la derecha.
3. Toca **"Instalar aplicación"** o **"Añadir a pantalla de inicio"**.
4. Aparecerá el icono nuevo en tu pantalla de inicio, y al abrirlo se verá como una app normal (sin la barra del navegador).

**iPhone (Safari):**
1. Abre la URL.
2. Toca el icono de compartir (cuadrado con flecha hacia arriba).
3. Toca **"Añadir a pantalla de inicio"**.

## 🔄 Actualizar la app cuando le pidas más cambios a Claude

Cada vez que Claude te entregue una nueva versión de `index.html`:
1. Sube el nuevo `index.html` a tu repositorio de GitHub (sustituyendo al anterior).
2. **Importante:** abre `service-worker.js` y cambia el número de la primera línea útil, por ejemplo de:
   `const CACHE_NAME = 'jb-gastos-v1';` a `const CACHE_NAME = 'jb-gastos-v2';`
   Esto obliga a los móviles a descargar la versión nueva en vez de seguir usando la guardada. Si lo olvidas, puede tardar un poco más en verse el cambio, pero no se rompe nada.
3. Sube también ese `service-worker.js` actualizado.
4. En el móvil, cierra la app del todo y vuelve a abrirla (o espera unos segundos con conexión a internet) para que se actualice.

## 🎨 Sobre el icono

El icono (carpeta `icons/`) es una tarjeta con una moneda de euro, en degradado mint — mismo estilo visual (JB Design System v2) que el resto de tus apps. Si más adelante quieres cambiarlo, dímelo y genero uno nuevo con la misma paleta.

## ⚠️ Nota sobre el tipo de cambio

La app usa la API pública y gratuita de Frankfurter (`api.frankfurter.dev`) para las conversiones de moneda. No necesita clave ni configuración — funciona sola en cuanto el móvil tiene internet. Sin conexión, sigue funcionando con la última tasa guardada.
