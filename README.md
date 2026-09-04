# 3D Products Chile — CRM

App de una sola página (`index.html`), sin backend. Los datos se guardan en el navegador de cada persona (`localStorage`). Lista para publicarse en `crm.3dproductschile.cl`.

## Qué falta para que quede 100% real

No tengo credenciales de hosting, del panel DNS del dominio ni de Google Cloud — esas tres cosas las tiene que hacer alguien con acceso a esas cuentas. Son 3 pasos únicos, ~10 minutos en total.

### 1. Publicar el archivo (elige una opción)

**Opción A — GitHub Pages (recomendada, gratis, ya está preparado aquí)**
1. Crea un repositorio vacío en GitHub (público o privado), por ejemplo `3dproductschile-crm`.
2. En esta carpeta:
   ```
   git remote add origin https://github.com/<tu-usuario>/3dproductschile-crm.git
   git push -u origin main
   ```
3. En GitHub → Settings → Pages: Source = rama `main`, carpeta `/ (root)`. Guardar.
4. En Settings → Pages → Custom domain, escribe `crm.3dproductschile.cl` (el archivo `CNAME` de este repo ya lo deja preconfigurado) y activa "Enforce HTTPS" (tarda unos minutos en aparecer disponible tras el paso 2 del DNS).

**Opción B — Netlify / Vercel (si ya usan alguno)**
Arrastra esta carpeta en app.netlify.com/drop, o conéctala a un repo de GitHub desde su panel. Luego en "Domain settings" agrega `crm.3dproductschile.cl` como dominio personalizado — el panel te dará el valor exacto para el registro DNS del punto 2.

### 2. Apuntar el subdominio (en el panel DNS donde está 3dproductschile.cl)
Crear un registro:
- Tipo: `CNAME`
- Nombre/Host: `crm`
- Valor:
  - GitHub Pages: `<tu-usuario>.github.io`
  - Netlify: el valor que te indique su panel (algo como `nombre-del-sitio.netlify.app`)
- TTL: automático

Puede tardar entre minutos y algunas horas en propagarse.

### 3. Habilitar Google Calendar de verdad
En [Google Cloud Console](https://console.cloud.google.com/) → APIs y servicios → Credenciales → tu ID de cliente OAuth (o crea uno nuevo, tipo *Aplicación web*):
- En **Orígenes de JavaScript autorizados**, agrega `https://crm.3dproductschile.cl`.
- Copia el Client ID y pégalo dentro del CRM en Configuración → Google Calendar → Conectar.

## Acceso de prueba
- ID: `admin`
- Clave: `cadencia`

Se puede crear el acceso real del equipo desde la misma pantalla de inicio de sesión ("Registrar empleado") o desde Configuración → Equipo una vez adentro.
