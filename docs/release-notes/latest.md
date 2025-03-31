---
id: latest
title: Release Notes (v5.x)
sidebar_label: v5.x
sidebar_position: 1
slug: /latest
---

## v5.1 (March 29, 2025)
Improvements:

* Significantly improved Result Viewer stability and filter accuracy
* Result opening, as well general CENOS UI response time is decreased, making CENOS more responsive to opening, saving and other processes
* Result saving speed is increased in cases with Complex motion
* Added possibility to zip and share log files directly from CENOS
  
Bugfixes:

* Fixed a bug where in some cases current appeared as 1A in results
* Fixed an issue which did not send attachments with first chat message
* Fixed a bug which made mesh disappear when mesh cutting was used on a single domain
* Fixed a bug in remeshing, which caused some cases to fail when calculating with complex motion and for a longer period of time
* Fixed numerous backend starting and license check issues, which blocked CENOS usage at start
* Fixed a bug which caused overheating if Natural cooling boundary condition was used


## v5.0 (January 21, 2025)

Features:

* New built-in Result Viewer which enables more intuitive and easy result evaluation

Improvements:

* Improved PDF report source image generation
* Significantly improved automatic meshing algorithm quality and stability
* Added warning if time steps converge with only 1 iteration, which could lead to incorrect results
* Improved property update speed in Physics
* Added checks to prevent case to be run if time step is selected as 0 or negative number
* Updated material B(H) curves to improve case convergence and general stability

Bugfixes:

* Fixed connectivity issues which blocked some users from using the latest version
* Fixed a bug which did not allow to replace CAD files more than once within one simulation
* Fixed an issue which caused MaxTemperature field in results to glitch if more than one workpiece was present
* Fixed a bug which appeared when user manually tried to change any material property value
* Fixed a bug which allowed to compress the case with results, even when no results were present
* Fixed a bug which incorrectly assigned Inductor role if terminals were selected for multiple inductors during air box generation
* Fixed a bug which prevented to edit material property table values, if only 1 value was entered
* Fixed an issue which caused case to fail if anisotropic material properties were defined through Expressions
* Fixed an issue which did not allow to run completely thermal analysis (without Electromagnetics enabled)
* Fixed an issue with cooling definition, which did not hide irrelevant input fields in some cases
* Fixed a bug which did not allow to generate a video from results
* Fixed a bug which did not allow to run multiple cases in a batch
* Fixed an issue where cooling was not working correctly, if lock on inductor together with motion in Z direction was used
* Fixed a bug which did not save results if case with Complex Motion crashed during calculation

