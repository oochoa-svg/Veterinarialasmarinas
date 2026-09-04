# Vet. Octavio Ochoa — Veterinario de cabecera a domicilio

Landing personal de Octavio Ochoa. A diferencia de `las-marinas` y `mi-fiel-amigo`,
que son sitios de clínicas, esta es una **marca personal**: el protagonista es el
profesional, no el local.

```
vet-octavio/
├── public/
│   ├── index.html       ← la landing completa (un solo archivo)
│   └── img/             ← foto de perfil, logo y certificados (pendiente)
├── firebase.json        ← hosting, site "vetoctavio8a"
├── .firebaserc          ← proyecto Firebase (veterinarialasmarinas)
└── README.md
```

## Rol de la landing dentro de la estrategia

Octavio paga anuncios (Meta Ads) que traen tráfico directo a este sitio. La landing es
un **filtro antes del WhatsApp**: nadie ve un número de celular clickeable en ningún
lado (ni en el hero, ni en el nav, ni en el footer, ni en el botón flotante). Todo el
sitio empuja a completar el formulario de `#turno`, y **recién ahí**, al final, se abre
WhatsApp con el mensaje ya armado.

El problema que esto resuelve: sin filtro, cualquiera que ve el número escribe "hola,
una consulta" y hay que ir preguntando de a poco zona, mascota y motivo. Con el
formulario, el primer mensaje ya llega completo.

Más allá del filtro, la landing también:

- **Que lo conozcan**: trayectoria, formación, matrículas y certificados reales.
- **SEO**: captar a quien busca "veterinario a domicilio `<barrio>`" en Google y
  todavía no lo conoce. Por eso las zonas se nombran una por una (ver más abajo).
- **Contenido**: videos y material de Canal Veterinario.

## El filtro (`#turno`)

Arranca con un triage de 2 opciones:

| Elige… | Qué pasa |
|---|---|
| Coordinar una consulta a domicilio | Sigue el formulario de 3 pasos → WhatsApp con todo cargado |
| Es urgente | Panel: si es grave, ir directo a una veterinaria de urgencias 24 hs (una visita a domicilio coordinada por WhatsApp no es lo más rápido). Igual puede seguir al formulario si prefiere. |

El formulario tiene 3 pasos:

1. **Zona** — buscador/desplegable (ver siguiente sección), no la nube de tags que
   había antes.
2. **Mascota y motivo** — nombre, especie, edad, motivo de consulta (select).
3. **Preferencia de día/horario + datos del tutor** — chips de día (Martes a Sábado +
   "Cualquiera") y de franja horaria (Mañana/Tarde/Lo que tengas), nombre del tutor y
   comentarios. Antes de enviar se previsualiza el mensaje tal cual se va a mandar.

El botón final abre `wa.me` con el mensaje armado por JS (función `armarMensaje()` en
el `<script>` de `index.html`). El número de WhatsApp está en la constante
`OCTAVIO_WHATSAPP` al principio del script — cambiarlo es una sola línea.

### Por qué NO hay selector de fecha/hora fijo (como en Mi Fiel Amigo)

Mi Fiel Amigo tiene un horario fijo semanal (miércoles y jueves, 15 a 17.30), así que
ahí el formulario genera fechas concretas ("miércoles 9 de septiembre"). **Acá no**,
porque Octavio describió su disponibilidad a domicilio como cambiante:

> Lunes por lo pronto no. Martes a la mañana, miércoles 15 a 20, jueves y viernes con
> más disponibilidad — y a partir del miércoles 16 empieza a trabajar día por medio en
> otra veterinaria, así que algunos miércoles va a estar libre para domicilios y otros
> no (miércoles 23 sí, por ejemplo).

