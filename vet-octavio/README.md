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

- Violeta (principal): `#4A2470` · Violeta oscuro: `#32174A` — **tomado del logo**,
  muestreado del archivo original para que web y logo sean la misma marca
- Ámbar (acento): `#E8A33D`
- Carbón: `#2B2B2B` · Crema: `#FBF6EE`
- Tipografías: Baloo 2 (títulos) + Nunito (texto), igual que el resto del ecosistema

## Datos

- WhatsApp (laboral): **11 7062-3869** → `wa.me/5491170623869`
- Instagram: **@vetoctavio8a**
- Matrículas: **MP 16465 · MN 11170**
- Formación: Médico Veterinario (UBA, 2024), Intensificación en Pequeños Animales
- Docente (Ayudante de Segunda rentado), Cátedra de Anatomía Veterinaria FCV-UBA, desde 2017
- Clínica de pequeños animales desde 2021 (Hospital Veterinario Virreyes, Veterinaria
  Santa Rita, Veterinaria Pacheco) y dirección clínica de consultorio desde 2025
- Fundador de Canal Veterinario Live (formación continua **para veterinarios**)
- Investigación: Beca Estímulo UBACyT (2022–2024), plastinación y conservación anatómica;
  presentaciones en congresos de anatomía

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

- [x] ~~Foto de perfil~~ → `img/octavio.jpg`, recortada de la foto con la perra negra.
      Se descartó la del gato blanco: tiene vía y vendaje, se lee como paciente
      internado y choca con el mensaje de "sin estrés".
- [x] ~~Logo~~ → `img/logo.png`, extraído del retrato con fondo hecho transparente.
- [ ] **Videos propios dirigidos a dueños** en la sección "Para que decidas informado"
      (hoy hay 3 tarjetas de ejemplo). **No reutilizar material de Canal Veterinario
      Live**: esa plataforma le habla a colegas veterinarios, no a dueños de mascotas.
      Son dos audiencias distintas.
- [x] ~~Imagen Open Graph~~ → `img/og-image.jpg` (1200×630).
- [ ] **Logo en origen**: el actual se extrajo de un JPG, así que tiene bordes con
      algo de ruido. Si aparece el archivo vectorial (SVG/PDF), conviene reemplazarlo.

## Dos audiencias que no hay que mezclar

Octavio produce contenido para **veterinarios** (Canal Veterinario Live) y esta landing
le habla a **dueños de mascotas**. Canal Veterinario funciona acá como credencial —
enseña a colegas, lo cual suma autoridad— pero su material no sirve como contenido de
la landing. Los videos para dueños hay que producirlos aparte.

## Sincronía con Meta Business IA

Las preguntas frecuentes de la landing y la base de conocimiento de la IA deben decir
lo mismo. Conviene tratar el bloque FAQ de `index.html` como la fuente de verdad y
copiar de ahí a Meta, no al revés.
