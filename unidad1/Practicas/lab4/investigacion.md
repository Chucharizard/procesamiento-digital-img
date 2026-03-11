# Filtro Bayer y uso en imágenes digitales

## ¿Qué es el filtro Bayer?

El **filtro Bayer** es una especie de “rejilla de colores” que se pone encima del sensor de la cámara.
Cada cuadradito del sensor queda tapado con un filtro **rojo, verde o azul**, así que cada píxel solo ve **un color**, no los tres a la vez.

El patrón que se usa normalmente tiene **dos píxeles verdes, uno rojo y uno azul** en cada bloque de 2×2.
Hay más verdes porque el ojo humano es más sensible al verde y así la imagen se ve con más detalle y más natural.

Este diseño lo propuso **Bryce Bayer**, de la empresa Kodak, en los años 70, y por eso lleva su apellido.

---

## ¿Por qué se usa en procesamiento digital de imágenes?

Sin este filtro, el sensor solo podría sacar una foto en **blanco y negro**, porque solo mide cuánta luz llega, pero no sabe de qué color es.
Con el filtro Bayer, cada punto de la imagen aporta al menos un color (R, G o B) y luego el procesador de la cámara o el programa en la PC se encarga de reconstruir la imagen a color.

Ese proceso se llama **demosaicing**: el programa mira los píxeles vecinos y **rellena los colores que faltan** haciendo promedios y estimaciones.
Al final, de tener un mosaico de puntitos rojos, verdes y azules, se pasa a tener una imagen normal donde cada píxel ya tiene sus tres valores RGB.

En PDI esto es importante porque **antes de aplicar filtros, detectar bordes o segmentar**, la imagen ya pasó por este paso del filtro Bayer y el demosaicing.
Si esta parte sale mal, se ven colores raros o bordes feos que luego afectan todo lo demás.

---

## Versiones del filtro Bayer en OpenCV

En OpenCV hay varios códigos según cómo esté ordenado el mosaico en el sensor.
Se usan con `cv2.cvtColor` para pasar del mosaico Bayer a una imagen RGB lista para procesar:

| Código de OpenCV        | Patrón que usa |
|-------------------------|----------------|
| `cv2.COLOR_BayerBG2RGB` | BGGR → RGB     |
| `cv2.COLOR_BayerGB2RGB` | GBRG → RGB     |
| `cv2.COLOR_BayerRG2RGB` | RGGB → RGB     |
| `cv2.COLOR_BayerGR2RGB` | GRBG → RGB     |

La idea práctica en el código es:

1. Cargar la imagen en formato Bayer.
2. Llamar a `cv2.cvtColor` con el código correcto.
3. Trabajar con la imagen RGB resultante en los demás ejercicios de PDI.

---

## Mini resumen

- El sensor solo mide luz, no color.
- El filtro Bayer pone filtros R, G y B encima para que cada píxel vea un color.
- Hay el doble de verdes porque así vemos mejor el detalle.
- Luego un algoritmo (demosaicin)