Con ese patrón, ofrecer una fecha puntual generada automáticamente ("elegí miércoles
16") habría sido activamente incorrecto en cuanto empiece el esquema día por medio. En
vez de eso, el formulario pide una **preferencia** (días de la semana + franja horaria)
que se manda como dato informativo, y el día/horario exacto **siempre se confirma por
WhatsApp**, como aclara el texto arriba de los chips. Si en algún momento el horario a
domicilio se vuelve estable, ahí sí conviene pasar a un selector de fechas concretas
como el de Mi Fiel Amigo.

## Zona: buscador en vez de nube de tags

Antes había una sección "Dónde atiendo" con dos tarjetas de chips (Zona Norte / CABA).
Ahora ese contenido es el **paso 1 del formulario**: un input con autocompletado
(`#zona-input` + `#zona-lista`) que filtra por texto y agrupa por Zona Norte / CABA a
medida que se escribe. Si el barrio no está en la lista, se puede escribir igual y
avanzar («¿No ves tu barrio? Escribilo igual»).

Como los nombres de los barrios ya no están todos visibles de entrada (aparecen recién
al escribir en el buscador), se agregó un párrafo chico (`.zcobertura`) debajo del
buscador con **todos los barrios en texto plano**, para no perder el valor SEO que
tenía la nube de tags original (la razón por la que se nombran uno por uno sigue
siendo la misma: captar búsquedas por barrio).

## Certificados de formación continua — falta el material real

En "Quién te va a atender" → "Formación continua" hay un carrusel horizontal
(`.cert-track`, con scroll-snap y flechas en desktop) pensado para las fotos reales de
los certificados/diplomas de Octavio. **Hoy tiene 3 placeholders** (`.cert-placeholder`,
con borde punteado y el texto "Certificado (falta subir foto)") porque no hay fotos
reales cargadas todavía.

Para completarlo: agregar los archivos a `img/` (ej. `cert-01.jpg`, `cert-02.jpg`, …) y
reemplazar cada placeholder por:

```html
<figure class="cert-card">
  <img src="img/cert-01.jpg" loading="lazy" alt="Certificado: <nombre del curso> — Octavio Ochoa" />
</figure>
```

No hay límite de cantidad: el carrusel scrollea para el costado (swipe en mobile,
flechas en desktop) sin importar cuántas se agreguen.

## Identidad de marca

Paleta propia, distinta de las dos clínicas (naranja en Las Marinas, azul/verde en
Mi Fiel Amigo), para que se lea como una marca aparte:

- Violeta (principal): `#4A2470` · Violeta oscuro: `#32174A` — **tomado del logo**,
  muestreado del archivo original para que web y logo sean la misma marca
- Ámbar (acento): `#E8A33D`
- Carbón: `#2B2B2B` · Crema: `#FBF6EE`
- Tipografías: Baloo 2 (títulos) + Nunito (texto), igual que el resto del ecosistema
- El violeta (`.btn-turno`, `.turno-float`, chips, botón "Siguiente") se reserva para
  **"llevar al formulario"**. El verde de WhatsApp (`.btn-wa-send`) se reserva
  exclusivamente para el botón que de verdad abre WhatsApp, al final del formulario —
  para que un clic en violeta nunca se confunda con "esto abre el chat".

## Datos

- WhatsApp (laboral, solo en el JS del formulario — no aparece como link en ningún
  otro lado de la página): **11 7062-3869** → constante `OCTAVIO_WHATSAPP` en `index.html`
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

Están en el array `ZONAS` del `<script>` (buscador del paso 1) y en el párrafo
`.zcobertura` (texto plano para SEO) — hay que mantener ambos en sync si cambia la
cobertura.

## Plan Básico — eliminado

La landing tenía un "Plan Básico" (3 meses, $65.000, débito automático, acompañamiento
100% a distancia). **Se sacó por completo** de `index.html` (sección, CSS y menciones
en nav/hero/FAQ): Octavio pidió enfocar el sitio en el filtro de consultas a domicilio.
Si se retoma en el futuro, el diseño y el análisis de precios/posicionamiento que se
había hecho quedó en el historial de git de este README (versión anterior a este
cambio) — no hace falta rehacer ese trabajo desde cero.

## Pendientes de contenido

- [x] ~~Foto de perfil~~ → `img/octavio.jpg`, recortada de la foto con la perra negra.
- [x] ~~Logo~~ → `img/logo.png`, extraído del retrato con fondo hecho transparente.
- [ ] **Fotos reales de certificados** para el carrusel de "Formación continua" (ver
      sección de arriba) — hoy son 3 placeholders.
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
copiar de ahí a Meta, no al revés. El FAQ también está como JSON-LD (`FAQPage`) para
que Google pueda mostrarlo como resultado enriquecido.
