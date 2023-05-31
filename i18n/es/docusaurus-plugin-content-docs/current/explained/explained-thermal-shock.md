---
id: thermal-shock
title: Choque térmico
sidebar_label: Choque térmico
sidebar_position: 3
---

En el caso de los resultados que muestran un choque térmico (en la escala de temperatura observará una temperatura negativa), suele estar causado por un paso de tiempo enorme, una malla demasiado gruesa o una combinación de ambos; se produce principalmente en casos con un calentamiento muy rápido o una velocidad de traslación muy alta, le recomendamos que refine la malla o/y reduzca su paso de tiempo.


## ¿Qué es el choque térmico?

Cuando un cuerpo inicialmente caliente se enfría repentinamente o un cuerpo frío se calienta bruscamente a través de la superficie, puede aparecer una variación brusca de la temperatura denominada choque térmico.

Un ejemplo podría ser el calentamiento con calefactores radiativos de potencia conocida o con calefactores resistivos montados directamente en la pared. En estos casos se debe utilizar la condición de contorno Flujo Térmico $W/m^2$ o Transferencia de calor $W$.

Los choques térmicos tienen un efecto a corto plazo y su efecto desaparece cuando se desarrolla el perfil de temperatura. Pero la resolución adecuada de estos efectos impone restricciones adicionales al paso de tiempo y a la resolución de malla en el análisis MEF:

$$
\Delta t = \frac{\rho c}{\lambda} \frac{\Delta x}{6}
$$

Aquí $\Delta t$ es el paso de tiempo, $\Delta x$ es el tamaño de la malla. El coeficiente 6 es empírico, y varía en diferentes fuentes bibliográficas.

Para ilustrar el problema, consideremos un ejemplo 1D (en CENOS se hace como un caso 3D con 1 grosor de elemento en las direcciones Y y Z y N divisiones en la dirección X):

La barra tiene propiedades $\lambda = 50 W/mK$, $\rho = 1000 kg/m^3$, $c = 500 J/kg K$. La longitud es de 1 m, la temperatura inicial y la temperatura en el lado izquierdo $T_0 = 22 C$, el flujo de calor $q = 1000 W/m^2$.

Consideremos la malla con N = 5, por lo que $\Delta x = 0,2 m$. Esto conduce al valor crítico del paso de tiempo $\Delta t = 400 s$.

<p align="center">

![Bar Geometry](assets/thermal-shock/geometry.png)

</p>

La distribución de la temperatura en la barra después de 50 segundos obtenida con $\Delta t = 5$ y diferentes tamaños de malla se muestran en la siguiente figura:

<p align="center">

![thermalShock](assets/thermal-shock/ThermalShock.png)

</p>

Esta figura muestra que para la malla con $N=5$ $(\Delta x = 0.2)$ aparece temperatura no física en el valor $x=0.8$. Dado que la condición inicial y la condición de contorno en uno de los extremos es 22 C, la temperatura nunca debería estar por debajo de este valor. 
En otras palabras, la temperatura y el tamaño de la malla están vinculados y no pueden elegirse de forma totalmente independiente.


:::note Nota

*Para más información*:
https://hal-mines-paristech.archives-ouvertes.fr/hal-00576032/document

:::
