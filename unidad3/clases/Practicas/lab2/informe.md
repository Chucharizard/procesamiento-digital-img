# Informe de Práctica: Aliasing y Patrones de Moiré

**Laboratorio 2 - Unidad 3**

## ¿Qué hicimos en esta práctica?

En este laboratorio se trabajó con dos problemas muy comunes al trabajar con imágenes digitales: el **aliasing** y los **patrones de Moiré**.

### 1. Suavizado de Patrones de Moiré

Usamos una imagen base (`Moire.png`) y le generamos patrones de franjas superpuestas para simular un efecto de Moiré bastante marcado. Para solucionarlo, implementamos filtros de **convolución diagonal** y **diagonal inversa**.
La ventaja de estos filtros es que promedian los píxeles en direcciones específicas, lo que resulta súper efectivo para atenuar estos patrones repetitivos sin destruir por completo el resto de la imagen.

### 2. Reducción de Aliasing (Anti-aliasing)

Por otro lado, trabajamos con la imagen `Aliasing.png` para ver qué ocurre al reducir drásticamente el tamaño (resolución) de una imagen:

- **Sin pre-blur:** Al achicarla directamente, notamos cómo aparecen los molestos bordes dentados y distorsiones visuales fuertes (aliasing puro).
- **Con pre-blur:** Aplicamos un suavizado (filtro Gaussiano) justo antes de reducirla. Aunque la imagen resultante es más suave o "borrosa", logramos eliminar los artefactos del aliasing. Esto funciona como un filtro paso bajo para respetar el límite de frecuencias antes del muestreo.

### Conclusión

Se vió de forma práctica que si no tratamos las altas frecuencias antes de cambiar resoluciones o al enfrentar patrones repetitivos finos, aparecen efectos indeseados. Usar filtros previos (anti-aliasing) y convoluciones direccionales (como la diagonal) nos ayuda a "limpiar" la imagen y obtener un resultado mucho más presentable.
