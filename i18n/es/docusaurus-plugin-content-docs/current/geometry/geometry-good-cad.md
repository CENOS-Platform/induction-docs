---
id: good-cad
title: Cómo crear un buen modelo CAD para simulación de Calentamiento por Inducción
sidebar_label: Cómo crear un buen modelo CAD
sidebar_position: 2
---

El modelo gométrico de la pieza de trabajo y del inductor desempeña un papel importante en la facilidad o dificultad de configuración y obtener resultados precisos de una simulación de calentamiento por inducción.

Hemos resumido los principales aspectos ue deben seguirse para conseguir un buen archivo CAD y **crear una geometría sencilla y sin problemas** para su simulación.

## Crear la geometría como un único sólido

En muchos softwares CAD es más fácil construir la geometría del inductor a partir de bloques, que luego se combinan para formar un inductor CAD completo. Al crear la geometría para la simulación, estos **bloques deben fusionarse para formar un único sólido** - hacer esto ayuda a eliminar caras innecesarias entre bloques y simplifica la configuración de las propiedades geométricas, pero también el proceso de mallado.

<p align="center">

![Single solid](assets/good-cad/1.png)

</p>

## Simplificar la geometría

La simulación por ordenador comienza con un modelo geométrico del problema de la vida real: es necesario representar con exactitud la geometría para calcular con precisión los aspectos físicos del modelo. Sin embargo, en la mayoría de los casos **puede prescindir de algunos de los detalles geométricos, que no tienen un impacto tan significativo en los resultados físicos**, para optimizar la simulación.

Las siguientes características pueden omitirse, ya que consumen una cantidad significativa de tiempo de cálculo y potencia informática sin contribuir de forma considerable a los resultados.

### Remover las terminales

Los terminales del inductor no son importantes para la simulación de calentamiento por inducción y deben retirarse.

<p align="center">

![Single solid](assets/good-cad/2.png)

</p>

### Borrar elementos innecesarios

Se pueden eliminar elementos del inductor como piezas de agarre o conexiones con elementos exteriores.

<p align="center">

![Single solid](assets/good-cad/3.png)

</p>

### Deshacerse de los pequeños detalles

Los pequeños detalles tienen un impacto insignificante en los resultados de la simulación, pero consumen mucho tiempo de cálculo, ya que deben resolverse a través de la malla, lo que aumenta significativamente el número de elementos de malla. **Deshágase de detalles como pequeñas curvaturas, orificios y huecos estrechos** tanto en la pieza de trabajo como en el inductor, etc.

<p align="center">

![Single solid](assets/good-cad/4.png)

</p>

:::info Importante

Si tiene un conducto de refrigeración atravesando su inductor, ¡no olvide **eliminar también las curvaturas dentro** de él!

:::

## Resolver partes geométricas conectadas de forma imprecisa

Durante la creación de la geometría, tenga cuidado con las conexiones entre las distintas partes del inductor: las conexiones incorrectas provocarán problemas de mallado y errores de cálculo.

### Superposición

<p align="center">

![Single solid](assets/good-cad/5.png)

</p>

### Huecos

<p align="center">

![Single solid](assets/good-cad/6.png)

</p>

## Asegúrese de que la geometría del inductor es continua

Si su inductor tiene un canal de refrigeración, asegúrese de que el **canal de refrigeración es continuo en toda la longitud del inductor**, de lo contrario causará problemas durante el mallado.

<p align="center">

![Single solid](assets/good-cad/7.png)

</p>

Si sigue estos consejos para conseguir un buen modelo CAD, tendrá una geometría **fácil de manipular y mallar**, y **rápida de calcular**.