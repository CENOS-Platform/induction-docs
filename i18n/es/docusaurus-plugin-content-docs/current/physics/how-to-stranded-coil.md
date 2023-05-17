---
id: stranded-coil
title: Bobina trenzada/Hilo de Litz
sidebar_label: Bobina trenzada/Hilo de Litz
sidebar_position: 1
---

En el proceso de calentamiento por inducción se utilizan muchas bobinas e inductores diferentes, uno de los cuales es la bobina trenzada. Por bobina trenzada se entiende una **bobina formada por muchas vueltas finas de alambres conductores**.

El análisis electromagnético de una bobina trenzada puede ser complicado, porque la geometría de la bobina es compleja. CENOS le ofrece la ventaja de **definir una bobina sólida como trenzada** mediante un tipo de dominio específico, y facilitar la simulación de la misma al mínimo. CENOS le permite definir y simular un tipo específico de bobina trenzada, denominada **hilo Litz**.

<p align="center">

![Stranded coil](assets/stranded-coil/1.1.png)
![Litz wire](assets/stranded-coil/1.png)

</p>

## ¿Cuándo utilizar el dominio de bobina trenzada?

El tipo de dominio *Bobina Trnzada - Stranded Coil* puede utilizarse en **simulaciones 2D y 3D** de bobinas trenzadas en las que el **número de trenzados es demasiado alto para resolverlos eficientemente a través de la geometría**.

Con la definición del tipo *dominio de bobina trenzada* no sólo puede **reducir el número de elementos de malla y el tiempo de cálculo** de su simulación, sino también **facilitar el proceso de creación de geometría**, creando una bobina sólida y definiéndola como trenzada, sin necesidad de crear manualmente cada filamento.

:::info Importante

Basta con **sustituir la bobina trenzada por una forma de sección transversal de tamaño equivalente**, definirla como *fuente de bobina trenzada* y ¡calcular!

:::

<p align="center">

![Stranded coil source properties](assets/stranded-coil/2.png)

</p>

## ¿Cómo utilizar una bobina trenzada?

Puede acceder fácilmente al dominio *Stranded Coil Source* en el menú desplegable de *tipo de dominio*.

<p align="center">

![Stranded coil source properties](assets/stranded-coil/3.png)

</p>

Cuando se ha seleccionado *Stranded Coil Source*, aparecerán las  *propiedades de dominio*, que constan de 4 parámetros - *Corriente (Amplitud)* o *Voltaje* (sólo para 2D), *Número de vueltas*, *Factor de llenado* y *Área de sección transversal* (específico sólo para definiciones 3D).

<p align="center">

![Stranded coil source properties](assets/stranded-coil/4.png)

</p>

*Número de vueltas*, *Factor de llenado* y *Área de sección transversal* son parámetros específicos de los filamentos, que se utilizan para **definir la distribución geométrica de los filamentos sobre el inductor sólido**.

Si desea simular un inductor con *alambre Litz*, simplemente marque la casilla *Litz wire*.

<p align="center">

![Stranded coil source properties](assets/stranded-coil/4.3.png)

</p>

### Corriente

La definición de corriente depende del tipo de bobina trenzada que esté utilizando. 

La corriente que defina cuando utilice sólo el tipo de dominio *Fuente de Corriente Trenzada* es **corriente en una hebra**.

+ **Ejemplo**: Si desea cambiar de un inductor sólido con una corriente de 1000 A a una *bobina trenzada simple* con 10 hilos y una corriente total de 1000 A, deberá introducir 100 A en la casilla *Current (Amplitude)*.

<p align="center">

![Stranded coil source properties](assets/stranded-coil/4.4.png)

</p>

Si ha marcado la casilla **Litz wire**, entonces la **corriente total será igual a la corriente en cada filamento**, ya que los filamentos están conectados entre sí en los extremos.

+ **Ejemplo**: Si desea pasar de un inductor sólido con una corriente de 1000 A a un *hilo Litz* con 10 filamentos y una corriente total de 1000 A, entonces deberá introducir 1000 A en la casilla *Current (Amplitude)*.

<p align="center">

![Stranded coil source properties](assets/stranded-coil/4.5.png)

</p>

Al revisar los resultados dentro del archivo .cvs generado por Cenos.

**Para bobina trenzada**: 
Verá los resultados para cada filamento (corriente, resistencia, etc)

**Para alambre Litz**:
Verá los resultados de todo el inductor.

### Número de vueltas

Cada filamento de una bobina se denomina vuelta. Con *Número de vueltas* define **cuántas hebras** tiene su bobina.

<p align="center">

![Stranded coil source properties](assets/stranded-coil/5.png)

</p>

### Factor de llenado/Área de sección transversal

*El Factor de Llenado* define **qué parte del área sólida del inductor está ocupada por filamentos**.

*El Área de Sección Transversal define el área total ocupada por los filamentos.

Por ejemplo, si se define un cuadrado de 10x10 mm como *fuente de bobina trenzada* (área en azul) con 1 vuelta y un radio de 5 mm, el *factor de llenado* y el *área de sección transversal* (área en verde) podrían calcularse como sigue:

<p align="center">

![Stranded coil source properties](assets/stranded-coil/6.png)

</p>

### Malla

El dominio *fuente de bobina trenzada* permite no sólo simplificar la geometría, sino también ahorrar en el número de elementos. Si utilizas este dominio, **no necesitas resolver la capa de piel** como harías si utilizaras el dominio simple *Current Source*. 

:::caution Importante

¡Asegúrese de que la malla en el dominio *Fuente de bobina trenzada* sea uniforme!

:::

<p align="center">

![Stranded coil source properties](assets/stranded-coil/8.png)

</p>
