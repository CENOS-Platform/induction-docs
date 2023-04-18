---
id: mesh-overview
title: El mallado en Salome
sidebar_label: Visión general
sidebar_position: 1
---

La creación de la malla o cuadrícula numérica es una de las partes más importantes de la configuración de la simulación. Sus **resultados dependen directamente de la calidad de la malla**, siendo la malla gruesa una de las mayores razones de resultados incorrectos o incluso poco físicos.

CENOS tiene un constructor de malla integrado, donde el usuario puede seleccionar el tamaño, densidad, gradiente de la malla, así como modificar los valores automáticos y refinar aristas o caras específicas. No obstante, si el usuario requiere crear su propia malla desde la herramienta de terceros *Salome*, aún es factible desde nuestra interfaz.

En este artículo repasaremos la creación de mallas en *Salome*, una de las herramientas de código abierto utilizadas por CENOS. Aprenderá **cómo interactuar con la ventana de configuración de la malla** y repasará **diferentes aspectos y enfoques utilizados en la creación de mallas**.

Una vez que haya terminado de configurar tanto la geoemetría como la física, vaya al módulo de malla, en el módulo de malla haga clic en el botón *More properties*.

<p align="center">

![Mesh module](assets/mesh-overview/c4.png)

</p>

Luego haga click en el botón **OPEN ADVANCED EDITOR**, aparecerá una instancia de Salome y una ventana de Python, no cierre la ventana de Python, y trabaje dentro de Salome.

<p align="center">

![Mesh module](assets/mesh-overview/2c4.png)

</p>

## Cómo crear una malla

Ahora podemos sumergirnos en la creación de mallas. Antes de hacerlo cambie del módulo de geometría al módulo de vista de malla.

<p align="center">

![Mesh module](assets/mesh-overview/1.png)

</p>

Para crear una malla:

+ Seleccione la partición a partir de la cual desea crear su malla en ***Geometry*** (![createMesh](assets/mesh-overview/geom.png)).

<p align="center">

![Mesh module](assets/mesh-overview/2.png)

</p>

+ Haga clic en el icono ***Create Mesh*** (![createMesh](assets/mesh-overview/createmesh.png)) o selecciónelo en el menú desplegable de ***Mesh → Create Mesh***.

## Interfaz de mallado

Ahora se abrirá la interfaz de configuración de malla. La ventana de malla en Salome tiene cuatro pestañas - **3D, 2D, 1D y 0D**. Cada dimensión (volúmenes - superficies - aristas) tiene **su propio algoritmo de mallado con sus propios parámetros**.

:::note

También puede establecer parámetros de mallado para elementos 0D (puntos), pero esto se utiliza raramente.

:::

<p align="center">

![Mesh](assets/mesh-overview/mesh_main.png)

</p>

<p align="center">

![Mesh](assets/mesh-overview/tabs.png)

</p>


Los ingenieros de CENOS siempre comienzan con la **malla automática**, que **aplica algoritmos por defecto para todas las dimensiones** y sólo necesita la definición del tamaño máximo del elemento, que en realidad es el tamaño de la arista del elemento. **En la malla automática, el algoritmo 1D determina el tamaño de la malla**, ya que los algoritmos *2D* y *3D* se basan en las aristas *1D*.

Puede crear una malla automática haciendo clic en ***Assign a set of hypotheses → Automatic Tetrahedralization***. Para el dominio del aire (malla principal) el valor por defecto *Max Lenght* suele ser suficiente.

<p align="center">

![Mesh](assets/mesh-overview/max_size.png)

</p>

:::caution IMPORTANTE

**La longitud máxima (tamaño de la malla)** puede cambiarse posteriormente en la pestaña **1D** haciendo clic en ***Edit algorithm parameters*** (![Edit algorithm parameters](assets/mesh-overview/3.png)).

:::

Para ver cÓmo queda la malla, presione **calculate the mesh**.  Para ello haga click izquierdo en la malla creada (![createMesh](assets/mesh-overview/mesh.png)) y presione ***Compute*** (![createMesh](assets/mesh-overview/compute.png)). Mientras busca los parámetros de malla adecuados, le sugerimos que utilice la función ***Clear mesh data*** (haga clic con el botón izquierdo del ratón en la malla) antes de volver a calcular.

:::caution IMPORTANTE

