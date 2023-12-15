---
id: mesh-extrusion
title: Extrusión de malla
sidebar_label: Extrusión
sidebar_position: 2
---
Las geometrías finas y continuas como **tuberías, placas, láminas, inductores multivuelta** y muchas otras, pueden ser un **desafío para mallar** para los algoritmos de mallado por defecto - *NETGEN* y *Triangle: Mefisto*, ya que estos algoritmos producirán un número de elementos de malla innecesariamente grande.

Afortunadamente, hay una forma de evitar esto, creando la malla con un enfoque más "práctico". El método de mallado utilizado para este tipo de geometrías es el algoritmo **Extrusion 3D**. Este método funciona tomando una cara 2D y extruyéndola a lo largo del volumen del objeto, creando una malla **muy fina, pero baja en número de elementos**.

![Comparison](assets/mesh-extrusion/0.png)

## Cómo usar Extrusión 3D

Primero tiene que elegir la cara y el volumen para la extrusión.

**Defina un extremo del volumen como un grupo de caras 2D separado**. Usaremos esta cara para extruir su malla a lo largo del volumen del objeto. En este ejemplo llamaremos a esta cara "*Slice*".

**Defina el volumen de su objeto**, sobre el que se extruirá la malla de la cara "Slice" creada previamente. En este ejemplo llamaremos a este volumen "*Workpiece_One*".

![How to use Extrusion 3D](assets/mesh-extrusion/1.png)

:::info Importante

Si su geometría es **continua**, puede agrupar el resto de los volúmenes también en este paso.

:::

![How to use Extrusion 3D](assets/mesh-extrusion/2.png)

Después de definir los grupos, pase al módulo *Mesh*, haga una malla simple con geometría de partición y empiece a definir las sub-mallas.

Haga una sub-malla 2D para el grupo **Slice**. Elija el algoritmo *NETGEN 2D* y defina las *Capas viscosas* si es necesario. Esta definición de capas viscosas se utilizará automáticamente en el algoritmo *Extrusión 3D*.

![How to use Extrusion 3D](assets/mesh-extrusion/3.png)

Ahora necesitamos definir la parte de extrusión de la malla.

Cree una nueva sub-malla para el primer grupo de volúmenes, "*Workpiece_One*". En la sección **3D** elija **Extrusion 3D** como algoritmo.

En la sección **2D** déjelo en **None**. En la sección **1D** elija **Wire Discretisation**  y para *Hipótesis* elija **Number of Segments**. Este valor determina en cuántas secciones la malla **Slice** será extruida a lo largo del volumen. Cuanto mayor sea el *Número de Segmentos*, más fina será la malla.

![How to use Extrusion 3D](assets/mesh-extrusion/4.png)

Después de hacer la sub-malla de volumen, establezca el orden de las sub-mallas. Asegúrese de poner la *Slice* con mayor prioridad que el volumen, ya que el volumen necesitará primero la malla *Slice* para poder extruirlo.

<p align="center">

![How to use Extrusion 3D](assets/mesh-extrusion/5.png)

</p>

En la imagen de abajo está el resultado del algoritmo *Extrusión 3D*. Si quiere extruir el resto de los volúmenes después del primero, ¡simplemente defínalos de la misma manera que el primero!

![How to use Extrusion 3D](assets/mesh-extrusion/6.png)

## Extrusión de objetos redondos

A veces la geometría es **continua y cerrada**, en la que todavía se puede utilizar el algoritmo de Extrusión.

Echemos un vistazo a este anillo, que es axialmente simétrico a uno de los ejes. Como puede ver, es un anillo entero, pero dividido en 2 volúmenes - lo que se hace a propósito, porque **si el anillo es completamente sólido, el algoritmo de Extrusión 3D no funcionará.**

<p align="center">

![How to use Extrusion 3D](assets/mesh-extrusion/7.png)

</p>

Para la extrusión de objetos redondos primero hay que sacar uno de los planos de la sección transversal y crear un grupo para cada una de las mitades del anillo y para una sección transversal 2D. 

En este ejemplo también llamaremos a esta cara "*Slice*".

<p align="center">

![How to use Extrusion 3D](assets/mesh-extrusion/8.png)

</p>

Después de pasar por los pasos de mallado discutidos anteriormente, podemos obtener los resultados de esta parte simétrica, como se observa aquí.

![Extrusion on round objects](assets/mesh-extrusion/9.png)

## Limitaciones

Sin embargo, el algoritmo *Extrusión 3D* tiene algunos inconvenientes. Hay que tener en cuenta que **se empleará más tiempo en preparar el caso**, pero esto **resultará en un ahorro de tiempo total, ya que la simulación terminará más rápido** debido a una malla más optimizada.

### Continuidad de la geometría

Si su geometría consiste en 2 o más sólidos unidos, asegúrese de que la geometría sea lo más limpia posible, con los volúmenes continuando al final de cada uno.

En la imagen, preste atención a la estructura del volumen. El primero tiene elementos limpios y continuos, el otro tiene **elementos no alineados - esto no permitirá utilizar 3D Extrusion**.

<p align="center">

![How to use Extrusion 3D](assets/mesh-extrusion/10.png)

</p>