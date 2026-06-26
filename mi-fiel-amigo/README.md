# Veterinaria Mi Fiel Amigo — Landing Page

Landing de **Veterinaria Mi Fiel Amigo** (Villa del Parque, CABA).
Mismo formato/UX que la de Las Marinas, con identidad propia: logo verde/azul
y paleta azul (principal) + verde (acento).

## Estructura

```
mi-fiel-amigo/
├── public/
│   ├── index.html       ← la landing completa (un solo archivo)
│   └── img/
│       └── logo.png     ← logo (fondo transparente)
├── firebase.json        ← configuración de hosting
├── .firebaserc          ← ID del proyecto Firebase (placeholder)
└── README.md
```

## Identidad de marca

- Azul (principal): `#0060A8`  · Azul oscuro: `#004f86`
- Verde (acento del logo): `#78C018`
- Carbón (texto/fondos oscuros): `#2B2B2B`
- Crema (fondo claro): `#FBF6EE`
- Tipografías: Baloo 2 (títulos) + Nunito (texto)

Los colores están centralizados en variables CSS al inicio de `index.html`
(`:root`), así que cambiarlos es modificar 4–5 líneas.

## Modelo de atención

- **M.V. María José González** — dirección técnica, está todos los días. Atiende **por orden
  de llegada** (sin turno). Contacto: **teléfono de línea / contestador**
  `011 4504-7282` + **mail**. No usa WhatsApp.
  Horario: **Lun–Vie 10:30–12:30 y 17:30–20 · Sáb 10–13**.
- **Dr. Octavio Ochoa** — cubre los horarios en que María José no está, **con
  turno**. Turnos por **WhatsApp** `11 7062-3869` (`wa.me/5491170623869`).
  Horario (a confirmar): **Mié y Jue 12:30–17:30 · Vie 12:30–14:30**.
- **Acción principal del sitio**: "Sacar turno". Hoy abre WhatsApp a Octavio con
  un mensaje que pide **nombre + mascota + día/horario**, así queda el dato de la
  persona. Más adelante se reemplaza por un formulario/sistema que guarde esos
  datos automáticamente (ver "Para configurar después").
- **Recordatorio de vacunas** → por **mail** (pendiente de armar).

## ⚠️ Pendiente de completar

- [ ] **Email de María José**: falta la dirección de mail para mostrarla en
      contacto y usarla en el recordatorio de vacunas.
- [ ] **Horarios de Octavio**: están como "a confirmar" (Mié/Jue 12:30–17:30,
      Vie 12:30–14:30). Los de María José ya están cargados.
- [x] **Servicios**: 3 tarjetas finales — Consultorio/Clínica, Emergencias en
      horario de consulta, Laboratorio clínico.
- [x] **Reseñas**: 4,9 en Google + 3 reseñas reales (Johanna Vargas, Mariano A.,
      Jessica Balboa). Se pueden sumar más.
- [x] **Galería**: 5 fotos de mascotas (recortadas de las reseñas de Google).
      Se pueden reemplazar o sumar fotos del local y del equipo.
- [ ] **Logo**: `logo.png` recortado de la foto enviada. Si hay versión
      vectorial/oficial, reemplazar el archivo.

## Para configurar después

- **Captura de turnos / datos**: hoy "Sacar turno" abre WhatsApp a Octavio con
  nombre + mascota + día/horario. El objetivo es que esos datos queden guardados
  automáticamente (formulario → planilla / sistema de reservas, como el de Las
  Marinas). Eso se configura aparte.
- **Recordatorio de vacunas por mail**: pendiente de armar.

## Datos actuales

- **Dirección**: Cuenca 3526, Villa del Parque, CABA (C1419AAB)
- **Teléfono**: 011 4504-7282
- **Responsable**: M.V. María José González
- **Google Maps**: https://maps.app.goo.gl/Q4i8B3WC7TpmkzVq9

## Deploy

Configurado vía GitHub Actions, como **segundo sitio de Hosting dentro del mismo
proyecto** `veterinarialasmarinas` (compartido con Las Marinas):

- Proyecto Firebase: `veterinarialasmarinas`.
- Sitio de Hosting: **`mifielamigo`** → `https://mifielamigo.web.app`.
- Workflow: `.github/workflows/firebase-deploy-mifielamigo.yml`. Se dispara con
  cada push a `main` que toque `mi-fiel-amigo/**`. Reusa el secret
  `FIREBASE_SERVICE_ACCOUNT_VETERINARIALASMARINAS` (no requiere uno nuevo).
- El sitio destino se fija con `"site": "mifielamigo"` en `firebase.json`, para
  que el deploy no pise el de Las Marinas.

Para publicar: fusionar la rama a `main`, o correr el workflow a mano desde
**Actions → "Deploy Mi Fiel Amigo to Firebase Hosting" → Run workflow**.
