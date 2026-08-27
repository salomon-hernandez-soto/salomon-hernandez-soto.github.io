---
title: "EchoArm (W.I.P)"
excerpt: "This 3-DOF human controlled robot arm is capable of lifting 1.1kg and won Best Implementation in a mechatronics showcase."
header:
  image: /assets/img/Holder-Banner.JPEG
  teaser: /assets/img/Holder-Thumbnail.JPEG
gallery:
  - url: /assets/img/Holder-Renders.png
    image_path: /assets/img/Holder-Renders.png
    alt: "CAD Renders of the bike phone holder in use"
  - url: /assets/img/Holder-Bottom-Clamp.png
    image_path: /assets/img/Holder-Bottom-Clamp.png
    alt: "CAD render of the bottom clamp"
  - url: /assets/img/Holder-Top-Clamp.png
    image_path: /assets/img/Holder-Top-Clamp.png
    alt: "CAD render of the top clamp"
---

## Background
This project was made as a full exercise of my mechatronics skillset. I decided to make a robot arm which the user can control with their own arm's movements. This makes it a remote-controlled actuator arm. The idea is that if the arm could be manufactured in a very large or very small scale, it would allow human dexterity at a non-human scale. Additionally, if the idea were taken further it could potentially be combined with a complete robotic body to allow remote control of a robot by a human, perhaps with VR goggles and a bodysuit. This idea also has existing applications in the medical field, through the form of microsurgical human-controlled robots [[1]](https://www.youtube.com/watch?v=Jln-NDaIVc8).

The EchoArm functions as a proof-of-concept of these ideas, a showcase of full-stack electromechanical product design, and as an expression of my joy for design, because this was a fun project from start to finish.

## Problem Statement
How might I create a human-controllable robot arm which demonstrates a proof-of-concept for a remote-controlled actuator arm, which can lift at least 500g, has a hemispherical range of motion, and costs under $200 to create?

## CAD Model
<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH90d2dQT28d5b602811b1b77df3680c571c?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>

## Design
(Insert GIF or video of me using the EchoArm)

Constructing and integrating the EchoArm includes knowing about the mechanical assembly, the electrical wiring, and the code driving the design. 

(Insert pic of EchoArm in a 3D print slicer)

The mechanical parts of the EchoArm are all 3D-printed components made of PLA filament, alongside off-the-shelf parts like fasteners and heat-set inserts. The box features space for a DC power supply, a breadboard, an Arduino Uno R3, and a servo motor. The robot base features slots for the base servo horn and for the shoulder servo body. The first arm link has slots for the shoulder servo horn and elbow servo body. The second arm link has slots for the elbow servo horn and for the gripper assembly. Finally, the gripper assembly has space for a smaller servo and servo claws, which are 4-bar linkages and move with a geared assembly that is attached to the plastic servo horn.

(Insert wiring diagram pic and IRL wiring pic)

The electrical wiring consists of the two MPU 6050 6-axis IMU’s, three DSSERVO 35 kg*cm servos, one TowerPro SG92R servo, one potentiometer, one momentary push button, one latching button, an RGB LED, a DC power supply, a breadboard, and an Arduino Uno R3. The IMU’s use 3.3V power from the Arduino, the LED’s and buttons use digital 0V/5V output from the Arduino, and the servos use 5V power from the DC power supply and digital output from the Arduino for all pulse-width data.

In the code, the two IMU’s use their accelerometers and gyroscopes to talk to the Arduino through I2C serial communication. This data is then converted to yaw-pitch-roll angles by the IMU’s digital motion processor, and the Arduino processes these angles to pulse-width output for the three larger servos. Alongside this, the potentiometer data is also collected and processed into pulse-width output for the smaller servo. The latching button is used to pause the device, the momentary button is used to calibrate the IMU’s while the device is paused, and the LED shows the status of the device, which can be red for paused, purple for calibrating, green for running, or yellow if the device is unpaused without having calibrated at least once.

## Assembly and Use Instructions
(Insert BOM Tables)

(Insert assembly instruction list)

{% include gallery caption="Assorted related pictures from the bike phone holder project." %}
