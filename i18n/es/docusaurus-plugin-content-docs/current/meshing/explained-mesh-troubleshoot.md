---
id: mesh-troubleshoot
title: Solución de problemas de malla
sidebar_label: Solución de problemas de malla 
sidebar_position: 5
---
El preprocesamiento o preparación de la geometría y el mallado para la simulación es la parte más importante de la configuración de la simulación, ya que puede afectar en gran medida a los resultados.

La creación de mallas para geometrías complejas puede suponer un reto, por lo que es necesario comprender cómo **preparar correctamente la geometría** para el mallado, **resolver los errores** que pueden producirse durante el mallado y **evaluar la calidad** de la malla en caso de que el solucionador se niegue a calcular la malla.

## Preparar la geometría

Antes de realizar el mallado, asegúrese de que la geometría está lo más simplificada posible. Deben realizarse [**simplificaciones de la geometría**](/geometry/geometry-simplification) generales para reducir el número de elementos y disminuir el tiempo de cálculo, pero esto no acaba aquí.

### Fusionar objetos multibloque

Si tiene una geometría que consta de varios bloques separados, conviene fusionarlos para simplificar el trabajo con la geometría y deshacerse de todas las aristas y planos innecesarios entre los bloques, que pueden dificultar el mallado más adelante.

Para fusionar bloques, haga clic en ***Operations*** → ***Boolean*** → ***Fuse***, seleccione los bloques que le interesen y haga clic en *Aplicar*.

<p align="center">

![Fuse multi-block objects](assets/mesh-troubleshoot/fuse.png)

</p>

## Solucionar los errores

Para entender cómo corregir un error de mallado, tenemos que entender cómo leer el error y prestar atención a lo que es importante.

Un error en Salome consta de tres partes:

+ **Algoritmo** - define qué argumento está asociado al error.
+ **Subforma** - define qué parte de la geometría está asociada al error.
+ **Error** - proporciona una descripción escrita del error.

<p align="center">

![Fuse multi-block objects](assets/mesh-troubleshoot/1.png)

</p>

Algunos errores son caudados por el algoritmo, otros por la geometría, por lo que es importante saber qué parte - *algoritmo* o *geometría* - es más probable que esté causando el error.

### Solución de problemas de subformas

Lo primero que hay que comprobar es qué parte de la geometría está resaltada como causa del error. Haga clic en ***Show Sub-shape*** en la esquina inferior izquierda de la ventana *Mesh Computation* - se resaltará parte de su geometría.

Si se resalta todo un dominio, es probable que el algoritmo de mallado del dominio esté mal definido.

<p align="center">

![Fuse multi-block objects](assets/mesh-troubleshoot/2.png)

</p>

Si sólo se resalta una pequeña parte de la geometría, examínela detenidamente. Los algoritmos de mallado pueden fallar debido a **detalles defectuosos en la geometría** como:

+ Aristas superpuestas.
+ Espacios estrechos entre dominios.
+ Curvaturas pequeñas.
+ Líneas innecesarias.
+ Orificios en la superficie.

En este ejemplo se produce un error debido a las líneas innecesarias dentro de la geometría.

<p align="center">

![Fuse multi-block objects](assets/mesh-troubleshoot/3.png)

</p>

### Solución de problemas de algoritmos

Si la geometría no es defectuosa, pero sigue apareciendo el error, compruebe qué tipo de algoritmo - 1D, 2D o 3D - está causando el error.

:::info Importante

Después de cada modificación del algoritmo de submalla es aconsejable **borrar los datos de la malla antes de volver a calcular** toda la malla, ya que de lo contrario puede producirse un error. Para ello, haga clic derecho en *Mesh_1* y haga clic en *Clear Mesh Data*.

:::

Si el error es causado por el **algoritmo 1D**:

1. ***Ajuste el algoritmo 1D basándose en la descripción del error*** - lo más probable es que haya dejado algo en blanco, y la descripción del error le dará la información de lo que es.

Si es **algoritmo 2D**:

1. ***Disminuir el valor Max. Length*** de la malla del dominio. Si introduce un valor *Max. Length* que es relativamente grande comparado con el tamaño de la geometría, el algoritmo de mallado se bloqueará.

2. ***Cambiar el algoritmo defectuoso*** por otro alternativo (*Triángulo: Mefisto* por *NETGEN 2D* y viceversa, por ejemplo).

Si es **algoritmo 3D**:

1. ***Comprobar si hay conflictos de estrategia de mallado***. Si elige diferentes estrategias de mallado para diferentes dominios, por ejemplo, *Tetraedralización automática* para palanquilla y *NETGEN 1D-2D-3D* para conductor, los algoritmos pueden interactuar entre sí y causar errores. El ejemplo mencionado no es el único que podría causar un error, así que asegúrese de combinar todos los dominios con los mismos algoritmos, si es posible.