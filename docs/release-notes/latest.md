---
id: latest
title: Release Notes (v4.x)
sidebar_label: v4.x
sidebar_position: 1
slug: /latest
---

## v4.4.2 (August 1, 2024)

Bugfixes:

* Fixed issue with multithreading not working correctly


## v4.4.1 (July 4, 2024)

Bugfixes:

* Fixed issue which did not allow user to stop calculation
* Fixed issue which did not allow user to stop mesh generation


## v4.4.0 (June 27, 2024)

Improvements:
* Updated B(H) material data for Alloy Steel 42CrMo4
* Decreased calculation speed for cases with Complex Motion and many time steps (above 100-200 steps)
* Improved manual mesh skin layer UI
* Improved reliability of PDF report generation
* Improved overall calculation stability

Bugfixes:

* Time charts are now readable, if coil grouping has been used in the case setup
* For workpieces with internal, sealed cavities, air domain is now generated correctly


## v4.3.2 (May 8, 2024)

Bugfixes:

* Fixed an issue where calculation was stopped if internet connection was lost


## v4.3.1 (March 18, 2024)

Bugfixes:

* Fixed a bug which did not allow the mesh from Salome to be sent to CENOS in FromCAD approach
* Fixed a bug which did not allow to open Salome in some cases, if Advanced Geometry Editor workflow was used
* Fixed an issue that did not allow PDF file to be opened if Salome was used in the case setup
* Fixed a bug that showed phase shift if Transient EM calculation was selected in Electromagnetics block
* Fixed a bug that did not allow Transient EM calculation to be run in Electromagnetics block
* Fixed an issue where Curvature Safety control in CENOS meshing window was not working
* Fixed a bug which corrupted grouped inductor mesh if more than 9 windings were grouped together
* Fixed a bug which corrupted magnetic permeability field, if temperature dependant permeability was defined
* Fixed an issue where, if OTHER geometry role was defined, the domain did not show up in the results


## v4.3 (February 6, 2024)

Features:

* Sliced coil winding grouping
* Thermal analysis for 3D Litz wire

Improvements:

* Air Symmetry role in 2D FromCAD cases now optional to allow planar case calculation

Bugfixes:

* Fixed an issue which caused unphysical hot spots, if specific cooling parameters were chosen

Other:

* Updated [Terms & Conditions](https://www.cenos-platform.com/terms-conditions)


## v4.2 (September 22, 2023)

Features:

* 2D CAD support in From CAD approach
* Mesh inspection (clipping) in CENOS mesher

Bugfixes:

* Fixed a bug where convective power losses showed up incorrectly in 3D slice cases
* Fixed a bug where in PDF reports “Error” was shown at Terminals section
* Fixed a bug which caused the hardening profile filter to work incorrectly in some cases
* Fixed an issue which caused previous result overwriting if Continue From function was used
* Fixed a bug which caused PDF report generation to fail in cases with calculated hardness
* Fixed interpolation issue which caused problems with some material definitions
* Fixed a bug which caused Surface Impedance approach to fail
* Fixed a bug which showed Mode: Not Found in PDF report generation
* Fixed a bug which did not allow to use time step table values
* Fixed an issue which showed different calculation times in log and PDF report


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
