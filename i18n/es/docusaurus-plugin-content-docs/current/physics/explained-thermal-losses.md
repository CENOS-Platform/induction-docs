---
id: thermal-losses
title: Definición de pérdidas térmicas en CENOS
sidebar_label: Pérdidas térmicas
sidebar_position: 6
---


La transferencia de calor es una parte muy importante de la configuración física de la simulación: sin una definición correcta del intercambio de calor no se pueden obtener resultados precisos. Existen diferentes parámetros para definir el intercambio de calor, cada uno con valores específicos que dependen de las propiedades del material y de los métodos de enfriamiento.

## Tipos y valores de transferencia de calor

CENOS ofrece **4 tipos de definiciones de intercambio de calor** - *convección*, *radiación*, *flujo térmico* y *transferencia de calor*. Cada una de estas definiciones puede utilizarse para aplicaciones específicas, dependiendo de la temperatura y del enfoque de enfriamiento.

### Convección

La transferencia de calor por convección, a menudo denominada simplemente convección, es la transferencia de calor de un lugar a otro por el movimiento de un fluido o un gas. La convección suele ser la forma dominante de transferencia de calor en líquidos y gases, y desempeña un papel importante en una amplia gama de aplicaciones de tratamiento térmico. La transferencia de calor por convección se define con $h$ - **Coeficiente de transferencia de calor** $( W/m^2K )$ y la $T_0$ - **Temperatura ambiente** $(^{\circ} C)$. El coeficiente $h$ mide la intensidad a la que el calor es retirado de la superficie por el fluido o gas con temperatura $T_0$.
El valor adecuado del *Coeficiente de Transferencia de Calor* es muy importante para la correcta definición de la simulación. Oscila entre números pequeños y muy grandes y puede ser confuso. El *Coeficiente de Transferencia de Calor* depende del método de enfriamiento elegido (convección natural o forzada) y del fluido utilizado en el proceso. Los valores aproximados de los distintos métodos de refrigeración son los siguientes:

| Convección forzada:                                     | $W/m^2K$ :   |
|:-------------------------------------------------------:|:------------:|
| Flujo de aire a baja velocidad sobre una superficie     | 10           |
| Flujo de aire a velocidad moderada sobre una superficie | 100          |
| Flujo moderado de agua en una tubería                   | 3000         |
| Agua y líquidos                                         | 50 to 10'000 |

| Convección natural:      | $W/m^2K$ :   |
|:------------------------:|:------------:|
| Gases y vapores secos    | 5 to 37      |
| Flujo de gas en tubos    | 10 to 350    |
| Agua y líquidos          | 50 to 3000   |
| Aire                     | 10 to 100    |
| Agua                     | 100 to 1200  |
| Agua que fluye por tubos | 500 to 1200  |
| Aceite                   | 50 to 350    |

Es posible definir el *coeficiente de transferencia de calor* en función de la temperatura para líquidos refrigerantes especiales, como las soluciones PAG.

<div class="cen-multiple">

**Dependencia de latemperatura  del coeficiente de transferencia de calor en solución de enfriamiento por pulverización  PAG 12%**

</div>

<div class="cen-multiple">


| Temperatura $(^{\circ} C)$ : | Coeficiente de transferencia de calor $(W/m^2K)$ : |
|:--------------------:|:------------------------------:|
| 33                   | 2975                           |
| 59                   | 3828                           |
| 99                   | 7972                           |
| 149                  | 10004                          |
| 198                  | 11264                          |
| 245                  | 11832                          |
| 296                  | 13011                          |
| 348                  | 14799                          |
| 398                  | 17155                          |
| 447                  | 17887                          |
| 499                  | 18415                          |
| 544                  | 18049                          |
| 598                  | 17115                          |
| 646                  | 16099                          |
| 699                  | 13823                          |
| 749                  | 12076                          |
| 798                  | 10045                          |
| 848                  | 7566                           |
| 898                  | 5088                           |

</div>

### Radiación

La radiación térmica es la radiación electromagnética emitida por el material. Toda materia con una temperatura superior al cero absoluto emite radiación térmica. La radiación se define con **Emisividad** y **Temperatura ambiente**. Se produce a través del vacío o de cualquier medio transparente (sólido, fluido o gas) y juega un gran papel a temperaturas superiores a 800 $^{circ} C$.

El coeficiente de emisividad para algunos materiales comunes se puede encontrar en la siguiente tabla. El coeficiente de emisividad de algunos materiales varía con la temperatura. Los coeficientes de emisividad que se indican a continuación corresponden a una temperatura de 26.85 $(^{\circ} C)$.

| Material:                                                 |Emisividad ($\epsilon$) :|
|:---------------------------------------------------------:|:--------------:|
| Placa comercial de aluminio                               | 0.09           |
| Hierro fundido, torneado y calentado                      | 0.60 - 0.70    |
| Cobre, calentado y recubierto de una gruesa capa de óxido | 0.78           |
| Cobre pulido                                              | 0.023 - 0.052  |
| Oro                                                       | 0.47           |
| Oro pulido                                                | 0.025          |
| INCONEL X, oxidado                                        | 0.71           |
| Hierro pulido                                             | 0.14 - 0.38    |
| Hierro, lingote bruto                                     | 0.87 - 0.95    |
| Hierro fundido, torneado y calentado                      | 0.60 - 0.70    |
| Níquel pulido                                             | 0.072          |
| Platino, placa pulida                                     | 0.054 - 0.104  |
| Acero al carbono/inoxidable                               | 0.7 - 0.8      |
| Estaño sin oxidar                                         | 0.025          |

### Flujo Térmico y Transferencia de Calor

*Flujo de Calor* o flujo térmico es un flujo de energía por unidad de superficie por unidad de tiempo ($W/m^2$).

*Transferencia de Calor* ($W$) es el valor integral de *Flujo de calor*.

Estas definiciones de intercambio de calor **pueden utilizarse si se conoce el valor de la energía que atraviesa un área específica**.