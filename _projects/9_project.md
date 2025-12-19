---
layout: page
title: Custom-Built Centrifuge
description: Designed and engineered a fully functional centrifuge from scratch, integrating mechanical, electrical, and software components.
img: assets/img/centrifuge_screenshot.png
importance: 4
category: Systems Programming
---

## Demo for No-Touch Command Centrifuge

<video controls playsinline preload="metadata" style="width: 100%; max-width: 900px; border-radius: 10px;">
  <source src="{{ '/assets/video/NoTouchCommand.mov' | relative_url }}" type="video/quicktime">
  Your browser does not support the video tag.
</video>

<div class="caption">
  Demo of the no-touch initiation/cancellation command for the centrifuge.
</div>

## Novel Component: Accessible & Sanitary Commands

Implemented a distinct initiation and cancellation command used to both start and stop the centrifuge. This supports a more accessible and inclusive system for users with disabilities (e.g., paraplegic individuals, individuals with eyesight issues, Parkinson’s patients, etc.) and helps prevent the centrifuge from becoming unsanitary or contaminated through repeated physical contact.

## No-Touch Command Design

The no-touch command uses an **LED–phototransistor** pair that is identical in principle to the optical system used for the rotational speed counter, but with a different occlusion target:

- **Speed counter**: the rotor base blocks the LED light as it rotates.
- **No-touch command**: the user’s hand blocks the LED light.

### Signal path and logic

- The phototransistor output is fed into a **comparator**.
- The comparator outputs a digital signal to the **Arduino**.
- When the comparator output is **low** (indicating the LED light is blocked by the user’s hand), the Arduino triggers:
  - **Initiation (start)** on the first hand-block event
  - **Cancellation (stop)** on the second hand-block event

## System Block Diagram

<div class="row justify-content-sm-center">
  <div class="col-sm-12 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/BlockDiagram.png" title="Block diagram of the centrifuge system" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Figure 1: Block diagram of entire centrifuge system that includes the overall input and output and the mechanical, control, sensor, and actuator subsystems contributing to the centrifuge’s function.
</div>

## Circuit Implementation (Built + Schematic)

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/BuiltCircuit.png" title="Circuit built" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/CircuitSchematic.png" title="Circuit schematic" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Figure 3: Circuit built (left) and circuit schematic (right) that represent the controller, visual unit, part of the rotational speed counter, and part of the user interface blocks of the block diagram. Note there are two comparator systems: one for the speed counter (connected to pin 7) and one for the no-touch command (connected to pin 8). The Arduino receives input signals from the button and two comparators and outputs signals to the motor and LCD screen.
</div>
