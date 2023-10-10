---
id: shaft-scanning
title: Scanning Hardening of a Splined Shaft
sidebar_label: Scanning Hardening of a Splined Shaft
---

*Shafts*, *steering racks*, *worm gears* and other long or extended mechanical parts are being widely used in **automotive**, **aerospace** and many other industries in different mechanical assemblies.

To manufacture these parts, they need to be **hardened to improve hardness and wear resistance**, and to **increase fatigue life**. The best way to harden such parts is through **induction hardening**. It provides **selective hardening**, which **increases system efficiency** and **decreases the thermal distortions** of the part.

In this article we are going to **learn how to build a simple splined shaft scanning hardening process** using *CENOS Induction Heating* simulation software.

The setup consists of a **2 winding inductor** and low carbon steel **AISI 1020 shaft**. In simulation **4 kHz frequency** and **11 kA current** is considered, as well as **thermal losses** from the shaft.

<p align="center">

![shaft scanning](assets/shaft-scanning/shaft.gif)

</p>

:::note Application files
Download the CAD files used in this tutorial [**here**](./assets/shaft-scanning/SplinedShaft.zip)
:::



## 1. Prepare your geometry

Geometry is the beginning and a cornerstone of every simulation, so we need to **start by preparing our geometry** for the simulation.

### 1.1 Import CAD files

First we need to select the geometry creation approach. In CENOS home window click **From CAD**.

<p align="center">

![shaft scanning](assets/shaft-scanning/1.png)

</p>

Click the blinking **Folder** icon to select the CAD files you want to import.

<p align="center">

![shaft scanning](assets/shaft-scanning/2.png)

</p>

**Select STEP files** of your system and click **Open** to import them into CENOS.

<p align="center">

![shaft scanning](assets/shaft-scanning/3.png)

</p>

:::note
For this example we imported 2 different STEP files - one for the inductor, and the other for the shaft. You can also import both of them in a single STEP file (assembly), it really doesn't make any difference to the simulation!
:::

### 1.2 Generate air box

Once the CAD files are uploaded, CENOS will ask if you want to automatically generate the air box (ambient environment around your system). Click **Yes** on the choice, and then **CONTINUE**.

<p align="center">

![shaft scanning](assets/shaft-scanning/4.png)

</p>

**Select your inductor terminals** for reference, and click **CREATE AIR** to automatically generate the air box!

<p align="center">

![shaft scanning](assets/shaft-scanning/5.png)

</p>

### 1.3 Define groups

Once the air box is generated, you will be redirected to group creation window. Here you will see a **list of groups you need to define** for your system, such as which one is workpiece, where are inductor terminals etc.

<p align="center">

![shaft scanning](assets/shaft-scanning/6.png)

</p>

**Select the group** (in this example, *Workpiece*), **select the corresponding volume** from the list or directly from the screen, and click **ASSIGN Workpiece**.

<p align="center">

![shaft scanning](assets/shaft-scanning/7.png)

</p>

In the same way define the rest of the groups.

<p align="center">

![shaft scanning](assets/shaft-scanning/8.png)

</p>

:::note
You can **rename each group** by clicking the *edit button* next to the name!

<p align="center">

![shaft scanning](assets/shaft-scanning/9.png)

</p>
:::

Once ready, click **GO TO PHYSICS** for Physics definition!

<p align="center">

![shaft scanning](assets/shaft-scanning/10.png)

</p>

## 2. Define physics

You will be redirected to the *Physics* window, where physical definitions are present. On the left you can see the **preview window** of your geometry, but on the right - the actual **physical definitions**. You can **navigate physics through the domain tabs** above the physical definitions.

<p align="center">

![shaft scanning](assets/shaft-scanning/11.png)

</p>

### 2.1 Simulation control

In the SIMULATION CONTROL window define the simulation as *transient* with **4 kHz** *frequency*, **17 s** *End time* and **0.25 s** *time step*. For *Computation algorithm* choose **Fast**.

<p align="center">

![shaft scanning](assets/shaft-scanning/12.png)

![shaft scanning](assets/shaft-scanning/13.png)

</p>

### 2.2 Splined shaft

Select SHAFT from *Domain bar*. For *Material* click SELECT… and choose **Low carbon steel 1020 (B(H), $t^{o}$ depend)**.

<p align="center">

![shaft scanning](assets/shaft-scanning/14.png)

</p>

Under THERMAL ANALYSIS for **WORKPIECE SURFACE1** choose **Combined** – check the **Convection** and **Radiation** boxes and enter **15** for *Convection* and **0.8** for *Radiation*.

<p align="center">

![shaft scanning](assets/shaft-scanning/15.png)

</p>

### 2.3 Inductor

Switch to INDUCTOR in *Domain bar*. For *Material* choose **Copper (Temperature dependent)**.

<p align="center">

![shaft scanning](assets/shaft-scanning/16.png)

</p>

Under ELECTROMAGNETICS choose **Current (Amplitude)** for TERMINAL1, **Ground** for TERMINAL2 and enter **11000 A** as *Current (Amplitude)*.

<p align="center">

![shaft scanning](assets/shaft-scanning/17.png)

</p>

### 2.4 Scanning

Switch to MOTION tab and click CREATE NEW MOTION.

<p align="center">

![shaft scanning](assets/shaft-scanning/18.png)

</p>

Check **Complex motion** as motion type, **Inductor** as the domain you want to move, and enter movement speed of **0.01 m/s** in Y direction.

<p align="center">

![shaft scanning](assets/shaft-scanning/19.png)

</p>

With the Motion definition you have finished the physics setup! Click **RUN** to calculate your simulation!


<p align="center">

![shaft scanning](assets/shaft-scanning/20.png)

</p>

## 3. Evaluate results

In the end of the calculation our post-processing tool *ParaView* will automatically **open with a pre-set temperature state**, and you will be able to see the **temperature field distribution** in the workpiece in the last time step.

<p align="center">

![shaft scanning](assets/shaft-scanning/21.png)

</p>

Results can be further manipulated by using ParaView filters - find out more in CENOS [**result evaluation**](/results) article.

This concludes our Splined Shaft Scanning Hardening tutorial. For any recommendations or questions contact our support.
