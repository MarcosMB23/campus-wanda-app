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
- **Secundario:** personal de la Dirección de la Juventud de Wanda, con oficina en el campus. Candidato a cargar y actualizar los datos de la app.

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
| 2. Definición de funciones | En curso |
| 3. Arquitectura de información | Pendiente |
| 4. Wireframes y prototipo (Figma) | Pendiente |
| 5. UI con la marca del campus | Pendiente |
| 6. Validación (test de usabilidad) | Pendiente |
| 7. Arquitectura técnica | Pendiente |
| 8. Desarrollo | Pendiente |
| 9. Testing | Pendiente |
| 10. Despliegue y traspaso | Pendiente |

Regla: las decisiones de diseño se toman en Figma antes de programar.

## Filtros para evaluar funciones

1. **Pertinencia:** ¿se necesita fuera del campus o cambia? Si no, duplica la señalética.
2. **Viabilidad de datos:** ¿hay fuente y responsable de actualización? Si no, queda en pausa.
3. **Alineación:** ¿aporta a la contención de los estudiantes o a reducir barreras logísticas?
4. **Valor para el usuario:** frecuencia de uso y cuánto resuelve.
5. **Esfuerzo viable:** diseño y programación dentro del tiempo disponible.
6. **Priorización MoSCoW:** Must, Should, Could, Won't.

Una función sin fuente de datos ni responsable no puede ser Must.

## Funciones en evaluación

| Función | Estado |
|---|---|
| Horarios estimados de colectivos | Cumple F1, F3, F4 y F5. En pausa por F2 (fuente y responsable sin confirmar). |
| Horarios de apertura del campus | Por evaluar. El valor está en las excepciones, no en el horario fijo. |
| Agenda de actividades | Por evaluar. Depende de la carga de la Dirección de la Juventud. |
| Buffet (menú y precios) | En análisis de viabilidad. Depende del protocolo de carga del concesionario. |
| Mapa o wayfinding interno | Descartada: duplica la señalética. |

**Modelo de datos propuesto para colectivos:** se cargan los horarios de salida de cada línea desde la terminal y los minutos de recorrido hasta cada parada. La app calcula la hora de pasada (salida + minutos). Mismo principio que el estándar GTFS. Son horarios estimados y la app debe indicarlo.

## Requerimientos no funcionales

- Sin registro ni login para consultar.
- Liviana, pensada para datos móviles limitados.
- Acceso directo a la información más consultada.
- Panel de carga simple para personal sin conocimientos técnicos.
- Accesibilidad según WCAG 2.2.
- Usar "horarios programados" o "estimados", nunca "tiempo real", salvo que exista una fuente automatizada.

## Decisiones técnicas

- **Diseño:** Figma.
- **Demo:** GitHub Pages (solo sitios estáticos). Para la demo alcanza con datos en JSON; un backend externo solo si hay que mostrar el panel de carga funcionando.
- **Stack, backend y estructura de carpetas:** sin definir. Se deciden en la etapa 7.

## Pendientes clave

- Líneas de colectivo que pasan por el campus, empresas y si publican horarios.
- Responsable de actualizar cada módulo.
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
