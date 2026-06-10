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

- [ ] Número de WhatsApp: buscar `5491147253322` y reemplazar con el número real
- [ ] Reseñas: podés actualizar el texto de los comentarios
- [ ] Foto del local o del equipo: agregar una imagen en `/public/` y referenciarla en el hero
- [ ] Dominio propio en Firebase Console

## Identidad de marca

- Naranja principal: `#EF8A22`
- Carbón (texto/fondos oscuros): `#2B2B2B`
- Crema (fondo claro): `#FBF6EE`
- Tipografías: Baloo 2 (títulos) + Nunito (texto)
- Logo: emblema de huella sobre cuadro naranja (SVG embebido)

## Deploy

El deploy es automático vía GitHub Actions: cada push a `main` que toque
`las-marinas/**` dispara `.github/workflows/firebase-deploy.yml` y publica
en Firebase Hosting (proyecto `veterinarialasmarinas`).
