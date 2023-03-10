---
id: billet
title: Static aluminum billet heating using Templates
sidebar_label: Aluminum billet heating
---

When you need to simulate a **2D axial symmetric induction heating** case with billet and coil of standard, regular shape, it is convenient to use **Induction Heating Templates**.

In this tutorial you will learn how to set up and use the Induction Heating Templates for 2D axial symmetric simulation of a cylindrical rod with a rectangular profile coil. We will create the geometry by choosing one of the available templates for each domain, define the mesh quality, enter the specific values and boundary conditions in the physics setup and in the end evaluate the results using our post-processor.

Induction Heating Template is an easy and fast way to set up and calculate induction heating cases for standard geometries. In the next pages an induction heating example of **aluminum** billet at **15 kHz** and **2 kA** with radiation and convection boundary conditions is presented.

<p align="center">

![Diagram](assets/billet/0.png)

</p>

## 1. Open Templates

To enter geometry templates, in CENOS home window click **Template**.

![Open template](assets/billet/1.1.png)

**Template automatically defines the non-critical parts of the simulation setup** and offers new users a **preset simulation physical and geometrical values**, so you only need to change the parameters that are already there.

## 2. Create Geometry

### 2.1 Units and mesh

You can **define case units** in lower left corner of *Create Geometry* screen. For this tutorial, leave *milimeters* as case units.

<p align="center">

![Common properties](assets/billet/2.1.1.png)

</p>

If you want to **change mesh density**, click SHOW MESH OPTIONS.

<p align="center">

![SHOW MESH OPTIONS](assets/billet/2.1.2.png)

</p>

Then choose from *Mesh density* dropdown.

<p align="center">

![Mesh density](assets/billet/2.1.3.png)

</p>

**IMPORTANT**: When using templates, mesh is generated automatically before the start of the calculation. With *Mesh density* you define how fine or coarse the mesh will be.

### 2.2 Workpiece geometry

Switch to the WORKPIECE domain. Select **Billet** for *Shape*.

<p align="center">

![Billet](assets/billet/2.2.1.png)

</p>

Under *Properties* enter **0.02** for *Diameter* and **0.2** for *Height*.

<p align="center">

![Workpiece properties](assets/billet/2.2.2.png)

</p>

### 2.3 Inductor geometry

Switch to the INDUCTOR domain. Select **Rectangular profile** for *Shape*.

<p align="center">

![Rectangular profile with flux concentrator](assets/billet/2.3.1.png)

</p>

Under *Properties* make sure that the *Hollow coil* box is checked and enter the values for the coil and concentrator as follows:

<p align="center">

![Inductor and concentrator properties](assets/billet/2.3.2.png)

</p>

When the geometry is set, click **Go to PHYSICS** in the upper right corner of the window.

<p align="center">

![Inductor and concentrator properties](assets/billet/2.3.3.png)

</p>

## 3. Define physics

:::note important
Part of the window is painted grey meaning that every setting in the grey area is pre-set for this specific template, leaving only the core settings to your mind.
:::

If you want to **edit settings in the grey area**, enable **Edit all properties**.

<p align="center">

![Edit all properties](assets/billet/3.0.png)

</p>

### 3.1 Simulation control

In the SIMULATION CONTROL window you can access and **define global simulation parameters** such as frequency, calculation time, time step, computational algorithms and many more.

Define the simulation as *Transient* with **15 kHz** *frequency*, **20 s** *End time* and **2 s** *time step*.

<p align="center">

![Simulation control](assets/billet/3.1.1.png)

</p>

### 3.2 Workpiece definition

Switch to WORKPIECE in *Domain bar*. For *Material* click SELECT… and choose **Low carbon steel 1020 B(H), $t^{o}$ depend**.

<p align="center">

![Simulation control](assets/billet/3.2.1.png)

</p>

Under THERMAL ANALYSIS leave the default **10** for *Heat Transfer Coefficient*, but change *Emissivity* to **0.3**.

![Thermal analysis](assets/billet/3.2.2.png)

### 3.3 Coil definition

Switch to WINDING_0.. in *Domain bar*. Select **Copper** as your material.

<p align="center">

![Simulation control](assets/billet/3.2.3.png)

</p>

Enter **2000 A** for *Current (Amplitude)*. 

<p align="center">

![Inductor definition](assets/billet/3.3.1.png)

</p>

### 3.4 Concentrator definition

Switch to CONCENTRATOR in *Domain bar*. For *Material* select **Flux concentrator FLUXTROL A**. 

<p align="center">

![Concentrator definition](assets/billet/3.4.1.png)

</p>


Physical definition for the air domain is set fully automatically, so after you define concentrator and conductor domains, **click RUN** in the right upper corner of the window.

## 4. Evaluate results

In the end of the calculation the post-processing tool *ParaView* will automatically **open with a pre-set temperature state**, and you will be able to see the **temperature field distribution** in the workpiece in the last time step.

![Temperature distribution](assets/billet/4.1.1.png)

Results can be further manipulated by using ParaView filters - find out more in CENOS [**result evaluation**](/results) article.

This concludes our Induction Heating Template tutorial. For any recommendations or questions contact our support.