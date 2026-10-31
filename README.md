# EcoMonitor Ind. – Landing page con Tailwind CSS v4 e IA

Trabajo individual del Seminario en Gestión de Software Ágil Asistido por Inteligencia Artificial (FET).
Autor: Samuel Felipe Losada Rojas · Profesor: Camilo Morales Vargas

- **Sitio publicado:** https://samuellosadaro-cmyk.github.io/ecomonitor-tailwind/
- **Repositorio:** https://github.com/samuellosadaro-cmyk/ecomonitor-tailwind
- **Video:** [pendiente: enlace de YouTube]

## Temática
Landing page del Sistema Web para el Monitoreo y Análisis de Consumo Energético en el Sector Industrial, dirigida a gerentes y jefes de mantenimiento de empresas industriales en Colombia. Objetivo: que soliciten una demostración.

## Paleta (regla 60-30-10)
| Rol | Color |
|---|---|
| Dominante (60 %) | #FFFFFF |
| Secundario (30 %) | #1D4ED8 |
| Acento (10 %) | #C2410C |
| Éxito / Error / Advertencia | #15803D / #B91C1C / #B45309 |

Fuentes: Poppins (títulos) e Inter (textos).

## Prompt maestro
[ROL]
Actúa como un desarrollador frontend Senior experto en UI/UX y Tailwind CSS v4.

[CONTEXTO]
Necesito que construyas la landing page de mi "Sistema Web para el Monitoreo y Análisis de Consumo Energético en el Sector Industrial". Esta página está dirigida a gerentes y jefes de mantenimiento de empresas industriales en Colombia. El objetivo principal del sitio es convencerlos de que soliciten una demostración del software.

[TAREAS]
1. Navbar fija en la parte superior que incluya un logo, enlaces de navegación, un botón funcional para activar el modo oscuro y un menú hamburguesa para la versión móvil.
2. Sección Hero con un título principal atractivo, un subtítulo descriptivo y un botón de llamada a la acción.
3. Sección de Tarjetas destacando las funciones del sistema. Debe usar un sistema Grid que sea de 1 columna en móviles, 2 en tablets y 3 en pantallas de escritorio.
4. Sección "Nosotros" que explique brevemente quiénes somos y el propósito del desarrollo.
5. Sección de Preguntas Frecuentes (FAQ) construida con un componente de acordeón interactivo.
6. Sección de Formulario para "Solicitar demo". Debe incluir validación con JavaScript puro, mostrando los mensajes de error debajo de cada campo correspondiente, y lanzar una notificación tipo Toast al enviarse con éxito.
7. Footer con la información de derechos y enlaces básicos.

[RESTRICCIONES]
- Importa Tailwind utilizando exactamente este CDN: https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4
- Usa la directiva @theme para configurar la paleta de colores siguiendo la regla 60-30-10: Fondo dominante #FFFFFF (60 %), Color secundario #1D4ED8 (30 %), y Color de acento #C2410C (10 %).
- Incluye en el @theme los colores semánticos para los estados de éxito, error y advertencia.
- Importa solo dos fuentes de Google Fonts: 'Poppins' para los títulos e 'Inter' para los textos.
- Aplica el enfoque mobile-first en todo el diseño.
- Solo puedes usar JavaScript puro (Vanilla JS) para la interactividad (menú, modo oscuro, acordeón, validación y toast).
- Aplica buenas prácticas de accesibilidad: atributos alt en imágenes, etiquetas label en los inputs, un ratio de contraste mínimo de 4.5:1 y foco visible (focus-visible) para la navegación por teclado.

[FORMATO]
Devuelve la respuesta en un solo archivo index.html que contenga todo. Utiliza comentarios en español para separar claramente cada sección de la página y coloca todo el código JavaScript junto al final de la etiqueta <body>.

## Herramientas de IA usadas
- **Versión 1:** Gemini (Google), a partir del prompt maestro.
- **Iteraciones 1 a 5:** Claude (Anthropic).

## Bitácora de iteraciones
| # | Prompt de ajuste | Problema detectado | Resultado | ¿Funcionó? |
|---|---|---|---|---|
| 1 | "Los colores de éxito, error y advertencia no cumplen el contraste mínimo de 4.5:1 que pedí. Cámbialos por #15803D, #B91C1C y #B45309." | Gemini no respetó el prompt: puso #10B981, #EF4444 y #F59E0B. El texto blanco del toast sobre el verde daba un contraste de 2,5:1 y era difícil de leer. | Se cambiaron los tres colores en el `@theme`; el toast y los mensajes de error ya pasan 4.5:1. | Sí |
| 2 | "El hero tiene un cuadro gris que dice [Imagen del Dashboard Industrial] y la sección Nosotros no tiene imagen. Pon imágenes reales con texto alternativo." | La IA dejó un marcador de posición en lugar de una imagen, y sin imágenes no se podía demostrar el uso de `alt`. | El hero tiene una ilustración SVG del dashboard con `role="img"` y título accesible; Nosotros tiene una foto con `alt` descriptivo en un grid de dos columnas. | Sí |
| 3 | "El color secundario azul casi no aparece: el navbar es blanco y el footer gris. Aplica bien la regla 60-30-10 usando el azul en el navbar, el menú móvil y el footer." | El 30 % del color secundario no se cumplía; el azul solo estaba en los títulos. | Navbar, menú móvil y footer quedaron en `bg-secundario` con texto blanco; en modo oscuro pasan a gris. | Sí |
| 4 | "En el menú no hay enlace al formulario y el botón hamburguesa no indica si está abierto. Agrega un botón Solicitar demo en el menú y aria-expanded." | No había forma de llegar al formulario desde el navbar, y el botón del menú no informaba su estado a lectores de pantalla. | Se agregó el botón "Solicitar demo" (color acento) en el menú de escritorio y móvil, y el botón hamburguesa actualiza `aria-expanded` y `aria-label`. | Sí |
| 5 | "Solo hay 3 tarjetas y 2 preguntas; en tablet la tercera tarjeta queda sola. Agrega 3 funciones más y 2 preguntas frecuentes." | Con 3 tarjetas el grid de 2 columnas quedaba descuadrado y la página se veía con poco contenido. | 6 tarjetas (grid 1/2/3 columnas completo) y 4 preguntas en el acordeón. | Sí |

Las versiones de cada iteración están en la carpeta `versiones/` (v1 = Gemini, v2 a v6 = iteraciones 1 a 5).

## Cambios manuales (sin IA)
Hechos a mano por Samuel en VS Code sobre la versión 6 (resultado: `index.html` y `versiones/v7_final_con_cambios_manuales.html`).

1. **Validación real del correo.** La IA solo comprobaba que el correo tuviera una "@" (`includes('@')`), así que "a@" pasaba como válido. Lo cambié por la expresión regular `/^[^\s@]+@[^\s@]+\.[^\s@]+$/`, que exige texto, @, dominio y extensión.
2. **El modo oscuro se recuerda.** Al recargar la página el sitio volvía al modo claro. Agregué `localStorage.setItem('tema', ...)` dentro de `toggleTheme()` y, al cargar, si el tema guardado es "oscuro" se vuelve a activar.
3. **El menú móvil se cierra al tocar un enlace.** En celular el menú quedaba abierto tapando la sección. Agregué un `forEach` sobre `#mobile-menu a` que oculta el menú y pone `aria-expanded="false"` al hacer clic.
