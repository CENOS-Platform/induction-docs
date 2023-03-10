---
id: rotating-workpieces
title: Heating of large rotating workpieces
sidebar_label: Large rotating workpieces
sidebar_position: 2
---

<p align="center">

![Pipe preheat](assets/rotating-workpieces/animation.gif)

</p>

In CENOS you are not limited to using one type of domain for the whole object. You can combine multiple types of domains with **different physics calculations**.

A very useful application is when creating a **large workpiece** you can only simulate EM induction near the coil where most of the heating takes place. For the rest of the workpiece, only thermal calculations can be performed.

**Example** with preheating a large pipe for welding:

Practically, most of the induction heating happens near the coil, the other 80% of the pipe only has thermal processes.
We can separate the pipe in two domains, and **not simulate electromagnetics in the larger one**. What allows this to work is the ***thermal interface boundary*** condition.

The workpiece (pipe) domain is split into **two parts**, only in one of which we simulate electromagnetics.

<p align="center">

![Setup](assets/rotating-workpieces/1.png)

</p>

<p align="center">

![Setup](assets/rotating-workpieces/2.png)

</p>

**TIP:** When doing partition operation in Salome, the air domain will split the workpiece into the separate solids. You don't need to create them manually.

## Advantages

The main advantage of this method is the much lower number of mesh elements and consequently calculation time. With the traditional setup the number of elements would have been around **700 000** but with the simplified method it was **450 000 elements**.

## Boundary conditions

Here are the boundary conditions for the pipe simulation example:

<p align="center">

![Setup](assets/rotating-workpieces/3.png)

</p>