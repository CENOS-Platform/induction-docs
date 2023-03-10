---
id: overview
title: "Primeros pasos: descripción general de CENOS"
sidebar_label: Descripción general
sidebar_position: 1
slug: /
---

*CENOS Platform* is a simulation software for induction heating. It helps engineers to **save a significant amount of money and time** on induction coil prototyping by replacing physical tests with computer simulations.

In this article we will learn what a simulation is and go over the main points on how to create one.

## What is a simulation?

A numerical simulation  or **virtual testing** is a calculation done by a computer following a program that implements a mathematical model for a physical system.

It combines a **geometrical model** of the physical system with the **physics definitions** about that system to predict numerous **physical phenomenon** such as induction heating.

<p align="center">

![What is a simulation](assets/overview/documentacion1.png)

</p>

## Simulation with CENOS

CENOS stands for ***Connecting Engineering Open Source***, which highlights the way how CENOS creates and calculates simulations. By combining 3 powerful open-source tools - **Salome**, **GetDP** and **ParaView** - CENOS delivers the best tool for *Induction Heating* simulations. 

The workflow of CENOS simulation is based on these three open-source tools. It consists of 4 parts - **Geometry**, **Physics**, **Meshing** and **Results** - that represent the steps involved in creating an *Induction Heating* simulation.

<p align="center">

![What is a simulation](assets/overview/documentacion2.png)

</p>

## Geometry

There are 3 ways on how to create and prepare geometry for simulation in CENOS - ***Templates***, ***From CAD*** and ***Advanced geometry editor***. These approaches have different geometrical applications and can be used to **prepare any geometry**.

<p align="center">

![What is a simulation](assets/overview/2.png)

</p>


### Template

:::note
Fast heating estimations and only a couple of minutes to create
:::

*Template* allows you to choose from **different workpiece and inductor templates** to quickly set up a 2D axial-symmetric simulation.

As the **mesh is being created automatically**, you only need to define the key geometrical and physical parameters to set up a simulation.

<p align="center">

![What is a simulation](assets/overview/3.png)

</p>

<p align="center">

![What is a simulation](assets/overview/4.png)

</p>

### From CAD

:::note
Import premade CAD and simulate it without additional geometrical modifications
:::

*From CAD* is a geometry creation approach which allows you to **import one or more CAD files and prepare them** for simulation without manual geometry modifications.

**Create geometrical groups and boundary surfaces**, define physical parameters and run the simulation. Using this approach, **mesh is being generated automatically**!

<p align="center">

![What is a simulation](assets/overview/5.png)

</p>

<p align="center">

![From CAD](assets/overview/6.png)

</p>

### Advanced geometry editor

:::note
For advanced users who want to have a full control over geometry and mesh
:::

For more advanced users CENOS offers **fully manual geometry and mesh creation approach** - *Advanced geometry editor*. It allows to create geometry and mesh from scratch in CENOS geometry modeling tool - Salome.

Create custom geometry and a suitable mesh, define domains and boundaries, and **enjoy the full power of CENOS**!

<p align="center">

![From CAD](assets/overview/7.png)

</p>

<p align="center">

![From CAD](assets/overview/8.png)

</p>

**IMPORTANT**: Along geometry you also need to **prepare a mesh** to carry out a simulation. the quality of the mesh affects the precision of the results, For the *Advanced geometry editor* the mesh must be created manually.

## Physics

CENOS Platform offers a wide variety of variables to simulate ***Induction Heating**, focusing on ***Thermal*** and ***Electromagnetics***  analysis.


### Thermal Analysis

:::note
Calculate conventional heating applications
:::


<p align="center">

![From CAD](assets/overview/11.png)

</p>

### Electromagnetics

:::note
Fast current density, joule heat and other electromagnetic phenomenon predictions
:::

*Electromagnetics* physics allows you to Estimate *Current Density*, *Joule Heat*, *EM field* and other electromagnetic aspects of your model!


<p align="center">

![From CAD](assets/overview/13.png)

</p>

### Induction Heating

:::note
Simulate Induction Heating applications. 
:::

*Induction Heating*  is coupled electromagnetic and thermal physics, **designed specifically for induction heating simulations**.

<p align="center">

![From CAD](assets/overview/15.png)

</p>

## Results

:::note
Get precise  and vast visual and statistical results of your simulation
:::

CENOS incorporates a very powerful post-processor - *ParaView*, which together with .csv file energy statistics provides full control over results and every simulation aspect.

<p align="center">

![From CAD](assets/overview/16.png)

</p>

<p align="center">

![From CAD](assets/overview/17.png)

</p>

<p align="center">

![From CAD](assets/overview/18.png)

</p>
