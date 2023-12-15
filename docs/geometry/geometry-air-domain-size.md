---
id: air-domain-size
title: Rol del tamaño del dominio de aire
sidebar_label: Tamaño del dominio de aire
sidebar_position: 4
---

Para cada simulación que cree, un dominio de aire o entorno de simulación **es una necesidad**. Es necesario para los cálculos electromagnéticos, y su **tamaño puede tener un fuerte impacto** en los resultados de la simulación tanto para la pieza como para el inductor.

## ¿Qué tamaño debe tener el dominio de aire?

El dominio de aire alrededor de la geometría se puede crear en diferentes tamaños - demasiado pequeño dará lugar a resultados inexactos, pero demasiado grande aumentará el recuento de elementos y por lo tanto el tiempo de cálculo.

La condición **Infinito BC** se utiliza para los límites exteriores del dominio de aire, lo que significa que en estas superficies el potencial vectorial magnético es cero. Para que esta condición sea aplicable, es necesario asegurarse de que el campo electromagnético disminuye hasta valores despreciables en el límite exterior. Para satisfacer esta condición, el **dominio del aire debe ser al menos 3 veces mayor** que la bobina que se encuentra en su interior.

::: danger IMPORTANTE

Si la malla tiene demasiados elementos, puede reducir el tamaño del dominio de aire a 2,5 veces el tamaño de la bobina, en lugar de tres, ¡pero no menos! El tamaño del dominio aire se define como la distancia desde el centro de la bobina hasta el límite exterior del aire (Z). El tamaño de la bobina se define con su diámetro exterior (d).

:::

<p align="center">

![Domain size definition](assets/air-domain-size/1.png)

</p>

El tamaño del dominio de aire se caracteriza con respecto al diámetro de la bobina - si es más de 3 veces el tamaño del diámetro de la bobina, el error relativo para la tensión, la bobina y la palanquilla es despreciable.

<p align="center">

![Domain size definition](assets/air-domain-size/2.png)

</p>
