---
id: tips
title: Trucos y consejos para usuarios nuevos
sidebar_label: Trucos y Consejos
sidebar_position: 4
---


Como nuevo usuario de CENOS, la información que necesita saber sobre simulaciones, su configuración, resolución de problemas y muchas otras cosas puede ser realmente abrumadora. La mayoría de estas cosas las aprenderá a medida que progrese a través de tutoriales y sus proyectos personales, pero algunas no son tan sencillas. 

En este artículo revisaremos los **errores más comunes de los usuarios principiantes**, que debería tener en cuenta si quiere crear una simulación de éxito.

**NOTA**: Aunque estos consejos son útiles para evitar dolores de cabeza innecesarios sobre por qué la simulación no funciona, le aconsejamos **programar una reunión/entrenamiento con nuestros ingenieros** para hablar sobre la configuración de la simulación en detalle y responder a cualquier pregunta o confusión que pueda tener.

Dado que se cometen diferentes errores en distintas partes de la configuración de la simulación, dividiremos los consejos en **tres categorías**:

- Geometría
- Malla
- Física

## Geometría

Toda simulación comienza con una geometría. Si no ha simplificado la geometría, ajustado la calidad de su modelo CAD o se ha asegurado de que el posicionamiento es correcto, le costará mucho que la simulación funcione.

### Calidad del archivo CAD

Antes de crear una simulación, asegúrese de que su archivo CAD es apto para la simulación. Más información sobre [**cómo crear un buen CAD**](/geometry/good-cad) para la simulación de calentamiento por inducción.

**Elimine todos los huecos, curvaturas y otros detalles pequeños** que no sean relevantes para la simulación para facilitar el mallado y reducir el tiempo de cálculo. **Evite construir su geometría a partir de volúmenes más pequeños**, y fusiónelos siempre antes de importarlos a CENOS.

**Elimine los sobreposicionamientos y huecos** y asegúrese de que su geometría es continua.

<p align="center">

![CAD quality](assets/tips/1.png)

</p>

### Simetría

Utilice la simetría de su geometría y [**simule sólo parte de la geometría completa**](/geometry/geometry-simplification) para disminuir el tiempo de cálculo. Para simular simetría, utilice [**condiciones de frontera de simetría**](/physics/symmetry) disponible en CENOS.

<p align="center">

![CAD quality](assets/tips/2.png)

</p>

### Tamaño de la caja de aire

La caja de aire se utiliza para el cálculo del campo EM, y el [**tamaño de la caja de aire**](/geometry/air-domain-size) puede afectar directamente a los resultados de la simulación.

No cree la caja de aire demasiado pequeña, de lo contrario los resultados podrían ser incorrectos. Una buena regla es hacer el dominio de aire alrededor de **3 veces más grande** que el sistema de inducción en él en cada dirección.

<p align="center">

![CAD quality](assets/tips/3.png)

</p>

### Colocación de los terminales

Si está construyendo una simulación 3D, recuerde que **los terminales del inductor deben estar siempre en el mismo plano que uno de los lados de la caja de aire**.

<p align="center">

![CAD quality](assets/tips/4.png)

</p>

### Eje de rotación

Si está utilizando *Motion* para definir la rotación de una pieza totalmente axial-simétrica, el eje de rotación debe ser el **eje Z**.

Si está creando una geometría 2D axial-simétrica, recuerde que el eje de simetría debe ser el **eje Y**.
    
<p align="center">

![CAD quality](assets/tips/5.png)

</p>

## Malla

Los consejos para el mallado son útiles para aquellos que quieran comenzar con el*Editor Avanzado*, ya que el resto de enfoques de simulación crean la malla automáticamente.

### Efecto piel

Cree siempre una **resolución adecuada para las capas de efecto piel** en el inductor y la pieza de trabajo, sin capas viscosas en la malla, los resultados electromagnéticos y térmicos de la simulación serán incorrectos.

<p align="center">

![CAD quality](assets/tips/7.png)

</p>

### Tamaño de la malla

Preste mucha atención al tamaño de la malla, especialmente para simulaciones 3D. **Si el número de elementos supera los 300,000**, considere la posibilidad de simplificar la simulación mediante la geometría o la simetría, ya que las simulaciones con una malla grande tardarán **mucho más en calcularse**.

<p align="center">

![CAD quality](assets/tips/8.png)

</p>

## Física
 
### Amplitude de la corriente
 
Aquellos que calculan con corriente como su entrada de potencia, deben recordar que la **corriente definida en CENOS es la corrinete pico, no corriente RMS**.
 
<p align="center">

![CAD quality](assets/tips/9.png)

</p>

:::note Nota 

Si conoce el valor eficaz de la corriente (RMS) que circula por su inductor, debe multiplicarlo por la raíz cuadrada de dos antes de introducirlo en CENOS.

$$
\sqrt {2} I_{RMS}=I_{Amplitude}
$$

:::

### Simetría en *From CAD
 
Si está utilizando el enfoque *From CAD* para simular casos de simetría, recuerde que **la generación automática de cajas de aire funciona sólo para geometrías completas**, lo que significa que para casos de simetría tiene que crear e **importar aire como un archivo CAD** con el resto de su geometría.
 
<p align="center">

![CAD quality](assets/tips/11.png)

</p>

### Definición de simetría
 
 Si está calculando un caso de simetría, no olvide **cambiar la definición de simetría** de *Full 3D model* a *Slice* e introducir el ángulo de su corte para calcular la potencia y otros parámetros del sistema completo.
 
<p align="center">

![CAD quality](assets/tips/12.png)

</p>