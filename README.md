# Ludoteca Caron — Programa de Funciones

Sitio estático para GitHub Pages. Estructura:

```
index.html          ← la página (≈500 KB)
fonts/              ← 6 tipografías .woff2 (≈390 KB)
img/                ← tapas de juegos + coco.jpg + manifest.js
datos/partidas.json ← el registro de partidas jugadas (base de datos)
```

## Publicar

Reemplazá TODO el contenido del repo con estas carpetas y archivos.
La página queda en https://faviocaron.github.io/Ludoteca/

## Agregar la foto de un juego (2 pasos, sin tocar código)

1. Subí la imagen a `img/` con el nombre del código y extensión .jpg
   (el código está en cada ficha: `E·07` → archivo `E-07.jpg`, con guión).
   Ideal: cuadrada o 4:3, máx. 760 px de lado, JPG.
2. Abrí `img/manifest.js` y agregá el código a la lista:
   `window.FOTOS=["E-07","C-01",...];`

Al recargar, esa ficha pasa de cartel tipográfico a tapa automáticamente.
Si la imagen falta o falla, la ficha vuelve sola al cartel tipográfico.

## El Libro de Funciones (registro de partidas)

Al final de la página hay un board para anotar cada partida jugada: qué juego,
cuándo, quiénes estuvieron, quién ganó, puntajes, duración real y una anécdota.
Con eso arma solo la tabla de posiciones, las más jugadas y la lista de juegos
todavía sin estrenar.

El dato vive en **dos copias del mismo registro**:

| Copia | Dónde | Para qué |
|---|---|---|
| De trabajo | `localStorage` de tu navegador | Anotás al instante, sin cuentas ni internet |
| Publicada | `datos/partidas.json` en el repo | Versionada, la ve cualquiera, alimenta el sitio |

Se **unen por `id`**: lo local pisa a lo publicado, así reimportar o volver a
entrar después de commitear nunca duplica una partida. Si borrás algo que ya
estaba publicado, se guarda una lápida para que no reaparezca.

### Publicar las partidas (2 pasos)

1. En el board, tocá **«Copiar JSON»** (o «Descargar JSON»).
2. Pegá el contenido en `datos/partidas.json` y commiteá.

Desde ahí lo ve todo el mundo y queda en el historial de git. El botón
**«Borrar lo no publicado»** limpia la copia local y deja solo lo del repo,
útil para confirmar que lo commiteado quedó bien.

> El repo es público: los nombres que anotes se publican al commitear.
> Si querés probar sin publicar nada, usá el board y no commitees el JSON.

### Formato

```json
{ "v": 1, "actualizado": "2026-09-11",
  "partidas": [{
    "id": "p-abc123-x9y8",
    "juego": "C·01",
    "fecha": "2026-09-08",
    "jugadores": [{"nombre":"Favio","puntos":42,"gano":true},
                  {"nombre":"Ana","puntos":38}],
    "resultado": "victoria",
    "duracion": 75,
    "notas": "Casi perdemos en el último turno"
  }]}
```

`juego` es el código de la ficha (`C·01`), así que se cruza directo con el
catálogo. `duracion` es la duración **real**, para poder contrastarla contra la
estimada de cada ficha.

## Notas

- «Imprimir programa» (en la cabecera del programa de mano) imprime solo
  la cartelera, en tinta sobre blanco, respetando los filtros activos.
- Los filtros, la ruleta de Coco, la doble función y el Libro de Funciones
  requieren JavaScript; sin JS la página igual muestra todo el catálogo.
- El Libro no se imprime: «Imprimir programa» sigue sacando solo la cartelera.
