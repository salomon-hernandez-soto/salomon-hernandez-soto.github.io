---
title: "Multi Material Pliers (W.I.P)"
excerpt: "These pliers achieve a mechanical advantage of X with just multi-material and print-in-place methods."
header:
  image: /assets/img/Syringe-Pump-Banner.JPEG
  teaser: /assets/img/Syringe-Pump-Thumbnail.JPEG
gallery:
  - url: /assets/img/Syringe-Pump-1.png
    image_path: /assets/img/Syringe-Pump-1.png
    alt: "Labeled front view of syringe pump"
  - url: /assets/img/Syringe-Pump-2.png
    image_path: /assets/img/Syringe-Pump-2.png
    alt: "Wiring diagram of the syringe pump"
  - url: /assets/img/Syringe-Pump-3.png
    image_path: /assets/img/Syringe-Pump-3.png
    alt: "Syringe pump while calibrating flow rate"
---

## Introduction
  The aim of this project was to create some needle nose pliers using either print-in-place methods or a simple 3-piece assembly while using multiple materials. Success was dictated by precision high enough to pick up a through-hole resistor.

  Print-in-place refers to interesting or useful objects, often with functional joints, that can be used right off of a 3D printer's print bed [[1]](https://www.thingiverse.com/blog?p=print-in-place-beginners-guide). Print-in-place designs often fall in the categories of hand tools, novelty items, or small toys, which can all be seen [here](https://www.thingiverse.com/tag:print_in_place). Multi-material prints are prints using two different material filaments. These work best when the materials can fuse together. Materials fuse together well when they are chemically and physically similar, such as PLA and PETG. Dissimilar materials can be fused together using mechanical joints (click [here](https://en.wikipedia.org/wiki/Joinery) to learn more).

## CAD Model
There are two models, being a simple set to meet the goal, and an advanced set made for personal enjoyment.

Simple, Print-in-Place Pliers:
<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH90d2dQT28d5b602811a13250a8aa0c3677?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>

Advanced, 3-Part Assembly EZ-Pliers
<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH90d2dQT28d5b60281146f54a76afa0fc44?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>

## Design Process
  Throughout the design process, I made two separate designs, as I wanted to challenge myself above the requirements of the assignment. The first design was meant to be a set of print-in-place pliers, while the second set was meant to be a simple assembly set of pliers, more in line with what typical pliers look like. The second set features greater mechanical properties due to a completely rigid body. However, this also made for a more complex design process, which is why it was done as an additional exercise.
  For both pliers, a spring component was used made out of TPU, though this spring component served different functions in both designs. In the simpler print-in-place design, the spring works by putting the square in shear, which tightents the jaws as the spring deforms. In the more advanced assembly design, the spring also works by putting the square in shear, but is now mainly used to return the pliers to their original position once released. Instead of using an elastic pivot, the advanced pliers use a rigid locking mechanism to form a pivot, allowing for greater force application. The pivot design takes advantage of the fact that 30 degree overhangs do not require support material to print.
  Ideally, these pliers would both use a multi-material print with part adhesion. However, because the rigid PLA/ABS/PETG CF and elastic TPU segments are not chemically or mechanically similar, they can't fuse together. Thus, both spring components were kept in place through mechanical joints. The simple pliers use a dovetail joint with 0.1 mm of overlap to keep the parts firm in place, and the advanced pliers use a cylindrical joint with 0.1 mm of spacing to allow some rotation as the arms pivot.
  The materials used were PLA for some prototype iterations, TPU 95A for all spring components, ABS for the final simple pliers print, and PETG CF for the final advanced pliers print. Note ABS CF was also used but abandoned due to difficult printing and brittle properties compared to PETG CF. 
  Every iteration of the pliers can be seen above, with the following table dictating the major feature changes of each iteration for both designs. Note that I have named the advanced set the EZ-Pliers, in honor of how simple it is to print and assemble.

Simple Pliers design history:

| Version |                                          Changes                                         |
|---------|:----------------------------------------------------------------------------------------:|
| 1       |                                            N/A                                           |
| 2       | Increased center spring size, decreased open arm distance, decreased closed jaw distance |
| 3       |                            Achieved zero closed jaw distance                             |

Advanced EZ-Pliers design history:

| Version |                                              Changes                                              |
|---------|:-------------------------------------------------------------------------------------------------:|
| 1       |                                                N/A                                                |
| 2       |                 Adjusted locking mechanism as it was physically impossible to load                |
| 3       |            Added jaw teeth, redistributed pivot thicknesses to strengthen weakest point           |
| 4       |                 Fixed tolerancing from interference to transitionary at the pivot                 |
| 5       | Adjusted tolerancing from transitionary to clearance at and near pivot, fixed jaw teeth occlusion |

## Plier Specifications
Simple Pliers:

| Jaw Length (mm) | Jaw Capacity (mm) |
|:---------------:|:-----------------:|
|        30       |        9.6        |

EZ-Pliers:

| Jaw Length (mm) | Jaw Capacity (mm) |
|:---------------:|:-----------------:|
|       37.5      |        9.5        |

## Print Settings
For the simple plier arms, the print settings were kept on default for printing ABS with a copper 0.6 mm nozzle.

For the EZ-Plier arms, the following print settings were adjusted, using PETG-CF filament with a steel 0.6 mm nozzle.

| Setting Name          | Setting Value |
|-----------------------|:-------------:|
| Print Speed (% Based) |    50 mm/s    |
| Top Layers            |       7       |
| Bottom Layers         |       7       |
| Infill Density        |      55%      |
| Perimeters            |       5       |
| Infill Pattern        |     Gyroid    |

  For the TPU springs, the following print settings were adjusted, using TPU 95A filament with a copper 0.6 mm nozzle. Note that these settings generate the spring geometry using infill, without the need to design the pattern in CAD. The infill angle is meant to put the infill parallel to the square sides for a square grid.

| Setting Name   | Setting Value |
|----------------|:-------------:|
| Top Layers     |       0       |
| Bottom Layers  |       0       |
| Infill Density |      25%      |
| Perimeters     |       5       |
| Infill Angle   |   0 degrees   |
| Infill Pattern |      Grid     |

## Gallery

{% include gallery caption="Assorted related pictures from the syringe pump project." %}
