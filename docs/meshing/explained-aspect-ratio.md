---
id: aspect-ratio
title: Aspect ratio
sidebar_label: Aspect ratio
sidebar_position: 3
---

There are many different ways used to evaluate the quality of the mesh, one of them being *Aspect ratio*. In this article we will learn what the *Aspect Ratio* really is and how to resolve the errors caused by high aspect ratio elements.

<p align="center">

![FElements](assets/aspect-ratio/10.png)

</p>

## What is Aspect ratio?

*Aspect ratio* is the measure of mesh element's deviation from having all sides of equal length. A high aspect ratio occurs within long, thin elements, which **can cause the solver to crash during computation**. Because of this reason, a check is present in CENOS to make sure the mesh has no high aspect ratio elements, which could cause calculation errors.

*Aspect ratio* is usually low within air mesh (around 1) and high in viscous layers (up to 1000). **If the aspect ratio for some elements is higher than 10 000, CENOS built-in check will not let the user use such mesh.**

## Aspect ratio errors

At some point almost every simulation engineer will stumble into an error caused by high aspect ratio mesh elements. These errors occur mostly in 3D meshes, and because of this we need to understand how this error presents itself in both 3D geometry creation approaches available in CENOS - *From CAD* and  *Advanced Geometry Editor*.

### From CAD

*From CAD* creates mesh automatically for the geometry which you have imported, based on the physical parameters entered in the *Physics* part. Because the meshing is done automatically, the **mesh algorithms can sometimes fail on more complex geometries**. To see if the mesh is generated successfully, you need to calculate it before running the simulation.

To do that, you need to **first enter the physical parameters** of your simulation, and then go back to the geometry and click SHOW MESH OPTIONS in the bottom of the screen.

<p align="center">

![FElements](assets/aspect-ratio/1.png)

</p>

In mesh options under *Advanced Settings* click CREATE AUTOMATIC MESH NOW.

<p align="center">

![FElements](assets/aspect-ratio/2.png)

</p>

CENOS will generate the mesh and let you know if the mesh was successfully created. The most common error is connected with high aspect ratio elements - if there are such elements in an automatically generated mesh, a message will pop up.

<p align="center">

![FElements](assets/aspect-ratio/3.png)

</p>

This error means that **CENOS will not use the automatically generated mesh** and **you need to create it manually**. To do that, click OPEN ADVANCED EDITOR, which will send you to the CENOS geometry and mesh creation program: Salome. There you can manually adjust or create the mesh to eliminate high aspect ratio elements.


### Advanced Geometry Editor

When using the *Advanced Geometry Editor*, an error detailing *High Aspect Ratio* elements can appear right before you try to export the mesh to CENOS.

<p align="center">

![FElements](assets/aspect-ratio/4.png)

</p>

If you see such an error, it means that you need to recheck your mesh definitions and adjust them to get rid of elements with high aspect ratio.

## How to find elements with high aspect ratio

Sometimes the troublesome elements are small and hard to notice from the distance, therefore **CENOS automatically creates a group with these troublesome elements**, which you can visualize separately to understand where in the mesh they are present.

You can find this group named **Aspect ratio error elements** under *Groups of Faces/Volumes*.

<p align="center">

![FElements](assets/aspect-ratio/11.png)

</p>


 - Click the *Eye* icon (![Eye icon](assets/aspect-ratio/9.png)) to enable visibility for *Aspect ratio error elements* and disable visibility for *Mesh_1*.

Mesh elements with high aspect ratio wil become visible. **If you cannot see the mesh elements**, click on the mesh visualisation screen and press *Space-bar* on your keyboard.

<p align="center">

![FElements](assets/aspect-ratio/10.png)

</p>

## How to correct High Aspect Ratio elements

Once you have located the high aspect ratio elements, you can start to eliminate them. First you need to **visually understand in which part (sub-mesh) these elements are present**. Then you need to **adjust the mesh definition so that these elements would disappear**.

If the high aspect ratio elements are **located in the Viscous layers** of workpiece or inductor:

* Decrease the *Number of layers* (if possible);
* Decrease the *Stretch factor*;
* Decrease the *Max. size* for the whole sub-mesh.

If these elements are located in air domain or in any sub-mesh, but **not in the Viscous layers**:

* Decrease the *Max. size* for the whole sub-mesh;
* Change the 2D mesh algorithm from *Trinagle: Mefisto* to *NETGEN 2D* (or vice versa).

If you still cannot resolve High Aspect ratio error, contact our support!
