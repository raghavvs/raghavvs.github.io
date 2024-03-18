---
title: "Robot-Camera-Robot Calibration / Localization"
excerpt: "Pose estimation, calibration, testing and validation pipeline <br/><img src='/images/calib_1.jpeg'>"
collection: portfolio
---

![Overview](/images/abb_axbycz.png "Overview")

*The code is available on [GitHub](https://github.com/RMDLO/abb_dual_arm).*

This work was done at Bretl's Research Group, University of Illinois Urbana-Champaign alongside Holly Dinkel.

The primary goal involved determining the relative pose between two industrial robotic arms (ABB IRB120) with millimeter accuracy. The setup of the workspace: two robotic arms, one equipped with an Intel RealSense D435 stereo-vision camera and a OnRobot 2FG7 Gripper on the other arm.

Please refer to the previous work to understand the prior status of the arms.

This kind of calibration is commonly referred as, AXB = YCZ multi-robot calibration.

## Taxonomy

**Knowns:**

- A - Transformation from base link to end effector of robot 1
- B - Transformation from camera to calibration board
- C - Transformation from base link to end effector of robot 2

**Unknowns:**

- X - Transformation from end-effector to camera
- Y - Transformation from base link of robot 1 to base link of robot 2
- Z - Transformation from end-effector to calibration board

**Calibration board:** - ChArUco 

The AXB = YCZ calibration problem in multi-robot systems is a challenging problem that requires finding three unknown static transformations from three sets of time-varying measurements.

## The Need for Calibration

- Multi-robot calibration is the process of estimating the relative poses and parameters of multiple robots or sensors that work together in a coordinated manner.

- Multi-robot calibration is essential for many applications that require accurate and consistent information from different sources, such as mapping, localization, navigation, exploration, surveillance, manipulation, and collaboration.

- Multi-robot calibration can improve the performance and robustness of multi-robot systems by reducing errors, increasing redundancy, and enhancing capabilities.

- However, multi-robot calibration is also a challenging problem that involves dealing with noise, outliers, occlusions, dynamic environments, and communication constraints.

***work in progress***
