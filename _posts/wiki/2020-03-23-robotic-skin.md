---
title: Robotic Skin
description: Research Page
tags: [robotics,panda,simulator,research]
permalink: robotic_skin.html
---

# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}

# Introduction

{% include image.html url="research/skin_unit.png" max-width="72%" description="Flexible skin unit created by etching the circuit diagram into a copper sheet and then encasing it in the flexible polymer ecoflex." %}


Robots have been transitioning into human-populated environments and replacing physical separation from humans with complex perception and control software. However, current solutions are computationally expensive, prone to occlusion, and require a significant setup overhead.
Robots are in need of compact, self-contained sensing of nearby space to provide inherently safe interactions. In this work, we present the first prototype of a flexible, conformant whole-body artificial skin for collaborative robotics.
In order to locate all skin units on the surface of a robot, a novel kinematically calibration algorithm is required to reduce setup time.

# Contribution

1. <strong>Kinematic Calibration:</strong> we present a framework for automatic kinematic calibration that leverages an Inertial Measurement Unit (IMU) to automatically locate skin units, of arbitrary number, along the surface of a robot.

1. <strong>Skin Unit:</strong> we present a new <strong>flexible artificial skin</strong> that can conform to multiple surfaces. The skin utilizes an IMU and a proximity sensor to sense obstacles at a distance. Future prototypes will embed additional capabilities (e.g. pressure sensing, temperature sensing, tactile sensing...).

1. <strong>Control Example:</strong> we demonstrate an example control scenario where a robot arm utilizes artificial skin to <strong>avoid collision</strong>  with a human, increasing operational safety with and around people.


## Kinematic Calibration

To automatically locate skin units along the surface of a robot, we utilize an IMU that provides measurements of angular velocity and linear acceleration. Our optimization algorithm estimates the position and orientation of skin units using Denavit-Hartenberg as demonstrated in the figure below.

{% include image.html url="research/calibration.png" max-width="75%" description="Illustrated setup of skin units (S) placed along the robots links (L) that are separated by joints (J). We estimate the  Denavit-Hartenberg parameters of each joint in order to calculate the pose of each skin unit along the surface of the robot. " %}

## Skin Units

Skin units are embedded with an IMU for kinematic calibration and a proximity sensor to sense nearby objects. We chose to embed our circuit in a flexible polymer called ecoflex in order to have each skin unit conform to the shape of the surface it is placed on. The figure below shows the flexible capabilities of the skin sensor and an image of one unit mounted on a robotic arm.

{% include image.html url="research/skin_unit.jpg" max-width="50%" description="Flexible skin unit mounted on a robotic arm." %}

{% include image.html url="research/bent_skin_unit.jpg" max-width="50%" description="Demonstration of the skin’s flexible capabilities." %}

## Control Example

Calibrated skin units can be used to locate obstacles with respect to the robot’s links and avoid undesired collisions by exerting a repulsive force on the robotic arm. To avoid object we require the following information:

* Calibrated pose of the Skin Unit (x, y, z, φ, θ, ψ)
* Distance d normal to the skin sensor

With this information, we apply a repulsive force perpendicular to the skin unit as seen in the figure below.

{% include image.html url="research/control.png" max-width="75%" description=" A mounted skin unit exerting a repulsive force β on a robot's trajectory
<strong>T</strong> when an object is near the skin unit. The distance d is measured in millimeters. As an object approaches, β increases exponentially." %}


# Future Work

## 1. Dynamic Obstacle Avoidance

We plan to use proximity sensors embedded within each skin unit to avoid obstacles in two separate control schemes.

* End-effector movement
* Control point movement

As demonstrated in the paper “A Depth Space Approach to Human-Robot Collision Avoidance” by Flacco et al. a robot arm can avoid collision by exerting a repulsive vector to its end effector or control points along the robot arm. Both schemes can be used to increase safety when robots and humans work in close proximity.


## 2. Dense Coverage of a Robot Arm with Skin Units

In order to consistently avoid obstacles around the robot dense skin unit coverage is required. To achieve this goal we must efficiently distribute wiring and computational resources about the surface of the robot.
This has been accomplished by Mittendorfer et al. by using rigid printed circuit boards equipped with onboard microcontrollers and redundant connections in their paper “Realizing whole-body tactile interactions with a self-organizing, multi-modal artificial skin on a humanoid robot”.
Additional challenges arise due to the flexible and stretchable nature of our robotic skin that must conform to the surface it is placed on.

