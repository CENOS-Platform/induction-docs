---
id: v4
title: Release Notes (v4.x)
sidebar_label: v4.x
sidebar_position: 2
---

## v4.0.1 (January 31, 2023)

Improvements:

* Added mesh volume gradient slider
* Added mesh curvature safety slider
* Improved overall error message handling and UX

Bugfixes:

* Fixed meshing issue which corrupted air mesh during motion
* Fixed a bug where manual sub-mesh changes were not saved in CENOS meshing
* Fixed Kernel error that randomly appeared at RUN
* Fixed a meshing problem where coil mesh in Templates developed weirdly at low frequencies
* Fixed the Core: XXXXXX error in simulation terminal
* Fixed an issue that crashed PDF and result generation if adaptive time step was used
* Fixed an error with state files not working
* Fixed an issue where calculation crashed if thermal analysis on the inductor were enabled
* Fixed a bug in meshing during complex motion, which often caused thermal shock
* Fixed an issue which crashed calculation if 0 was entered in the motion table
* Fixed result calculation issue where, if permeability field was enabled, permeability was not calculated in flux concentrators
* Fixed an issue with unphysical temperature distribution in symmetry cases
* Fixed a problem with voltage input crashing electromagnetic calculation


## v4.0 (December 9, 2022)

Features:

* CENOS manual meshing
* CAD file replacement in From CAD approach
* Dynamic result processing during calculation
* Motion table values

Improvements:

* Improved convergence
* Significantly improved automatic meshing capabilities in FromCAD approach
* Improved error messaging for problems caused by convergence, meshing and material properties
* Reworked advanced result field interface
* Automatic volume naming based on applied geometry role in FromCAD approach
* Improved support chat functionality

Bugfixes:

* Fixed automatic skin layer mesh generation in FromCAD approach
* Preview highlighting when hovering over boundary conditions list is now working
* PDF report generation failed in some cases
