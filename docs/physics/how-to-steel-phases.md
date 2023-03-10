---
id: steel-phases
title: How to define phase change calculation in CENOS
sidebar_label: Steel phase calculation
sidebar_position: 3
---

To simulate the hardening of the steel it is important to know the steel phases that have occurred after the heat treatment. 

CENOS platform offers a **Phase calculation** model which allows calculating the steel phases such as austenite, bainite, pearlite, and martensite.

## How to use phase calculation?

When your geometry is ready and the mesh is exported to CENOS, you can define the material parameters. In Material customization window check **Phase calculation**. Define:
- $T_{Ac_{1}}$ (if possible) - the temperature at which the austenite phase change begins
- $T_{Ac_{3}}$ – the temperature at which the structure is fully austenite
- $T_{M_{s}}$ – martensite formation start temperature
- $t_s$- time data which represents the beginning of the phase change (usually when 1% of transformation has happened)
- $t_e$ – time data which represents the end of the phase change (usually when 99% of change has happened)

:::important
If temperature $T_{Ac_{1}}$ is not known, use the same temperature as $T_{Ac_{3}}$.
:::

<p align="center">

![Phase calculation variables](assets/steel-phases/phase-calculation-1.png)

</p>

## An example of how to get data from TTT diagram.

To do the phases change calculation you will need to use data from TTT (time-temperature-transformation) diagram which will look similar to the one below.

![An example of TTT diagram with different phases shown](assets/steel-phases/phase-calculation-ttt.png)

1. Since bainite, pearlite, and ferrite is calculated as one phase, **lines that define the start of the phase change need to be connected** as ferrite and bainite start lines are connected using green dots in this example. 
2. Similarly, **lines that define the end of the phase change need to be connected** as pearlite end line and bainite end line are connected using red in this example.
3. $t_s$ and $t_e$ temperature data need to be defined in the temperature range from $T_{M_{s}}$ to $T_{Ac_{3}}$. If the end line in the original TTT diagram does not cross the Ac3 line, as in the given example, you need to extrapolate it, otherwise, the calculation will not work.

An example of how to treat TTT diagram to get the data for $t_s$ and $t_e$:

![Example of how to treat TTT diagram to get data for $t_s$ and $t_e$](assets/steel-phases/phase-calculation-ttt2.png)
