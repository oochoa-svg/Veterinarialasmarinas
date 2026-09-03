# Veterinaria Mi Fiel Amigo — Landing Page

Landing de **Veterinaria Mi Fiel Amigo** (Villa del Parque, CABA).
Mismo formato/UX que la de Las Marinas, con identidad propia: logo verde/azul
y paleta azul (principal) + verde (acento).

## Estructura

```
mi-fiel-amigo/
├── public/
│   ├── index.html         ← la landing completa (un solo archivo)
│   ├── cartel-turnos.html ← cartel A5 con QR para la puerta (imprimible)
│   ├── cartel-calle.html  ← cartel A4/A3 para la vidriera (imprimible)
│   ├── farmacia.html      ← catálogo de farmacia online (busca + WhatsApp)
│   ├── farmacia-data.js   ← datos de productos (generados desde la lista de Arandu)
│   └── img/
│       ├── logo.png         ← logo (fondo transparente)
│       ├── qr-turnos.png     ← QR al pedido de turnos del sitio (#turnos)
│       └── qr-turnos.svg     ← mismo QR en vectorial
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

- En la página ambos figuran como **Vet.** (Vet. Octavio Ochoa / Vet. María
  José González). María José es la responsable / dirección técnica del lugar,
  pero eso no se repite por toda la landing.
- **Vet. María José González** — está todos los días. Atiende **por orden
  de llegada** (sin turno), exclusivamente. Contacto: **teléfono de línea /
  contestador** `011 4504-7282` + **mail**. No usa WhatsApp.
  Horario: **Lun–Vie 10–12:30 y 17:30–20 · Sáb 10–13**.
- **Vet. Octavio Ochoa** — atiende **solo con turno reservado**, los
  **miércoles y jueves de 15 a 17.30**. El turno se pide desde el sitio.
  WhatsApp: `5491170623869` (el mismo de la farmacia online).
- **Acción principal del sitio**: **pedir turno / coordinar la consulta**.
  La página es prácticamente sólo eso: una cabecera compacta (logo,
  dirección y horario en una línea) y, apenas debajo, el bloque
  `#turnos`. Todo lo demás — cómo atendemos, servicios, equipo, galería,
  reseñas, FAQ, mapa y CTA — quedó dentro de un `<details class="mas">`
  plegado ("Más sobre la veterinaria"): sigue en el HTML (los buscadores
  lo indexan igual) pero no compite con la acción principal.

### El sitio como primer filtro (`#turnos`)

El problema que resuelve: la gente escribía al celular de Octavio por
cualquier cosa (precios, horarios, stock, urgencias) porque el WhatsApp era
la primera puerta de entrada del sitio. Ahora **ningún celular aparece a la
vista**: el número se usa recién al final del formulario de turno.

El bloque `#turnos` arranca con un triage de 5 opciones y sólo dos llegan a
WhatsApp:

| Elige… | Qué pasa |
|---|---|
| Turno con el Vet. Octavio | Sigue al formulario → WhatsApp con todo cargado |
| Consulta con la Vet. María José | Panel con horarios, dirección y teléfono. Termina ahí |
| Aplicación de Cytopoint, Librela o ACS 16% | Formulario propio → WhatsApp para coordinar el día |
| Precios, vacunas o castraciones | "Acercate en el horario de atención" + teléfono. Termina ahí |
| Es una urgencia | En horario, venir a la veterinaria; fuera de horario, una 24 hs. Termina ahí |

El camino del turno son 3 pasos: **día** (se generan solos los próximos
miércoles y jueves, sin ofrecer el día de hoy), **horario** (15:00 a 17:00
cada 30 min) y **datos** (tutor, mascota, especie, edad, si ya es paciente,
motivo de una lista y detalle obligatorio). Antes de enviar se muestra el
mensaje ya armado; recién al confirmar se abre `wa.me` con el texto completo.

Toda la agenda vive en la constante `TURNOS` al inicio del `<script>` final
de `index.html` — días, horarios, cuántas semanas hacia adelante y el número
de WhatsApp se cambian ahí, en un solo lugar. **No hay agenda con
disponibilidad real**: el horario elegido es una preferencia y se confirma a
mano por WhatsApp.

### Aplicaciones (Cytopoint, Librela, ACS 16%)

Camino aparte dentro de `#turnos`, sin selector de día: se piden
**producto, tutor, mascota, especie, peso, si ya viene con el tratamiento,
fecha de la última aplicación y comentarios**, y se arma un mensaje de
WhatsApp para coordinar el día con el Vet. Octavio. Va sin elegir horario
porque la aplicación puede depender de que haya que pedir la dosis.

### Carteles imprimibles

**Puerta (`cartel-turnos.html`)**

