---
title: "Microfluidic Particle Sorter (W.I.P)"
excerpt: "This microfluidic particle sorter is capable of sorting ~150 micron from ~450 micron particles."
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

## Background
Sorting small particles is a popular and widely applicable challenge in microfluidics and medicine. This is because this simple function can lead to several powerful applications, such as separating cancer and blood cells for the study of circulating tumor cells (CTC's) [[1]](https://www.sciencedirect.com/science/article/pii/S0255270124004252#bib0131). There are several different methods for separating small particles, such as through filtering or through centrifugation. The method employed here, however, is pinch flow fractionation.

(Insert pic of PFF here)

Figure 1 - Pinch flow fractionation visualization

Pinch flow fractionation works through taking advantage of the natural flow spread of fluid past a sharp exit. When fluid flows from a thin channel to a broad one, the streamlines in the flow spread out proprtional to the width ratio between the two channels. In PFF, a particle containing inlet stream and a high flow rate fluid stream are made to collide at an angle, pushing all the particles to the upper channel wall. Once the flow spreads out, the particles spread out into streamlines based on their center of mass. This results in smaller particles ending up above larger ones, since their center of mass is closer to the narrow channel's upper wall. In more rigorous terms, the final position of the particles can be predicted based on the particle diameter, the pinched channel width, and the broad channel width. Thus by splitting the resulting flow, small particles can be sorted into bins of a range of sizes.

In practice, differences in flow resistance and flow rate, siphoning effects, presence of bubbles, and turbulent flow regions make this solution non-trivial to implement. This design then serves as a way to advance the efforts in implementing PFF in a simple manner, using as few outlet channels or active flow rate controls as possible.

## Problem Statement
Biomedical engineers need a better way to implement PFF, as current designs suffer from sensitive flow pattern controls and unreliable performance

## Functional Requirements
* Must fit in a 50 x 75 mm wide microscope slide
* Must sort 125 - 150 μm particles from 425 - 500 μm particles
* Mold must be made through SLA methods for small feature sizes
* Design must leverage PFF and not use filtering methods
* Bubbles must be minimized
* Aspect ratio must be <4:1 (height to width of features)

## Design

(Insert pic of my design here)

Figure 2 - My design for a PFF device

My design was informed by a couple of factors. To begin, since there was only time for a single iteration, I decided to go for a more predictable design which can be modeled through simple equations. I also decided to keep the design symmetric, for a better chance of achieving parallel, non-distorted streamlines. Lastly, I tried to keep the internal volume of the channels as small as possible, to aid the device in achieving laminar flow. Based on these factors, I decided to go with a simple PFF device, based on the original 2004 paper [[2]](https://pubs.acs.org/doi/10.1021/ac049863r).

For a simple PFF device, the location of the resulting particles can be predicted through the following equation...

(Insert labeled pic of major dimensions here)

Figure 3 - Major dimensions labeled on a PFF device

$$ Y_0=(w_p-\frac{D}{2})\frac{w_b}{w_p} $$

where $$ Y_0 $$ is the particle's position on the y-axis relative to the bottom of the broad region, $$ D $$ is the diameter of the particle, $$ w_p $$ is the width of the pinched region, and $$ w_b $$ is the width of the broad region. This equations suggests the following:

* Higher broad to pinched width ratio increases flow separation
* Smaller particles end up at higher positions
* The minimum pinched channel width is limited by the largest particle diameter

Taking these into consideration, the pinched width was made 600 μm and the broad width was made 30 mm. To see where the edge of the small and large particle bands are, you also have to add/subtract the radius of the particle, since a boundary hitting the middle of the particle would not create reliable splitting. From this, it was calcuated that the small particles will flow in a band between (X - X) mm, and the large ones within a band between (X - X) mm. So, to keep a symmetric profile, the regions were split at 8 mm and 22 mm, making the small particle and buffer outlet flows 8 mm wide, and the large particle outet flow 14 mm wide.

## Results
* Created a syringe pump capable of independent operation, only requiring wall outlet power to operate
* Syringe pump is capable of 0.1 – 5.0 mL/min flow rate, compatible with 10- and 20-mL syringes, and costs ~$90 to make from scratch
* See gallery and CAD model for extra information

## CAD Model

<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH90d2dQT28d5b60281188e565e158b1d8ed?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>

## User Instructions
<img src="/assets/img/Syringe-Pump-1.png" alt="Labeled front view of syringe pump" style="width:800px;"/>

Figure 1 - Labeled front view of the syringe pump

The buttons, from left to right:
* Potentiometer - Adjusts flow rate from 0.1 - 5.0 mL/min, in increments of 0.1
* Manual backwards button - Drives carriage backwards when the syringe pump is paused and/or empty
* Manual forwards button - Drives carriage forwards when the syringe pump is paused
* Pause button - Pauses operation of the syringe pump
* LED - Shines...
  * Green - if running
  * Yellow - if paused
  * Red - if empty

User instructions are as follows:
1. Update arduino code to match the used hardware (ex. syringe inner diameter)
2. Plug in the syringe pump to any common wall outlet 
  * It is recommended that the pump be paused, so that the syringe pump does not immediately start running
3. Retract the carriage until the syringe can be loaded into the pump. The barrel goes into the syringe-holding end support, and the plunger goes on the carriage, which has two slots. Clamp down the barrel with the M5 clamping screw at the front
  * The optional compatability sleeve is recommended for 10 mL syringes
4. Change the location of the empty switch if needed
5. Begin operation with the front panel

## Bill of Materials
Table I - Off-the-shelf Parts

| **Component**                       | **Count** |
|-------------------------------------|:---------:|
| NEMA-17 Motor                       |     1     |
| 2x8x200mm Lead Screw                |     1     |
| 8x200mm Linear Rod                  |     1     |
| 5mm to 8mm Flexible Coupler         |     1     |
| 8x8mm Brass Nut                     |     1     |
| 8mm Shaft Collar                    |     4     |
| V-Slot 20x40x300 Aluminum Extrusion |     1     |
| 8mm Linear Bearing                  |     2     |
| Flanged Ball Bearing                |     2     |
| M5x16 Bolt                          |     1     |
| M5x8 Bolt                           |     8     |
| M5 Tee Nut                          |     8     |
| M3x8 Thread Forming Screw           |     4     |
| M5 Heat Set Inserts for Plastic     |     5     |
| Potentiometer                       |     1     |
| Momentary Buttons                   |     2     |
| Latching Button                     |     1     |
| 3-color RGB LED                     |     1     |
| Limit Switch                        |     1     |
| Mean Well RT-65D Power Supply       |     1     |
| Breadboard                          |     1     |
| Arduino Uno                         |     1     |

*Note: BoM does not include minor components such as wires, fasteners used for collar clamps, or washers used for button placement*

Table II - Custom 3D-Printable Parts

| Component                   | Count |
|-----------------------------|:-----:|
| Motor Mounting Plate        |   1   |
| Simple End Support          |   1   |
| Syringe-holding End Support |   1   |
| Carriage                    |   1   |
| Limit Switch Holder         |   1   |
| Lid                         |   1   |
| Box                         |   1   |
| Compatability Sleeve        |   1   |


The Arduino code used to operate the syringe pump can be found [here](https://github.com/salomon-hernandez-soto/syringe-pump-arduino-code).

{% include gallery caption="Assorted related pictures from the syringe pump project." %}

