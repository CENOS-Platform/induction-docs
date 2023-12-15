---
id: taper
title: Disminución gradual
sidebar_label: Disminución gradual
sidebar_position: 4
---

Hay muchas formas diferentes de evaluar la calidad de la malla, una de ellas es la *disminución gradual*. En este artículo aprenderemos lo que significa realmente *disminución gradual* y cómo resolver los errores causados por elementos de alta conicidad.

![Taper](assets/taper/1.jpg)

## ¿Qué es la disminución gradual?

El parámetro de calidad de malla *disminución gradual* o *Taper*, representa la relación de área entre dos triángulos separados por una diagonal dentro de una cara cuadrilátera. El valor de *Taper* varía de 0 a 1, y a valores muy altos **pueden producirse problemas computacionales**. Por este motivo, CENOS incluye una comprobación para asegurarse de que la malla no tiene elementos cónicos con valores altos, que podrían causar errores de cálculo.

Los elementos con un valor alto de *taper* **suelen aparecer en capas viscosas**, si estas capas están definidas sólo en una parte de la superficie (terminan abruptamente). La comprobación de CENOS está diseñada para detectar este tipo de elementos con un valor de *taper* **superior a 0,5**.

## Errores de conicidad

Los errores relacionados con elementos de alta conicidad son relativamente raros, pero una vez que ocurren puede llevar bastante tiempo averiguar la razón. Los elementos de alta conicidad ocurren en elementos creados con *Capas Viscosas*, y la razón detrás de ello es **inconsistencia en las definiciones de las capas viscosas** (las capas no cubren toda la superficie sino que se detienen en el centro).

<p align="center">

![Taper](assets/taper/3.png)

</p>

Al utilizar el *Editor de Geometría Avanzado*, puede aparecer un error sobre elementos *de alta conicidad* justo antes de intentar exportar la malla a CENOS si los hay.

<p align="center">

![Taper](assets/taper/2.png)

</p>

Si ve un error de este tipo, significa que debe volver a comprobar las definiciones de la malla y ajustarlas para eliminar los elementos cónicos.

## Cómo encontrar elementos de alto valor de conicidad

A veces los elementos problemáticos son pequeños y difíciles de notar desde la distancia, por lo tanto **CENOS crea automáticamente un grupo con estos elementos problemáticos**, que puede visualizar por separado y entender en qué parte de la malla están presentes.

Puede encontrar este grupo llamado **Taper error elements** en *Groups of Faces/Volumes*.

<p align="center">

![Taper](assets/taper/4.png)

</p>

- Haga clic en el icono *Ojo* (![Eye icon](assets/aspect-ratio/9.png)) para activar la visibilidad de *Taper error elements* y desactivar la visibilidad de *Mesh_1*.

Los elementos de malla con alto valor de conicidad se harán visibles. **Si no puede ver los elementos de la malla**, haga clic en la pantalla de visualización de la malla y preione la *barra espaciadora* en el teclado.

## Cómo corregir los elementos de alto valor de conicidad

Una vez localizados los elementos de alto *Taper*, puede empezar a corregirlos. Primero necesita **entender en qué parte (sub-malla) están presentes estos elementos**. Luego hay que **ajustar la definición de la malla para que estos elementos desaparezcan**.

Si los elementos de alta conicidad están localizados en las *Capas Viscosas*, la solución universal para ello es **construir las *Capas Viscosas* en toda la superficie**, no sólo en una parte de ella.

Si sigue sin poder resolver el error de conicidad alta, ¡póngase en contacto con nuestro servicio de soporte!