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

## ⚠️ Pendiente de completar (placeholders)

Hay datos provisorios marcados que conviene confirmar antes de publicar:

- [ ] **WhatsApp**: hoy apunta a `541145047282` (la línea fija). Reemplazar por
      el **celular real con WhatsApp** (formato `54911...`). Aparece en los
      botones de hero, equipo, CTA y el botón flotante.
- [ ] **Horarios**: hay un horario de ejemplo (Lun–Vie 9–13 / 16–20, Sáb 9–13).
      Confirmar los reales (`<!-- TODO: confirmar horarios reales -->`).
- [ ] **Servicios**: ajustar las 6 tarjetas a lo que realmente ofrece la vete.
- [ ] **Reseñas**: los 3 comentarios son de ejemplo
      (`<!-- TODO: reemplazá estos comentarios... -->`).
- [ ] **Logo**: `logo.png` se generó a partir de la foto enviada (fondo
      recortado). Si hay una versión vectorial/oficial, reemplazar el archivo.

## Datos actuales

- **Dirección**: Cuenca 3526, Villa del Parque, CABA (C1419AAB)
- **Teléfono**: 011 4504-7282
- **Responsable**: M.V. María José González
- **Google Maps**: https://maps.app.goo.gl/Q4i8B3WC7TpmkzVq9

## Qué NO incluye (a diferencia de Las Marinas)

Por pedido, esta versión **no** trae el sistema de turnos online, el registro
de pacientes ni el formulario de vacunación. Se puede sumar más adelante.

## Deploy (pendiente de configurar)

El deploy a Firebase todavía no está configurado para esta vete. Opciones:

1. Crear un **proyecto Firebase propio** para Mi Fiel Amigo y poner su ID en
   `.firebaserc` (hoy figura `mifielamigo` como placeholder), o
2. Usar un *hosting target* dentro de un proyecto existente.

Una vez elegido, se agrega el workflow de GitHub Actions (como el de Las
Marinas) apuntando a `mi-fiel-amigo/**` con el secret del service account.
