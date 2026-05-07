# SOS Medellín · Cómo usar el prototipo en tu teléfono

Esta carpeta contiene una **PWA (Progressive Web App)** — una versión web del prototipo
que se puede **instalar como una app nativa** en cualquier teléfono Android o iPhone,
con icono en el escritorio, pantalla completa sin barras del navegador, y funcionamiento
sin conexión a internet.

## Archivos incluidos

```
sos-medellin-mobile/
├── index.html      ← La aplicación
├── manifest.json   ← Define cómo se instala
├── sw.js           ← Permite uso sin internet
├── icon-192.png    ← Icono para Android
├── icon-512.png    ← Icono grande
└── COMO_USAR.md    ← Esta guía
```

---

## OPCIÓN 1 · Lo más rápido (5 minutos · sin servidor)

Para mostrarle el prototipo a alguien en tu teléfono **ahora mismo**:

1. Copia los archivos a una carpeta de tu computador
2. Abre `index.html` directamente en Chrome o Firefox
3. Activa el modo móvil del navegador (F12 → icono del teléfono)

⚠️ **Limitación**: Esta opción NO permite instalar la app en el escritorio del teléfono.
Solo sirve para revisar/presentar desde el navegador.

---

## OPCIÓN 2 · Instalar como app real en tu teléfono (recomendado)

Las PWAs requieren ser servidas por HTTPS. La forma más fácil es usar **GitHub Pages**
(gratis, sin tarjeta de crédito):

### Pasos detallados

**1. Crea una cuenta en GitHub** (si no tienes)
- Ve a https://github.com/signup
- Es gratis, solo necesitas correo

**2. Crea un repositorio nuevo**
- En GitHub, clic en el "+" arriba a la derecha → "New repository"
- Nómbralo: `sos-medellin` (o como quieras)
- Marca "Public"
- Clic en "Create repository"

**3. Sube los archivos**
- En la página del repo, clic en "uploading an existing file"
- Arrastra los 5 archivos: `index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`
- Clic en "Commit changes"

**4. Activa GitHub Pages**
- En el repo, ve a "Settings" (arriba)
- En el menú izquierdo, clic en "Pages"
- En "Source", selecciona "Deploy from a branch"
- En "Branch", selecciona `main` y carpeta `/ (root)`
- Clic en "Save"
- Espera 1-2 minutos

**5. Obtén tu URL**
- Refresca la página de Pages
- Aparecerá: `https://TU-USUARIO.github.io/sos-medellin/`
- Esa es la URL de tu app

**6. Instala la app en tu teléfono**

### En Android (Chrome):
- Abre la URL en Chrome
- Toca el menú (⋮) arriba a la derecha
- Toca **"Instalar app"** o **"Añadir a pantalla de inicio"**
- Confirma
- Listo: el icono aparece en tu escritorio como cualquier app

### En iPhone (Safari):
- Abre la URL en **Safari** (no Chrome — iOS solo permite instalar desde Safari)
- Toca el botón de compartir (cuadrado con flecha hacia arriba)
- Desplaza y toca **"Añadir a pantalla de inicio"**
- Confirma con "Añadir"
- Listo: el icono aparece en tu escritorio

---

## OPCIÓN 3 · Servidor local (para desarrollo)

Si tienes Python instalado:

```bash
cd sos-medellin-mobile
python3 -m http.server 8000
```

Luego, en el teléfono **conectado a la misma WiFi** que el computador:
- Abre Chrome y ve a: `http://IP_DE_TU_COMPUTADOR:8000`
- Para encontrar la IP: en Mac/Linux escribe `ifconfig`, en Windows `ipconfig`

⚠️ **Limitación**: HTTP local funciona para probar, pero **no permite instalar**
como PWA porque las PWAs requieren HTTPS. Para instalación real, usa la Opción 2.

---

## Qué funciona en el teléfono

✅ Las 5 pantallas del lado ciudadano (inicio, alertas, mapa, reportar, ayuda)
✅ Toggle de Modo Sénior (la preferencia se guarda automáticamente)
✅ Mapa estilizado de Medellín con comunas reales
✅ Navegación por barra inferior
✅ Funciona sin internet después de la primera carga
✅ Pantalla completa sin barras del navegador
✅ Icono en el escritorio del teléfono

## Qué NO funciona (es un prototipo visual)

❌ Cámara real para tomar fotos
❌ GPS real para ubicación
❌ Llamadas telefónicas (los botones son demostrativos)
❌ Notificaciones push reales
❌ Datos en tiempo real (las alertas son ejemplos)
❌ Backend conectado al DAGRD

---

## Para una app real en producción

Este prototipo es funcional para presentación académica o demo. Para un producto real
necesitarías:

- **Backend**: Node.js + PostgreSQL para guardar reportes
- **Mapas reales**: Mapbox o Google Maps API
- **Notificaciones push**: Firebase Cloud Messaging
- **Cámara y GPS**: ya disponibles vía APIs del navegador (geolocation, getUserMedia)
- **Convertir a app nativa**: Capacitor.js o React Native (si quieres app store)
- **Integración DAGRD**: API gubernamental del SIATA o sistema interno

El código actual está estructurado de forma que el siguiente paso lógico sería migrarlo
a **React + Vite + Capacitor**, lo que te permitiría publicarlo en Google Play y App Store
manteniendo el mismo diseño.

---

## Soporte

Si la app no se instala en tu teléfono:
1. Verifica que la URL sea HTTPS (no HTTP)
2. Abre en Chrome (Android) o Safari (iPhone) — no otros navegadores
3. Prueba en modo incógnito por si hay caché viejo
4. En iPhone, asegúrate que iOS sea versión 11.3+
