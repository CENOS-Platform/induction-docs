---
id: motion
title: How to define motion in CENOS
sidebar_label: Motion
sidebar_position: 13
---

Movement is an important part for a lot of induction heating systems, as translational or rotational movement helps to heat/harden the specific part uniformly and efficiently. To **accurately simulate** such processes, you need to **take into account the respective types and speeds of the movement** present in your system.

In this article we are going to take a look at **how movement can be defined in CENOS**, what are the **requirements for movement** and what limitations are currently present with such setup.

## Motion in CENOS

CENOS supports both translational (*scanning*) and rotational (*single-shot*) movement. To define motion in your simulation, go to **Motion** tab in PHYSICS section and click **CREATE NEW MOTION**.

<p align="center">

![Motion](assets/motion/1.png)

</p>

Select the **type of motion**, **which part** you want to move, in **which direction** and with **what speed**, and CENOS will do the rest!

<p align="center">

![Motion](assets/motion/2.png)

</p>

## Types of Motion

When defining *Motion*, you will notice that there are 2 options to choose from - **Simple Motion** and **Complex Motion**.

<p align="center">

![Motion](assets/motion/3.png)

</p>

### Simple Motion

This option allows you to simulate motion for **axially symmetrical** or **continuous** workpieces.

<p align="center">

![Motion](assets/motion/4.png)

</p>

Some examples would include:

<p align="center">

![Motion](assets/motion/sm.gif)

</p>

As you can see, *Simple Motion* can be **applied to systems where it can be assumed that the geometry is not moving**. This can be very useful for completely symmetrical part rotation or modelling of continuous feed of material through the system.

:::note
Use *Simple Motion* if it is possible, as it calculates **a lot faster than** ***Complex Motion***.
:::

### Complex Motion

If *Simple Motion* is not applicable to your case, you need to use *Complex Motion*.

<p align="center">

![Motion](assets/motion/5.png)

</p>

For parts with splines, teeth, holes, gaps and other kinds on unsymmetrical details an actual motion needs to be simulated. *Complex Motion* enables you to move the respective parts in your system.

<p align="center">

![Motion](assets/motion/cm.gif)

</p>

:::note
Make sure that the calculation **time step is small enough to capture the rotation smoothly**! No more than 30 deg turn in one time step!
:::

## Limitations

Even though the Movement definition is easy to use, there are still some **things to keep in mind when defining movement** in CENOS.

### Rotation axis

Rotation currently is limited only around the Z axis, so be sure that your rotational system is **positioned around the Z axis**!

<p align="center">

![Motion](assets/motion/7.png)

</p>
