---
id: time-step
title: Paso de tiempo
sidebar_label: Paso de tiempo
sidebar_position: 10
---

Hay muchos parámetros físicos diferentes que, si se definen incorrectamente, pueden afectar a la precisión de los resultados. Uno de estos parámetros con un gran impacto en los resultados es el **paso de tiempo**. En este artículo aprenderemos qué es un paso de tiempo de cálculo, cómo puede afectar a los resultados y cómo definirlo.

## ¿Qué es un paso de tiempo?

En pocas palabras, el paso de tiempo de cálculo es un **periodo de tiempo tras el cual se realiza el cálculo electromagnético y térmico de la simulación**. Por eso es muy importante definir correctamente el tamaño del paso de tiempo, para que los resultados calculados sean continuos y sin saltos o aumentos no físicos de la temperatura y otros parámetros.

### ¿Cómo definir el paso de tiempo?

El paso de tiempo se define en los ajustes físicos bajo el CONTROL DE SIMULACIÓN.

<p align="center">

![graph](assets/time-step/1.png)

</p>

Hay dos formas de definir el paso de tiempo. Es posible definir un **paso de tiempo de cálculo constante** o utilizar el **paso de tiempo adaptativo** marcando la casilla *Use adaptive time step*.

Si utiliza **paso de tiempo constante**, entonces el **tamaño del paso de tiempo no cambiará** a lo largo de todo el tiempo de cálculo.

Si se utiliza el **paso de tiempo adaptativo**, su **tamaño cambiará automáticamente** en función de la velocidad a la que cambien los parámetros, como la temperatura.

Para saber qué definición de paso temporal elegir, hay que evaluar los resultados esperados y elegir la que proporcione la mayor precisión.

## Calentamiento estático

En el caso de una **simulación estática**, es decir, sin movimiento, el **aumento de temperatura en la pieza suele ser muy rápido al principio** del calentamiento. Por ello, debemos elegir un tamaño de paso de tiempo apropiado para resolver este calentamiento tan rápido.

A continuación se muestran los gráficos de temperatura en un punto de la superficie de la pieza de trabajo de la misma simulación. Se calculó con *paso de tiempo adaptativo* y *dos pasos de tiempo constantes diferentes* (0,1s y 1s).

<p align="center">

![graph](assets/time-step/Max_temp.png)

</p>

Como se puede ver, la temperatura aumenta rápidamente al principio. **Con un paso de tiempo más grande**, si la velocidad de calentamiento se proyecta al siguiente paso de tiempo, puede ser **irrealmente alta (1200 degC)**.

:::info Importante

La temperatura final es aproximadamente similar con un paso de tiempo más fino y más pequeño. Sin embargo, estos saltos creados por el paso de tiempo más grande pueden afectar al cálculo del perfil endurecido.

:::

Como se puede ver, incluso con el paso de tiempo de 0,1 s, sigue habiendo un pequeño salto en la temperatura durante el primer paso de tiempo. El **paso de tiempo adaptativo resuelve mucho mejor la parte inicial**, y aumenta el tamaño del paso de tiempo más adelante. Con adaptativo había *38* pasos de tiempo, frente a *50* con el paso de tiempo de 0,1s, lo que significa que **con el tamaño de paso adaptativo el tiempo de cálculo para este caso también era menor**.

### Valores de la tabla

Si quiere resolver mejor el calentamiento inicial, pero no quiere usar el paso de tiempo *Adaptativo* (para mantener el control sobre cuántos pasos de tiempo se calcularán), puede **definir el tamaño del paso de tiempo en una tabla** y hacer el tamaño del paso más pequeño en el inicio del calentamiento, y luego aumentarlo para ahorrar tiempo de cálculo.

<p align="center">

![Time step table](assets/time-step/2.png)

</p>

## Escaneado

Si su **sistema no es estático**, por ejemplo, existe un movimiento de traslación, el paso de tiempo puede afectar aún más a los resultados.

En una simulación de escaneo, el tamaño del paso de tiempo afecta directamente al movimiento del inductor. Si el paso de tiempo es demasiado grande, el inductor "saltará" de una posición a otra (como se ve en el GIF de abajo), haciendo que el **patrón térmico sea inconsistente y poco físico**.


![GIF](assets/time-step/comb123.gif)


Por esta razón, el **paso de tiempo debe elegirse de modo que se cree un movimiento suave** (*1 s en el ejemplo*), y **que no se creen saltos bruscos** en la posición del mismo (*15 s en el ejemplo*).

Para inductores simples, de perfil circular y un solo devanado, el **tamaño del paso de tiempo necesario puede determinarse** considerando la distancia desde la superficie de la pieza al inductor (**d**), así como la distancia que recorre el inductor en un paso de tiempo (**Δl**).

<p align="center">

![dimensions](assets/time-step/Scanning_dimensions.png)

</p>

Si la relación entre estos dos valores (**d** y **Δl**) es igual o inferior a 1, el tamaño del paso de tiempo será suficiente para una resolución precisa del resultado. A continuación puede encontrar una tabla con diferentes **d**, tamaño de paso de tiempo (**Δt**), **Δl** y su correspondiente proporción.

<p align="center">

![table](assets/time-step/table.png)

</p>
