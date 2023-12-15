---
id: field-expressions
title: Expresiones de campo
sidebar_label: Expresiones de campo
sidebar_position: 2
---

A veces las definiciones físicas de la simulación son demasiado complejas para definirlas con un valor constante o una tabla. Para **definir cosas como la anisotropía del material o el campo no uniforme, se dispone de expresiones de campo** en CENOS.

Las aplicaciones de las expresiones de campo sólo están limitadas por la imaginación del usuario, pero sigue siendo necesaria una pauta sencilla del usuario. En este artículo veremos **cómo podemos definir expresiones** y repasaremos algunas de las **aplicaciones más utilizadas para las expresiones**.

## Cómo utilizar expresiones

Puede utilizar las expresiones de dos maneras diferentes:

+ **Directamente** - introduzca la expresión directamente en el campo.

+ **Indirectamente** - introduzca la expresión como *Script del solucionador* y utilícela indirectamente.

### Definición directa

**Seleccione el campo** del valor físico que desea definir con una expresión. A continuación, en la parte derecha del campo **cambie el tipo de entrada** de *Constant* a *Expression*, e **introduza su expresión**.

<p align="center">

![Direct definition](assets/field-expressions/1.png)

</p>

### Definición indirecta

Puede **introducir la expresión o el valor como parámetro** en *Solver script* en *configuración avanzada de cálculo* y luego utilizar este parámetro como entrada de expresión en el campo que desee.

<p align="center">

![Direct definition](assets/field-expressions/2.png)

</p>

<p align="center">

![Direct definition](assets/field-expressions/3.png)

</p>

<p align="center">

![Direct definition](assets/field-expressions/4.png)

</p>

## Aplicaciones de las expresiones

Existen numerosas aplicaciones sobre el uso de expresiones. Aquí esbozaremos los ejemplos de expresiones más utilizados y le proporcionaremos un **ejemplo de expresiones** que podrá **copiar en su simulación y modificar a su gusto**.

### Anisotropía

Muchos materiales como el *Fluxtrol* tienen propiedades térmicas y magnéticas anisótropas, lo que significa que **las propiedades del material dependen de la dirección**.

:::note Ecuación

Tensor[**X**, 0, 0, 0, **Y**, 0, 0, 0, **Z**]

:::

donde X, Y y Z son los parámetros en las respectivas direcciones.
Esto se puede aplicar a cualquier parámetro tales como $σ, μ$ o $λ$.

Aquí hay un ejemplo de **anisotropía de conductividad térmica** para una pieza termoplástica de fibra de carbono, con una conductividad térmica más baja en la dirección **Z**. En este caso, elegimos ***Expression*** como tipo de parámetro y usamos:

<p align="center">

![Anisotropy](assets/field-expressions/Untitled.png)

</p>

<p align="center">

![Anisotropy](assets/field-expressions/7.png)

</p>

#### Rotar anisotropía
Si **el eje del tensor de anisotropía no se alínea con XYZ**, es posible rotar el tensor.

:::note Ecuación
Rotar [Tensor[X, 0, 0, 0, Y, 0, 0, 0, Z], **Rx, Ry, Rz**]
:::

donde, Rx, Ry, Rz son la rotación alrededor de ese eje en radianes.

**Ejemplo de cómo rotar un tensor**:

:::note Ecuación

Rotar [Tensor[2.50, 0, 0, 0, 2.50, 0, 0, 0, 0.32], 0, 0, **3.14/4**]

:::

En este ejemplo, la conductividad térmica sería máxima a lo largo de la línea girada 45 grados (**pi/4 radianes**) alrededor del **eje Z**.

### Parámetro de corriente global

En el caso de *corte 3D de bobinado múltiple* tendrás múltiples dominios de bobinado que tienen las mismas definiciones físicas, pero que no pueden agruparse debido a los diferentes nombres de las condiciones de frontera.

Si quiere cambiar la corriente para tal simulación, necesita *cambiar separadamente la corriente en cada devanado*.

Para simplificar esto, la corriente puede ser definida en *Solver script* como un parámetro, que puede ser introducido en la definición de corriente de cada devanado. De esta forma podrá **cambiar la corriente en todos los devanados simultáneamente** desde *Solver script*.

Introduzca una expresión como *I_0 = 5000;* en *Solver script*, y en la expresión de la corriente del devanado introduzca *I_0*. Cuando cambie el valor de *I_0*, los valores de corriente cambiarán también.

<p align="center">

![Anisotropy](assets/field-expressions/5.png)

</p>

### Enfriamiento por pulverización en movimiento

En la mayoría de las aplicaciones de escaneado de calentamiento por inducción, un anillo de enfriamiento o refrigeración sigue directamente al inductor, pulverizando líquido refrigerante sobre la pieza y enfriándola justo después del calentamiento. 

Con expresiones de campo se puede definir una zona de enfriamiento móvil para **simular un anillo de pulverización que se mueve junto con el inductor**. Esto se hace utilizando una expresión para el parámetro de convección ***h*** en el dominio de la pieza de trabajo.

:::note Ecuación

>**eje**[] < **y0** + **velocidad** * $Tiempo ? **enfriamiento_detrás** : **enfriamento_delante**

:::

Donde:

+ *eje* - eje del movimiento;
+ *y0* - posición inicial de la ducha de pulverización al principio del movimiento [m];
+ *velocidad* - velocidad de barrido [m/s];
+ *enfriamiento_detrás* - coeficiente de transferencia de calor (h) detrás de la posición del inductor;
+ *enfriamento_delante* - coeficiente de transferencia de calor (h) delante del inductor.

