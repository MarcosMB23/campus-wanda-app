# CLAUDE.md

Contexto e instrucciones para trabajar con Claude en este repositorio.

## Proyecto

Web app de servicios del Campus Estudiantil de Colonia Wanda (Misiones, Argentina). Es el Eje 4 (Ecosistema Digital) del Trabajo Final de Grado de Diseño Gráfico, FAyD, Universidad Nacional de Misiones (UNaM).

El proyecto completo tiene cuatro ejes:

1. Identidad institucional: marca autónoma respaldada por la Municipalidad de Wanda. **Terminada.**
2. Señalética accesible: wayfinding, Braille y alto contraste. **Casi terminada.**
3. UX física: co-diseño de la sala de streaming. **Marca terminada.**
4. Ecosistema digital: esta web app. **En curso.**

## Usuarios

- **Principal:** estudiantes de secundaria (EPET N° 48, Instituto Nuestra Señora del Iguazú, entre otras) que usan el campus entre turnos escolares.
- **Secundarios:** cargan y actualizan los datos desde el panel de carga, con dos roles:
  - **Admin** (Dirección del campus): edita todo y administra las cuentas.
  - **Buffet** (concesionario): solo carta, precios, menú del día, horario y WhatsApp del buffet.

Los estudiantes no crean cuentas.

## Principio rector

La app es una herramienta de apoyo, no un requisito. La experiencia en el campus no debe depender de usarla: la señalética resuelve lo esencial. La app aporta solo donde la señalética no llega:

- Información que se necesita **fuera del campus** (antes de ir, al planificar la salida).
- Información que **cambia** (horarios especiales, eventos, precios).

Los estudiantes no participan en el diseño de la app. Sí se prevé un test de usabilidad sobre el prototipo.

## Metodología

Doble Diamante (Descubrir, Definir, Desarrollar, Entregar) y los 5 planos de Jesse James Garrett.

| Etapa | Estado |
|---|---|
| 1. Investigación | Hecha |
| 2. Definición de funciones | Casi cerrada |
| 3. Arquitectura de información | En curso |
| 4. Wireframes y prototipo (Figma) | Pendiente |
| 5. UI con la marca del campus | Pendiente |
| 6. Validación (test de usabilidad) | Pendiente |
| 7. Arquitectura técnica | Pendiente |
| 8. Desarrollo | Pendiente |
| 9. Testing | Pendiente |
| 10. Despliegue y traspaso | Pendiente |

Regla: las decisiones de diseño se toman en Figma antes de programar.

Cierre de alcance: el alcance se cierra al empezar el prototipo. Las funciones nuevas que surjan después van a una versión futura; los ajustes a funciones existentes sí se aceptan.

## Filtros para evaluar funciones

1. **Pertinencia:** ¿se necesita fuera del campus o cambia? Si no, duplica la señalética.
2. **Viabilidad de datos:** ¿hay fuente y responsable de actualización? Si no, queda en pausa.
3. **Alineación:** ¿aporta a la contención de los estudiantes o a reducir barreras logísticas?
4. **Valor para el usuario:** frecuencia de uso y cuánto resuelve.
5. **Esfuerzo viable:** diseño y programación dentro del tiempo disponible.
6. **Priorización MoSCoW:** Must, Should, Could, Won't.

Una función sin fuente de datos ni responsable no puede ser Must.

## Funciones en evaluación

| Función | Prioridad | Detalle |
|---|---|---|
| Horario del campus | Must | Estado abierto/cerrado en el inicio, horario semanal y excepciones. Carga: admin. |
| Novedades | Must | Noticias y eventos del campus. Una novedad destacada aparece en el inicio. Carga: admin. |
| Inscripción a eventos con cupo | Should | Sin cuenta: nombre, apellido y teléfono. Control de duplicados por teléfono en cada evento. Datos borrados después del evento. |
| Buffet | Must | Carta, precios y botón de pedido por WhatsApp (wa.me). El menú del día es Could. Carga: rol buffet. |
| Campus Live | Must (pedido por la Municipalidad) | Reproductor dentro de la app, programación y novedades exclusivas de Campus Live. Estado "en vivo" vía API de YouTube, consultada por el servidor cada 15 minutos. Carga de programación y novedades: admin. |
| Horarios de colectivos | Should | Pendiente confirmar la fuente de datos. |

**Descartadas:** mapa interno (duplica la señalética), cuentas de estudiantes, últimas transmisiones.

**Modelo de datos propuesto para colectivos:** se cargan los horarios de salida de cada línea desde la terminal y los minutos de recorrido hasta cada parada. La app calcula la hora de pasada (salida + minutos). Mismo principio que el estándar GTFS. Son horarios estimados y la app debe indicarlo.

## Navegación

- Barra inferior con Inicio, Colectivos, Buffet, Novedades y Campus Live. Si Colectivos se descarta, quedan 4 secciones.
- El panel de carga se accede por una dirección aparte (`/panel`) y no figura en la navegación pública.

## Requerimientos no funcionales

- Sin registro ni login para consultar.
- Liviana, pensada para datos móviles limitados.
- Acceso directo a la información más consultada.
- Panel de carga simple para personal sin conocimientos técnicos.
- Accesibilidad según WCAG 2.2.
- Usar "horarios programados" o "estimados", nunca "tiempo real", salvo que exista una fuente automatizada.
- El reproductor no se reproduce automáticamente (datos móviles).
- Datos personales mínimos, con aviso de uso.
- Permisos por rol aplicados en el servidor.
- La clave de la API de YouTube queda en el servidor, nunca en el código de la app.
- Fecha de "última actualización" visible en precios y colectivos.

## Decisiones técnicas

- **Diseño:** Figma.
- **Backend:** la app requiere backend con autenticación por los roles.
- **API de YouTube:** cupo de 100 búsquedas por día; por eso la programación se carga a mano.
- **Stack y estructura de carpetas:** sin definir. Se deciden en la etapa 7.
- **Figma MCP:** para leer diseños de Figma y pasarlos a código.
- **Playwright MCP:** para probar la app en navegador (celular, conexión lenta) en la etapa de testing.
- **Skill Impeccable:** usarla solo como auditor y corrector (audit, critique, harden, clarify, adapt, optimize, polish). No usar bolder, overdrive, delight ni animate. Las decisiones visuales salen de Figma y de la marca del campus, no de la skill.
- **Skill emil-design-eng:** solo para el pulido final de transiciones, respetando prefers-reduced-motion.

## Pendientes clave

- Líneas de colectivo que pasan por el campus, empresas y si publican horarios.
- Hosting y dominio a largo plazo: quién los paga (fuera del alcance del proyecto).
- Turnos y horarios confirmados del campus.

## Instrucciones de interacción

- Responder solo lo pedido. No generar ideas, textos largos ni código no solicitados.
- Verificar la información y el código antes de afirmarlos. Cero suposiciones.
- Ser crítico: corregir errores de lógica de diseño o programación con fundamentos, sin halagos.
- Explicar los errores de forma simple, directa y técnica.
- Tono empático, directo y serio.
- Sin relleno conversacional.
- Al corregir código, mostrar solo el bloque modificado y marcar lo que no cambia con `// ... código existente ...`.
- Ante tareas extensas, proponer primero un esquema breve y preguntar qué desarrollar.
- En textos de diseño, usar viñetas o párrafos cortos.

## Documentación

Relevamientos, planos, entrevistas y la planilla de funciones están en `docs/`.

Etapa 3: el inventario de contenidos está en `docs/` y los mapas en FigJam (ETAPA 3 ARQ DE INFORMACIÓN).
