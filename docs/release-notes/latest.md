---
id: latest
title: Release Notes (v4.x)
sidebar_label: v4.x
sidebar_position: 1
slug: /latest
---
## v4.1.2 (June 5, 2023)

Bugfixes:

* Fixed a bug where the case crashed if IDEA 60 (20 kHz) flux concentrator material was used
* Fixed a problem where cases created in v4.0.1 and saved without a material were not opening in v4.1.1


## v4.1.1 (May 25, 2023)

Bugfixes:

* Fixed a bug which blocked users from creating new custom materials or editing and re-saving existing ones


## v4.1 (May 23, 2023)

Features:

* Hardness calculation from composition or hardness from cooling time table
* Reworked cooling definition interface

Improvements:

* Inductor Geometry Role is now automatically predefined in FromCAD approach

Bugfixes:

* Fixed a bug when submesh element count was not instantly updated after mesh recalculation
* Fixed a problem where PDF report was not generated
* Fixed an issue which did not allow to define counter-clockwise rotational movement
* Fixed a bug which crashed calculation if no thermal analysis was enabled
* Fixed a bug which caused geometry data inconsistency with mesh when mesh was created in Salome through FromCAD approach
* Fixed a bug where hardening profile and steel phases developed incorrectly if complex motion for workpiece was used
* Fixed a bug which did not save calculated results if collision between objects occurs
* Fixed a bug which caused an error when case with a state file was opened on another computer
* Fixed a bug which crashed calculation if temperature dependent emissivity was used
* Fixed a problem when in Advanced Geometry Editor approach resending changed group definitions from Salome to CENOS did not update previously sent groups
* Restored possibility to define expression to Fixed Temperature boundary condition
* Reduced thermal shock effect in cases with rotation




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
