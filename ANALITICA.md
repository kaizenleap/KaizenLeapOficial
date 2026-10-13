# Analítica de la web oficial — qué falta y cómo se termina

La capa de medición **ya está instalada y probada** en `index.html`. Registra las
conversiones reales del sitio y no hace ni una petición a terceros mientras los IDs
estén vacíos (verificado).

Lo único que falta son **dos IDs**, y para conseguirlos hay que entrar con tu cuenta
de Google y de Meta. No se pueden crear desde fuera: Google y Meta exigen tu sesión.

---

## Paso 1 — Google Analytics 4 (~3 minutos)

1. Entrá a **analytics.google.com** con tu cuenta de Google.
2. **Administrar** (el engranaje, abajo a la izquierda) → **Crear** → **Cuenta**.
3. Nombre de la cuenta: `Kaizen Leap`. Aceptá las condiciones.
4. **Crear propiedad**:
   - Nombre: `Web Oficial`
   - Zona horaria: **Colombia (GMT-5)**
   - Moneda: **Peso colombiano (COP)**
5. Sector: `Marketing y publicidad` · Tamaño: `Pequeña (1-10)`.
6. Objetivos: marcá **«Generar clientes potenciales»** y **«Examinar el tráfico web»**.
7. Plataforma: **Web**.
   - URL del sitio: `https://kaizenleap.github.io/KaizenLeapOficial/`
   - Nombre del flujo: `Web Oficial`
8. Te muestra el **ID de medición**: algo como **`G-AB12CD34EF`**. **Copialo.**

> 📌 Si te ofrece «instalar con Google Tag Manager», ignorálo. Ya está resuelto.

---

## Paso 2 — Píxel de Meta (~3 minutos)

1. Entrá a **business.facebook.com** → **Administrador de eventos**.
2. Si no tenés píxel: **Conectar orígenes de datos** → **Web** → **Crear un píxel**.
   - Nombre: `Kaizen Leap — Web`
3. Te da un **ID de píxel**: 15 o 16 dígitos, algo como **`1234567890123456`**. **Copialo.**
4. En **Configuración**, activá **«Seguimiento automático sin código»** si te lo ofrece.
   No hace falta: el código ya está instalado.

---

## Paso 3 — Pegar los IDs

Con los dos IDs, se instalan en un comando:

```bash
"C:/Users/Kaizen/.workbuddy-ai/binaries/python/envs/default/Scripts/python.exe" \
    "E:/Kaizen/herramientas/_test/instalar_analitica.py" \
    --ga G-AB12CD34EF --meta 1234567890123456
```

O a mano: abrí `index.html`, buscá `KL_GA4` (está arriba del todo) y pegá los valores
entre las comillas. Después subí el `index.html` como siempre.

**Pasámelos y lo hago yo.**

---

## Qué va a medir

| Evento | Cuándo se dispara |
|---|---|
| **`click_whatsapp`** | Cada clic a WhatsApp, con la ubicación (menú, hero, cuerpo, pie, formulario). **Es la conversión que importa.** |
| `formulario_enviado` | Al enviar el formulario, con el servicio elegido |
| `video_abierto` | Al abrir una pieza del portafolio, con su título |
| `salida_a_planes` | Clic hacia la Propuesta Global o el Tarifario |
| `salida_a_redes` | Clic a Instagram o TikTok |
| `scroll_50` / `scroll_90` | Cuando lee la mitad o el final de la página |

Con eso vas a poder responder: **cuánta gente entra, de dónde viene, cuántos te
escriben y qué sección los convence.** Hoy no podés responder ninguna.

---

## Sobre la ley de datos (Ley 1581 de Colombia)

GA4 y el píxel de Meta instalan cookies de terceros. Para una web que recoge datos
de visitantes, lo correcto es **avisar**. Dos opciones:

- **Simple**: una línea en el pie — «Usamos cookies para medir el tráfico» — con
  enlace a una página de privacidad. Es lo que hace la mayoría de pymes.
- **Completo**: un aviso de cookies con botón de aceptar que solo carga la analítica
  después del consentimiento.

Hoy **no hace falta**: con los IDs vacíos no se instala ninguna cookie. Cuando los
pongas, decime y añado el aviso en la misma tanda.

---

## La alternativa sin cuentas (si la querés)

Si preferís no depender de Google ni de Meta, se puede montar un contador propio que
guarda los datos en tu propia base, sin cookies y sin terceros. Da menos detalle que
GA4, pero los datos son tuyos y no hay que avisar de cookies.

No lo armé porque pediste las cuentas. Si te interesa, decilo y lo hago.
