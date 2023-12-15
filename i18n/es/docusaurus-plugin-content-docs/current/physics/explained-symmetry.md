---
id: symmetry
title: Simetría en Condiciones de Frontera
sidebar_label: Simetría
sidebar_position: 8
---

Con CENOS es posible simular una parte simétrica de un objeto (mitad, cuarto, rebanada, etc.), lo que da resultados válidos que pueden reflejarse para representar toda la geometría, pero al mismo tiempo disminuye significativamente el tiempo de cálculo.

Para tener en cuenta la simetría del objeto y configurar correctamente la simulación, se utiliza simetría en condiciones de contorno (CC), mediante las cuales se define la posición de las líneas de campo magnético con respecto a los planos de simetría.

:::info Importante

Los planos de simetría se definen como paralelos o normales con respecto al campo magnético creado por el inductor - si el inductor se coloca de forma no convencional, las definiciones de estos planos pueden cambiar.

:::

**Las condiciones de simetría deben definirse para cada dominio** de la simulación, por ejemplo, no sólo para el corte de la pieza, sino también para los dominios del aire y del concentrador de flujo.

## Simetría de condiciones de borde

Cuando una corriente fluye a través de un alambre, crea un campo magnético a su alrededor, con el campo magnético moviéndose alrededor de la dirección del flujo de corriente.

En el calentamiento por inducción, cuando se utilizan inductores complejos y se coloca un objeto dentro de este campo magnético, algunas **caras del objeto son paralelas a las líneas de campo magnético, mientras que otras son normales a ellas**.

<p align="center">

![Flux parallel](assets/symmetry/6.png)

</p>

Conociendo la posición de las líneas de campo magnético, podemos comprender su posición con respecto a diferentes superficies o límites de nuestra geometría.

Basándonos en este hecho, se introducen dos condiciones de contorno de simetría - *Flujo Paralelo* y *Flujo Normal*.

### Flujo paralelo

Las condiciones de borde de flujo paralelo define que las **líneas de campo magnético son paralelas a la superficie**, lo que significa que estas líneas no cruzan el plano.

En este ejemplo un inductor recto está generando un campo magnético, cuyas líneas se sitúan paralelas a un plano y van por el lado de éste.

<p align="center">

![Flux parallel](assets/symmetry/1.png)

</p>

### Flujo normal

Las condiciones de contorno de flujo normal define que las **líneas de campo magnético son normales a la superficie**, lo que significa que pasan directamente por el plano.

En este ejemplo, un inductor recto está generando un campo magnético cuyas líneas se sitúan normales a un plano y lo atraviesan directamente.

<p align="center">

![Flux parallel](assets/symmetry/2.png)

</p>

## Uso de simetría en BC

La simetría en BC se utiliza para simular sólo una pequeña parte de la geometría completa, disminuyendo significativamente el tiempo de cálculo y produciendo los mismos resultados precisos que los casos de geometría completa.

En los siguientes ejemplos **demostraremos las definiciones de los límites exteriores para diferentes casos de simetría**.

:::info Importante

La única diferencia en la configuración física para los casos de simetría son las condiciones de contorno adicionales en los planos de simetría - ¡el resto permanece igual!

:::

### Mitad

La mayoría de los sistemas de calentamiento por inducción son en cierto grado simétricos y **pueden cortarse por la mitad conservando la precisión de los resultados**.

En este ejemplo veremos una simple bobina de devanado múltiple y un sistema de palanquilla cilíndrica. Para el sistema completo en los límites exteriores definimos ***Corriente (Amplitud)*** y ***Tierra*** en los terminales, y las caras exteriores al aire con ***Infinito***.

:::info Importante

Observa como la misma condición de contorno (*Flujo paralelo*) es coloreada de forma diferente en superficies de dominios diferentes - **¡necesita definir la simetría de las condiciones de borde separadamente para cada dominio**!

:::

<p align="center">

![Flux parallel](assets/symmetry/7.png)

</p>

Si cortamos la geometría por la mitad, necesitamos condiciones de contorno adicionales para definir el corte de simetría. Necesitamos definir los nuevos planos de simetría para el aire y la pieza con ***Flujo paralelo***, y para cada mitad del bobinado necesitamos crear nuevos terminales, en los que definiremos ***Corriente (Amplitud)*** y ***Tierra***.

