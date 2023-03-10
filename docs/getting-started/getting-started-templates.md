---
id: templates
title: Templates
sidebar_label: Templates
sidebar_position: 2
---

Simulation consists of creating **geometry** and its **mesh**, defining physical **parameters**, and, after running calculations, **post-processing** the results into suitable quantities and graphics.

If you are **new to simulation** and CENOS, we suggest to **start with predefined geometry templates**, as they will focus more on the structure and basics of the simulation.

Alternatively, you can use your CAD file or create geometry from scratch.  

## Select the geometry building approach

To use geometry templates, click **Template** in the CENOS home window.

<p align="center">

![Select Template](assets/templates/Template1.png)

</p>

**Templates automatically define the non-critical parts of the simulation setup** and offer new users a **preset simulation physical and geometrical values** to get a view on how simulations are defined, to leave you with only the important decisions.

<p align="center">

![Select Template](assets/templates/2.png)

</p>

### Define units

On the *Create Geometry* window in the left lower corner click **select units of your geometry**. 

<p align="center">

![Select Template](assets/templates/3.png)

</p>

### Choose template

Under WORKPIECE and INDUCTOR tabs **choose the template** geometry that suits your system for simulation domains.

<p align="center">

![Select Template](assets/templates/4.png)

</p>

<p align="center">

![Select Template](assets/templates/5.png)

</p>

### Enter geometrical properties

Enter the geometrical properties such as diameter, height, thickness, etc. to **define your geometry**.

:::tip
**For reference on how to input the geometrical properties take a look at the sketch next to it!**
:::

<p align="center">

![Select Template](assets/templates/6.png)

</p>

When done, **switch to physics setup** by clicking GO TO PHYSICS in the upper right corner of the screen.

<p align="center">

![Select Template](assets/templates/7.png)

</p>

## Define simulation parameters

### Enter physical parameters

In the SIMULATION CONTROL window **define global parameters** such as *frequency*, *calculation time*, etc.

<p align="center">

![Select Template](assets/templates/8.png)

</p>

In the SIMULATION DOMAIN windows such as WORKPIECE and WINDINGS **define the physical parameters of each domain** like *material*, *heat exchange*, *current* etc.

<p align="center">

![Select Template](assets/templates/9.png)

</p>

### Run the simulation

Once the simulation has been set up, **click RUN** in the upper right corner of the CENOS screen.

<p align="center">

![Select Template](assets/templates/10.png)

</p>

## Post-processing

At the end of the calculation the post-processing tool *ParaView* will automatically **open with a pre-set temperature state**, and you will be able to see the **temperature field distribution** in the workpiece in the last time step.

<p align="center">

![Select Template](assets/templates/11.png)

</p>

To **learn more** about result manipulations, visit our [**result evaluation**](/results).

### Integral values

For integral values such as **apparent power, induced heat and complex voltage** you can use the .csv file, which comes along with the visual results. You can access it through *Note* button next to the *Visualization* block *Play* button.

<p align="center">

![Select Template](assets/templates/12.png)

</p>
