---
id: geometry-simplification
title: Simplificación de geometrías
sidebar_label: Simplificación del sistema
sidebar_position: 3
---

Casi todas las geometrías son simétricas en algún nivel, lo que nos permite simplificarlas y **disminuir enormemente el tiempo de cálculo**.

También se puede simular sólo una parte de la geometría con [**condiciones de contorno de simetría**](/physics/symmetry), y seguirá produciendo resultados adecuados para toda la geometría.

## Ekiminar geometría repetida

Si su geometría consta de más de un sistema pieza-conductor idéntico, seleccione uno para simular y elimine los demás.

<p align="center">

![Reduce system count](assets/geometry-simplification/1.png)

</p>

## Simular sólo la mitad

Si tiene una geometría de simetría lineal, simule sólo la mitad y refleje los resultados para representar la geometría completa.

<p align="center">

![Reduce system count](assets/geometry-simplification/2.png)

</p>

## Recortar sector

Si dispone de una geometría con simetría axial, recorte y simule un sector repetitivo de la misma, por ejemplo, un diente de un engranaje completo, y a continuación gire los resultados para representar la geometría completa.

<p align="center">

![Reduce system count](assets/geometry-simplification/3.png)

</p>

## 3D a 2D

Para la geometría de revolución no es necesaria la simulación 3D, simule sólo un corte plano de la geometría completa y revolucione los resultados para representar toda la geometría.

<p align="center">

![Reduce system count](assets/geometry-simplification/4.png)

</p>