La condición de contorno de la simetría para este caso es ***Flujo paralelo***, porque las partes del inductor que entran en el plano crean un campo magnético paralelo a estos planos.

<p align="center">

![Flux parallel](assets/symmetry/8.png)

</p>

### Cuarto

Puedes utilizar la simetría de tu geometría aún más y simular no la mitad, sino un **cuarto** de tu sistema.

Utilizaremos la misma geometría que en el ejemplo de media simetría, pero esta vez sólo simularemos una cuarta parte.

Las condiciones de contorno utilizadas son exactamente las mismas que para media simetría - definir los planos de simetría para el aire y la pieza de trabajo con ***Flujo paralelo***, y para cada cuarto del bobinado necesitamos crear nuevos terminales, en los que definiremos ***Corriente (Amplitud)*** y ***Tierra***.

La condición de contorno de simetría en ambos planos de simetría es ***Flujo paralelo***, porque los cuartos del inductor que entran en el plano crean un campo magnético paralelo a ambos planos de simetría.

<p align="center">

![Flux parallel](assets/symmetry/10.png)

</p>

### Porción

Para geometrías con cierto nivel de simetría axial puede simular sólo un **corte**.  

En el ejemplo de abajo se ha cortado media rebanada del diente del engranaje, y las condiciones de simetría deben utilizarse no sólo para la simetría paralela, sino también para la normal (observe que la **rebanada es sólo una parte de la altura total del sistema**).

<p align="center">

![Flux parallel](assets/symmetry/3.png)

</p>

Las CC de simetría paralela son exactamente las mismas que en los ejemplos anteriores - definir los planos de simetría para el aire y la pieza con ***Flux paralelo***, y para la rebanada del inductor crear terminales, en los que hay que definir ***Corriente (Amplitud)*** y ***Tierra***.

También necesitamos definir la simetría normal (parte de la altura completa del sistema), por lo que para las caras superior e inferior del inductor, el aire y la pieza de trabajo se define ***Flujo normal***.

:::info Importante

Si el inductor es cortado y sólo se simula una parte de la altura completa, el valor de la corriente debe disminuirse respectivamente, por ejemplo, si sólo se simula la mitad de la altura completa del conductor, la corriente debe disminuirse a la mitad.

:::

<p align="center">

![Flux parallel](assets/symmetry/4.png)

</p>


## Limitaciones

El uso de la simetría para la optimización de casos es muy útil, pero hay algunas cosas a tener en cuenta cuando se crean simulaciones con simetría.

### Devanados separados

Para simulaciones con geometrías completas tiene un volumen inductor, para el que define dos terminales. Si corta este inductor por la mitad o en partes más pequeñas para utilizar la simetría, recuerde que necesita **definir cada volumen inductor (bobinados) por separado** y **crear dos terminales y establecer la corriente en cada uno de ellos**.

<p align="center">

![Flux parallel](assets/symmetry/9.png)

</p>

::: info Importante

Para la entrada de control de voltaje, si tiene el valor de voltaje aplicado completo (digamos 1000v) y has cortado el inductor en 5x bucles, entonces el voltaje en cada uno de estos bucles será el voltaje completo / número de bucles

exmple= 1000 / 5 = 200 volts.

También hay que aplicar el ángulo de corte a esta ecuación.

Por ejemplo, tenemos una rebanada de 180 grados, rebanada de 180 grados significa que tenemos que dividir esta tensión por bucle por 2.
Es decir, 200 / 2 = 100 voltios como entrada para cada bucle.
En física, introduzca también el ángulo "Slice" de 180 grados, esto asegurará principalmente que la potencia calculada sea la esperada.

:::

### Rotación

Si quiere simular **rotación usando Movimiento Complejo**, las *Condiciones Límite de Simetría* **no se pueden aplicar** y tendrá que calcular un caso con geometría completa.

:::note Nota 

*para capacitación revise nuestro seminario web*:
https://www.youtube.com/watch?v=YKKJyNz-OPg

:::