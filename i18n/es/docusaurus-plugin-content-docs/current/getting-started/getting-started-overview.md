---
id: overview
title: Introducción - Visión general de CENOS
sidebar_label: Visión general de CENOS
sidebar_position: 1
slug: /
---

*CENOS Platform* es un software de simulación para el calentamiento por inducción. Ayuda a los ingenieros a **ahorrar una cantidad significativa de dinero y tiempo** en la creación de prototipos de bobinas de inducción sustituyendo las pruebas físicas con simulaciones por ordenador.

En este artículo aprenderemos qué es una simulación y repasaremos los puntos principales sobre cómo crear una.

## ¿Qué es una simulación?

Una simulación numérica o **prueba virtual** es un cálculo realizado por un ordenador siguiendo un programa que implementa un modelo matemático para un sistema físico.

Combina un **modelo geométrico** del sistema físico con las **definiciones físicas** sobre ese sistema para predecir numerosos **fenómenos físicos**, como el calentamiento por inducción.

<p align="center">

![What is a simulation](assets/overview/documentacion1.png)

</p>

## Simulación con CENOS

CENOS es el acrónimo de ***Connecting Engineering Open Source***, que destaca la forma en que CENOS crea y calcula simulaciones, con el compromiso de conectar ingenieros y software de código libre. Mediante la combinación de 3 potentes herramientas de código abierto - **Salome**, **GetDP** y **ParaView** - CENOS ofrece la mejor herramienta para simulaciones de *Calentamiento por inducción*. 

El flujo de trabajo de la simulación CENOS se basa en estas tres herramientas de código abierto. Consta de 4 partes - **Geometría**, **Física**, **Mallado** y **Resultados** - que representan los pasos requeridos para crear una simulación de *Calentamiento por inducción*.

<p align="center">

![What is a simulation](assets/overview/documentacion2.png)

</p>

## Geometría

Hay 3 maneras de crear y preparar la geometría para simulación en CENOS - ***Plantillas***, ***Archivo CAD*** y ***Editor avanzado de geometría***. Estos enfoques tienen diferentes aplicaciones geométricas y pueden utilizarse para **preparar cualquier geometría**.

<p align="center">

![What is a simulation](assets/overview/2.png)

</p>


### Template

:::note Nota

Cálculos rápidos de calentamiento, en solamente un par de minutos.

:::

*Template* le permite elegir entre **diferentes plantillas de piezas de trabajo e inductores** para configurar rápidamente una simulación 2D axial-simétrica.

Como la **malla es creada automáticamente**, basta con definir los parámetros geométricos y físicos clave para poner en marcha una simulación.

<p align="center">

![What is a simulation](assets/overview/3.png)

</p>

<p align="center">

![What is a simulation](assets/overview/4.png)

</p>

### From CAD

:::note Nota

Importe CAD prefabricados y simúlelos sin modificaciones geométricas adicionales.

:::

*From CAD* es un método de creación de geometría que permite **importar uno o varios archivos CAD y prepararlos** para la simulación sin modificaciones manuales de la geometría.

**Cree grupos geométricos y superficies de frontera**, defina los parámetros físicos y ejecute la simulación. Con este enfoque, ¡la **malla se genera automáticamente**!

<p align="center">

![What is a simulation](assets/overview/5.png)

</p>

<p align="center">

![From CAD](assets/overview/6.png)

</p>

### Advanced geometry editor

:::note Nota

Para usuarios avanzados que desean tener un control total sobre la geometría y la malla.

:::

Para usuarios más avanzados, CENOS ofrece **un enfoque de creación de geometría y malla totalmente manual** - *Advanced geometry editor*. Permite crear la geometría y la malla desde cero en la herramienta de modelado geométrico de CENOS - Salome.

¡Cree una geometría personalizada y una malla adecuada, defina dominios y condiciones de frontera y **disfrute de toda la potencia de CENOS**!

<p align="center">

![From CAD](assets/overview/7.png)

</p>

<p align="center">

![From CAD](assets/overview/8.png)

</p>

:::info Importante

Junto a la geometría también es necesario **preparar una malla** para llevar a cabo una simulación, la calidad de la malla afecta la precisión de los resultados. Para el *Editor de geometría avanzado* la malla debe crearse manualmente.

:::

## Física

CENOS Platform ofrece una amplia gama de variables para simular ***Calentamiento por inducción**, centrándose en el análisis ***Térmico*** y ***Electromagnético***.


### Análisis Térmico

:::note Nota

Calcular las aplicaciones convencionales de calentamiento.

:::


<p align="center">

![From CAD](assets/overview/11.png)

</p>

### Electromagnetismo

:::note Nota

Densidad de corriente rápida, calor joule y otras predicciones de fenómenos electromagnéticos.

:::

¡La física *Electromagnética* le permite estimar la *Densidad de Corriente*, el *Calor Joule*, el *campo EM* y otros aspectos electromagnéticos de tu modelo!


<p align="center">

![From CAD](assets/overview/13.png)

</p>

### Calentamiento por Inducción

:::note Nota

Simular aplicaciones de calentamiento por inducción.

:::

El software *Induction Heating* utiliza física electromagnética y térmica acoplada, **diseñada específicamente para simulaciones de calentamiento por inducción**.

<p align="center">

![From CAD](assets/overview/15.png)

</p>

## Resultados

:::note Nota

Obtenga resultados visuales y estadísticos precisos y amplios de su simulación.

:::

CENOS incorpora un post-procesador muy potente - *ParaView*, que junto con las estadísticas de energía, que se encuentran en el archivo .csv, proporciona un control total sobre los resultados y cada aspecto de la simulación.

<p align="center">

![From CAD](assets/overview/16.png)

</p>

<p align="center">

![From CAD](assets/overview/17.png)

</p>

<p align="center">

![From CAD](assets/overview/18.png)

</p>