Al calcular la malla, si hay *submallas*, se calcularán primero, y sólo entonces se aplicará la definición de malla de *Mesh_1* al resto de la geometría.

:::

## Mallas secundarias

*Sub-malla*, o malla secundaria, es lo mismo que la malla anterior en términos de definición, sólo que aplicada a un dominio más pequeño. **Son necesarias para aumentar la resolución de la malla localmente** para dominios como la pieza de trabajo y el inductor, donde se necesitan elementos de malla más pequeños, **mientras se dejan elementos de malla más grandes en otros dominios** (como el dominio del aire) donde no se necesita una resolución tan alta.

La *sub-malla* puede adoptar muchas formas: normalmente se utiliza para la resolución de la pieza y el inductor, pero también es posible crear una *sub-malla* para determinadas partes de la pieza o el inductor, como superficies y bordes, para obtener una resolución aún mayor.

### Sub-malla en un sólido

Para crear una *sub-malla* necesitas hacer **click-derecho** en tu malla principal (*Mesh_1*), y hacer click en ***Create Sub-mesh*** (![createMesh](assets/mesh-overview/createsubmesh.png)).

Desde el desplegable de particiones en *Object Browser* seleccione el grupo de geometría para el que desea crear una *sub-malla* y cree una malla automática como se ha mencionado anteriormente. La *sub-malla* aparecerá en ***SubMeshes on Solid***.

<p align="center">

![submeshes](assets/mesh-overview/solidsubmesh.png)

</p>

El tamaño de malla "automático" por defecto será probablemente demasiado grande, por lo que sugerimos ir **3-5 veces más pequeño en la primera iteración de tamaño**.

Tenga en cuenta que como normalmente creamos una *sub-malla* para cada dominio excepto el aire, la malla principal (*Mesh_1*) es responsable sólo del aire. Por ello, la malla principal suele ser bastante gruesa.

### Sub-malla en superficie

En algunos casos **se necesita una resolución local aún mayor de la malla**. Para ello puede utilizar y crear una *sub-malla* en una o más superficies.

Desde el desplegable de particiones en el *Object Browser* seleccione el grupo de geometría para el que desea crear una *sub-malla* y cree una malla automática como se ha mencionado anteriormente. La *submalla* aparecerá en ***SubMeshes on Face***.

Cuando se crean múltiples *sub-mallas* que **se solapan entre sí** (por ejemplo, una *sub-malla* sólida para el inductor y una *sub-malla* superficial para una parte de la misma superficie del inductor), aparecerá una ventana de ***Prioridad de la sub-malla***.

En la ventana *sub-mesh* se **define el orden** en que se calcularán las *sub-mallas* superpuestas. Es importante porque las *sub-mallas* con **menor prioridad** se basarán parcialmente en las *sub-mallas* con **mayor prioridad** - por ello priorice las *sub-mallas* para las que la **calidad de la malla es más importante**.

:::note

En este ejemplo se utilizan *sub-mallas* en la superficie del eje para crear una malla más fina cerca de la apertura de la cerradura y en parte de la superficie del eje:

:::

<p align="center">

![Mesh](assets/mesh-overview/priority.png)

</p>

<p align="center">

![submeshes](assets/mesh-overview/submeshes.png)

</p>

:::info IMPORTANTE

También se pueden crear *Sub-mallas* para **bordes** si necesita un refinamiento adicional o si está trabajando con un caso **2D**.

:::

## Algoritmos 2D 

Si utiliza la opción **malla automática**, utilizará el algoritmo ***Mefisto*** para la definición de superficies 2D.

El algoritmo ***Mesfisto*** crea una malla mayoritariamente uniforme. Aunque es suficiente la mayoría de las veces, a veces se necesita una distribución de elementos de malla más fina cerca de los diferentes bordes de la *sub-malla*. En ese caso puede cambiar el algoritmo *Mefisto* a *NETGEN 2D* en la pestaña 2D.

:::note

He aquí un ejemplo de *Mefisto* frente a la malla de aire *NETGEN 2D*:

:::

<p align="center">

![Mesh](assets/mesh-overview/mefisto_netgen.png)

</p>

Según nuestra experiencia, el algoritmo ***NETGEN*** tiende a ser **más resistente**, por lo que sugerimos utilizarlo para el rol de aire y geometrías más complejas.

## Efecto piel

