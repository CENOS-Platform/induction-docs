---
id: templates
title: Plantillas
sidebar_label: Plantillas
sidebar_position: 2
---

La simulación consiste en crear la **geometría** y su **malla**, definir los **parámetros físicos** y, tras realizar los cálculos, **postprocesar** los resultados en cantidades y gráficos adecuados.

Si usted es **nuevo en la simulación** y en CENOS, le sugerimos que **comience con las plantillas de geometría predefinidas**, ya que se centrarán más en la estructura y los fundamentos de la simulación.

También puede utilizar su archivo CAD o crear la geometría desde cero.

## Seleccionar el enfoque de construcción geométrica

Para utilizar plantillas de geometría, haga clic en **Template** en la ventana de inicio de CENOS.

<p align="center">

![Select Template](assets/templates/Template1.png)

</p>

**Las plantillas definen automáticamente las partes no críticas de la configuración de la simulación** y ofrecen a los nuevos usuarios un **preajuste de los valores físicos y geométricos de la simulación** para hacerse una idea de cómo se definen las simulaciones, para dejarle al usuario sólo las decisiones importantes.

<p align="center">

![Select Template](assets/templates/2.png)

</p>

### Definir las unidades

En la ventana *Create Geometry*, en la esquina inferior izquierda, haga clic en **seleccionar unidades de su geometría**. 

<p align="center">

![Select Template](assets/templates/3.png)

</p>

### Elegir plantilla

En las pestañas WORKPIECE e INDUCTOR **elija la geometría de plantilla** que se adapte mejor a su sistema para los dominios de simulación.

<p align="center">

![Select Template](assets/templates/4.png)

</p>

<p align="center">

![Select Template](assets/templates/5.png)

</p>

### Introducir propiedades geométricas

Introduzca las propiedades geométricas, tales como diámetro, altura, grosor, etc. para **definir su geometría**.

:::tip
**Para saber cómo introducir las propiedades geométricas, observe el esquema que se encuentra del lado derecho**.
:::

<p align="center">

![Select Template](assets/templates/6.png)

</p>

Cuando haya terminado, **cambie a la configuración de física** haciendo clic en *GO TO PHYSICS* en la esquina superior derecha de la pantalla.

<p align="center">

![Select Template](assets/templates/7.png)

</p>

## Definir parámetros de simulación

### Ingresar parámetros físicos

En la ventana CONTROL DE SIMULACIÓN **defina los parámetros globales** como *frecuencia*, *tiempo de cálculo*, etc.

<p align="center">

![Select Template](assets/templates/8.png)

</p>

En las ventanas de DOMINIO DE SIMULACIÓN como *WORKPIECE* y *WINDINGS* **defina los parámetros físicos de cada dominio** tales como *material*, *intercambio de calor*, *corriente* etc.

<p align="center">

![Select Template](assets/templates/9.png)

</p>

### Ejecutar simulación

Una vez configurada la simulación, **haga clic en RUN** en la esquina superior derecha de la pantalla de CENOS.

<p align="center">

![Select Template](assets/templates/10.png)

</p>

## Post-procesamiento

Al final de los cálculos, la herramienta de postprocesamiento *ParaView* se **abrirá automáticamente con un estado de temperatura preestablecido**, y podrás ver la **distribución del campo de temperatura** en la pieza en el último paso de tiempo.

<p align="center">

![Select Template](assets/templates/11.png)

</p>

Para **aprender más** sobre las manipulaciones de resultados, visite nuestra [**evaluación de resultados**](/results).

### Valores integrales

Para valores integrales como **potencia aparente, calor inducido y tensión compleja** puedes utilizar el archivo .csv, que viene junto con los resultados visuales. Puedes acceder a él a través del botón *Nota* situado junto al botón *Play* del bloque *Visualization*.

<p align="center">

![Select Template](assets/templates/12.png)

</p>