Cartel A5 imprimible (`window.print()`, `@page size:A5`) con el QR a
`https://mifielamigo.web.app/#turnos`, los dos modos de atención y los
avisos de precios, teléfono y urgencias.

**Calle / vidriera (`cartel-calle.html`)** — una sola cosa y nada más:
**"Pedí tu turno" con el Vet. Octavio Ochoa**, el QR grande (88 mm en A4,
124 mm en A3) y los **días de turno** (miércoles y jueves de 15 a 17.30).
Sin horarios de María José, sin avisos ni teléfono en el cuerpo: desde la
vereda tiene que leerse un solo mensaje. Botones para imprimir en **A4 o
A3** (el A3 cambia `@page` y escala el lienzo con `zoom`; para la vidriera
conviene A3). La información completa sigue en el cartel de la puerta.

Los QR `img/qr-turnos.png/.svg` apuntan a
`https://mifielamigo.web.app/#turnos` (generados con `segno`, colores
`#2b2b2b` sobre `#fbf6ee`).
- **Recordatorio de vacunas** → por **mail** (pendiente de armar).

## Farmacia online (`farmacia.html`)

Catálogo de productos con buscador y filtros por categoría, pensado para que
el visitante encuentre el producto y consulte disponibilidad y precio por
WhatsApp — **no es un e-commerce con carrito ni pago online**, todo se
confirma con el Vet. Octavio por WhatsApp (mismo criterio que la regulación
de SENASA sobre venta online de productos veterinarios, que exige estar
registrado como distribuidor salvo venta libre).

- **Origen de los datos**: lista de precios de **Distribuidora Arandu**
  (PDF que envía Octavio). Se curó a mano con un script (`build_catalog.py`,
  no versionado, quedó en el historial de la conversación) que:
  - Excluye lo que es de uso clínico exclusivo (anestésicos, eutanásicos,
    vacunas, insulina, tests diagnósticos) — no tiene sentido que un dueño
    de mascota los pida por su cuenta.
  - Clasifica el resto en 15 categorías (antiparasitarios, antiinflamatorios,
    dermatológicos, cardiológicos, etc.) por palabras clave del nombre.
  - Calcula el **precio de venta = precio con IVA de la lista × 1,8**,
    redondeado a la centena.
- **Botón "Consultar"**: arma un link `wa.me/<número>?text=...` con el
  nombre del producto y el precio ya calculado — el cliente lo ve y lo manda
  tal cual (no hay forma de ocultarlo con un link gratuito de WhatsApp).
  Número usado: el de la cuenta de WhatsApp de Octavio (mismo que el QR de
  los carteles).
- **Actualizar precios**: cuando cambie la lista de Arandu, Octavio manda el
  PDF nuevo y se regenera `farmacia-data.js`.
- Accesible desde el nav de `index.html` ("Farmacia online").

### Reglas de derivación (las que pidió Octavio)

- **Precios de vacunas, consultas, etc.** → acercarse a la veterinaria en el
  horario de atención.
- **Cualquier otra consulta** → teléfono `011 4504-7282`.
- **Castraciones y otras cirugías** → llamar o acercarse a hablarlo con la
  Vet. María José en su horario de atención.
- **Urgencias** → en horario de atención, venir a la veterinaria; fuera de
  horario, concurrir a una veterinaria de 24 hs. **No hay WhatsApp de
  urgencias.**
- **No hay pet shop**: no se venden alimentos ni accesorios. Los
  medicamentos se encargan por `farmacia.html`.

## ⚠️ Pendiente de completar

- [ ] **Email de María José**: falta la dirección de mail para mostrarla en
      contacto y usarla en el recordatorio de vacunas.
- [x] **Horarios de Octavio**: miércoles y jueves de 15 a 17.30, solo con
      turno reservado desde el sitio. Los de María José ya estaban cargados.
- [x] **Servicios**: 3 tarjetas finales — Consultorio/Clínica, Emergencias en
      horario de consulta, Laboratorio clínico.
- [x] **Reseñas**: 4,9 en Google + 3 reseñas reales (Johanna Vargas, Mariano A.,
      Jessica Balboa). Se pueden sumar más.
- [x] **Galería**: 5 fotos de mascotas (recortadas de las reseñas de Google).
      Se pueden reemplazar o sumar fotos del local y del equipo.
- [ ] **Logo**: `logo.png` recortado de la foto enviada. Si hay versión
      vectorial/oficial, reemplazar el archivo.

## Para configurar después

- [x] **Captura de turnos / datos**: el formulario de `#turnos` arma el
      mensaje de WhatsApp con día, horario, tutor, mascota, especie, edad,
      si ya es paciente, motivo y detalle. No hay agenda con disponibilidad
      real ni base de datos: si más adelante hace falta, el paso siguiente es
      guardar cada pedido (Google Sheet / Firestore) además de abrir WhatsApp.
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
