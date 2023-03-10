---
id: fluxtrol-heating
title: How to set up thermal calculation for flux concentrators
sidebar_label: Flux concentrator heating
sidebar_position: 11
---

The most basic induction heating system consists of only two parts - workpiece and inductor. More advanced systems incorporate flux concentrators, which help to concentrate the magnetic field and improve the economy of the system.

When flux concentrators are introduced in the simulation, additional parameters must be known from the results, such as **power loss and heating of concentrators**.

In this article we will **learn how to set up flux concetrator thermal definition** for calculation of heating and losses.

<p align="center">

![Concentrators](assets/fluxtrol-heating/0.png)

</p>

## Enable thermal calculation

To calculate *Thermal Analysis* of flux concentrators, you need to **enable this type of analysis** in the physics setup under concentrator domain.

<p align="center">

![Concentrators](assets/fluxtrol-heating/1.png)

</p>

## Add material properties

For additional analysis you need to define thermal properties and parameters for losses.

### Thermal properties

Define *Thermal Conductivity* and *Heat capacity* in the same way as for other domains, such as workpiece.

<p align="center">

![Concentrators](assets/fluxtrol-heating/2.png)

</p>

### Power loss

To calculate power loss in flux concentrators, check the *Use power losses in non-conducting material* box. Enter *Amplitude for power loss*, *Frequency exponent* and *Magnetic field exponent*.

<p align="center">

![Concentrators](assets/fluxtrol-heating/3.png)

</p>

## Define boundary conditions

For *Thermal analysis* you need to **create surface group for concentrator-air interface**, and **define heat exchange** on this surface.

<p align="center">

![Concentrators](assets/fluxtrol-heating/4.png)

</p>

If the concentrator is in contact with inductor (have a common surface), **create a separate group for concentrator-inductor surface**. Define it with *Fixed temperature* or *Heat Flow*.

For EM analysis define each of these groups as *Interface*.