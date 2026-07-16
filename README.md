# WHITEMOON-CERRAJEROS

Demo web para **Carlos · Cerrajero 24h Majadahonda y Zona Noroeste**, construida por
[WhiteMoon Agencia IA](https://whitemoon.es).

Demo: https://nexusforgeia.github.io/WHITEMOON-CERRAJEROS/

## Stack

- HTML/CSS/JS puro, sin frameworks ni dependencias externas (solo la fuente Sora).
- Supabase (`mlaqtniujnvfxcvcourm`) para el circuito de leads.
- Edge Function `cerrajeros-notify` (Deno) → CallMeBot para el aviso por WhatsApp.
- Deploy: GitHub Pages.

## Contacto (importante)

Todos los CTA de teléfono, WhatsApp y email son los de **WhiteMoon**, no los del cliente:

| Canal | Valor |
|---|---|
| Teléfono / urgencias 24h | `tel:+34643199580` |
| WhatsApp | `https://wa.me/34643199580` |
| Email | `comercial@whitemoon.es` |

El teléfono y el email de Carlos **no aparecen en ningún punto de la demo**. Solo se
cambiarán a los suyos cuando se convierta en cliente de pago.

## Circuito de leads

1. El chatbot recoge: urgencia/servicio → zona → nombre → teléfono.
2. Inserta el lead en `leads_web` (`sector='cerrajeria'`, `origen='cerrajeros-demo'`).
3. Llama a `cerrajeros-notify`, que envía el aviso por WhatsApp vía CallMeBot.

> `leads_web` no tiene columnas `zona` ni `servicio`. Siguiendo la convención del resto
> de demos, el servicio va en `interes` y la zona se guarda dentro de `mensaje`. En el
> payload de la Edge Function sí viajan como campos propios (`zona`, `servicio`).

El aviso va **siempre** a `WA_NUMBER` (34643199580, el WhatsApp de WhiteMoon).
`CALLMEBOT_APIKEY` y `WA_NUMBER` viven en los Secrets del proyecto Supabase y **nunca**
se exponen en el JS del cliente.

## Estructura

```
index.html                                  landing completa (estilos + JS inline)
og.jpg                                      Open Graph 1200x630
robots.txt / sitemap.xml / llms.txt         SEO / GEO / AEO
supabase/functions/cerrajeros-notify/       Edge Function (Deno)
```

## Datos del negocio

Cerrajero **a domicilio**: no hay local de atención al público, por lo que no se publica
dirección postal — solo localidad (Majadahonda) y `areaServed`. Más de 25 años de
experiencia, llegada en 20-30 min, 365 días al año, presupuesto cerrado antes del trabajo
y sin coste de desplazamiento.

No se publican reseñas, casos de éxito ni dirección: no existen y no se inventan.
