---
id: results
title: Cómo evaluar los resultados
sidebar_label: Evaluación de resultados
sidebar_position: 5
---

La plataforma CENOS incorpora una potente herramienta de postprocesamiento - [**ParaView**](https://www.paraview.org/). Está siendo utilizada en todo el mundo por especialistas de diferentes campos que van desde el *Análisis Estructural* al *CFD* y la *Investigación Climática*.

Siendo uno de los programas de análisis y visualización de datos de código abierto más potentes, se ha vuelto lo suficientemente complejo como para confundir a los nuevos usuarios sobre cómo utilizarlo.

En este artículo veremos **algunos de los filtros más comunes de ParaView** y su uso, así como **filtros especialmente útiles en el análisis de resultados de simulación de calentamiento por inducción**.

## Cómo elegir qué valores de resultado calcular

Antes de sumergirnos en *ParaView* y su funcionamiento, necesitamos entender primero qué se visualiza en *ParaView*. Por defecto *ParaView* nos muestra los componentes visuales de los resultados, como *Temperatura* o *Densidad de corriente*, pero **puedes añadir algunos resultados adicionales**, como *Fuerza de Lorentz, Potencial eléctrico escalar, Potencial magnético vectorial y Permeabilidad magnética*.

Para añadir estos resultados debe ir al bloque **Física** y hacer clic en *Show* en la pestaña de **resultados adicionales a calcular**.

Ahí puedes **seleccionar o deseleccionar los valores que quieres calcular**:

<p align="center">

![Post-processing settings](assets/results/29.png)

</p>


Si ha calculado el caso, pero **olvidó seleccionar un valor específico**, puede seleccionarlo incluso después del cálculo y recalcular sólo la parte del resultado para obtener el valor que le interesa. Basta con hacer clic en **Recalcular** para calcular los valores de resultado que faltan:


## Cómo acceder a los filtros

Los *filtros* de ParaView son algoritmos que extraen una información específica, como isocontornos y datos puntuales, del conjunto de datos del resultado inicial y **se utilizan para visualizar propiedades físicas específicas** de la simulación calculada.

Se puede acceder a los filtros de distintas maneras. Si sabe qué filtro necesita, puede hacer clic en *Filtros → Buscar...* y **buscar directamente el filtro** introduciendo su nombre en la ventana *Buscar* y haciendo clic en *Enter*.

En el ejemplo siguiente se ha escrito la palabra ***plot*** en la ventana *Buscar*, y todos los filtros cuyos nombres incluyen ***plot*** se encuentran y están disponibles para su selección.

<p align="center">

![Post-processing settings](assets/results/1.png)

</p>


Si no sabe qué filtro utilizar, puede elegir entre todos los filtros disponibles haciendo clic en *Filtros → Alfabético*.

<p align="center">

![Post-processing settings](assets/results/2.png)

</p>


## Cómo utilizar los filtros

Para utilizar los filtros en ParaView, primero debe elegirse un ***conjunto de datos*** sobre el que se aplicará el filtro. Una vez finalizado el cálculo, CENOS abrirá la ventana ParaView con un estado preestablecido consistente en 1 ventana de resultados (en el caso 3D) o 2 ventanas de resultados (en el caso 2D de simetría axial). Los datos de simulación también se dividirán en conjuntos de datos más pequeños, como *Pieza de trabajo*, *Inductor*, etc.

**IMPORTANTE**: Si desea aplicar filtros a un conjunto de datos específico, primero debe seleccionarlos en el *Buscador de filtros*.

Por ejemplo, si desea aplicar un filtro como *Plot Over Line* a la pieza de trabajo, debe elegirse el conjunto de datos correspondiente antes de seleccionar el filtro; de lo contrario, no podrá seleccionarse ninguno de los filtros.

<p align="center">

![Post-processing settings](assets/results/3.png)

</p>

## Filtros más utilizados

Los filtros más utilizados como medio de **evaluación visual de los resultados** son también los primeros que se utilizan para **determinar la validez de los resultados**. Aunque no son tan complejos como otros filtros, siguen siendo importantes para el postprocesamiento.

### Extract Block

*Extract Block* permite **extraer uno o varios dominios del conjunto de datos completo** y manipular los resultados en estos dominios de forma independiente. CENOS exporta automáticamente conjuntos de datos de los dominios *pieza de trabajo* e *inductor*, pero *Extract Block* puede utilizarse aún más.

Por ejemplo, en el caso de [** disparo único**](/physics/motion#simple-motion) CENOS exporta y visualiza automáticamente la distribución de temperatura en la pieza de trabajo, así como un inductor sólido.

<p align="center">

![Post-processing settings](assets/results/4.png)

</p>

**IMPORTANTE**: Dado que los conjuntos de datos de la pieza de trabajo y del inductor se han exportado por separado, podemos manipular los resultados de forma independiente para cada dominio.

Si seleccionamos *Inductor* en *Pipeline Browser* y cambiamos la visualización de *Solid Color* a *Current Density*, podemos visualizar el flujo de corriente en el inductor, manteniendo la distribución de temperatura en la pieza.

<p align="center">

![Post-processing settings](assets/results/5.png)

</p>

La simulación de disparo único incorpora *concentradores* alrededor de la bobina, pero **no se exportan automáticamente**. Para visualizar los concentradores, seleccione *Simulation Data* en *Pipeline Browser* y [**open Extract Block filter**](/results#how-to-access-filters). En la ventana de *Propepiedades* seleccione el dominio del concentrador (*yoke* en este caso) y haga clic en *Apply*.

<p align="center">

![Post-processing settings](assets/results/6.png)

</p>

Seleccione el recién creado *ExtractBlock1* y cambie la visualización de *Current Density* a *Solid Color*.

<p align="center">

![Post-processing settings](assets/results/7.png)

</p>

### Slice

*Slice* permite **cortar el dominio con un plano** y visualizar sólo una capa del mismo.

Para utilizar *Slice*, seleccione el dominio de interés (parte extraída o dominio computacional completo) y [**abra el filtro Slice**](/results#how-to-access-filters). En las *propiedades* introduzca los parámetros que definen el plano que se utilizará para crear el corte.

<p align="center">

![Post-processing settings](assets/results/8.png)

</p>

Desmarque la casilla *Show Plane* para desactivar la visibilidad del plano de corte y haga clic en *Apply*. Seleccione *Slice1* en *Pipeline Browser* y cambie la visualización por defecto *Current Density* a *Temperature*.

<p align="center">

![Post-processing settings](assets/results/9.png)

</p>

### Clip

*Clip* es similar al filtro *Slice* y permite **cortar el dominio por la mitad** y visualizar sólo una parte del mismo.

Para utilizar *Clip*, seleccione el dominio de interés (parte extraída o dominio computacional completo) y [**abra el filtro Clip**](/results#how-to-access-filters). En *propiedades* introduzca los parámetros que definen el plano que se utilizará para crear el clip.

<p align="center">

![Post-processing settings](assets/results/10.png)

</p>

Desmarque la casilla *Show Plane* para desactivar la visibilidad del plano de corte y haga clic en *Apply*. Seleccione *Clip1* en *Pipeline Browser* y cambie la visualización por defecto *Current Density* a *Temperature*.

<p align="center">

![Post-processing settings](assets/results/11.png)

</p>

### Stream Tracer

*Stream Tracer* permite generar líneas de corriente para campos vectoriales. Es útil para **visualizar líneas de campo magnético**.

Para visualizar mejor las líneas de campo magnético, el filtro debe aplicarse a todo el dominio computacional, porque **genera líneas de corriente dentro del dominio seleccionado**, lo que significa que si quieres visualizar líneas de campo magnético alrededor de su geometría, necesita generar líneas de corriente en el dominio de aire que encierra la geometría, no en la geometría misma.

**IMPORTANTE**: Para generar líneas de corriente alrededor de la geometría, aplique *Stream Tracer* al dominio del aire o a todo el dominio computacional, que contiene la geometría.

Para utilizar *Stream Tracer*, seleccione el dominio de interés (seleccione *Simulation data* para todo el dominio computacional), [**open Stream Tracer filter**](/results#how-to-access-filters) y haga clic en *Apply*.

<p align="center">

![Post-processing settings](assets/results/12.png)

</p>

Para visualizar mejor las líneas de campo magnético, cambie *Vectores* a **Magnetic Flux Density**, aumente la **Longitud máxima de la línea de flujo**, cambie *Tipo de semilla* a **Nube de puntos**, aumente el *Radio de la esfera* y el *Número de puntos*, y disminuya la *Opacidad*.

<p align="center">

![Post-processing settings](assets/results/13.png)

</p>

Extraiga y haga visible la geometría alrededor de la cual desea generar las líneas de corriente y, con las propiedades *Stream Tracer* ajustadas, haga clic en *Apply*.

<p align="center">

![Post-processing settings](assets/results/14.png)

</p>

## Filtros útiles para el calentamiento por inducción

Algunos filtros y métodos de evaluación de resultados son especialmente útiles para el **análisis en profundidad** de los resultados de las simulaciones de calentamiento por inducción.

### Plot Selection Over Time

*Plot Selection Over time* le permite **trazar gráficos dependientes del tiempo en un punto especificado**.

Para utilizar *Plot Selection Over time*, primero necesita marcar su punto de interés. Para ello, haga clic en la tecla "d" del teclado y, a continuación, haga clic con el botón izquierdo del ratón en la pieza de trabajo para marcar el punto especificado.

**IMPORTANTE**: Puede trazar gráficos sólo en los puntos donde se cruzan las líneas de malla.

Para comprender mejor qué puntos están disponibles para el trazado, cambie la representación visual del dominio de interés de *Superficie* a ***Superficie con aristas***, y seleccione el punto en el que desea trazar un gráfico.

<p align="center">

![Post-processing settings](assets/results/15.png)

</p>

Cuando haya seleccionado el punto, seleccione el dominio de interés (parte extraída o dominio computacional completo), [**abra el filtro Plot Selection Over Time**](/results#how-to-access-filters) y haga clic en *Apply*.

Todos los resultados disponibles se representarán junto a los resultados de la simulación como valores dependientes del tiempo.

<p align="center">

![Post-processing settings](assets/results/16.png)

</p>

Para **cambiar entre diferentes resultados o trazar un gráfico específico**, seleccione la ventana con gráficos y en la ventana *PlotSelectionOverTime1* *Properties* bajo *Series Parameters* seleccione sólo las *Variables* como *Temperatura* y pulse *Apply* para trazar el nuevo gráfico dependiente del tiempo.

<p align="center">

![Post-processing settings](assets/results/17.png)

</p>

### Plot Over Line

*Plot Over Line* permite trazar los resultados a lo largo de una línea dibujada a través del dominio computacional.

Para usar *Plot Over Line*, seleccione el dominio de interés (parte extraída o dominio computacional completo), [**abra el filtro Plot Over Line**](/results#how-to-access-filters) y haga clic en *Apply*.

<p align="center">

![Post-processing settings](assets/results/18.png)

</p>

Para **cambiar entre diferentes resultados**, seleccione la ventana con gráficos y en la ventana *PlotOverLine1* *Properties* bajo *Series Parameters* seleccione sólo las *Variables* como *Temperatura* y pulse *Apply* para trazar el nuevo gráfico temporal.

**IMPORTANTE**: Puede ajustar la línea utilizada para trazar el gráfico moviendo su punto inicial y final.

<p align="center">

![Post-processing settings](assets/results/19.png)

</p>

### Zona endurecida

Puede visualizar la zona endurecida con el filtro *Hardened Profile*. Es necesario crear una zona separada en la que la **temperatura supera en cualquier momento la temperatura de austenización**.

Para utilizar *Hardened Profile*, seleccione el dominio de interés (pieza de trabajo), [**abra el filtro Hardened Profile**](/results#how-to-access-filters) y haga clic en *Apply*.

**IMPORTANTE**: En la *lista de objetos* del lado izquierdo, haga clic en el *icono del ojo* junto a la pieza de trabajo para **activar su visibilidad y ver la zona templada**.

<p align="center">

![Post-processing settings](assets/results/27.png)

</p>

Se creará un **bloque separado**. Puede cambiar su color en la pestaña de propiedades de la izquierda con ***Editar color***.

<p align="center">

![Post-processing settings](assets/results/23.png)

</p>

Resultado final:

<p align="center">

![Post-processing settings](assets/results/22.gif)

</p>

Para los casos de **3D**, una vez que haya vuelto a activar la visibilidad de la pieza de trabajo, le sugerimos que cambie su modo de representación (en la parte superior) a **Feature Edges**:

<p align="center">

![Post-processing settings](assets/results/25.png)

</p>

<p align="center">

![Post-processing settings](assets/results/26.png)

</p>

:::caution Importante

La **temperatura de austenización por defecto es de 800 degC** - ¡averigüe y modifique la temperatura de temple en función de su material!

:::

Cambie la temperatura de austenización en la ventana *HardenedProfile1* *Properties* en *Value Range*.

<p align="center">

![Post-processing settings](assets/results/24.png)

</p>

## Gráficos de tiempo

Una vez que haya abierto ParaView se crearán dos diseños, ***Vista 3D*** y ***Gráficos de tiempo***. Este segundo diseño contiene varios parámetros del archivo .csv trazados en el tiempo que muestran cómo la potencia, la tensión o cualquier otro parámetro cambia con el tiempo.

<p align="center">

![Post-processing settings](assets/results/layout.png)

</p>

Tras cambiar a la vista de gráfico, verá cuatro gráficos predeterminados que muestran diversos parámetros. Puede crear gráficos personalizados editando el ***Script*** en la ventana de ***propiedades***.

<p align="center">

![Post-processing settings](assets/results/properties.png)

</p>

1. Seleccione la vista haciendo clic en cualquier lugar de la misma.
2. Ir a la ventana *Script* en el panel *propiedades*.
3. Introduzca el **nombre del dominio** entre las primeras comillas.
4. Introduzca el **nombre del parámetro** del archivo .csv en las segundas comillas.
5. Haga clic en cualquier parte del gráfico para actualizarlo.

Ejemplo:

<p align="center">

![Post-processing settings](assets/results/howto.png)

</p>

>plot1 = ["", ""]<br />
>plot2 = ["billet", "Active_Power_[W]"]<br />
>plot3 = ["", ""]<br />
>plot4 = ["", ""]<br />

**IMPORTANTE**: Asegúrese de que no hay **espacios** al principio ni al final de los nombres, y que tiene **ambas comillas**, de lo contrario no se creará el gráfico.