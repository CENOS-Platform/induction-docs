---
id: parametric-geometry
title: Cómo parametrizar la geometría
sidebar_label: Geometría Paramétrica
sidebar_position: 1
---

Las simulaciones de calentamiento por inducción son una gran herramienta para encontrar los parámetros adecuados para el perfil de calentamiento deseado, desde los valores de corriente y frecuencia hasta la posición del inductor respecto a la pieza de trabajo.

En la plataforma CENOS es posible crear un **modelo paramétrico** y **cambiar los valores geométricos previamente definidos**, como la posición del inductor, el tamaño del bobinado, etc.

Sin valores paramétricos, cada modificación de la geometría requiere la creación de un nuevo modelo de simulación desde el principio, lo que puede llevar mucho tiempo. **Si el modelo es paramétrico, las modificaciones de la geometría sólo requieren el cambio de un parámetro como el radio de la bobina y la exportación de la nueva malla.**

## ¿Cuándo utilizar geometrías paramétricas?

La parametrización de geometrías es útil cuando se **busca la posición correcta** entre la pieza y los devanados de la bobina para conseguir el perfil de calentamiento óptimo dentro de la pieza de trabajo.

En el ejemplo siguiente se muestra una configuración estándar de bobina-pieza con 3 parámetros ajustables: radio de la bobina, radio del devanado y paso entre los devanados.

<p align="center">

![Simple parameters](assets/parametric-geometry/1.png)

</p>

## ¿Cómo crear un modelo paramétrico?

Primero tiene que decidir qué parámetro quiere hacer paramétrico. Entonces debe crear un nuevo parámetro y e implementarlo durante el proceso de construcción de la geometría.

En los siguientes pasos aprenderemos a crear un modelo geométrico 2D con un diámetro de bobina ajustable.

### 1. Crear un nuevo parámetro variable

Las variables en Salome se definen a través de *NoteBook*, al que se accede pulsando el botón *NoteBook* bajo *Object Browser*.

<p align="center">

![Simple parameters](assets/parametric-geometry/2.png)

</p>

En la ventana *NoteBook* introduzca los nombres y valores de las variables que va a utilizar en su modelo. En este ejemplo crearemos una variable llamada *winding_radius (radio_devanado)* y le asignaremos un valor específico.

<p align="center">

![Simple parameters](assets/parametric-geometry/3.png)

</p>

### 2. Implementar variables en la geometría

**Las variables se implementan en la geometría utilizándolas para definir parámetros relacionados con la creación de formas primitivas, operaciones de traslación y otras acciones de creación/modificación de la geometría.**

Si queremos definir el diámetro del devanado de la bobina, primero debemos pensar en cómo crear los devanados. La forma más fácil es crear un círculo base para el bobinado superior y luego utilizar la herramienta *Multi-Translation* para crear el resto.

**Dado que el tamaño del círculo en la herramienta de construcción de círculos se define a través del radio, podemos implementar la variable diámetro a través del tamaño del radio** en la creación del círculo base del bobinado superior. Para ello, creamos el círculo con la herramienta *Circle Construction*, pero en la casilla *Radius* no escribimos un número concreto, sino el nombre de la variable que creamos anteriormente - *winding_radius*.

<p align="center">

![Simple parameters](assets/parametric-geometry/4.png)

</p>

:::caution IMPORTANTE

Para implementar eficientemente las variables en la geometría, primero debe entender cómo crear el aspecto geométrico específico del modelo y donde se utilizará la variable de interés.

:::

### 3. Cambiar la geometría

Cuando el resto del modelo haya sido creado y particionado, puede volver al *NoteBook* y cambiar el parámetro especificado anteriormente. Después de cambiar el valor, haga clic en **Update Study** para actualizar los datos y evalúe la nueva geometría.

<p align="center">

![Simple parameters](assets/parametric-geometry/5.png)

</p>

Después de **actualizar el estudio** la geometría parametrizada cambiará, así como la geometría y la malla construidas a partir de ella.

<p align="center">

![Simple parameters](assets/parametric-geometry/6.png)

</p>

:::caution IMPORTANTE

¡Tras el cambio de parámetros y la actualización del estudio, es necesario **cambiar al módulo Mesh y exportar la nueva malla** a CENOS antes de recalcular la simulación!

:::

## Limitaciones

Aunque es una forma eficaz de cambiar rápidamente la geometría, hay que tener en cuenta una serie de cosas a la hora de crear un modelo paramétrico.

### Número paramétrico de objetos

Mientras que hacer paramétricos los tamaños y las distancias en tu modelo te permitirá modificar tu geometría con sólo unas pocas acciones, otros parámetros pueden tardar más en cambiar.

:::caution IMPORTANTE

El cambio de parámetros que definen un número de objetos, no su tamaño, requerirá un nuevo grupo y una nueva malla para cada modificación.

:::

Por ejemplo, si usted crea un parámetro para el número de devanados, esencialmente **cambiará el número de objetos** en su partición cada vez que lo cambie. Esto significa que creará conflictos en los grupos antiguos, por lo que tendrá que volver a crear los grupos cada vez que cambies el número de devanados.

Aunque la malla se re-calculará a sí misma, todavía tendrá que dedicar tiempo adicional para asegurarse de que todo con los grupos y la malla está correctamente definido/creado.

### Superposición de la geometría

**Al cambiar los valores de los parámetros, la geometría puede dejar de ser física**, es decir, dominios como la pieza de trabajo y la bobina o los propios devanados de la bobina pueden solaparse entre sí - ¡evite estas situaciones y compruebe siempre la geometría después de cada actualización del estudio!

En el ejemplo de la parametrización del diámetro del devanado de la bobina, si el *radio_devanado* se define como mayor de 10, los devanados se solaparán entre sí.

Esto a su vez puede causar problemas en el mallado y en el cálculo de la simulación, ya que no es físicamente correcto.

<p align="center">

![Simple parameters](assets/parametric-geometry/7.png)

</p>
