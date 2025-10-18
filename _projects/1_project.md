---
layout: page
title: HACKER FAB
description: Designing DIY lithography systems for accessible semiconductor fabrication - contributing to Stepper v2.1, a precision optical patterning tool.
img: assets/img/hacker_fab.jpg
importance: 1
category: work
related_publications: true
github: https://github.com/hacker-fab/stepper_cad
---

## Overview

[CMU Hacker Fab](https://hackerfab.org/) is an open-source initiative to democratize semiconductor fabrication by creating DIY machines and processes that enable anyone with internet access to fabricate semiconductor devices. Our mission is to make chip fabrication accessible beyond expensive cleanroom facilities.

During my time with the team, I contributed to the design and development of the **Lithography Stepper v2.1**, a critical tool in the photolithography process for patterning micron-scale features onto semiconductor wafers.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_img/project1/stepperv2.1.webp" title="Stepper v2.1" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    CAD design of Stepper v2.1 - a complete redesign focused on mechanical rigidity and vibration reduction.
</div>

## Lithography Stepper v2.1

The Stepper v2.1 is an automated photolithography system that projects UV patterns onto photoresist-coated wafers with micron-level precision. It represents a significant evolution from Stepper v2, with fundamental redesigns to improve mechanical stability and optical performance.

### Key Technical Specifications

- **Optical Resolution**: 1 µm (theoretical), 2 µm (developed)
- **Exposure Area**: 1.04 mm × 0.58 mm per exposure
- **Mechanical Step Size**: 1.5 µm
- **Vibration Tolerance**: 1.2 µm peak-to-peak (on optical table)
- **Alignment Accuracy**: 5 µm overlay accuracy
- **Total Cost**: ~$3,000 in parts
- **Core Technology**: TI DLP projector with UV-modified optics

### Design Improvements and Contributions

The v2.1 iteration introduced several critical improvements over v2, many of which I contributed to during the mechanical design phase:

#### 1. **Rotated Optical Architecture**
We redesigned the optical path to orient the objective lens downward instead of sideways. This fundamental change allowed us to utilize the high-precision X-Y axes of the motion stage (previously only X-Z were used), dramatically improving movement resolution and repeatability. This also eliminated the need for a vacuum chuck, reducing system complexity and vibration sources.

#### 2. **Rigid Mechanical Frame**
A major source of vibration in v2 was the flexible mounting of optics relative to the projector housing. For v2.1, I worked on designing a rigid mounting system using optical posts and a custom aluminum plate to directly secure all optical components. This decoupled the stepper's structural integrity from the projector's plastic case, reducing relative motion between optics and stage.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_img/project1/frame_image.avif" title="Frame Assembly" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Vibration characterization showing sub-2-micron stability during 10-second exposure window.
</div>

#### 3. **Improved Camera System**
We switched from a FLIR Blackfly (1" sensor) to a Basler Ace camera (1/1.2" sensor). This change reduced cost while providing better software support through Basler's Pylon Viewer suite. The smaller sensor is optimized for our actual field of view, eliminating unused sensor area.

#### 4. **Vibration Characterization**
I developed a quantitative vibration testing protocol using high-speed imaging and ImageMagick processing. By capturing 10-second video clips of chip features and analyzing frame-to-frame deviations, we measured a maximum vibration amplitude of **1.2 µm** under ideal conditions - a substantial improvement over v2.

### CAD and Mechanical Design

My primary contributions were in the mechanical CAD design using SolidWorks, focusing on:
- Custom adapter plates for rigid optics mounting
- Motor and sensor mounts for the XYZ motion stage
- Alignment fixtures ensuring optical axis parallelism
- Thermal management considerations for the UV LED array

The complete CAD files and build documentation are available on the [Hacker Fab GitHub](https://github.com/hacker-fab/stepper_cad) and [documentation site](https://docs.hackerfab.org/home/fab-toolkit/patterning/lithography-stepper-v2.1).

## Impact and Future Work

The Stepper v2.1 has enabled reliable photolithography for feature sizes down to 2 µm, supporting the fabrication of MOSFETs and basic integrated circuits in a DIY setting. The mechanical improvements have set the foundation for future work on automatic alignment systems and potentially custom DLP projector designs for better UV control.

This project exemplifies how thoughtful mechanical design, rigorous characterization, and open-source collaboration can make advanced manufacturing accessible to researchers and makers worldwide.
