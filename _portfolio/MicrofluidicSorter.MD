---
title: "Microfluidic Particle Sorter (W.I.P)"
excerpt: "This microfluidic particle sorter is capable of sorting ~150 micron from ~450 micron particles."
header:
  image: /assets/img/PFF-Banner.JPEG
  teaser: /assets/img/PFF-Thumbnail.JPEG
gallery:
  - url: /assets/img/PFF-Mold.JPEG
    image_path: /assets/img/PFF-Mold.JPEG
    alt: "Mold used to cast the PFF device"
  - url: /assets/img/PFF-Thumbnail.JPEG
    image_path: /assets/img/PFF-Thumbnail.JPEG
    alt: "Picture of my microfluidic sorter"
  - url: /assets/img/PFF-Visualization.png
    image_path: /assets/img/PFF-Visualization.png
    alt: "Visualization of how PFF works and the major dimensions"
---

## Background
Sorting small particles is a popular and widely applicable challenge in microfluidics and medicine. This is because this simple function can lead to several powerful applications, such as separating cancer and blood cells for the study of circulating tumor cells (CTC's) [[1]](https://www.sciencedirect.com/science/article/pii/S0255270124004252#bib0131). There are several different methods for separating small particles, such as through filtering or through centrifugation. These methods, however, may be prone to clogging or may require active filtering. The method employed here is pinch flow fractionation, which runs passively, continuously, and with a lower chance for clogging than other techniques.

<img src="/assets/img/PFF-Paper-Figure-1.jpg" alt="Visualization of PFF sorting two particles in a fluid flow" style="width:800px;"/>
Figure 1 - Pinch flow fractionation visualization from the original 2004 paper [[2]](https://pubs.acs.org/doi/10.1021/ac049863r)

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

## CAD Model
<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH90d2dQT28d5b602811109f64f9701b0d9d?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>

## Design
<img src="/assets/img/PFF-Thumbnail.JPEG" alt="Picture of the finished casted PFF sorter part" style="width:800px;"/>
Figure 2 - My design for a PFF device

My design was informed by a couple of factors. To begin, since there was only time for a single iteration, I decided to go for a more predictable design which can be modeled through simple equations. I also decided to keep the design symmetric, for a better chance of achieving parallel, non-distorted streamlines. Lastly, I tried to keep the internal volume of the channels as small as possible, to aid the device in achieving laminar flow. Based on these factors, I decided to go with a simple PFF device, based on the original 2004 paper [[2]](https://pubs.acs.org/doi/10.1021/ac049863r).

For a simple PFF device, the location of the resulting particles can be predicted through the following equation...

<img src="/assets/img/PFF-Visualization.png" alt="Visualization of major dimensions in a PFF device" style="width:800px;"/>
Figure 3 - Major dimensions labeled on a PFF diagram

$$ Y_0=(w_p-\frac{D}{2})\frac{w_b}{w_p} $$

where $$ Y_0 $$ is the particle's position on the y-axis relative to the bottom of the broad region, $$ D $$ is the diameter of the particle, $$ w_p $$ is the width of the pinched region, and $$ w_b $$ is the width of the broad region. This equations suggests the following:

* Higher broad to pinched width ratio increases flow separation
* Smaller particles end up at higher positions
* The minimum pinched channel width is limited by the largest particle diameter

Taking these into consideration, the pinched width was made 600 μm and the broad width was made 30 mm. To see where the edge of the small and large particle bands are, you also have to add/subtract the radius of the particle, since a boundary hitting the middle of the particle would not create reliable splitting. From this, it was calcuated that the small particles will flow in a band between 26.18 - 26.94 mm, and the large ones within a band between 17.25 - 19.59 mm. So, to keep a symmetric profile, the regions were split at 8 mm and 22 mm, making the small particle and buffer outlet flows 8 mm wide, and the large particle outet flow 14 mm wide. Note also that the flow separation points are rounded, to reduce bubbles and promote laminar flow.

To tackle the flow balancing problem, a strong attempt was made to keep the pressure differential for each outlet channel equal. The following derivation shows the equation used behind this method, taking into account the outlet channels are rectangular in shape. Note that outlet A is the small particle channel, outlet B is the large particle channel, and outlet C is the buffer channel. Outlets A and C share all geometry due to symmetry.

$$ \Delta P_{A/C} = \Delta P_B $$

$$ \Rightarrow R_{A/C}Q_{A/C} = R_BQ_B $$

$$ \Rightarrow R_{A/C} \frac{Q_{A/C}}{Q_B} = R_B $$

Now relating the geometry of the outlets to the flow rate...

$$ \frac{Q_{A/C}}{8mm} = \frac{Q_B}{14mm} $$

$$ \Rightarrow \frac{Q_{A/C}}{Q_B} = \frac{8}{14} $$

$$ \Rightarrow \frac{8}{14}R_{A/C} = R_B $$

Plugging back to the original equation..

$$ \Rightarrow \frac{8}{14}R_{A/C} = R_B $$

$$ \Rightarrow \frac{8}{14} (\frac{1}{1-0.63\frac{h_{A/C}}{w_{A/C}}} \frac{12 \mu_{A/C} l_{A/C}}{h_{A/C}^3 w_{A/C}}) = \frac{1}{1-0.63\frac{h_B}{w_B}} \frac{12 \mu_B l_B}{h_B^3 w_B} $$

And finally since the fluid viscosity is constant for both outlets, and if we keep the width and height of each outlet channel the same this simplifies to...

$$ l_{A/C} = \frac{14}{8}l_B $$

Some additional considerations are maintaining laminar flow, which is made easier with a smaller width and height, and reducing the resistance contribution of the sloped gradient region and the external outlet tubing, which is done by increasing the resistance of the straight rectangular outlet channels. From this, the outlet channel width was made 1.4 mm, the outlet channel height was made 0.7 mm, the outlet B length was made 19 mm, and the outlet A and C lengths were made 33.25 mm.

Overall, the design choices were made to be conducive for parallel streamlines and ideal flow.

## Instructions
The creation of the microfluidic device was quite simple, but was done carefully to avoid any defects. The inside of the mold was never touched to avoid affecting the roughness of the casted part.

<img src="/assets/img/PFF-Mold.JPEG" alt="Clear resin-printed mold used to cast the microfluidic device" style="width:800px;"/>
Figure 4 - Mold used to cast the particle sorter body

Fistly, the mold was printed out of FormLabs' Clear Resin v5, for easy visibility of design features. A layer height resolution of 0.05 mm was used to ensure all height dimensions were kept accurate. The mold was cleaned for 5 minutes while attached to the buildplate, and 5 miniutes while off the buildplate, keeping this time short to avoid IPA absorption. The mold was dried at an incline for 45 minutes to allow IPA to dry and drip out. The mold was then blown with compressed air to dislodge debris. Lastly, the mold was cured at room temp for 1 minute only, to ensure no warping occurs.

<img src="/assets/img/Plasma-Treating-Image.jpg" alt="Plasma treating of the PDMS mold and a glass slide" style="width:800px;"/>
Figure 5 - Plasma treating of the mold

This mold was then casted out of PDMS and treated so that it could bond with a glass slide.

## Discussion
Resin printing was chosen for the manufacturing method of the mold. This is because resin printing allows for quick printing of fine detail parts. On this note however, resin printing does have a resolution limit. For example, the smallest layer height that can be made is 25 microns, and the XY resolution for a Form 4 printer is 50 microns. On top of fabrication challenges with casting tiny features, this puts a limit on how small of a particle the device can sort, since for larger flow separation you need either a very narrow pinched channel or a very wide broad channel.

On a related note, to allow for more particles of different sizes, the device would likely have to be scaled up, and the outlet channel locations and lengths would have to be recalculated according to the earlier calculations. However, the methods detailed earlier make this process replicable, though the device may not be able to be kept symmetrical based on the expected particle sizes and number of size categories needed.

As for the performance of the device, difficulty with casting the device caused the flat surface of the device to be tilted, distorting the resistance of the channels and the performance of the device. Additionally, a thin casted layer made it difficult to anchor the microfluidic barbs. Lastly, operator error caused the device to malfunction. Clearly, the major improvements lie with the testing of the devices, such as creating a stand for the particle-containing syringe pump, improving casting technique, and perhaps replacing flexible tubing with rigid tubing, to avoid disturbances. The device could have also been optimized for easier casting by increasing the height of the channels, or optimized for easier testing by increasing the width of the pinched and broad section to avoid clogging or collisions. However, these come with the drawbacks of space limitations on the glass slide and potentially worsening the laminar flow profile of the device. One interesting feature to explore would be the addition of a separation enhancer as well [[3]](https://pubs-aip-org.proxy.library.vanderbilt.edu/aip/apl/article/93/20/203507/336137/Separation-enhancement-in-pinched-flow), to make the device more robust to outer disturbances.

Embeded below is footage of fellow student Kathleen's device which makes use of enhanced PFF. Note how the enhancer segment pulls the large particles further down. This idea explored further could lead to more robust devices in the future that can operate with less precise testing conditions.

{% include video id="SAfPZsFUudo" provider="youtube" %}

{% include gallery caption="Assorted related pictures from the microfluidic sorter project." %}

