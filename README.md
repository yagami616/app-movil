# FitRoad Chile — Guía de instalación

## Opción 1: Instalar como app desde el navegador (PWA) — INMEDIATO

1. Abre `index.html` en Chrome Android / Safari iOS
   - O sube los archivos a cualquier hosting gratuito (Netlify, Vercel, GitHub Pages)
2. Chrome mostrará "Agregar a pantalla de inicio"
3. La app se instala como aplicación nativa — funciona offline ✅

---

## Opción 2: Convertir a APK con PWABuilder — SIN CÓDIGO (5 minutos)

1. Sube la carpeta a **GitHub Pages** o **Netlify** (gratis)
   ```
   netlify drop → arrastra la carpeta fitroad-pwa/
   ```
2. Ve a **https://www.pwabuilder.com**
3. Pega la URL de tu sitio → Click "Start"
4. Selecciona "Android" → Descarga el APK firmado
5. Instálalo directamente en tu Android (habilita "Fuentes desconocidas")

---

## Opción 3: Compilar APK con Android Studio — CÓDIGO COMPLETO

### Requisitos
- Android Studio Hedgehog o superior
- JDK 17+
- Android SDK 34

### Pasos
```bash
# 1. Clona o crea proyecto nuevo en Android Studio
# 2. Copia los archivos Kotlin del spec técnico
# 3. Añade dependencias en build.gradle.kts:

dependencies {
    implementation("androidx.room:room-runtime:2.6.1")
    implementation("androidx.room:room-ktx:2.6.1")
    ksp("androidx.room:room-compiler:2.6.1")
    implementation("com.google.dagger:hilt-android:2.50")
    ksp("com.google.dagger:hilt-compiler:2.50")
    implementation("com.squareup.retrofit2:retrofit:2.9.0")
    implementation("com.squareup.retrofit2:converter-gson:2.9.0")
    implementation("androidx.camera:camera-core:1.3.1")
    implementation("com.google.mlkit:barcode-scanning:17.2.0")
    implementation("io.coil-kt:coil-compose:2.5.0")
}

# 4. Build → Generate Signed APK
```

---

## Opción 4: Usar Capacitor (HTML → APK nativo)

```bash
npm install @capacitor/core @capacitor/cli @capacitor/android
npx cap init FitRoad cl.fitroad.app
cp index.html www/
npx cap add android
npx cap open android   # Abre Android Studio
# Build → APK
```

---

## Archivos incluidos en este paquete

| Archivo | Descripción |
|---------|-------------|
| index.html | App completa (HTML/CSS/JS) |
| manifest.json | Manifiesto PWA |
| sw.js | Service Worker (offline) |
| icon-192.png | Ícono app 192×192 |
| icon-512.png | Ícono app 512×512 |
| README.md | Esta guía |

---

**FitRoad Chile v1.0** · Mifflin-St Jeor · Open Food Facts · Datos 100% locales
