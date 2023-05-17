---
id: effective-mu
title: Cómo estimar la permeabilidad efectiva (μ)
sidebar_label: Estimación efectiva de μ
sidebar_position: 13
---

Las definiciones correctas de los materiales en CENOS son críticas para obtener buenos resultados. Una de estas definiciones es la curva B(H), necesaria para simular con precisión la respuesta de los materiales al campo electromagnético. Sin embargo, la **curva B(H) aumenta el tiempo de cálculo significativamente**, por lo que no es tan eficaz utilizarla durante las primeras iteraciones de diseño.

Por este motivo, es posible **sustituir la definición de B(H) por un valor de permeabilidad constante**, que proporciona los mismos resultados, pero en mucho **menos tiempo**.

En este artículo veremos **cómo estimar el valor correcto de permeabilidad** para utilizarlo en lugar de una curva B(H) completa.

## ¿Cómo encontrar el valor de μ efectiva?

La permeabilidad efectiva se puede estimar encontrando el campo eléctrico máximo en la pieza de trabajo. Esto se puede hacer dentro de la simulación que ya tiene, o usted puede hacer una versión simplificada de su sistema (a través de la simetría, por ejemplo) para hacer la estimación más rápida.

Hay dos enfoques para encontrar el valor máximo del campo eléctrico H - con y sin cálculo inicial B(H).

## μ efectiva a partir del cálculo de B(H)

Este enfoque requiere un cálculo de simulación inicial con la definición completa del material B(H). El cálculo de B(H) llevará **más tiempo**, pero al final la estimación de μ será **más precisa**.

### 1) Calcular el caso inicial con B(H)

Realice una simulación puramente electromagnética de su sistema, **sin análisis térmico** para reducir el tiempo de cálculo.

Asegúrese de que para este cálculo de prueba tiene activada la **curva B(H)** para el material de la pieza, los **ajustes de potencia son precisos** y el **cálculo del campo µ está marcado** en los resultados (para acceder a los ajustes de resultados, haga clic en el **icono de engranaje** bajo el bloque de *Resultados*).

<p align="center">

![Permeability](assets/effective-mu/1.png)

![Permeability](assets/effective-mu/9.png)

</p>

### 2) Calcular el valor máximo del campo magnético H

Calcular la intensidad del campo magnético a través de $H = \frac{B}{μ μ_0}$ donde

- $B$ - **Mayor** valor del campo magnético dentro del dominio de la pieza.

<p align="center">

![Permeability](assets/effective-mu/2.png)

</p>

- $μ$ - **Valor de permeabilidad más bajo** en la superficie de la pieza de trabajo a partir de los resultados.

<p align="center">

![Permeability](assets/effective-mu/3.png)

</p>

- $μ_0 = 12.57×10^{-7}$ [H/m]

Para este ejemplo:

$H = \frac{3.93}{8×12.57×10^{-7}} = 390811 A/m$

### 3) Graficar μ(H)

Ahora necesita hacer un gráfico de µ(H). Para ello, primero copie la definición de B(H) de las propiedades de material de CENOS y péguela en *MS Excel* (o en cualquier otro sitio).

**En el ejemplo se utiliza la curva B(H) de AISI 1045**.

<p align="center">

![Permeability](assets/effective-mu/4.png)

</p>

Convertir la curva B(H) a µ(H) mediante

$µ = \frac{B}{H μ_0}$

(tomar los valores necesarios del cálculo realizado anteriormente).

Para este ejemplo obtenemos tal gráfico *μ(H)*:

<p align="center">

![Permeability](assets/effective-mu/5.png)

</p>

Como se puede ver, se visualizan dos gráficos. El **superior** muestra cómo cambia la **permeabilidad a valores de campo H muy bajos**: aumenta y luego disminuye en una curva suave.

En el **gráfico inferior**, donde se visualiza **todo el rango H**, este cambio de permeabilidad inicial se muestra sólo como un pico, por lo que en el gráfico completo no podemos ver la curva con tanta claridad.

### 4) Leer la μ efectiva a partir del gráfico μ(H)

Una vez visualizado el gráfico μ(H), puede leer el valor μ efectivo correspondiente al valor H máximo.

<p align="center">

![Permeability](assets/effective-mu/7.png)

</p>

En este ejemplo, el valor estimado de permeabilidad efectiva es 6.

### 5) Probar la μ efectiva estimada

Una vez que haya estimado la µ efectiva, sustituya la curva B(H) por ella en la definición del material CENOS. Ejecute la simulación con el nuevo valor de µ (ajuste la potencia si es necesario).

**Si el resultado no coincide exactamente** con el que obtuvo con la curva B(H) completa, **aumente o disminuya el valor de µ** y calcule algunas iteraciones hasta alcanzar el mismo resultado que con la curva B(H).

Una vez que los resultados coincidan, habrá encontrado el valor µ efectivo, que puede utilizar en lugar de B(H).

## μ efectiva sin cálculo de B(H)

Este enfoque necesita un cálculo de simulación inicial con la permeabilidad del material de la pieza definida como 1. El cálculo inicial llevará **menos tiempo**, pero al final la estimación de μ sólo ayudará a **determinar el orden del valor de μ** (1, 10, 100, etc.).

### 1) Definir la pieza de trabajo μ como 1.

En CENOS desactive la definición B(H) para el material de su pieza de trabajo y sustitúyala por μ = 1. ¡Asegúrese de que los **ajustes de potencia son precisos**!

<p align="center">

![Permeability](assets/effective-mu/8.png)

</p>

### 2) Comprobar el valor del campo magnético B en la pieza

Ejecute una simulación puramente electromagnética (**sin análisis térmico**) y compruebe en los resultados el valor máximo del campo magnético B en la pieza.

### 3) Calcular el valor H del campo eléctrico máximo

Calcular el valor H máximo mediante

$H = \frac{B}{μ_0}$

### 4) Estimar el valor μ efectivo

Una vez calculado el valor máximo de H, siga los pasos 3. - 5. del planteamiento anterior para estimar el valor μ efectivo.


:::info Importante

Este método es **sólo una aproximación** con alto margen de error, que ayudará a determinar sólo el orden del valor μ (1, 10, 100, etc.). Si desea obtener una primera estimación más aproximada de la permeabilidad efectiva, deberá utilizar el método de la curva B(H).

:::