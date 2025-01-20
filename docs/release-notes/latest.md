---
id: latest
title: Release Notes (v5.x)
sidebar_label: v5.x
sidebar_position: 1
slug: /latest
---


## v5.0.0 (January 20, 2025)
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