Con esta expresión se **define una línea que es paralela al eje de movimiento y divide la frontera en la que se ha fijado en dos partes cada una con diferente coeficiente de transferencia de calor**. Cuando cambie el tiempo, esta línea cambiará también su posición, simulando de esta forma la ducha de pulverización en movimiento.

:::caution Advertencia

Los valores iniciales de posición y velocidad deben escribirse en *m* y *m/s*, independientemente de la unidad establecida en la geometría.

:::

En la siguiente ilustración se puede ver un simple modelo con la expresión de convección establecida en su superficie. Al principio del cálculo (t = 0s) la línea divisoria está situada en el eje X (porque y0 = 0), por lo que por debajo de ella h = 5000, pero por encima de ella h = 10. Después de dos segundos la línea se ha movido 0.02m en dirección Y, y ahora la división de la superficie de la pieza ha cambiado y la mayor parte de la superficie de la pieza tiene h = 5000. Si se imagina que delante de esta línea se mueve un inductor, entonces de esta manera se simula el enfriamiento por pulverización.

<p align="center">

![Anisotropy](assets/field-expressions/11.png)

</p>

:::info Información

El enfriamiento por pulverización en movimiento no está conectada al movimiento del inductor: se define por separado y se ajusta para que siga al inductor.

:::

Simplemente hay que elegir el valor de *y0* de forma que siga al inductor. Por ejemplo, si el inductor se mueve a lo largo del eje Y y su posición inicial es *Y=20mm*, entonces para la definición de la ducha pulverizadora elegiría *y0=0.01m* (dependiendo del diámetro del inductor).

**Ejemplo:**

<p align="center">

![Anisotropy](assets/field-expressions/9.png)

</p>

:::note Ecuación

> **Y**[] < **-0.01** + **0.01** * $Time ? **5000** : **10**

:::

Donde:

+ *Y* - eje del movimiento;
+ *-0.01 m* - posición inicial de la ducha de pulverización al principio del movimiento;
+ *0.01 m/s* - velocidad de barrido;
+ *5000* - coeficiente de transferencia de calor (h) detrás de la posición del inductor;
+ *10* - coeficiente de transferencia de calor (h) delante del inductor.

**En este ejemplo el inductor se mueve a lo largo del eje Y**. La expresión pone h = 5000, si la coordenada Y es menor que *y0*, de lo contrario pone h = 10. Observa cómo *y0* y *velocidad* se ajustan a los valores que se toman de las *variables de geometría dinámica* - la velocidad sigue siendo la misma (para el movimiento del inductor se usaron *mm/s*), pero el valor de *y0* es 10 mm menor que la posición inicial del inductor para simular que la ducha está detrás del inductor.

<p align="center">

![Anisotropy](assets/field-expressions/6.png)

</p>

En seguida se muestra una comparación entre diferentes definiciones de *Convección* para la misma simulación. A la izquierda están los resultados con la constante *h = 10* (observe el **sobrecalentamiento excesivo** en la superficie), y a la derecha está la definición de pulverización en movimiento usando la expresión.


:::important Definiciones de los gifs a continuación

Izquierda: *h = 10*

Derecha: *Y[] < -0.01 + 0.01$Time ? 5000 : 10*

:::

<p align="center">

![Moving spray](assets/field-expressions/combined.gif)

</p>

### Temperatura inicial no uniforme

Para algunas simulaciones se requiere **una distribución de calor inicial no uniforme**. Se puede definir dicha distribución mediante expresiones, definiendo la temperatura inicial como dependiente de la coordenada.

:::note Ecuación

>**eje**[] < **coordenada_referencia** ? **T1** : **T2**

:::

Donde
+ *eje* - eje de la distribución no uniforme.
+ *coordenada_referencia* - coordenada de referencia, coordenada en la que cambia la temperatura.
+ *T1* - temperatura si la coordenada es menor que *coordenada_referencia*.
+ *T2* - temperatura si la coordenada es mayor que *coordenada_referencia*.

Que pone *T = T1* si *coordenada* es menor que *coordenada_referencia*, en caso contrario pone *T = T2*.

Para definir la temperatura inicial no uniforme mediante una expresión, introdúzcala en el campo *Condiciones iniciales* bajo el dominio de la pieza de trabajo.

<p align="center">

![Anisotropy](assets/field-expressions/9.png)

</p>

**Ejemplo de temperatura inicial no uniforme**:

:::note Ecuación

**Y**[] < **0** ? **100** : **200**

:::

En este ejemplo, la distribución de la temperatura se produce a lo largo del eje **Y**. La expresión utiliza una temperatura de 100 °C en la pieza por debajo de la coordenada Y = 0. Por encima, utiliza una temperatura de 200 °C.

<p align="center">

![Anisotropy](assets/field-expressions/10.png)

</p>

## Limitaciones

Las expresiones de campo son muy útiles para la configuración avanzada de simulaciones, pero hay que recordar algunas cosas para configurarlas correctamente.

### Unidades

Los valores que introduzca en la expresión, como la posición inicial o la velocidad, **deben introducirse en metros**, porque es la única unidad que soportan las expresiones en este momento - si introduce valores en otras unidades, la expresión seguirá funcionando, pero el valor estará en metros, por lo que los resultados serán incorrectos.

### Letras mayúsculas

Las letras de las expresiones de campo distinguen entre mayúsculas y minúsculas. Para una definición correcta **en las expresiones eje, y otras letras, deben introducirse en mayúsculas**, de lo contrario la expresión producirá un error.

Correcto:

> **Y**[] < -0.01 + 0.01 * $Time ? 5000 : 10

Incorrecto:

> **y**[] < -0.01 + 0.01 * $Time ? 5000 : 10