---
id: boundary-conditions
title: Condiciones de contorno
sidebar_label: Condiciones de contorno
sidebar_position: 5
---

Las condiciones de contorno (CC) son definiciones físicas en las superficies de contorno del dominio para las condiciones térmicas y de electromagnetismo. Aquí se enumeran **todas las condiciones límite utilizadas en CENOS**, así como el **uso más común para cada CC**.

## Condiciones de contorno térmicas

Las CC térmicas son condiciones de contorno a través de las cuales se define el intercambio de calor entre dominios.

### Temperatura fija

La condición de contorno *temperatura fija* define una temperatura fija en la superficie límite.

<p align="center">

![Fixed temperature](assets/boundary-conditions/fixed-temperature.png)

</p>

:::note Uso

Cuando *Motion* se usa en palanquilla infinita, la superficie a través de la cual la palanquilla ingresa al dominio computacional se puede definir con *Temperatura fija*.

:::

### Flujo térmico

La condición límite de *flujo térmico* define una densidad de flujo térmico constante en la superficie de contorno.

<p align="center">

![Heat flux](assets/boundary-conditions/heat-flux.png)

</p>

:::note Uso

Puede utilizarse si se conoce el flujo de calor que atraviesa un área específica

:::

### Transferencia de calor

La condición de contorno de *transferencia de calor* define un flujo de calor constante (en watts) en la superficie límite.

<p align="center">

![Heat flow](assets/boundary-conditions/heat-flow.png)

</p>

:::note Uso

Puede utilizarse si se conoce la transferencia de calor que atraviesa una zona específica

:::

### Convección

La condición de contorno de *convección* define el flujo térmico como dependiente de la temperatura ambiente y el coeficiente de transferencia de calor. *Convección* se define como:

$$
q=h(T-T_{amb})
$$

<p align="center">

![Convection](assets/boundary-conditions/convection.png)

</p>

:::note Uso

*Convección* se utiliza en la interfaz pieza de trabajo-aire para definir el intercambio de calor cuando la temperatura es baja. Normalmente se utiliza junto con *Radiación*.
:::

