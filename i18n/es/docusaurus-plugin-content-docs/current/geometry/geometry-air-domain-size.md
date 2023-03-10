---
id: air-domain-size
title: Role of air domain size
sidebar_label: Air domain size
sidebar_position: 4
---

For every simulation you create, an air domain or simulation environment **is a necessity**. It is needed for the electromagnetic calculations, and its **size can have a strong impact** on the simulation results for both workpiece and inductor.

## How big the air domain should be?

Air domain around the geometry can be created at different sizes - too small will result in inaccurate results, but too large will increase the element count and thus the calculation time.

The **Infinity BC** is used for the air domain outer boundaries, meaning that on these surfaces magnetic vector potential is zero. For this condition to be applicable, it is necessary to ensure that electromagnetic field is declining to negligible values at the outer boundary. to satisfy this condition, **air domain should be at least 3 times larger** than the coil within it.

**IMPORTANT**: If the mesh has too many elements, you can reduce the size of the air domain to 2.5 times the coil size, instead of three, but not less!
The air domain size is defined as the distance from the center of the coil to the air outer boundary (Z). The coil size is defined with its outer diameter (d).

<p align="center">

![Domain size definition](assets/air-domain-size/1.png)

</p>

The air domain size is characterized in respect to the coil diameter - if it is more than 3 times the size of the coil diameter, the relative error for voltage, coil and billet is negligible.

<p align="center">

![Domain size definition](assets/air-domain-size/2.png)

</p>
