---
id: mesh-troubleshoot
title: Mesh troubleshoot
sidebar_label: Mesh troubleshoot
sidebar_position: 5
---
Pre-processing or geometry and mesh preparation for the simulation is the most important part of the simulation setup, because it can strongly affect the results of the simulation.

Mesh creation for complex geometries can be challenging, which is why we need to understand how to properly **prepare the geometry** for meshing, **troubleshoot the errors** which can occur during the meshing and **evaluate the quality** of the mesh in case the solver refuses to compute the mesh.

## Prepare the geometry

Before the meshing ensure that the geometry is simplified as much as possible. Overall [**geometry simplifications**](/geometry-simplification) should be made to reduce the element count and decrease the calculation time, but it does not end there.

### Fuse multi-block objects

If you have a geometry which consists of multiple separate blocks, they should be fused together to simplify the work with the geometry and to get rid of all the unnecessary edges and planes between the blocks, which can make meshing difficult later on.

To fuse blocks, click ***Operations*** → ***Boolean*** → ***Fuse***, select the blocks of interest and click *Apply*.

<p align="center">

![Fuse multi-block objects](assets/mesh-troubleshoot/fuse.png)

</p>

## Troubleshoot the errors

In order to understand how to correct a meshing error, we need to understand how to read the error and pay attention to what is important.

An error in Salome consists of three parts:

+ **Algorithm** - defines which argument is associated with the error
+ **Sub-shape** - defines which part of the geometry is associated with the error
+ **Error** - gives written error description

<p align="center">

![Fuse multi-block objects](assets/mesh-troubleshoot/1.png)

</p>

Some errors are caused by the algorithm, some by the geometry, which is why it is important to understand which part - *algorithm* or *geometry* - is more likely to be causing the error.

### Sub-shape troubleshoot

The first thing to check is which part of the geometry is highlighted as the cause of the error. Click ***Show Sub-shape*** in the lower left corner of the *Mesh Computation* window - part of your geometry will be highlighted.

If a whole domain is highlighted, it is likely that the meshing algorithm for the domain is wrongly defined.

<p align="center">

![Fuse multi-block objects](assets/mesh-troubleshoot/2.png)

</p>

If only a small part of the geometry is highlighted, examine it closely. Meshing algorithms can crash because of **faulty details in the geometry** such as:

+ Overlapping edges
+ Narrow gaps between domains
+ Small filets
+ Unnecessary lines
+ Holes in the surface

In this example an error occurs because of the unnecessary lines within the geometry.

<p align="center">

![Fuse multi-block objects](assets/mesh-troubleshoot/3.png)

</p>


### Algorithm troubleshoot

If the geometry is not faulty, but error still appears, check what kind of algorithm - 1D, 2D or 3D - is causing the error.

**IMPORTANT**: After every sub-mesh algorithm modification it is advisable to **clear the mesh data before recomputing** the whole mesh, because otherwise an error may occur. To do that, right-click on *Mesh_1* and click *Clear Mesh Data*.

If the error is cause by **1D algorithm**:

1. ***Adjust the 1D algorithm based on the error*** description - most likely you have left something blank, and the error description will give you the information of what it is.

If it is **2D algorithm**:

1. ***Decrease the Max. Length value*** of the domain mesh. If you enter a *Max. Length* value which is relatively big compared to the size of the geometry, meshing algorithm will crash.

2. ***Change the faulty algorithm*** to an alternative (*Triangle: Mefisto* to *NETGEN 2D* and vice versa, for example).

If it is **3D algorithm**:

1. ***Check for meshing strategy conflicts***. If you choose different meshing strategies for different domains, for example, *Automatic Tetrahedralization* for billet and *NETGEN 1D-2D-3D* for conductor, algorithms can interact with each other and cause error. The mentioned example is not the only one that could cause an error, so make sure to mesh all domains with the same algorithms, if it is possible.
