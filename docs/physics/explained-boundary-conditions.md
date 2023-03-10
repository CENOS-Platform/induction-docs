---
id: boundary-conditions
title: Boundary conditions
sidebar_label: Boundary conditions
sidebar_position: 5
---

Boundary conditions (BC) are physical definitions on domain boundary surfaces for thermal conditions and electromagnetism. Here are listed **all boundary conditions used in CENOS**, as well as the **most common usage for each BC**.

## Thermal BC

Thermal BC's are boundary conditions through which the heat exchange between domains is defined.

### Fixed temperature

*Fixed temperature* boundary condition defines a fixed temperature on the boundary surface.

<p align="center">

![Fixed temperature](assets/boundary-conditions/fixed-temperature.png)

</p>

:::note usage
When *Motion* is used on infinite billet, the surface through which the billet enters the computational domain can be defined with *Fixed Temperature*.
:::

### Heat flux

*Heat flux* boundary condition defines a constant heat flux density on the boundary surface.

<p align="center">

![Heat flux](assets/boundary-conditions/heat-flux.png)

</p>

:::note usage
Can be used if the heat flux going through a specific area is known
:::

### Heat flow

*Heat flow* boundary condition defines a constant heat flow (in watts) on the boundary surface.

<p align="center">

![Heat flow](assets/boundary-conditions/heat-flow.png)

</p>

:::note usage
Can be used if the heat flow going through a specific area is known
:::

### Convection

*Convection* boundary condition defines the heat flux as dependent from the ambient temperature and heat transfer coefficient. *Convection* is defined as:

$$
q=h(T-T_{amb})
$$

<p align="center">

![Convection](assets/boundary-conditions/convection.png)

</p>

:::note usage
*Convection* is used on the workpiece-air interface to define heat exchange when temperature is low. Usually used together with *Radiation*.
:::

To **learn more** about *Convection* definition, [**click here**](/thermal-losses#convection).

### Radiation

*Radiation* boundary condition defines the thermal radiation to infinity on the boundary surface, where the heat flux is defined as:

$$
q=\sigma_{SB}\epsilon(T^4-T_{amb}^4)
$$

<p align="center">

![Radiation](assets/boundary-conditions/radiation.png)

</p>

:::note usage
*Radiation* is used on the workpiece-air interface to define heat exchange when temperature is high. Usually used together with *Convection*.
:::

To **learn more** about *Radiation* definition, [**click here**](/thermal-losses#radiation).

### Combined

*Combined* boundary condition allows you to combine multiple BC such as *Convection*, *Radiation*, *Heat Flux* and *Heat Flow* on a single domain surface.

<p align="center">

![Combined](assets/boundary-conditions/combined.png)

</p>

:::note usage
*Combined* is used on workpiece-air interface to define both *Convection* and *Radiation* for a complete heat trasfer definition over wide temperature range.
:::

### Adiabatic

*Adiabatic* boundary condition defines 0 heat flux on the surface.

<p align="center">

![Adiabatic](assets/boundary-conditions/adiabatic.png)

</p>

:::note usage
*Adiabatic* is used on symmetry surfaces for domains with thermal analysis.
:::

### Interface

*Interface* boundary condition defines boundary surface as the internal surface between two domains.

<p align="center">

![Interface](assets/boundary-conditions/interface.png)

</p>

:::note usage
Used to define interface between two domains which both have thermal analysis definition.
:::

### Thermal Contact Resistance

*Thermal Contact Resistance* boundary condition defines thermal resistance between two domains.

<p align="center">

![TCR](assets/boundary-conditions/tcr.png)

</p>

:::note usage
Used to define interface between two domains who both have thermal analysis definition.
:::

## Electromagnetics

Electromagnetic BC's are boundary conditions through which the magnetic flux is defined.

### Infinity

*Infinity* boundary condition defines a zero vector potential on the boundary surface.

<p align="center">

![Infinity](assets/boundary-conditions/infinity.png)

</p>

:::note usage
*Infinity* is used to define the outer surface of the air box.
:::

### Flux parallel

*Flux parallel* boundary condition defines the magnetic field lines as parallel to the boundary surface.

<p align="center">

![Flux parallel](assets/boundary-conditions/flux-parallel.png)

</p>

:::note usage
*Flux parallel* is used to define symmetry boundary conditions on the sides of slices and sectors.
:::

To **learn more** about *Flux parallel* definition, [**click here**](/symmetry#flux-parallel).

### Flux normal

*Flux normal* boundary condition defines the magnetic field lines as normal to the boundary surface.

<p align="center">

![Flux normal](assets/boundary-conditions/flux-normal.png)

</p>

:::note usage
*Flux normal* is used to define symmetry boundary conditions on top and bottom of slices and sectors.
:::

To **learn more** about *Flux normal* definition, [**click here**](/symmetry#flux-normal).

### Interface

*Interface* boundary condition defines boundary surface as the internal surface between two domains.

<p align="center">

![Interface](assets/boundary-conditions/interface.png)

</p>

:::note usage
Used to define interface between two domains from which only one has thermal analysis definition.
:::

### Surface Impedance

*Surface Impedance* boundary condition can be accessed only through the *Surface Impedance* domain. It defines the boundary surface as an infinitely thin layer for VH frequency skin layer resolution.

<p align="center">

![Surface Impedance](assets/boundary-conditions/surface-impedance.png)

</p>

:::note usage
*Surface Impedance* is used to replace manual skin layer resolution through mesh at very high frequency setup.
:::

### Symmetry axis

*Symmetry axis* is a 2D-axial-symmetric specific boundary condition which defines 0 vector potential on the symmetry axis.

<p align="center">

![Symmetry axis](assets/boundary-conditions/symmetry-axis.png)

</p>

:::note usage
*Symmetry axis* is used in every 2D axial-symmetric case to define rotational axis.
:::

## Current source

Current BC's are accessed only under the *Current source* domain and through which the current or voltage flowing through the conductor are defined.

### Voltage

*Voltage* boundary condition defines the voltage on the boundary surface.

<p align="center">

![Voltage](assets/boundary-conditions/voltage.png)

</p>

:::note usage
*Voltage* is used to define the voltage on one of inductor terminals. For the other terminal use *Ground*.
:::

### Current

*Current* boundary condition defines a positive current supply to the boundary surface and the value of current.

<p align="center">

![Current](assets/boundary-conditions/current.png)

</p>

:::note usage
*Current* is used to define current on one of the inductor terminals. For the other terminal use *Ground*.
:::

### Ground

*Ground* boundary condition defines a negative current supply to the boundary surface.

<p align="center">

![Ground](assets/boundary-conditions/ground.png)

</p>

:::note usage
*Ground* is used to define one of the inductor terminals. For the other terminal use *Voltage* or *Current*.
:::
