---
id: geometry-simplification
title: Geometry simplification
sidebar_label: System simplification
sidebar_position: 3
---

Almost every geometry is at some level symmetric, which allows us to simplify it and by doing so **greatly decrease calculation time**.

You can also simulate only a part of the geometry with [**symmetry boundary conditions**](/physics/symmetry), and it will still produce adequate results for the whole geometry.

## Delete repeating geometry

If your geometry consists of more than one identical workpiece-conductor system, select one to simulate and delete the others.

<p align="center">

![Reduce system count](assets/geometry-simplification/1.png)

</p>

## Simulate only half

If you have geometry of linear symmetry, simulate only half of it and mirror results to represent the whole geometry.

<p align="center">

![Reduce system count](assets/geometry-simplification/2.png)

</p>

## Cut out sector

If you have axial symmetric geometry, cut out and simulate one repeating sector of it, for example, one tooth from a whole gear, then revolve results to represent whole geometry.

<p align="center">

![Reduce system count](assets/geometry-simplification/3.png)

</p>

## 3D to 2D

For revolved geometry there is no need for 3D simulation, simulate only plane slice from full geometry and revolve results to represent the whole geometry.

<p align="center">

![Reduce system count](assets/geometry-simplification/4.png)

</p>
