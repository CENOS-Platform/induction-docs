---
id: taper
title: Taper
sidebar_label: Taper
sidebar_position: 4
---

There are many different ways on how to evaluate the quality of the mesh, one of them being *Taper*. In this article we will learn what the *Taper* really means and how to resolve the errors caused by high taper elements.

![Taper](assets/taper/1.jpg)

## What is Taper?

*Taper* mesh quality parameter represents the area ratio between two triangles separated by a diagonal within a quadrilateral face. *Taper* value varies from 0 to 1, and at very high values **computational problems may occur**. Because of this reason a check is present in CENOS to make sure the mesh has no high value taper elements, which could cause calculation errors.

Elements with high *taper* value **usually occur in Viscous Layers**, if these layers are defined on only a part of the surface (end abruptly). CENOS check is designed to catch such elements with *taper* value **above 0.5**.

## Taper errors

Errors connected to high taper elements are relatively rare, but once they occur it can take quite a time to figure out the reason. High taper elements occur in elements created with *Viscous Layers*, and the reason behind it is **inconsistency in the viscous layers definitions** (layers do not cover the whole surface but stops in the middle).

<p align="center">

![Taper](assets/taper/3.png)

</p>

When using *Advanced Geometry Editor*, error about *High Taper* elements can appear right before you try to export the mesh to CENOS if there are any.

<p align="center">

![Taper](assets/taper/2.png)

</p>

If you see such error, it means that you need to recheck your mesh definitions and adjust them to get rid of high taper elements.

## How to find high Taper value elements

Sometimes the troublesome elements are small and hard to notice from the distance, therefore **CENOS automatically creates a group with these troublesome elements**, which you can visualize separately and understand in which part of the mesh they are present.

You can find this group named **Taper error elements** under *Groups of Faces/Volumes*.

<p align="center">

![Taper](assets/taper/4.png)

</p>

 - Click the *Eye* icon (![Eye icon](assets/aspect-ratio/9.png)) to enable visibility for *Taper error elements* and disable visibility for *Mesh_1*.

Mesh elements with high taper value will become visible. **If you cannot see the mesh elements**, click on the mesh visualisation screen and press *Space-bar* on your keyboard.

## How to correct high Taper value elements

Once you have located the high taper elements, you can start to correct them. First you need to **understand in which part (sub-mesh) these elements are present**. Then you need to **adjust the mesh definition so that these elements would disappear**.

If the high taper elements are located in the *Viscous Layers*, the universal fix for it is to **build the *Viscous Layers* on the whole surface**, not on just a part of it.

If you still cannot resolve high Taper error, contact our support!
