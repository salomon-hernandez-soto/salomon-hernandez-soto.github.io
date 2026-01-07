---
title: "Custom Syringe Pump"
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
Syringe pumps are devices that administer precise drug doses and calibrate injections.
They are mostly used in microfluidics as well as in the biomedical field and in hospitals. Syringe
pumps exist in lots of different variations, with different footprints, varying smart features, and
with flow rates varying from 0.012 to 300 mL/min [[1]](https://www.sciencedirect.com/topics/engineering/syringe-pump). However,
syringe pumps can cost anywhere between hundreds and thousands of dollars, which limits their
use due to financial reasons. A more affordable alternative is to design, purchase, and 3D print
components for a syringe pump. The following sections detail the design process and results of
an affordable syringe pump design, made with custom 3D-printed components, simple machine
parts, and basic electronic components.

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

<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH90d2dQT28d5b60281188e565e158b1d8ed?mode=embed" width="800" height="600" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>

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
1. Will
2. Finish
3. Later

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

The Arduino code used to operate the syringe pump can be found [here](https://github.com/salomon-hernandez-soto/syringe-pump-arduino-code)

{% include gallery caption="Assorted related pictures from the syringe pump project." %}
