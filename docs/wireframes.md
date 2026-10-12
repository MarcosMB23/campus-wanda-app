# Wireframes

Especificación de la etapa 4 (wireframes y prototipo en Figma).

## Base

- Frame 360 × 800. Grilla de 4 columnas, margen 16, medianil 16, múltiplos de 8. Área táctil mínima 48 × 48.
- Contenedor "Contenido": vertical, separación 16, padding 16 / 24 / 16 / 80. Con el botón fijo del buffet, el padding inferior es 144.
- Alto del frame = alto de Contenido, con un mínimo de 800. La barra inferior queda fija en Y = 736.

## Estilos de texto

Tipografía provisoria.

| Estilo | Tamaño / alto de línea | Peso |
|---|---|---|
| Etiqueta | 14 / 20 | Regular |
| Dato | 20 / 28 | Bold |
| Detalle | 16 / 24 | Regular |
| Pestaña | 12 / 16 | Regular |
| Pestaña activa | 12 / 16 | Bold |

- Texto secundario: #666666 como mínimo (contraste 4.5:1 sobre blanco y sobre #EEEEEE).

## Componentes

- **Tarjeta:** etiqueta → imagen opcional (16:9, alto 168) → fila principal (Dato + flecha) → detalle. Variantes: Simple, Con imagen, Vacía (sin flecha, mensaje en #666666).
- **Pestaña:** 72 × 64, ícono de 24 arriba y texto abajo, separación 4. Variantes Inactiva / Activa. La activa lleva texto bold, ícono negro y una línea superior de 24 × 3 en posición absoluta. Propiedad booleana "En vivo" para el punto.
- **Barra inferior:** Inicio, Colectivos, Buffet, Novedades, Live. Fondo blanco y borde superior de 1 px #CCCCCC.
- **Encabezado:** 360 × 56. Variante Sección: ícono de la sección (decorativo, el mismo de la pestaña, alt="") + título. Variante Detalle: botón volver de 48 × 48 + título.
- **Fila pasada (colectivos):** hora (Dato) + bloque vertical (línea → destino en Detalle, empresa en Etiqueta). Lista plana con divisoria, no tocable.
- **Fila producto (buffet):** nombre y descripción + precio. Variante Disponible Sí / No; en No muestra el texto "Sin stock".
- **Botón:** 48 de alto. Activo con ícono de enlace externo ↗. Desactivado con texto que explica el motivo ("Pedidos desde las 8:00").

## Reglas

- Tarjeta con sombra = tocable. Lo que no es tocable no lleva sombra ni flecha.
- Las tarjetas del Inicio se tocan enteras (sin enlaces sueltos) y llevan a su sección.
- La etiqueta de la tarjeta usa el nombre completo de la sección. La pestaña puede usar una forma corta: "Live" (no entra "Campus Live" en 72 px). La pantalla de destino se titula "Campus Live".
- Los estados no dependen solo del color (WCAG 1.4.1).

## Pantallas

- **01 Inicio · normal:** Campus, Colectivos, Buffet, Novedad destacada.
- **01b Inicio · en vivo:** Campus, Live, Colectivos, Buffet, Novedad (Live en segundo lugar, visible sin desplazar).
- **01c Inicio · domingo:** campus cerrado, sin colectivos, buffet cerrado.
- **01d Inicio · sin novedades:** tarjeta Vacía.
- **02 Colectivos:** subtítulo "Parada Campus", aviso "Horarios estimados, pueden variar · Actualizado: [fecha]", lista de pasadas.
- **02c Colectivos · sin servicio.**
- **03 Buffet / 03b Buffet · cerrado:** estado, menú del día (Could), carta por categoría, fecha de actualización de precios, botón de WhatsApp fijo sobre la barra (Y = 672). Cerrado: la carta sigue visible y el botón queda desactivado con su motivo.

## Contenido del Inicio

- **Campus:** hora absoluta como dato principal ("Cierra a las 20:00"). El contador de tiempo restante queda como referencia para la etapa 5: sin segundos y actualizado por minuto (WCAG 2.2.2).
- **Novedad destacada:** etiqueta, imagen, título y tipo · fecha. Sin descripción. En un evento se muestra la fecha y hora del evento; en una noticia, la fecha de publicación.
- **Novedad sin imagen:** ilustración automática asignada al publicar (no aleatoria en cada carga).
