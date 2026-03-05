---
title: "Microfluidic Particle Sorter"
excerpt: "This custom syringe pump is capable of 0.1 - 5.0 mL/min flowrate, and is compatible with common 10 mL and 20 mL syringes."
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
Sorting small particles is a popular and widely applicable challenge in microfluidics and medicine. This is because this simple function can lead to several powerful applications, such as separating cancer and blood cells for the study of circulating tumor cells (CTC's) [[1]](https://www.sciencedirect.com/science/article/pii/S0255270124004252#bib0131).

## Problem Statement
Medical practitioners need an affordable alternative to on-the-market syringe pumps, as even entry level models can cost between hundreds and thousands of dollars.

## Personal Contribution
* Led a 4-person team in the design and manufacture of an affordable syringe pump design
* Took a CAD model from design to real-life assembly using Fusion360 and 3D printing
* Created an electrical circuit, wired and soldered electrical components, and developed Arduino code for a professional, finished product using proper
logic for syringe pump use
* Led the drafting of the technical report detailing the endeavor

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

