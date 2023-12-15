---
id: power-control
title: Simulación de potencia controlada
sidebar_label: Control de potencia
sidebar_position: 9
---

CENOS es una potente herramienta que le permite introducir ***voltaje***, ***corriente*** , o ***potencia*** para controlar su sistema.

Para ello, vaya a la sección *inductor* del módulo **física**, allí podrá seleccionar ***voltaje***, ***corriente*** o ***potencia*** como entrada de control.

<p align="center">

![From CAD](../getting-started/assets/cad/ind.png)

</p>

El control del proceso de calentamiento por inducción más utilizado es el control de potencia, pero ¿qué ocurre cuando hay que configurarlo con tensión o corriente? Cuando se construye una simulación para optimizar el proceso de calentamiento, muchos ingenieros tropiezan con el hecho de que en su lugar **necesitan definir la corriente o la tensión en el inductor.**

## ¿Cómo encontrar la corriente de entrada?

Si se desconocen los valores de corriente o tensión en el inductor, se pueden utilizar varios métodos en función de la configuración de la simulación.

### Sin utilizar B(H) (permeabilidad constante)

Si no utiliza una curva B(H) en su simulación, puede **calcular fácilmente el valor de corriente** que corresponde a su valor de potencia deseado con una sola simulación.

:::info Important

¡Ejecute el cálculo de prueba **sin Análisis Térmico**, se ejecutará más rápido y el valor de corriente calculado será correcto para la simulación con análisis térmico también!

:::

Para ello, tiene que seguir estos pasos:

1) Elija un valor de corriente aleatorio y ejecute un paso de tiempo. Encontrará el valor de potencia correspondiente a la corriente que haya definido.

$$
I_1 \to P_1
$$

2) Sin la curva B(H) el valor de la potencia es proporcional a la corriente. Calcule el valor de corriente necesario $I_2$, ya que se conoce la relación entre $I_1$ y $P_1$.

$$
P=UI=I^2R \to \frac{P_1}{P_2}=\frac{I_1^2}{I_2^2}
$$

$$
I_2=\sqrt\frac{I_1^2P_2}{P_1}
$$

:::note Example

Tenemos un consumo de **3kW de potencia**, y queremos calcular la corriente necesaria para poner en CENOS.

1) Ejecute un paso de tiempo con **150 A**. A partir de los resultados vemos que **150 A** de corriente produce **12,45 W** de potencia.

2) Usamos la ecuación mencionada anteriormente y calculamos la corriente necesaria para producir **3 kW**:

$$
I_2=\sqrt\frac{150^2*3000}{12.45}=2328.45 A
$$

Una vez calculada la corriente necesaria $I_2$ se puede activar el análisis térmico, introducir el valor de corriente calculado y ejecutar la simulación con una potencia especificada.

:::

### Utilizando B(H)

Si se utiliza la curva B(H), la corriente de entrada ya no será proporcional a la potencia de salida. En tal caso, tiene que hacer su mejor estimación de lo que podría ser la corriente del inductor y ejecutar un paso de tiempo de simulación puramente electromagnética. Observe el valor de potencia en los resultados y **aumente o disminuya la corriente hasta que alcance el consumo de potencia deseado**.

$$
I_1 \to P_1
$$

$$
I_2 \to P_2
$$

$$
I_3 \to P_3
$$

Con este planteamiento tendrá que realizar un par de simulaciones para encontrar el valor de corriente correcto. ¡Recuerde **calcular sólo 1 paso de tiempo sin análisis térmico**!

### μ(T) (calentada por encima de la temperatura de Curie)

Si la pieza se calienta por encima de la temperatura de Curie, la simulación controlada por potencia no es posible, ya que la impedancia del sistema cambia alrededor y después del punto de Curie, lo que provoca saltos en los valores de corriente y tensión. Debido a esto, para mantener el mismo valor de potencia, es necesario que haya diferentes valores de corriente o tensión antes y después del punto de Curie.

En tal caso **la corriente o la tensión pueden definirse como valores en una tabla** en función del tiempo. Basta con realizar un cálculo puramente EM con una corriente constante a lo largo de todo el rango de calentamiento.

Abra el archivo .csv y eche un vistazo a la potencia total calculada en cada paso temporal.

<p align="center">

![CSV](assets/power-control/5.png)

</p>

Como conoce la corriente de entrada, sólo tiene que aplicar la ecuación anteriormente discutida para calcular $I_2$ para cada paso de tiempo.

<p align="center">

![CSV 2](assets/power-control/7.png)

</p>

A continuación, copie el nuevo valor de la tabla en CENOS y habrá encontrado la tabla de corriente necesaria para obtener una potencia constante durante todo el tiempo de calentamiento.

<p align="center">

![CENOS](assets/power-control/9.png)

</p>
