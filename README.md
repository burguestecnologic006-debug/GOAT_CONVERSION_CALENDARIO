# Agenda — Goat Conversion

Calendario de agendamiento para clientes, con panel de administrador.

## 🚀 Puesta en marcha (una sola vez)

### 1. Crear el proyecto de Firebase (la base de datos, gratis)

1. Ve a https://console.firebase.google.com y crea una cuenta / inicia sesión con Google.
2. Clic en **"Agregar proyecto"**, ponle un nombre (ej. `goat-conversion-agenda`) y créalo (puedes desactivar Google Analytics, no lo necesitas).
3. En el menú lateral, ve a **Compilación → Firestore Database** → **"Crear base de datos"**.
   - Ubicación: la más cercana a Colombia (ej. `us-east1` o `southamerica-east1`).
   - Modo: elige **"Iniciar en modo de producción"**.
4. Ve a la pestaña **"Reglas"** dentro de Firestore y reemplaza el contenido por lo que está en el archivo `firestore.rules` de este repositorio. Publica los cambios.
5. Vuelve a **Configuración del proyecto** (ícono de engranaje arriba a la izquierda) → pestaña **"General"** → baja hasta **"Tus apps"** → clic en el ícono `</>` (Web) → dale un apodo y **"Registrar app"**.
6. Firebase te va a mostrar un bloque de código con `apiKey`, `authDomain`, `projectId`, etc. **Copia esos valores.**

### 2. Pegar la configuración en el archivo

Abre `index.html` en un editor de texto, busca esta sección cerca del inicio:

```js
const FIREBASE_CONFIG = {
  apiKey: "TU_API_KEY",
  authDomain: "TU_PROYECTO.firebaseapp.com",
  projectId: "TU_PROYECTO",
  storageBucket: "TU_PROYECTO.appspot.com",
  messagingSenderId: "TU_SENDER_ID",
  appId: "TU_APP_ID"
};
```

Reemplaza cada valor por el que copiaste de Firebase. Guarda el archivo.

### 3. Subir el repositorio a GitHub

1. Ve a https://github.com y crea una cuenta si no tienes.
2. Clic en **"New repository"** (botón verde). Nómbralo, por ejemplo, `agenda-goat-conversion`. Marca **"Public"**. Clic en **"Create repository"**.
3. En la página del repositorio recién creado, clic en **"uploading an existing file"**.
4. Arrastra `index.html`, `README.md` y `firestore.rules`. Clic en **"Commit changes"**.

### 4. Activar GitHub Pages (para tener el link público)

1. Dentro del repositorio, ve a **Settings → Pages** (menú lateral izquierdo).
2. En "Build and deployment" → "Source", elige **"Deploy from a branch"**.
3. En "Branch", elige `main` y la carpeta `/ (root)`. Clic en **"Save"**.
4. Espera 1-2 minutos y recarga la página. Arriba te va a aparecer el link público, algo como:

```
https://tu-usuario.github.io/agenda-goat-conversion/
```

Ese es el link que le compartes a tus clientes y que usas tú mismo en modo administrador.

### 5. Notificación por correo (Make.com)

Sigue las instrucciones dentro de la misma app: modo administrador → Configuración → "Notificación por correo" → "¿Cómo la consigo?". Cuando tengas la URL del webhook, pégala ahí y guarda.

### 6. Cambiar el PIN de administrador

Por defecto es `1234`. Entra en modo administrador y cámbialo desde Configuración lo antes posible.

## ⚠️ Nota de seguridad

El PIN de administrador es solo una barrera dentro de la app — no es autenticación real. Las reglas de `firestore.rules` incluidas permiten lectura y escritura pública en la colección de datos de la agenda (es necesario para que los clientes puedan reservar sin cuenta). Cualquier persona con conocimientos técnicos podría, en teoría, leer o modificar los datos directamente en Firebase. Para un negocio pequeño esto es un riesgo aceptable, pero si más adelante quieres seguridad real (autenticación de verdad para el modo administrador), avísame y lo agregamos.

## 🔄 Actualizar cambios más adelante

Cada vez que quieras modificar el diseño o la funcionalidad, edita `index.html` y vuelve a subirlo al repositorio (Settings → o directamente arrastrando el archivo nuevo en la vista principal del repo, GitHub te deja "reemplazar"). GitHub Pages se actualiza solo en 1-2 minutos.
