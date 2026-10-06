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
  - **Buffet** (concesionario): solo carta, precios, menú del día, horario, WhatsApp y el interruptor "Cerrado hoy".

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
| 2. Definición de funciones | Cerrada. Pendiente: confirmar la fuente de datos de colectivos. |
| 3. Arquitectura de información | Cerrada. Pendientes menores: ubicación de la información general (pie del inicio u "Horario completo") y confirmar que tocar la sección actual estando en un detalle vuelve a la pantalla principal de la sección. |
| 4. Wireframes y prototipo (Figma) | Siguiente etapa |
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

## Funciones

| Función | Prioridad | Detalle |
|---|---|---|
| Horario del campus | Must | Estado abierto/cerrado en el inicio; horario semanal y excepciones en "Horario completo". Carga: admin. |
| Novedades | Must | Noticias y eventos. Una novedad destacada aparece en el inicio. Campo "destino": General o Campus Live. Carga: admin. |
| Inscripción a eventos con cupo | Should | Sin cuenta: nombre, apellido y teléfono. Un teléfono puede inscribir a varias personas (ej.: hermanos); el par nombre + teléfono es único por evento, comparando el nombre sin mayúsculas, tildes ni espacios de más. No se pide DNI (minimización de datos, Ley 25.326 art. 4). Datos borrados después del evento. |
| Buffet | Must | Carta y precios siempre visibles. Botón de pedido por WhatsApp (wa.me) activo solo dentro del horario cargado por el buffet; fuera de horario, aviso "cerrado, abre a las X". Interruptor "Cerrado hoy" que se restablece solo al día siguiente. Menú del día: Could. |
| Campus Live | Must (pedido por la Municipalidad) | Reproductor dentro de la app (sin reproducción automática), programación cargada a mano y 1 o 2 novedades exclusivas. Estado "en vivo" por API de YouTube, consultada por el servidor cada 15 minutos. |
| Horarios de colectivos | Should | Pendiente fuente de datos. La app recuerda en el celular la última parada usada; por defecto, la del campus. |

**Descartadas:** mapa interno, cuentas de estudiantes, últimas transmisiones.

**Modelo de datos propuesto para colectivos:** se cargan los horarios de salida de cada línea desde la terminal y los minutos de recorrido hasta cada parada. La app calcula la hora de pasada (salida + minutos). Mismo principio que el estándar GTFS. Son horarios estimados y la app debe indicarlo.

## Navegación

- Barra inferior: Inicio, Colectivos, Buffet, Novedades, Campus Live. Ícono + texto. Punto rojo en Campus Live cuando hay transmisión. Si se descarta Colectivos, quedan 4.
- Tocar la sección en la que ya estás: no pasa nada.
- Volver regresa a la pantalla de origen. Desde la pantalla principal de una sección, regresa al Inicio. Desde el Inicio, sale de la app.
- Cambiar de sección con la barra no se acumula en el historial de Volver (el botón atrás del navegador debe respetar esto).
- Atajos del Inicio (próximo colectivo, novedad destacada, En vivo ahora): Volver regresa al Inicio.
- Desde "Inscripción confirmada", Volver regresa al detalle del evento, no al formulario.
- Enlaces externos (WhatsApp, YouTube) se indican con ícono de enlace externo.
- Panel: dirección aparte (`/panel`), menú según el rol, Volver regresa al inicio del panel, sesión vencida pide iniciar sesión y vuelve a la pantalla en la que estaba.

## Estados a diseñar en wireframes

- Campus cerrado y horario especial.
- Sin más colectivos hoy.
- Buffet cerrado y producto sin stock.
- Cupo completo.
- Persona ya anotada.
- Error de envío.
- Sin transmisión en vivo.
- Error de campo en el panel.

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
- **Backend:** obligatorio, con autenticación por los roles.
- **API de YouTube:** la búsqueda tiene un cupo de 100 consultas por día; por eso la programación se carga a mano.
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

- Inventario de contenidos (vigente): https://docs.google.com/spreadsheets/d/1fChj3B5jwjhQJagW3sqGoWAqUAAX3ArWnE9qBIoiN6Y/edit?gid=588683704#gid=588683704
- FigJam de la etapa 3 (mapas, flujos y navegación): https://www.figma.com/board/vsJ75rbz2edxVHa8HHgNhi
