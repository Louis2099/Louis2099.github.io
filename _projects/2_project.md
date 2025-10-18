---
layout: page
title: Object Tracking Robot
description: A ROS2-based autonomous robot using YOLOv8 and Isaac ROS for real-time detection and tracking of 80 COCO dataset objects with stereoscopic depth perception.
img: assets/img/project_img/project2/Finding the Teddy Bear_short - SD 480p.gif
importance: 2
category: work
giscus_comments: true
github: https://github.com/w3ichen/18842_A7.git
---

## Overview

This project was developed as the final assignment for **Autonomous Robotics I** (Spring 2025) at Carnegie Mellon University, taught by [Prof. Ziad Youssfi](https://z4ziad.github.io/2025-05-13-auto_robo_update_2/). The goal was to build an autonomous mobile robot capable of finding and tracking any user-specified object from the 80 classes in the COCO dataset using state-of-the-art computer vision and robotics frameworks.

The robot successfully integrates deep learning-based object detection, ROS 2 (Robot Operating System 2) for distributed control, and NVIDIA's Isaac ROS accelerated libraries for real-time inference on edge computing hardware.

## System Architecture

### Hardware Platform
- **Mobile Base**: Waveshare JetBot chassis with differential drive
- **Computing**: NVIDIA Jetson Orin Nano (GPU-accelerated edge AI computer)
- **Vision**: Intel RealSense D435i camera with RGB and stereoscopic depth sensing
- **Power**: Onboard battery system for autonomous operation

### Software Stack
- **Operating System**: Ubuntu 20.04 with ROS 2 Foxy
- **Object Detection**: YOLOv8 (You Only Look Once) trained on COCO dataset
- **Acceleration**: NVIDIA Isaac ROS for GPU-optimized computer vision pipelines
- **Control Framework**: ROS 2 Action Server/Client architecture for asynchronous task management

## Implementation

The system was implemented using a distributed ROS 2 architecture:

### 1. **Perception Pipeline**
- Real-time video streaming from Intel RealSense camera
- Hardware-accelerated YOLOv8 inference using Isaac ROS DNN nodes
- Detection of 80 object classes (person, car, bottle, teddy bear, etc.) with confidence scores
- Depth estimation for 3D localization of detected objects

### 2. **ROS 2 Action Server**
- Implemented a custom action server for object search and tracking tasks
- Accepts client requests specifying target object class
- Provides feedback on search progress (scanning, object detected, tracking)
- Returns success/failure status with final object position

### 3. **ROS 2 Action Client**
- Command interface allowing users to specify target objects
- Handles action goal submission and result processing
- Manages state transitions between searching, tracking, and idle modes

### 4. **Motion Control**
- Differential drive controller for base navigation
- PID-based visual servoing to center target in camera frame
- Adaptive speed control based on object distance and confidence
- Obstacle avoidance using depth information

## Performance and Results

The robot successfully demonstrated autonomous object finding and tracking capabilities across multiple object classes:

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_img/project2/Finding the Teddy Bear_short - SD 480p.gif" title="Teddy Bear Tracking" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_img/project2/Finding an orange_short - SD 480p.gif" title="Orange Detection" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Real-time demonstrations: (Left) Successfully finding and tracking a teddy bear; (Right) Detecting and tracking an orange among other objects.
</div>

### Key Achievements:
- **Detection Accuracy**: Successfully detected target objects with >90% confidence in varied lighting conditions
- **Tracking Stability**: Maintained continuous visual tracking while navigating toward targets
- **Real-time Performance**: Achieved 15-20 FPS inference rate on Jetson Orin Nano
- **Multi-object Handling**: Correctly distinguished between different object classes in cluttered scenes
- **Depth Integration**: Used stereoscopic depth for distance estimation and approach control

### Technical Highlights:
- **Robust Object Recognition**: YOLOv8's single-shot detection enabled fast, accurate identification without manual feature engineering
- **GPU Acceleration**: Isaac ROS reduced inference latency by ~3x compared to CPU-only implementation
- **Asynchronous Control**: ROS 2 action framework allowed non-blocking task execution with real-time feedback
- **Modular Architecture**: Clean separation between perception, planning, and control enabled rapid debugging and iteration

## Challenges and Solutions

### Hardware Logistics
The project faced significant logistical challenges with late delivery of the robot base and supply constraints on the Jetson Orin Nano (NVIDIA's price reduction led to widespread unavailability). Despite having only a few weeks for hardware testing, the team successfully integrated all components and achieved the demonstration objectives.

### Software Integration
Integrating Isaac ROS with custom ROS 2 nodes required careful attention to message types, timing, and GPU memory management. The solution involved using ROS 2's component composition for efficient zero-copy message passing and configuring Isaac ROS parameters for optimal Jetson performance.

## Future Improvements

Potential enhancements identified for future iterations:
- Integration with **Isaac Sim** for software-in-the-loop testing before hardware deployment
- Implementation of **Visual SLAM** for autonomous mapping and localization
- **Path planning algorithms** (e.g., A*, RRT) for navigation in complex environments
- **SMACC2 state machines** for more structured behavior management
- Multi-object tracking for simultaneous detection of multiple targets

## Course Context

This project synthesized knowledge from three main course modules:
1. **Deep Learning Fundamentals**: Understanding CNNs, loss functions, and training pipelines
2. **ROS 2 Ecosystem**: Publishers, subscribers, services, actions, and distributed systems
3. **Isaac ROS Integration**: GPU-accelerated perception for real-time robotics applications

The hands-on nature of the project made abstract ML concepts tangible and demonstrated the practical challenges of deploying AI on resource-constrained robotics platforms. Special thanks to Prof. Ziad Youssfi and the teaching assistants for their support throughout the semester!
