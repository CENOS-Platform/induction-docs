---
id: cad
title: Crear simulación con From CAD
sidebar_label: Uso de archivos CAD
sidebar_position: 3
---

Usted puede importar archivos CAD prefabricados y preparar la geometría para la simulación directamente en CENOS.

**Genere automáticamente una caja de aire y una malla**, y configure la simulación sin necesidad de editar manualmente la geometría o la malla.

## Seleccionar el enfoque de construcción geométrica

Para importar archivos CAD prefabricados, haga clic en **From CAD** en la ventana de inicio de CENOS.

<p align="center">

![From CAD](assets/cad/1.png)

</p>

Haga clic en el icono *Carpeta* para **seleccionar e importar archivos CAD**.

<p align="center">

![From CAD](assets/cad/2.png)

</p>

### Crear una caja de aire

Cree una caja de aire automáticamente.

<p align="center">

![From CAD](assets/cad/3.png)

</p>

**Seleccione las terminales del inductor** como referencias para el tamaño de la caja de aire y pulse en *create air*.

<p align="center">

![From CAD](assets/cad/4.png)

</p>

### Preparar volúmenes

:::info Importante

Para facilitar la selección y preparación de volúmenes y superficies, la función *From CAD* incluye múltiples herramientas útiles.

:::

<p align="center">

![From CAD](assets/cad/14.png)

</p>

 + **Select all** - Selecciona todos los volúmenes o condiciones de frontera disponibles para la selección.
 
 + **Show all** - Activa o desactiva la visibilidad del objeto seleccionado.
 
 + **Merge** - Fusiona o *agrupa* varios volúmenes o superficies en uno solo.
 
 + **Unmerge** - Dividir objetos previamente fusionados o *agrupados* en su estado inicial.

**Agrupe y renombre los dominios de volumen** según sea necesario.

<p align="center">

![From CAD](assets/cad/5.png)

</p>

### Preparar las condiciones de frontera

Haga clic en **Workpice surface**, donde seleccionará las caras que servirán como condiciones de frontera para el análisis, también puede filtrar las caras por volumen, para facilitar la selección.

<p align="center">

![From CAD](assets/cad/7.png)

</p>

Por último, añada tantas funciones como requiera su sistema, como **piezas de trabajo adicionales**, **inductores adicionales y sus terminales**, **concentradores de flujo**, **aire** y *otros*.

<p align="center">

![From CAD](assets/cad/8.png)

</p>

Después de configurar la geometría, haga clic en **GO TO PHYSICS** para entrar en la configuración de la física.

<p align="center">

![From CAD](assets/cad/10.png)

</p>

## Definir los parámetros de simulación

### Introducir los parámetros físicos

En la ventana SIMULATION CONTROL **defina los parámetros globales** como *frecuencia*, *tiempo de cálculo*, etc.

<p align="center">

![From CAD](assets/cad/11.png)

</p>

En las ventanas de DOMINIO DE SIMULACIÓN como "WORKPIECE" **defina los parámetros físicos y las condiciones de frontera de cada dominio** como *material*, *intercambio térmico*, *corriente*, etc.

<p align="center">

![From CAD](assets/cad/12.png)

</p>

En la sección de inductores, podrás introducir ***voltaje***, ***corriente*** o ***potencia***.

<p align="center">

![From CAD](assets/cad/ind.png)
 
</p>

## Mallado

CENOS cuenta con un generador de mallas integrado, después de configurar la física, haga clic en **GO TO MESH** para entrar en la configuración de la física.

<p align="center">

![From CAD](assets/cad/mesh0.png)
 
</p>

Seleccione la densidad que desea que tenga la malla automática.
 
<p align="center">

![From CAD](assets/cad/mesh1.png)

</p>

En caso de que desee realizar algún cambio en la malla generada por nuestro algoritmo puede hacerlo activando el ***refinamiento de malla*** y seleccionando el elemento que quiera ajustar.

<p align="center">

![From CAD](assets/cad/mesh2.png)

</p>

En esta sección, podrá desactivar la calculadora automática de capas viscosas y refinar toda la sección, o las caras y bordes, según sus necesidades.
 
<p align="center">

![From CAD](assets/cad/mesh3.png)

</p>

**Para saber más** sobre el mallado, visita nuestra [**documentación sobre mallado**](#meshing).

## Post-procesamiento

Al finalizar los cálculos, la herramienta de post-procesamiento *ParaView* se **abrirá automáticamente con un estado de temperatura preestablecido**, y podrá ver la **distribución del campo de temperatura** en la pieza en el último paso de tiempo.

<p align="center">

![From CAD](assets/cad/13.png)

</p>

**Para obtener más información** acerca de cómo personalizar la visualización de los resultados, visite nuestro artículo [**evaluación de resultados**](/results).

### Valores integrales

Para valores integrales, tales como **potencia aparente, calor inducido y tensión compleja**, puedes utilizar el archivo .csv, que se genera junto con los resultados visuales. Puedes acceder a él a través del botón *Nota* situado junto al botón *Play* del bloque *Visualization*.

<p align="center">

![From CAD](assets/cad/15.png)

</p>