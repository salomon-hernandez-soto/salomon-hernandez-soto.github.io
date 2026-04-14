---
title: "Bike Phone Holder (W.I.P)"
excerpt: "This bike phone holder can hold a phone in landscape or portrait orientation."
header:
  image: /assets/img/Holder-Banner.JPEG
  teaser: /assets/img/Holder-Thumbnail.JPEG
gallery:
  - url: /assets/img/Holder-Renders.png
    image_path: /assets/img/Holder-Renders.png
    alt: "CAD Renders of the bike phone holder in use"
  - url: /assets/img/PFF-Thumbnail.JPEG
    image_path: /assets/img/PFF-Thumbnail.JPEG
    alt: "Picture of my microfluidic sorter"
  - url: /assets/img/PFF-Visualization.png
    image_path: /assets/img/PFF-Visualization.png
    alt: "Visualization of how PFF works and the major dimensions"
---

## Background
This project was done mainly as an exercise in top-down modeling. In CAD, parts can either be created individually and brought together as an assembly, or they can be made in the context of an assembly in relation to other parts. The latter is called top-down modeling, and it is a powerful way to design models quickly. 

Top-down modeling was leveraged here as for a bike phone holder, there are many interlocking parts that have to fit together, from the detent mechanism used to rotate the phone, to the clamp that fits on the handlebars, and to the holding mechanism itself. Since top-down modeling creates parts in relation to each other, updating one part updates all the other parts that are affected by its geometry. This was critical for the bike phone holder design, as it consists of 10 parts which affect each other in many ways, such as for tool clearances or for proper part tolerancing.

## Functional Requirements
* Must fit on 23 mm – 25 mm handlebars
* Must be able to rotate phone between portrait and landscape orientations
* Must clamp onto the phone securely
* Must be created with top-down modeling

## CAD Model
<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH90d2dQT28d5b602811b1b77df3680c571c?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>

## Design
<img src="/assets/img/Holder-Design.JPEG" alt="Picture of the bike phone holder on handlebars, holding a phone" style="width:800px;"/>
My design consists of two notable features, the detent mechanism and the clamping mechanism.


<img src="/assets/img/Holder-Section-View.png" alt="Cross-sectional views of the detent mechanism" style="width:800px;"/>
A detent mechanism is one that locks onto some number of positions. This is useful as it allows rotation onto specific angles, which is perfect for locking a phone into landscape or portrait orientations. Here, the detent was implemented through a circular hub holding a spring and a ball, fitted into an outer hub with ball indentations. As the hub rotates, the spring pushes the ball into the wall, which naturally stops at the ball indentations. It then locks until enough torque is applied for the ball to move inwards again. The force was found through printing a small testing mechanism with varying indentation depths and then feeling by hand which depth gave the best “sweet spot” between too little and too much holding strength.

(Insert pic of rack and pinion mechanism)
The clamping mechanism works through a rack and pinion design. A rack and pinion is a gear system that translates rotation into linear motion. This was perfect for keeping the clamping hands symmetrical, such that when one clamp moves outwards, the other does as well. This looks aesthetically pleasing and distributes the weight of the phone evenly throughout the device. More info on gears can be found [here].

The gears were made with a module of 1.5 and a pressure angle of 25 degrees. Also, the gear is relatively large, having a 31.5 cm pitch diameter. These choices were made to get relatively large teeth, as 3D-printing tolerances can be quite loose, which ruins the involute teeth profile for small-tooth gears. The rack and pinion profiles were generated [here]. 

## Assembly and Use Instructions
(Insert BOM)

To assemble the holder, start by placing heat set inserts inside all of the holes. There are two M5 inserts on the bottom clamp, four M3 inserts on the top clamp’s top face, two M3 inserts on the top of the circular hub, one M3 insert in the middle of the holder centerpiece, and one M3 insert on the back of both phone clamps.

First, assemble the clamp. Then, attach the circular hub to the top clamp. Next, squeeze the spring and ball into the rotating cylinder’s hole and squeeze it into the circular hub. Next, put the lid on top of the hub to stop the cylinder from coming out, and press the centerpiece into the hex head, making sure the phone orientation will be correct. Finally, install the gears, install the phone clamps in a symmetric fashion, and install the extension spring in the back, holding the ends with M3 screws and nuts. If you’ve done it right, the holder will be able to clamp onto a handlebar and rotate like this!

<img src="/assets/img/Holder-Rotation.gif" alt="GIF of the holder going through all 8 rotation positions, including landscape and portrait" style="width:800px;"/>
## Manufacturing Methods
For the phone clamps, powder printing with Nylon 12 powder was used. Though they can be filament printed, the support material makes it very difficult to get a smooth fit for the rack, and since the rack is effectively a thin cantilever beam, it benefits a lot from the strong mechanical properties of Nylon 12 powder.

For all other parts, filament printing with PLA was used, with 4 perimeter walls on the centerpiece due to the thin phone ledge. The whole assembly was optimized for minimal support material, so filament printing offered the quickest and easiest prototyping. Theoretically, other technologies could be used, but resin printing was not an option for any parts with heat set inserts, as resin printing uses thermoset polymers.

(Pics of individual components and CAD render of holder + phone in the gallery)

{% include gallery caption="Assorted related pictures from the bike phone holder project." %}