Tanto el dominio del inductor como el de la pieza de trabajo necesitan una capa de malla fina en la superficie para **modelar la alta densidad de corrientes cerca de la superficie**. Esto se produce debido al fenómeno físico conocido como _efecto piel (skin effect)_. En Salome esto puede resolverse fácilmente con ***Capas viscosas***. 

Para simulaciones de calentamiento por inducción (normalmente en la pieza de trabajo) las *Capas viscosas* sirven para **el doble propósito de resolver tanto las corrientes superficiales como la conducción de calor desde la capa de piel** más profunda en la pieza de trabajo.

:::note

Aquí puede ver un ejemplo de *Capas Viscosas* utilizadas para crear pequeños elementos en capas en la superficie de la pieza de trabajo para resolver la densidad de corriente:

:::

<p align="center">

![Mesh|20%](assets/mesh-overview/layers.png)

</p>

### Creación de Capas Viscosas

Para crear *Capas Viscosas* en su ventana *sub-malla* seleccione la pestaña **2D o 3D** dependiendo del tipo de simulación - *2D* o *3D*. Haga clic en el ícono **gear** (![gear icon](assets/mesh-overview/4.png)) junto a *Add. Hipótesis* y seleccione *Viscous Layers*.
<p align="center">

![Mesh](assets/mesh-overview/skinlayer.png)

</p>

Para definir *Capas Viscosas*, debe introducir 3 parámetros: *Espesor total*, *Número de capas* y *Factor de estiramiento*.

+ ***Grosor total (Total thickness)*** - tamaño total de la capa de piel, que depende de la frecuencia y de las propiedades del material;

+ ***Número de capas (Number of layers)*** - define cuántas capas se crearán dentro del tamaño de capa de piel definido previamente;

+ ***Factor de estiramiento (Stretch factor)*** - determina el gradiente del tamaño de las capas - en cuánto será mayor la siguiente capa que la anterior;

<p align="center">

![Mesh|small](assets/mesh-overview/stretch.png)

</p>

Sugerimos empezar con los siguientes parámetros, donde **δ es la profundidad del efecto piel** para el dominio respectivo:
    
|                  |     Workpiece    |    Inductor    |
|------------------|:----------------:|:--------------:|
| Total thickness  |   1.5 δ          |     δ          |
| Number of layers |     ≈ 5 to 8     |    ≈  4 to 7   |
| Stretch factor   |        1.5       |       1.4      |


### Caras sin capas (entradas y salidas)

Esta característica permite excluir ciertas caras o aristas de la capa de la piel, posiblemente disminuyendo el número de elementos significativamente. Esto debería usarse para:

 * Terminales del inductor
 * Superficie interior del inductor si éste tiene un **canal de refrigeración**.
 * Eje de simetría de una pieza 2D. 
 * Cualquier otra pieza alejada del inductor.

Para utilizar esta función:
1. Seleccione los grupos deseados en su ***partición*** o selecciónelos directamente en la *ventana Objeto*;
2. Haga clic en ***Add***;
3. Verifique el número de caras o aristas en la ventana ***caras seleccionadas***;
4. Haga clic en ***OK*** y ***Apply*** y ***Close***.
5. **Borrar datos de malla** y **recalcular** la sub-malla para ver los cambios.

<p align="center">

![Mesh](assets/mesh-overview/withoutfaces.png)

</p>

<p align="center">

![Mesh](assets/mesh-overview/withoutfaces2.png)

</p>


## Tamaño de malla

Recomendamos **comenzar con una malla gruesa**, para tener un tiempo de cálculo más corto, sólo para ver si todo funciona correctamente.
Incluso con la malla más gruesa, la estimación de la temperatura y la potencia será de sólo un **6%** de diferencia. 

Cuando tenga aproximadamente los resultados que estaba buscando, puede entonces disminuir el tamaño de la malla para aumentar la precisión de sus resultados.

<p align="center">

![Graph](assets/mesh-overview/Figure_2.png)

</p>

:::info INFORMACIÓN

Estos resultados son sólo para demostrar los efectos y **no deben utilizarse como referencia**, ya que la forma de la geometría tendrá un efecto significativo en los resultados.
Como puede ver, el tiempo de cálculo aumenta **exponencialmente** con el tamaño de la malla, por lo que no merece la pena perseguir las ganancias marginales con una malla demasiado fina.

:::
