---
id: algorithms
title: Algoritmos de cálculo
sidebar_label: Algoritmos de cálculo
sidebar_position: 4
---

Al configurar una simulación en CENOS, verá en la sección de CONTROL DE SIMULACIÓN que se le da la **opción de seleccionar el algoritmo de cálculo**.

En este artículo echaremos un vistazo a los algoritmos de cálculo, **comprenderemos sus diferencias** y descubriremos **en qué situaciones utilizar cada algoritmo**.

## Rápido

El algoritmo Rápido (también acoplamiento débil, acoplamiento unidireccional) **calcula las fuentes electromagnéticas una vez y las aplica al modelo térmico**. La interacción inversa (cambio de las propiedades electromagnéticas debido al calentamiento) no se tiene en cuenta.

<p align="center">

![alt-text](assets/algorithms/1.png)

</p>

:::info Información

El algoritmo rápido da buenos resultados si el **paso de tiempo es pequeño** en comparación con la velocidad de calentamiento.

:::

Esquema de cálculo con **algoritmo Rápido**:

<p align="center">

![alt-text](assets/algorithms/FastAlgo.svg)

</p>

## Preciso

El algoritmo Preciso utiliza el acoplamiento bidireccional - **las fuentes electromagnéticas se recalculan en función del campo de temperatura** hasta que se alcanza la convergencia.

<p align="center">

![alt-text](assets/algorithms/2.png)

</p>

:::info Información

El algoritmo de Precisión proporciona **resultados muy precisos** con un tamaño de paso de tiempo más aproximado y es importante para problemas altamente no lineales.

:::

Esquema de cálculo con **algoritmo Preciso**:

<p align="center">

![alt-text](assets/algorithms/AccurateAlgo.svg)

</p>

## Automático

El algoritmo Automático cambia entre **rápido** y **preciso** en función de los datos introducidos por el usuario:

* **Rápido si** los materiales tienen permeabilidad y conductividad eléctrica constantes;

* **Preciso si** los materiales tienen propiedades magnéticas no lineales ([**modelo B-H**](/physics/magnetic-properties#treatment-of-non-linear-magnetic-properties-in-harmonic-ac-simulation) y/o [**dependencia de la temperatura**](/physics/magnetic-properties#temperature-dependence-of-magnetic-properties)) y conductividad eléctrica dependiente de la temperatura.

<p align="center">

![alt-text](assets/algorithms/3.png)

</p>
