---
id: billet
title: Calentamiento estático de bloques de aluminio utilizando plantillas
sidebar_label: Calentamiento de palanquillas de aluminio
---

Cuando necesite simular un caso **2D de calentamiento por inducción axial simétrica** con palanquilla y bobina de forma estándar y regular, es conveniente utilizar **plantillas de calentamiento por inducción**.

En este tutorial aprenderá a configurar y utilizar las Plantillas de Calentamiento por Inducción para la simulación 2D axial simétrica de una varilla cilíndrica con una bobina de perfil rectangular. Crearemos la geometría eligiendo una de las plantillas disponibles para cada dominio, definiremos la calidad de la malla, introduciremos los valores específicos y las condiciones de contorno en la configuración física y al final evaluaremos los resultados utilizando nuestro post-procesador.

Induction Heating Template es una forma fácil y rápida de configurar y calcular casos de calentamiento por inducción para geometrías estándar. En las páginas siguientes se presenta un ejemplo de calentamiento por inducción de **bloque de aluminio** a **15 kHz** y **2 kA** con condiciones límite de radiación y convección.

<p align="center">

![Diagram](assets/billet/0.png)

</p>

## 1. Abrir plantillas

Para entrar en las plantillas de geometría, en la ventana de inicio de CENOS haga clic en **Template**.

![Open template](assets/billet/1.1.png)

**Template define automáticamente las partes no críticas de la configuración de la simulación** y ofrece a los nuevos usuarios unos **valores físicos y geométricos de simulación preestablecidos**, por lo que sólo hay que cambiar los parámetros que ya están ahí.

## 2. Crear geometría

### 2.1 Unidades y malla

Puede **definir las unidades del caso** en la esquina inferior izquierda de la pantalla *Crear Geometría*. Para este tutorial, deje *milímetros* como unidades de caso.

<p align="center">

![Common properties](assets/billet/2.1.1.png)

</p>

Si desea **cambiar la densidad de la malla**, haga clic en SHOW MESH OPTIONS.

<p align="center">

![SHOW MESH OPTIONS](assets/billet/2.1.2.png)

</p>

A continuación, elija en el menú desplegable la *densidad de malla*.

<p align="center">

![Mesh density](assets/billet/2.1.3.png)

</p>

:::info Importante

Cuando se utilizan plantillas, la malla se genera automáticamente antes de iniciar el cálculo. Con *densidad de malla* se define lo fina o gruesa que será la malla.

:::

### 2.2 Geometría de la pieza de trabajo

Cambie al dominio WORKPIECE. Seleccione **Billet** para la *forma*.

<p align="center">

![Billet](assets/billet/2.2.1.png)

</p>

En *Propiedades* introduzca **0,02** para *Diámetro* y **0,2** para *Altura*.

<p align="center">

![Workpiece properties](assets/billet/2.2.2.png)

</p>

### 2.3 Geometría del inductor

Cambie al dominio INDUCTOR. Seleccione **Perfil rectangular** para la *forma*.

<p align="center">

![Rectangular profile with flux concentrator](assets/billet/2.3.1.png)

</p>

En *Propiedades* asegúrese de que la casilla *Hollow coil* esté marcada e introduzca los valores para la bobina y el concentrador de la siguiente manera:

<p align="center">

![Inductor and concentrator properties](assets/billet/2.3.2.png)

</p>

Una vez establecida la geometría, haga clic en **Go to PHYSICS** en la esquina superior derecha de la ventana.

<p align="center">

![Inductor and concentrator properties](assets/billet/2.3.3.png)

</p>

## 3. Definir la física

:::nota Importante

Parte de la ventana está pintada de gris, lo que significa que todos los ajustes de la zona gris están preconfigurados para esta plantilla específica, dejando sólo los ajustes principales a su criterio.

:::

Si desea **editar los ajustes de la zona gris**, active **Editar todas las propiedades**.

<p align="center">

![Edit all properties](assets/billet/3.0.png)

</p>

### 3.1 Control de la simulación

En la ventana de CONTROL DE LA SIMULACIÓN puede acceder y **definir los parámetros globales de la simulación**, como la frecuencia, el tiempo de cálculo, el paso de tiempo, los algoritmos de cálculo y muchos más.

Defina la simulación como *Transient* con **15 kHz** en *frequencia*, **20 s** en *tiempo final* y **2 s** en *paso de tiempo*.

<p align="center">

![Simulation control](assets/billet/3.1.1.png)

</p>

### 3.2 Definición de la pieza de trabajo

Cambie a WORKPIECE en *Barra de dominio*. En *Material*, haga clic en SELECCT... y elija **Acero bajo en carbono 1020 B(H), $t^{o}$ dependiente**.

<p align="center">

![Simulation control](assets/billet/3.2.1.png)

</p>

En ANÁLISIS TÉRMICO deje el valor por defecto **10** para *Coeficiente de Transferencia de Calor*, pero cambie *Emisividad* a **0,3**.

![Thermal analysis](assets/billet/3.2.2.png)

### 3.3 Definición de la bobina

Cambie a WINDING_0.. en *Domain bar*. Seleccione **Cobre** como material.

<p align="center">

![Simulation control](assets/billet/3.2.3.png)

</p>

Introduzca **2000 A** para *Corriente (Amplitud)*.

<p align="center">

![Inductor definition](assets/billet/3.3.1.png)

</p>

### 3.4 Definición del concentrador

Cambie a CONCENTRADOR en *Domain bar*. Para *Material* seleccione **Concentrador de flujo FLUXTROL A**. 

<p align="center">

![Concentrator definition](assets/billet/3.4.1.png)

</p>


La definición física para el dominio aire se establece de forma totalmente automática, por lo que después de definir los dominios concentrador y conductor, **haga clic en RUN** en la esquina superior derecha de la ventana.

## 4. Evaluar resultados

Al final del cálculo, la herramienta de postprocesado *ParaView* se **abrirá automáticamente con un estado de temperatura preestablecido**, y podrá ver la **distribución del campo de temperatura** en la pieza en el último paso de tiempo.

![Temperature distribution](assets/billet/4.1.1.png)

Los resultados pueden manipularse aún más utilizando los filtros de ParaView - obtenga más información en el artículo de CENOS [**evaluación de resultados**](/results).

Con esto finaliza nuestro tutorial de Plantilla de Calentamiento por Inducción. Para cualquier recomendación o pregunta contacte a nuestro soporte.