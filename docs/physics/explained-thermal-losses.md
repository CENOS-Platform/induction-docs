---
id: thermal-losses
title: Thermal loss definition in CENOS
sidebar_label: Thermal losses
sidebar_position: 7
---

		
Heat transfer is a very important part of the simulation physical setup - without correct heat exchange definition accurate results cannot be acquired. There are different parameters to define heat exchange, each with specific values that depend on material properties and cooling methods.

## Heat transfer types and values

CENOS offers **4 types of heat exchange definitions** - *convection*, *radiation*, *heat flux*, and *heat flow*. Each of these definitions can be used for specific applications, depending on temperature and  cooling approach.

### Convection

Convective heat transfer, often referred to simply as convection, is the transfer of heat from one place to another by the motion of fluid or gas. Convection is usually the dominant form of heat transfer in liquids and gases, and plays a significant role through a wide range of heat treatment applications. Convective heat transfer is defined with $h$ - **Heat Transfer Coefficient** $( W/m^2K )$ and the $T_0$ - **Ambient temperature** $(^{\circ} C)$. Coefficient $h$ measures the intensity at which the heat is removed from the surface by the fluid or gas with temperature $T_0$.
The appropriate *Heat Transfer Coefficient* value is very important for correct simulation definition. It ranges from small to very large numbers and can be confusing. *Heat Transfer Coefficient* depends on the chosen cooling approach (natural or forced convection) and the fluid used in the process. The approximate values of different colling approaches are as follows:

| Forced convection :                       | $W/m^2K$ :   |
|:-----------------------------------------:|:------------:|
| Low speed flow of air over a surface      | 10           |
| Moderate speed flow of air over a surface | 100          |
| Moderate flow of water in a pipe          | 3000         |
| Water and liquids                         | 50 to 10'000 |

| Natural convection :    | $W/m^2K$ :   |
|:-----------------------:|:------------:|
| Gases and dry vapors    | 5 to 37      |
| Gas flow in tubes       | 10 to 350    |
| Water and liquids       | 50 to 3000   |
| Air                     | 10 to 100    |
| Water                   | 100 to 1200  |
| Water flowing in tubes  | 500 to 1200  |
| Oil                     | 50 to 350    |

It is possible to define *Heat Transfer Coefficient* as temperature dependent for special cooling liquids, such as PAG solutions.

<div class="cen-multiple">

**PAG 12% solution spray quench Heat Transfer Coefficient dependance from temperature**

</div>

<div class="cen-multiple">

| Temperature $(^{\circ} C)$ : | Heat Transfer Coeff. $(W/m^2K)$ : |
|:--------------------:|:------------------------------:|
| 33                   | 2975                           |
| 59                   | 3828                           |
| 99                   | 7972                           |
| 149                  | 10004                          |
| 198                  | 11264                          |
| 245                  | 11832                          |
| 296                  | 13011                          |
| 348                  | 14799                          |
| 398                  | 17155                          |
| 447                  | 17887                          |
| 499                  | 18415                          |
| 544                  | 18049                          |
| 598                  | 17115                          |
| 646                  | 16099                          |
| 699                  | 13823                          |
| 749                  | 12076                          |
| 798                  | 10045                          |
| 848                  | 7566                           |
| 898                  | 5088                           |

</div>

### Radiation

Thermal radiation is electromagnetic radiation emitted from the material. All matter with a temperature greater than absolute zero emits thermal radiation. Radiation is defined with **Emissivity** and **Ambient Temperature**. It occurs through vacuum or any transparent medium (solid, fluid, or gas) and plays a big role at temperatures above 800 $^{\circ} C$.

Emissivity coefficient for some common materials can be found in the table below. Emissivity coefficient for some materials varies with temperature - emissivity coefficients given below are at the temperature of 26.85 $(^{\circ} C)$.

| Material :                                        |Emissivity ($\epsilon$) :|
|:-------------------------------------------------:|:--------------:|
| Aluminum commercial sheet                         | 0.09           |
| Cast iron, turned and heated                      | 0.60 - 0.70    |
| Copper, heated and covered with thick oxide layer | 0.78           |
| Copper, polished                                  | 0.023 - 0.052  |
| Gold                                              | 0.47           |
| Gold, polished                                    | 0.025          |
| INCONEL X, oxidized                               | 0.71           |
| Iron, polished                                    | 0.14 - 0.38    |
| Iron, rough ingot                                 | 0.87 - 0.95    |
| Cast iron, turned and heated                      | 0.60 - 0.70    |
| Nickel, polished                                  | 0.072          |
| Platinum, polished plate                          | 0.054 - 0.104  |
| Carbon/stainless steel                            | 0.7 - 0.8      |
| Tin, unoxidized                                   | 0.025          |

### Heat Flux and Heat Flow

*Heat Flux* or thermal flux is a flow of energy per unit area per unit of time ($W/m^2$).

*Heat Flow* ($W$) is the integral value of *Heat Flux*.

These heat exchange definitions **can be used if the energy value that is going through a specific area is known**.