Para **aprender más** sobre la definición de *Convección*, [**haga clic aquí**](/physics/thermal-losses#convection).

### Radiación

La condición de contorno *radiación* define la radiación térmica hasta el infinito en la superficie límite, donde el flujo de calor se define como:

$$
q=\sigma_{SB}\epsilon(T^4-T_{amb}^4)
$$

<p align="center">

![Radiation](assets/boundary-conditions/radiation.png)

</p>

:::note Uso

La *radiación* se utiliza en la interfaz pieza de trabajo-aire para definir el intercambio de calor cuando la temperatura es alta. Normalmente se utiliza junto con *Convección*.

:::

Para **aprender más** sobre la definición de *radiación*, [**haga clic aquí**](/physics/thermal-losses#radiation).

### Combinadas

La condición de contorno *combinada* le permite combinar múltiples CC como *convección*, *radiación*, *flujo de calor* y *transferencia de calor* en una única superficie de dominio.

<p align="center">

![Combined](assets/boundary-conditions/combined.png)

</p>

:::note Uso

La CC *combinada* se utiliza en la interfaz pieza de trabajo-aire para definir tanto *convección* como *radiación* para una definición completa de la transferencia de calor en un amplio rango de temperaturas.

:::

### Adiabática

La condición de contorno *adiabática* define un flujo de calor 0 en la superficie.

<p align="center">

![Adiabatic](assets/boundary-conditions/adiabatic.png)

</p>

:::note Uso

La CC *adiabática* se utiliza en superficies de simetría para dominios con análisis térmico.

:::

### Interfaz

La condición de contorno *interfaz* define la superficie de contorno como la superficie interna entre dos dominios.

<p align="center">

![Interface](assets/boundary-conditions/interface.png)

</p>

:::note Uso

Se utiliza para definir la interfaz entre dos dominios que tienen ambos definición de análisis térmico.

:::

### Resistencia térmica de contacto

La condición de contorno *resistencia de contacto térmico* define la resistencia térmica entre dos dominios.

<p align="center">

![TCR](assets/boundary-conditions/tcr.png)

</p>

:::note Uso

Se utiliza para definir la interfaz entre dos dominios que tienen ambos definición de análisis térmico.

:::

## Electromagnetismo

Las CC electromagnéticas son condiciones de contorno a través de las cuales se define el flujo magnético.

### Infinito

La condición límite *infinito* define un potencial vectorial cero en la superficie de contorno.

<p align="center">

![Infinity](assets/boundary-conditions/infinity.png)

</p>

:::note Uso

La CC *infinito* se utiliza para definir la superficie exterior de la caja de aire.

:::

### Flujo paralelo

La condición límite *flujo paralelo* define las líneas de campo magnético como paralelas a la superficie límite.

<p align="center">

![Flux parallel](assets/boundary-conditions/flux-parallel.png)

</p>

:::note Uso

El *flujo paralelo* se utiliza para definir condiciones de contorno de simetría en los lados de los cortes y sectores.

:::

Para **aprender más** sobre la definición de *flujo paralelo*, [**haga clic aquí**](/physics/symmetry#flux-parallel).

### Flujo normal

La condición de contorno *flujo normal* define las líneas de campo magnético como normales a la superficie de contorno.

<p align="center">

![Flux normal](assets/boundary-conditions/flux-normal.png)

</p>

:::note Uso

El *flujo normal* se utiliza para definir las condiciones de contorno de simetría en la parte superior e inferior de los cortes y sectores.

:::

Para **aprender más** sobre la definición de *flujo normal*, [**haga clic aquí**](/physics/symmetry#flux-normal).

### Interfaz

La condición de contorno *interfaz* define la superficie de contorno como la superficie interna entre dos dominios.

<p align="center">

![Interface](assets/boundary-conditions/interface.png)

</p>

:::note Uso

Se utiliza para definir la interfaz entre dos dominios de los que sólo uno tiene definición de análisis térmico.

:::

### Impedancia superficial

Sólo se puede acceder a la condición de contorno *impedancia superficial* a través del dominio *impedancia superficiale*. Define la superficie límite como una capa infinitamente fina para la resolución de capa de piel de frecuencia VH.

<p align="center">

![Surface Impedance](assets/boundary-conditions/surface-impedance.png)

</p>

:::note Uso

*Impedancia superficial** se utiliza para reemplazar la resolución manual de la capa de piel a través de la malla en la configuración de frecuencias muy altas.

:::

### Eje de simetría

*Eje de simetría* es una condición de contorno específica 2D-axial-simétrica que define un potencial vectorial 0 en el eje de simetría.

<p align="center">

![Symmetry axis](assets/boundary-conditions/symmetry-axis.png)

</p>

:::note Uso

*Eje de simetría* se utiliza en todos los casos 2D axial-simétricos para definir el eje de rotación.

:::

## Fuente de corriente

Las CC de corriente son accesibles solo bajo el dominio *fuente de corriente* y a través de las cuales se define la corriente o voltaje que fluye a través del conductor.

### Voltaje

La condición límite *voltaje* define la tensión en la superficie límite.

<p align="center">

![Voltage](assets/boundary-conditions/voltage.png)

</p>

:::note Uso

*Voltaje* se utiliza para definir el voltaje en uno de los terminales del inductor. Para el otro terminal utilice *tierra*.

:::

### Corriente

La condición límite *corriente* define un suministro de corriente positiva a la superficie de contorno y el valor de la corriente.

<p align="center">

![Current](assets/boundary-conditions/current.png)

</p>

:::note Uso

*Corriente* se utiliza para definir la corriente en uno de los terminales del inductor. Para el otro terminal utilice *tierra*.

:::

### Tierra

La condición límite *tierra* define un suministro de corriente negativo a la superficie límite.

<p align="center">

![Ground](assets/boundary-conditions/ground.png)

</p>

:::note Uso

*Tierra* se utiliza para definir uno de los terminales del inductor. Para el otro terminal utilice *Voltaje* o *Corriente*.

:::
