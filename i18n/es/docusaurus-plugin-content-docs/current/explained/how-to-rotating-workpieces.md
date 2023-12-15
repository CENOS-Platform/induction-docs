---
id: rotating-workpieces
title: Calentamiento de grandes piezas giratorias
sidebar_label: Grandes piezas giratorias
sidebar_position: 2
---

<p align="center">

![Pipe preheat](assets/rotating-workpieces/animation.gif)

</p>

En CENOS no está limitado a utilizar un tipo de dominio para todo el objeto. Puede combinar múltiples tipos de dominios con **diferentes cálculos de física**.

Una aplicación muy útil es cuando al crear una **pieza de trabajo grande** sólo se puede simular la inducción EM cerca de la bobina, donde tiene lugar la mayor parte del calentamiento. Para el resto de la pieza, sólo se pueden realizar cálculos térmicos.

**Ejemplo** con el precalentamiento de un tubo grande para soldar:

En la práctica, la mayor parte del calentamiento por inducción se produce cerca de la bobina, el 80% restante del tubo sólo tiene procesos térmicos.
Podemos separar el tubo en dos dominios, y **no simular el electromagnetismo en el mayor**. Lo que permite que esto funcione es la condición ***límite de la interfaz térmica***.

El dominio de la pieza de trabajo (tubería) se divide en **dos partes**, sólo simulamos el electromagnetismo en una de ellas.

<p align="center">

![Setup](assets/rotating-workpieces/1.png)

</p>

<p align="center">

![Setup](assets/rotating-workpieces/2.png)

</p>

:::tip

Al hacer la operación de partición en Salome, el dominio de aire dividirá la pieza de trabajo en los sólidos separados. No es necesario crearlos manualmente.

:::

## Ventajas

La principal ventaja de este método es el número mucho menor de elementos de malla y, en consecuencia, de tiempo de cálculo. Con la configuración tradicional, el número de elementos habría sido alrededor de **700 000**, pero con el método simplificado fue de **450 000 elementos**.

## Condiciones de contorno

Estas son las condiciones de contorno para el ejemplo de simulación de la tubería:

<p align="center">

![Setup](assets/rotating-workpieces/3.png)

</p>