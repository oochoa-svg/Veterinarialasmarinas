# Veterinaria Las Marinas — Landing Page

## Estructura del proyecto

```
las-marinas/
├── public/
│   └── index.html       ← la landing completa (un solo archivo)
├── firebase.json        ← configuración de hosting
├── .firebaserc          ← ID de tu proyecto Firebase
└── README.md
```

---

## Cómo desplegar en Firebase Hosting

### 1. Instalar Firebase CLI (una sola vez)

```bash
npm install -g firebase-tools
```

### 2. Iniciar sesión con tu cuenta Google

```bash
firebase login
```

### 3. Editar `.firebaserc`

Reemplazá `TU-PROJECT-ID-AQUI` con el ID real de tu proyecto Firebase.
Lo encontrás en: https://console.firebase.google.com → Configuración del proyecto.

### 4. Desplegar

```bash
cd las-marinas
firebase deploy --only hosting
```

Firebase te va a dar una URL del tipo:
`https://tu-proyecto.web.app`

---

## Configurar dominio propio (opcional)

En Firebase Console → Hosting → Agregar dominio personalizado.
Ej: `vetlasmarinas.com.ar`

---

## Cosas a personalizar antes de publicar

- [x] Números de WhatsApp: Abel `5491151827408`, Octavio `5491170623869` (registro de vacunación llega a Octavio)
- [ ] Reseñas: podés actualizar el texto de los comentarios
- [ ] Foto del local o del equipo: agregar una imagen en `/public/` y referenciarla en el hero
- [ ] Dominio propio en Firebase Console

## Identidad de marca

- Violeta (logo/marca): `#6B3FA0`
- Naranja principal: `#EF8A22`
- Carbón (texto/fondos oscuros): `#2B2B2B`
- Crema (fondo claro): `#FBF6EE`
- Tipografías: Baloo 2 (títulos) + Nunito (texto)
- Logo: medallón vectorial (cordón + caduceo + "M") embebido como SVG

## Formulario de vacunación → Google Sheets

La sección "Plan de vacunación" guarda los registros en una planilla de Google.
Mientras `SHEET_ENDPOINT` (en el `<script>` de `index.html`) esté vacío, el
formulario envía los datos por WhatsApp como respaldo. Para conectarlo a una
planilla:

1. Creá una **Google Sheet** nueva (con tu cuenta `oochoa@fvet.uba.ar`).
   Poné estos encabezados en la fila 1, columnas A–K:
   `Fecha registro | Tutor | Email | Celular | Mascota | Especie | Raza | Vacunas | Fecha aplicación | Comentarios | Origen`
2. En la Sheet: menú **Extensiones → Apps Script**. Borrá lo que haya y pegá:

   ```javascript
   function doPost(e) {
     const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheets()[0];
     const p = e.parameter;
     sheet.appendRow([
       new Date(), p.tutor, p.email, p.celular,
       p.mascota, p.especie, p.raza, p.vacuna, p.fecha, p.comentarios, p.origen
     ]);
     return ContentService.createTextOutput("ok");
   }
   ```

3. **Implementar → Nueva implementación → Aplicación web**.
   - Ejecutar como: **Yo**
   - Quién tiene acceso: **Cualquier usuario**
   - Implementar y autorizar los permisos. Copiá la **URL de la app web**
     (termina en `/exec`).
4. Pegá esa URL en `SHEET_ENDPOINT` dentro de `index.html`, commiteá y pusheá.
   Listo: cada registro cae en la planilla.
5. Para Beth Center: **Archivo → Descargar → CSV / Excel** desde la Sheet e
   importá ese archivo.

## Deploy

El deploy es automático vía GitHub Actions: cada push a `main` que toque
`las-marinas/**` dispara `.github/workflows/firebase-deploy.yml` y publica
en Firebase Hosting (proyecto `veterinarialasmarinas`).
