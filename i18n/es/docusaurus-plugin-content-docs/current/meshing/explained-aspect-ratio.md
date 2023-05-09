---
id: aspect-ratio
title: Relación de aspecto
sidebar_label: Relación de aspecto
sidebar_position: 3
---

Hay muchas formas diferentes de evaluar la calidad de la malla, una de ellas es la *relación de aspecto*. En este artículo aprenderemos qué es realmente la *relación de aspecto* y cómo resolver los errores causados por elementos de alta relación de aspecto.

<p align="center">

![FElements](assets/aspect-ratio/10.png)

</p>

## ¿Qué es la relación de aspecto?

*La relación de aspecto es la medida de la desviación de un elemento de malla de tener todos los lados de igual longitud. Una relación de aspecto alta se produce en elementos largos y delgados, lo que **puede provocar que el solucionador se bloquee durante el cálculo**. Por esta razón, CENOS realiza una comprobación para asegurarse de que la malla no tiene elementos con una relación de aspecto elevada, lo que podría provocar errores de cálculo.

*La relación de aspecto* suele ser baja en las mallas de aire (alrededor de 1) y alta en las capas viscosas (hasta 1000). **Si la relación de aspecto de algunos elementos es superior a 10 000, la comprobación integrada de CENOS no permitirá al usuario utilizar dicha malla.

## Errores de relación de aspecto

En algún momento, casi todos los ingenieros de simulación se toparán con un error causado por elementos de malla de alta relación de aspecto. Estos errores ocurren sobre todo en mallas 3D, y por ello necesitamos entender cómo se presenta este error en los dos enfoques de creación de geometría 3D disponibles en CENOS - *From CAD* y *Advanced Geometry Editor*.

### From CAD

*From CAD* crea mallas automáticamente para la geometría que ha importado, basándose en los parámetros físicos introducidos en la parte *Física*. Como el mallado se hace automáticamente, los algoritmos de **malla pueden fallar a veces en geometrías más complejas**. Para ver si la malla se ha generado correctamente, es necesario calcularla antes de ejecutar la simulación.

Para ello, es necesario **introducir primero los parámetros físicos** de la simulación y, a continuación, volver a la geometría y hacer clic en *SHOW MESH OPTIONS* en la parte inferior de la pantalla.

<p align="center">

![FElements](assets/aspect-ratio/1.png)

</p>

En las opciones de malla, en *Configuración Avanzada*, haga clic en *CREATE AUTOMATIC MESH NOW*.

<p align="center">

![FElements](assets/aspect-ratio/2.png)

</p>

CENOS generará la malla y le indicará si se ha creado correctamente. El error más común está relacionado con elementos de alta relación de aspecto: si hay elementos de este tipo en una malla generada automáticamente, aparecerá un mensaje.

<p align="center">

![FElements](assets/aspect-ratio/3.png)

</p>

Este error significa que **CENOS no utilizará la malla generada automáticamente** y **tiene que crearla manualmente**. Para ello, haga clic en OPEN ADVANCED EDITOR, que le enviará a la geometría de CENOS y al programa de creación de mallas: Salomé. Ahí usted podrá ajustar o crear manualmente la malla para eliminar los elementos de alta relación de aspecto.

### Editor de geometría avanzada

Cuando se utiliza el *Editor de Geometría Avanzado*, puede aparecer un error detallando elementos de *Alta Relación de Aspecto* justo antes de intentar exportar la malla a CENOS.

<p align="center">

![FElements](assets/aspect-ratio/4.png)

</p>

Si ve un error de este tipo, significa que debe volver a comprobar las definiciones de malla y ajustarlas para eliminar los elementos con una relación de aspecto elevada.

## Cómo encontrar elementos con alta relación de aspecto

A veces los elementos problemáticos son pequeños y difíciles de notar desde la distancia, por lo tanto **CENOS crea automáticamente un grupo con estos elementos problemáticos**, que puede visualizar por separado para entender en qué parte de la malla están presentes.

Puede encontrar este grupo llamado **Aspect ratio error elements** en *Groups of Faces/Volumes*.

<p align="center">

![FElements](assets/aspect-ratio/11.png)

</p>

- Haga clic en el icono *Ojo* (![Eye icon](assets/aspect-ratio/9.png)) para activar la visibilidad de los *Elementos de error de relación de aspecto* y desactivar la visibilidad de *Malla_1*.

Los elementos de malla con alta relación de aspecto se harán visibles. **Si no puede ver los elementos de la malla**, haga clic en la pantalla de visualización de la malla y pulse *barra espaciadora* en el teclado.

<p align="center">

![FElements](assets/aspect-ratio/10.png)

</p>

## Cómo corregir los elementos de relación de aspecto elevada

Una vez localizados los elementos de alta relación de aspecto, puede empezar a eliminarlos. Primero necesita **entender visualmente en qué parte (sub-malla) están presentes estos elementos**. Después necesita **ajustar la definición de la malla para que estos elementos desaparezcan**.

Si los elementos de relación de aspecto alta están **ubicados en las capas viscosas** de la pieza de trabajo o en el inductor:

* Disminuir el *Número de Capas* (si es posible);
* Disminuir el *Factor de Estiramiento*;
* Disminuir el *Tamaño Máximo* de toda la sub-malla.

Si estos elementos se encuentran en el dominio del aire o en cualquier sub-malla, pero **no en las capas viscosas**:

* Disminuir el *Tamaño Máximo* para toda la submalla;
* Cambiar el algoritmo de malla 2D de *Trinagle: Mefisto* a *NETGEN 2D* (o viceversa).

Si sigue sin poder resolver el error de relación de aspecto elevada, ¡póngase en contacto con nuestro servicio de soporte!