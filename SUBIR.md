# Cómo subir la web oficial — y por qué las portadas salen negras

## El problema, en una línea

El `index.html` **sí está publicado y es correcto**. Lo que falta es la carpeta
`portafolio/` con las 34 imágenes. Verificado contra el sitio en vivo:

```
index.html                     200  ✔
icons/*                        200  ✔
portafolio/*.webp (34)         404  ✘  <- por esto todas las portadas salen negras
```

El navegador pide cada portada, recibe un 404 y deja el hueco en negro. No es un
fallo del diseño ni de las imágenes: **las imágenes no están allá.**

---

## Opción A — Subirlo ya, sin credenciales (2 minutos)

1. Abrí **https://github.com/kaizenleap/KaizenLeapOficial**
2. Botón **Add file** → **Upload files**
3. **Arrastrá la carpeta `portafolio` completa** desde
   `E:\Kaizen Leap\Recursos personal\Web Oficial\`
   (Chrome acepta arrastrar carpetas y respeta las rutas)
4. Abajo, **Commit changes**

En un minuto GitHub Pages publica y las portadas aparecen.

> ⚠️ Arrastrá **la carpeta**, no los archivos sueltos: si subís los 34 archivos
> sueltos quedan en la raíz y las rutas `portafolio/xxx.webp` no van a encontrarlos.

---

## Opción B — Arreglar el `git push` de una vez (recomendado)

Esto es lo que resuelve el problema para siempre. Ya dejé el repositorio listo:
el historial está reconciliado y **la subida es un avance directo**, sin forzar nada.

Abrí una terminal **tuya** (PowerShell o Git Bash) y pegá:

```
cd "E:\Kaizen Leap\Recursos personal\Web Oficial"
git push origin main
```

Se va a abrir el navegador pidiendo autorizar Git Credential Manager con tu cuenta
de GitHub. **Autorizá una vez** y queda guardado: a partir de ahí todas las subidas
son un `git push` normal.

Si el navegador no abre o falla, la alternativa segura es un token:

1. Entrá a **github.com/settings/tokens** → **Generate new token (classic)**
2. Marcá el permiso **`repo`**. Caducidad: la que quieras.
3. Copiá el token y, cuando `git push` pida usuario y contraseña, poné:
   - usuario: tu usuario de GitHub
   - contraseña: **el token** (no tu contraseña de GitHub)

---

## Por qué esto ya pasó tres veces

Porque subir a mano es frágil: cada vez que toco el `index.html` **también cambian
archivos de apoyo** (fuentes, imágenes), y esos se quedan atrás sin que se note.
La página se ve rota y no hay ningún aviso.

Con el `git push` funcionando, eso desaparece: sube todo junto, siempre.

---

## Qué va a subir cuando hagas el push

| | |
|---|---|
| **Añade** | 35 imágenes (`portafolio/`) |
| **Borra** | 3 logos crudos de 2025 que el sitio no usa |
| **Renombra** | `icons/Kaizen PNG.png` → `icons/kaizen-leap-isotipo.png` |
| **Modifica** | `index.html` (contenido idéntico al que ya está en línea) y el manifiesto |

El `index.html` que está en línea **ya es el correcto**: tiene las fuentes
incrustadas, el isotipo incrustado y la capa de medición. No hace falta volver a
subirlo a mano.
