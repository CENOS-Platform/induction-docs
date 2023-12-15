---
id: shaft-scanning
title: Endurecimiento por barrido de un eje estriado
sidebar_label: Endurecimiento por barrido de un eje estriado
---

*Ejes*, *cremalleras de dirección*, *engranajes helicoidales* y otras piezas mecánicas largas o extendidas están siendo ampliamente utilizadas en áreas de **automoción**, **aeroespacial** y muchas otras industrias en diferentes montajes mecánicos.

Para fabricar estas piezas, es necesario **endurecerlas para mejorar la dureza y la resistencia al desgaste**, y para **aumentar la vida útil a la fatiga**. La mejor forma de endurecer estas piezas es mediante el **endurecimiento por inducción**. Proporciona un **endurecimiento selectivo**, que **aumenta la eficacia del sistema** y **disminuye las distorsiones térmicas** de la pieza.

En este artículo vamos a **aprender a construir un sencillo proceso de endurecimiento por escaneado de un eje estriado** utilizando el software de simulación *CENOS Induction Heating*.

La configuración consiste en un **inductor de 2 devanados** y un **eje de acero de bajo contenido en carbono AISI 1020**. En la simulación se consideran **4 kHz de frecuencia** y **11 kA de corriente**, así como **pérdidas térmicas** del eje.

<p align="center">

![shaft scanning](assets/shaft-scanning/shaft.gif)

</p>

:::note Archivos de aplicación

Descargue los archivos CAD utilizados en este tutorial [**aquí**](assets/shaft-scanning/SplinedShaft.zip)

:::


## 1. Prepare su geometría

La geometría es el principio y la piedra angular de toda simulación, así que tenemos que **empezar por preparar nuestra geometría** para la simulación.

### 1.1 Importar los archivos CAD

Primero tenemos que seleccionar el enfoque de creación de geometría. En la ventana de inicio de CENOS, haga clic en **From CAD**.

<p align="center">

![shaft scanning](assets/shaft-scanning/1.png)

</p>

Haga clic en el ícono de **carpeta** para seleccionar los archivos CAD que desea importar.

<p align="center">

![shaft scanning](assets/shaft-scanning/2.png)

</p>

**Seleccione los archivos STEP** de su sistema y pulse **Abrir** para importarlos a CENOS.

<p align="center">

![shaft scanning](assets/shaft-scanning/3.png)

</p>

:::note Nota 

Para este ejemplo hemos importado 2 archivos STEP diferentes. También puede importar ambos en un único archivo STEP (ensamblaje), ¡realmente no hay ninguna diferencia en la simulación!

:::

### 1.2 Generar caja de aire

Una vez cargados los archivos CAD, CENOS le preguntará si desea generar automáticamente la caja de aire (entorno ambiental alrededor de su sistema). Haga clic en **Yes** y, a continuación, en **CONTINUE**.

<p align="center">

![shaft scanning](assets/shaft-scanning/4.png)

</p>

**Seleccione los terminales de su inductor** como referencia y haga clic en **CREATE AIR** para generar automáticamente la caja de aire.

<p align="center">

![shaft scanning](assets/shaft-scanning/5.png)

</p>

### 1.3 Definir grupos

Una vez generada la caja de aire, será redirigido a la ventana de creación de grupos. Aquí verá una **lista de grupos que necesita definir** para Su sistema, como cuál es la pieza de trabajo, dónde están los terminales del inductor, etc.

<p align="center">

![shaft scanning](assets/shaft-scanning/6.png)

</p>

**Seleccione el grupo** (en este ejemplo, *workpiece*), **seleccione el volumen correspondiente a la pieza de trabajo** de la lista o directamente de la pantalla, y haga clic en **ASSIGN Workpiece**.

<p align="center">

![shaft scanning](assets/shaft-scanning/7.png)

</p>

Define del mismo modo el resto de los grupos.

<p align="center">

![shaft scanning](assets/shaft-scanning/8.png)

</p>

:::note Nota

Puedes **cambiar el nombre de cada grupo** haciendo clic en el botón *editar* situado junto al nombre.

<p align="center">

![shaft scanning](assets/shaft-scanning/9.png)

</p>

:::

Una vez listo, haz clic en **GO TO PHYSICS** para ver la definición de física.

<p align="center">

![shaft scanning](assets/shaft-scanning/10.png)

</p>

## 2. Definir la física

Será redirigido a la ventana *Física*, donde están las definiciones físicas. A la izquierda puedes ver la **ventana de vista previa** de su geometría, del lado derecho observará las **definiciones físicas** correspondientes. Puede **navegar por los paámetros de física a través de las pestañas de dominio** encima de las definiciones físicas.

<p align="center">

![shaft scanning](assets/shaft-scanning/11.png)

</p>

### 2.1 Control de la simulación

En la ventana de SIMULATION CONTROL defina la simulación como *transitoria* con **4 kHz** en *frecuencia*, **17 s** en *tiempo final* y **0,25 s** en *pasos de tiempo*. Para *Algoritmo de cálculo* elija **Fast**.

<p align="center">

![shaft scanning](assets/shaft-scanning/12.png)

![shaft scanning](assets/shaft-scanning/13.png)

</p>

### 2.2 Eje estriado

Seleccione SHAFT en la barra *Dominio*. En *Material*, haga clic en SELECT... y elija **Acero bajo en carbono 1020 (B(H), $t^{o}$dependiente)**.

<p align="center">

![shaft scanning](assets/shaft-scanning/14.png)

</p>

En ANÁLISIS TÉRMICO para **WORKPIECE SURFACE1** elija **Combinado** - marque las casillas **Convection** y **Radiation** e introduzca **15** para *Convección* y **0,8** para *Radiación*.

<p align="center">

![shaft scanning](assets/shaft-scanning/15.png)

</p>

### 2.3 Inductor

Cambie a INDUCTOR en *Barra de dominio*. Para *Material* elija **Cobre (dependiente de la temperatura)**.

<p align="center">

![shaft scanning](assets/shaft-scanning/16.png)

</p>

En ELECTROMAGNETICS elija **Current (Amplitude)** para TERMINAL1, **Ground** para TERMINAL2 e introduzca **11000 A** como *Corriente (Amplitud)*.

<p align="center">

![shaft scanning](assets/shaft-scanning/17.png)

</p>

### 2.4 Escaneo

Cambie a la pestaña MOTION y haga clic en CREATE NEW MOTION para agregar movimiento.

<p align="center">

![shaft scanning](assets/shaft-scanning/18.png)

</p>

Seleccione **Complex motion** como tipo de movimiento, **Inductor** como dominio que desea mover, e introduzca una velocidad de movimiento de **0,01 m/s** en la dirección Y.

<p align="center">

![shaft scanning](assets/shaft-scanning/19.png)

</p>

¡Con la definición de Movimiento ha terminado la configuración de la física! Haga clic en **RUN** para calcular su simulación.


<p align="center">

![shaft scanning](assets/shaft-scanning/20.png)

</p>

## 3. Evaluar resultados

Al final del cálculo, nuestra herramienta de postprocesado *ParaView* se **abrirá automáticamente con un estado de temperatura preestablecido**, y podrá ver la **distribución del campo de temperatura** en la pieza en el último paso temporal.

<p align="center">

![shaft scanning](assets/shaft-scanning/21.png)

</p>

Los resultados pueden manipularse aún más utilizando los filtros de ParaView - obtenga más información en el artículo de CENOS [**evaluación de resultados**](/results).

Esto concluye nuestro tutorial de Endurecimiento de Escaneo de Ejes Estriados. Para cualquier recomendación o pregunta contacte con nuestro equipo de soporte.