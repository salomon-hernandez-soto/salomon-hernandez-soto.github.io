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
Sorting small particles is a popular and widely applicable challenge in microfluidics and medicine. This is because this simple function can lead to several powerful applications, such as separating cancer and blood cells for the study of circulating tumor cells (CTC's) [[1]](https://www.sciencedirect.com/science/article/pii/S0255270124004252#bib0131). There are several different methods for separating small particles, such as through filtering or through centrifugation. These methods, however, may be prone to clogging or may require active filtering. The method employed here is pinch flow fractionation, which runs passively, continuously, and with a lower chance for clogging than other techniques.

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



{% include gallery caption="Assorted related pictures from the syringe pump project." %}

