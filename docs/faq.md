---
id: faq
title: Frequently asked questions
sidebar_label: FAQ
sidebar_position: 8
---

### Can a spray quenching which follows inductor in a scanning induction hardening system be simulated in CENOS?

Moving cooling zone can be defined through expressions. Read more [**here**](/field-expressions#moving-spray-cooling).

### How to correctly define coil windings in symmetry case?

In 2D or 3D symmetry cases you need to define each winding half or slice separately in physics setup. If you group all windings in one group, current set on this group will distribute over all windings and produce incorrect results.

### What to do with inductor-air interface?

Inductor-air interface needs to be defined only if you are interested in thermal analysis of the inductor. Otherwise you don’t need to separately define it.

### Is it necessary to identify hollow center of the inductor as Air in physics?

If you are building simulation of inductor with cooling channel in either 2D or 3D, you need to include the cooling channel to the *Air* group for correct EM field calculation.

### What to do with concentrator-air interface?

Concentrator-air interface needs separate definition only when thermal analysis is carried out in concentrators. If you do calculate heating in concentrators, check the documentation article about flux concentrator thermal calculation.

### Can asymmetrical coil be simplified to 2D plane?

Induction heating simulation can be simplified to 2D only for very axial-symmetric geometries. If your inductor or concentrator placement is not axial-symmetric, 2D simplification of such geometry will not provide results which could represent the full geometry.

### What does mesh priority mean?

Mesh priority is the order in which sub-meshes are calculated. If two sub-meshes (inductor and concentrator) have a common surface, one sub-mesh will be calculated first, and the other will be partially based on the first sub-mesh. Those sub-meshes who are on top of the list will be calculated first, and you should prioritize the sub-meshes with greater importance (inductor > concentrator).

### After I reopened Shaper, geometry is not there and it says "Part_1 (not loaded)". How to access this geometry?

Geometry is still there, it is simply not loaded. Right-click on *Part_1 (not loaded)* and click *Activate*. Then you should be able to access everything you have created under *Part_1*.

### When using *Adaptive* time step, jumps up and down in time step size occur. What could be the reason for this?

If you are using *Adaptive* time step, CENOS automatically sets the size of the time step. At points where heating becomes more rapid, it creates smaller time steps, but when heating is not so dynamic, times steps are created larger to save calculation time. This behaviour can create jumps up and down in time step size. If you want to get rid of these jumps, you need to set constant time step small enough for a good resolution of every part of the heating, as you cannot adjust the parameters of *Adaptive* time step.

### What does "ERROR: Elements found with aspect ratio > 10000" mean?

When exporting mesh to CENOS, sometimes error about aspect ratio occurs. It means that mesh has been created succesfully, but it contains elements that are very long and narrow, and which can affect the simulation results. If so, you need to find out where these elements are, and change the meshing approach on that domain. You can find out more in documentation article about [**Aspect Ratio**](/aspect-ratio).

### Can I enter RMS current as input?

In CENOS only *Amplitude* current can be used as current input. If you know the RMS current value, you need to multiply it by √2 to convert it to *Amplitude* current.

### How to save custom results in ParaView?

You can save your custom results as a state file in *ParaView*. State file will save your current result state (with filters, graphs, custom visualization approaches etc.), and you will be able to load it later and access your custom results. To save the state file, in *ParaView* click *File → Save State…*. When you open ParaView next time, your custom results will automatically open.

### How to set the direction of the current flowing in the coil?

If you want to change the direction of current in a specific winding, you need to add minus sign “-” before the current value.
