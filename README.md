# Ludoteca Caron — Programa de Funciones

Sitio estático para GitHub Pages. Estructura:

```
index.html          ← la página (≈480 KB)
fonts/              ← 6 tipografías .woff2 (≈390 KB)
img/                ← tapas de juegos + coco.jpg + manifest.js
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

## Notas

- «Imprimir programa» (en la cabecera del programa de mano) imprime solo
  la cartelera, en tinta sobre blanco, respetando los filtros activos.
- Los filtros, la ruleta de Coco y la doble función requieren JavaScript;
  sin JS la página igual muestra todo el catálogo.
