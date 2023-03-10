---
id: good-cad
title: How to make good CAD for Induction Heating simulation
sidebar_label: How to make a good CAD
sidebar_position: 2
---

The gometrical model of your workpiece and inductor plays a big role in how easy or hard it will be to set up and get accurate results from an induction heating simulation.

We have summarized the main aspects for good, simulation-friendly CAD file, which should be followed in order to **create a simple, trouble-free geometry** for your simulation.

## Create geometry as a single solid

In many CAD softwares it is easier to build the inductor geometry from blocks, which are then combined to form a complete inductor CAD. When creating geometry for simulation, these **blocks must be fused together to form a single solid** – doing this helps remove unnecessary faces between blocks and simplifies setting up geometric properties, but the meshing process as well.

<p align="center">

![Single solid](assets/good-cad/1.png)

</p>

## Simplify geometry

Computer simulation starts with a geometrical model of the real life problem – you need to accurately depict the geometry to precisely calculate the physical aspects of the model. However, in most cases **you can disregard some of the geometrical details, which do not have such a significant impact on the physical results**, to optimize the simulation.

The following features can be deleted, as they take up significant amount of calculation time and computer power without considerable contribution to results. 

### Remove terminals

Inductor terminals are not important for induction heating simulation and should be removed.

<p align="center">

![Single solid](assets/good-cad/2.png)

</p>

### Delete unnecessary elements

Inductor elements such as holding parts or connections with outer elements can be deleted. 

<p align="center">

![Single solid](assets/good-cad/3.png)

</p>

### Get rid of small details

Small details have a negligible impact on the simulation results, but they take up a lot of calculation time, as they need to be resolved through mesh, which increases the mesh element count significantly. **Get rid of details such as small fillets, holes and narrow gaps** in both workpiece, inductor etc.

<p align="center">

![Single solid](assets/good-cad/4.png)

</p>

**IMPORTANT**: If you have a cooling duct running through your inductor, do not forget to **remove fillets within** it as well!

## Resolve inaccurately connected geometrical parts

During geometry creation be careful with connections between different inductor parts – inaccurate connections will result in meshing problems and calculation errors!

### Overlapping

<p align="center">

![Single solid](assets/good-cad/5.png)

</p>

### Gaps

<p align="center">

![Single solid](assets/good-cad/6.png)

</p>

## Ensure that the inductor geometry is continuous

If your inductor has a cooling channel, be sure that the **cooling channel is continuous through all inductor length**, otherwise it will cause problems during meshing.

<p align="center">

![Single solid](assets/good-cad/7.png)

</p>

If you follow these tips for achieving good CAD, you will have a geometry which will be **easy to manipulate and mesh**, and **fast to calculate**!
