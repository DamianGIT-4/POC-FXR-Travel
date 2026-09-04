# POC-FXR-Travel

Prototipo navegable de un funnel de vuelos (resultados → tarifa/pago) con **selector de moneda tipo wallet**, para explorar cómo debería comportarse el cambio de divisa en un sitio de viajes con configuración por mercado.

Un solo archivo, sin dependencias ni build: `index.html`.

**[Ver demo](https://damiangit-4.github.io/POC-FXR-Travel/)**

> Prototipo de exploración de diseño con datos ficticios. Identidad visual neutra (“trayecto”): no representa a ninguna marca real. Vuelos, tarifas y tipos de cambio son inventados.

## Qué se puede probar

| Zona | Qué hace |
|---|---|
| Barra superior | Cambia el mercado simulado (MX / AR) y muestra u oculta las notas de diseño |
| Wallet del nav (`MXN ($)`) | **Cambia la moneda real de cotización.** Opciones fijas por configuración del sitio: local + USD |
| Botón `≈ Comparar` | **No cambia el precio real.** Añade una línea de estimado bajo cada tarifa, en cualquier moneda de referencia |
| Wallet del resumen | Mismo cambio real, pero en el paso de tarifa |
| Micro-encuesta | Al elegir una moneda no local, pregunta el motivo |
| Panel de datos | Simulación local de la instrumentación: aperturas por punto de contacto, motivos y monedas elegidas |

Los filtros, el orden (mejor / más barato / más rápido) y la navegación entre pasos funcionan.

## La idea de diseño

**Dos mecanismos separados, no el mismo control repetido.**

- El **wallet** cambia la moneda en la que el sitio cotiza y cobra. Sus opciones están fijadas por configuración del mercado, no son un conversor universal.
- El **estimado (`≈`)** no toca esa moneda: solo añade una referencia secundaria bajo cada precio, para calcular mentalmente sin salir del funnel.

**Regla de formato de moneda.** El problema de origen es que `$` significa tanto peso mexicano como peso argentino:

- **Dentro del selector:** siempre `CÓDIGO (símbolo) · Nombre` — es el momento en que se está desambiguando.
- **Precios en la moneda local del sitio:** solo símbolo (`$3.180`) — el contexto ya elimina la ambigüedad.
- **Precios en cualquier otra moneda:** símbolo + código ISO (`US$173 USD`) — el código aparece exactamente cuando aparece el riesgo de confusión.

**Moneda de visualización ≠ moneda de cobro.** El resumen de tarifa lo dice explícitamente y se adapta: si estás viendo USD pero el cobro se procesa en la moneda local, la microcopia muestra ambos importes.

## Uso local

```bash
open index.html
```

## Licencia

MIT
