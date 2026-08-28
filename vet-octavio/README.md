# Vet. Octavio Ochoa — Veterinario de cabecera a domicilio

Landing personal de Octavio Ochoa. A diferencia de `las-marinas` y `mi-fiel-amigo`,
que son sitios de clínicas, esta es una **marca personal**: el protagonista es el
profesional, no el local.

```
vet-octavio/
├── public/
│   ├── index.html       ← la landing completa (un solo archivo)
│   └── img/             ← foto de perfil y miniaturas de videos (pendiente)
├── firebase.json        ← hosting, site "vetoctavio8a"
├── .firebaserc          ← proyecto Firebase (veterinarialasmarinas)
└── README.md
```

## Rol de la landing dentro de la estrategia

La coordinación de turnos y las consultas **no** se resuelven acá: eso lo maneja
Octavio por WhatsApp, apoyado en Meta Business IA. La landing cumple otras funciones:

- **Que lo conozcan**: trayectoria, formación y matrículas.
- **Explicar el Plan Cabecera**, que es demasiado extenso para un chat o un posteo.
- **SEO**: es el único canal que capta a quien busca "veterinario a domicilio
  <barrio>" en Google y todavía no lo conoce. Por eso las zonas se nombran una por una.
- **Contenido**: videos y material de Canal Veterinario.

Todos los CTA van a WhatsApp con un **mensaje prearmado distinto según la sección**
(consulta a domicilio, Plan Cabecera, consulta general), para saber de dónde viene
cada mensaje sin necesidad de tracking.

## Identidad de marca

Paleta propia, distinta de las dos clínicas (naranja en Las Marinas, azul/verde en
Mi Fiel Amigo), para que se lea como una marca aparte:

- Petróleo (principal): `#14606B` · Petróleo oscuro: `#0E4854`
- Ámbar (acento): `#E8A33D`
- Carbón: `#2B2B2B` · Crema: `#FBF6EE`
- Tipografías: Baloo 2 (títulos) + Nunito (texto), igual que el resto del ecosistema

## Datos

- WhatsApp (laboral): **11 7062-3869** → `wa.me/5491170623869`
- Instagram: **@vetoctavio8a**
- Matrículas: **MP 16465 · MN 11170**
- Formación: Médico Veterinario (UBA), Intensificación en Pequeños Animales
- Docente de Anatomía, FCV-UBA, desde 2017
- Fundador de Canal Veterinario (educación online)

## Zonas de cobertura

- **Zona Norte**: Vicente López, Olivos, La Lucila, Martínez, Acassuso, San Isidro,
  Beccar, Boulogne, Victoria, San Fernando, Virreyes, Tigre, Rincón de Milberg,
  Don Torcuato, General Pacheco, Nordelta, Benavídez.
- **CABA**: Villa del Parque, Villa Devoto, Villa Pueyrredón, Agronomía, La Paternal,
  Villa Santa Rita, Monte Castro, Villa Real, Versalles, Floresta, Villa Urquiza,
  Parque Chas.

Se mencionan por nombre a propósito: es lo que permite aparecer en búsquedas por barrio.

## Plan Cabecera

$65.000 por 3 meses en un solo pago (se muestra también como $21.600/mes para que
el número comunique mejor).

El **reintegro de hasta $25.000** se subió al primer lugar de los beneficios: en la
versión original estaba al final entre las restricciones, siendo probablemente lo más
valioso del plan.

### Pendiente de definir

Estos puntos todavía no están resueltos y hoy la página no los afirma:

- [ ] **¿Por mascota o por hogar?** Es la primera pregunta que va a aparecer.
- [ ] **¿Qué pasa al vencer los 3 meses?** ¿Renovación automática, mismo precio?
- [ ] **¿Existe opción de pago mensual?** Hoy solo figura el pago único.
- [ ] **Monto del copago adicional** para consultas presenciales/domicilio.
- [ ] **Cuenta del peor escenario**: un cliente que usa todos los beneficios. El
      reintegro solo representa el 38% del valor del plan; conviene verificar que el
      margen cierre antes de promocionarlo fuerte.

## Pendientes de contenido

- [ ] **Foto de perfil** → `img/octavio.jpg` (hoy hay un placeholder con ícono).
- [ ] **Videos reales** de Canal Veterinario en la sección "Para que decidas informado"
      (hoy hay 3 tarjetas de ejemplo).
- [ ] **Imagen Open Graph** para cuando se comparta el link por WhatsApp o redes.

## Sincronía con Meta Business IA

Las preguntas frecuentes de la landing y la base de conocimiento de la IA deben decir
lo mismo. Conviene tratar el bloque FAQ de `index.html` como la fuente de verdad y
copiar de ahí a Meta, no al revés.
