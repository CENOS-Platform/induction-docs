---
id: steel-phases
title: Cómo definir el cálculo del cambio de fase en CENOS
sidebar_label: Cálculo de fase del acero
sidebar_position: 3
---

Para simular el endurecimiento del acero es importante conocer las fases del acero que se han producido tras el tratamiento térmico. 

La plataforma CENOS ofrece un modelo de **Cálculo de Fases** que permite calcular las fases del acero como austenita, bainita, perlita y martensita.

## ¿Cómo utilizar el cálculo de fases?

Cuando su geometría esté lista y la malla sea exportada a CENOS, puede definir los parámetros del material. En la ventana de personalización de materiales marque **Phase calculation**. Defina:

- $T_{Ac_{1}}$ (si es posible) - la temperatura a la que comienza el cambio de fase de la austenita.
- $T_{Ac_{3}}$ - la temperatura a la que la estructura es totalmente austenita.
- $T_{M_{s}}$ - temperatura de inicio de la formación de martensita.
- $t_s$ - dato de tiempo que representa el inicio del cambio de fase (normalmente cuando se ha producido el 1% de la transformación).
- $t_e$ - dato de tiempo que representa el final del cambio de fase (normalmente cuando se ha producido el 99% de la transformación).

:::info Información

Si no se conoce la temperatura $T_{Ac_{1}}$, utilizar la misma temperatura que $T_{Ac_{3}}$.

:::

<p align="center">

![Phase calculation variables](assets/steel-phases/phase-calculation-1.png)

</p>

## Un ejemplo de cómo obtener datos del diagrama TTT.

Para realizar el cálculo del cambio de fase, necesitará utilizar los datos del diagrama TTT (tiempo-temperatura-transformación), que tendrá un aspecto similar al que se muestra a continuación.

![An example of TTT diagram with different phases shown](assets/steel-phases/phase-calculation-ttt.png)

1. Dado que la bainita, la perlita y la ferrita se calculan como una sola fase, **las líneas que definen el inicio del cambio de fase deben conectarse**, ya que las líneas de inicio de la ferrita y la bainita se conectan mediante puntos verdes en este ejemplo. 
2. Del mismo modo, **las líneas que definen el final del cambio de fase deben conectarse**, ya que la línea final de perlita y la línea final de bainita se conectan mediante puntos rojos en este ejemplo.
3. Los datos de temperatura $t_s$ y $t_e$ necesitan ser definidos en el rango de temperatura de $T_{M_{s}}$ a $T_{Ac_{3}}$. Si la línea final en el diagrama TTT original no cruza la línea Ac3, como en el ejemplo dado, es necesario extrapolarla, de lo contrario, el cálculo no funcionará.

Un ejemplo de cómo tratar el diagrama TTT para obtener los datos de $t_s$ y $t_e$:

![Example of how to treat TTT diagram to get data for $t_s$ and $t_e$](assets/steel-phases/phase-calculation-ttt2.png)
