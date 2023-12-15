---
id: motion
title: Cómo definir el movimiento en CENOS
sidebar_label: Movimiento
sidebar_position: 12
---

El movimiento es una parte importante para muchos sistemas de calentamiento por inducción, ya que el movimiento de traslación o rotación ayuda a calentar/endurecer la pieza específica de manera uniforme y eficiente. Para **simular con precisión** este tipo de procesos, es necesario **tener en cuenta los respectivos tipos y velocidades de movimiento** presentes en el sistema.

En este artículo vamos a echar un vistazo a **cómo puede definirse el movimiento en CENOS**, cuáles son los **requisitos para el movimiento** y qué limitaciones existen actualmente con dicha configuración.

## Movimiento en CENOS

CENOS admite movimiento traslacional (*escaneo*) y rotacional (*disparo único*). Para definir el movimiento en su simulación, vaya a la pestaña **MOTION** en la sección FÍSICA y haga clic en **CREAR NUEVO MOVIMIENTO**.

<p align="center">

![Motion](assets/motion/1.png)

</p>

Seleccione el **tipo de movimiento**, **qué parte** desea mover, en **qué dirección** y con **qué velocidad**, ¡y CENOS hará el resto!

<p align="center">

![Motion](assets/motion/2.png)

</p>

## Tipos de movimiento

Cuando defina *movimiento*, notará que hay 2 opciones para elegir - **Movimiento simple** y **Movimiento complejo**.

<p align="center">

![Motion](assets/motion/3.png)

</p>

### Movimiento simple

Esta opción le permite simular el movimiento para piezas **axialmente simétricas** o **continuas**.

<p align="center">

![Motion](assets/motion/4.png)

</p>

Algunos ejemplos serían:

<p align="center">

![Motion](assets/motion/sm.gif)

</p>

Como puede ver, el *movimiento simple* puede **aplicarse a sistemas en los que puede suponerse que la geometría no se mueve**. Esto puede ser muy útil para la rotación de piezas completamente simétricas o el modelado de la alimentación continua de material a través del sistema.

:::note Nota

Utilice *movimiento simple* si es posible, ya que calcula **mucho más rápido** que el **movimiento complejo**.

:::

### Movimiento complejo

Si el *movimiento simple* no es aplicable a su caso, debe utilizar *movimiento complejo*.

<p align="center">

![Motion](assets/motion/5.png)

</p>

Para piezas con ranuras, dientes, agujeros, huecos y otros tipos de detalles asimétricos, es necesario simular un movimiento real. El *movimiento complejo* le permite mover las piezas correspondientes en su sistema.

<p align="center">

![Motion](assets/motion/cm.gif)

</p>

:::note Nota

¡Asegúrese de que el **paso de tiempo de cálculo es lo suficientemente pequeño como para capturar la rotación suavemente**! ¡No más de 30 grados de giro en un paso de tiempo!

:::

## Limitaciones

Aunque la definición de *movimiento* es fácil de usar, hay **algunas cosas que hay que tener en cuenta al definir el movimiento** en CENOS.

### Eje de rotación

¡La rotación actualmente está limitada sólo alrededor del eje Z, así que asegúrese de que su sistema de rotación está **posicionado alrededor del eje Z**!

<p align="center">

![Motion](assets/motion/7.png)

</p>
