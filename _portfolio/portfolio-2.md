---
title: "Autonomous Precision Landing of Model Rockets"
excerpt: "Our Model Rocket <br/><img src='/images/a4.png'>"
collection: portfolio
---

![Overview](/images/t8.png "Overview")

This project aims to build a model rocket that can land vertically. By establishing an automatic control system, we contrive to pull out any perturbations and disturbances ensuring active control. Thrust Vector Control (TVC) is the technique used for attitude (pitch and yaw) control, this gimbal mount allows the rocket to be actively stabilized and is the key component to allow the rocket to land vertically.

![Methodology: Design Phase](/images/Methodology_Design_Phase_1.png "Methodology: Design Phase")

A closed­loop feedback control system consisting of a Proportional Integral Derivative (PID) controller is employed to maneuver the rocket, additional components such as the Kalman Filter will be used to eliminate noise and disturbances from sensory feedback. A flight computer is utilized to monitor the rocket, this includes data logging, stabilization, prediction, and state indication. The rocket is powered by a solid propellant motor serving as the propulsion system.

![Methodology: Testing Phase](/images/Methodology_Testing_Phase_1.png "Methodology: Testing Phase")

The rocket body and its components are designed considering the principles of Design for Assembly (DFA) and Design for Manufacturing (DFM), using Computer­Aided Design (CAD) software and analyzed using Finite Element Method (FEM) solvers. Computational Fluid Dynamics (CFD) is applied to visualize the flow around the rocket airframe and to evaluate the design of passive fins.

# Dynamics

<div style="text-align:center">
    <img src="/images/rocket_FBD3.png" alt="Free Body Diagram" title="Free Body Diagram" />
</div>

## Rigid body dynamics (Euler's equations)

### Assumptions
- No roll
- No motion in Y-axis (lateral velocity = 0)


**Calculation:**\
\
$$ 
\text{Weight} = \text{Mass} \times 9.81 \\
\text{Net Force} = \text{Weight} - \text{Thrust} - \text{Drag Force} \\
\text{Acceleration} = \frac{\text{Net Force}}{\text{Mass}} \\
\text{Velocity} = \int \text{Acceleration} \\
\text{Drag Force} = \frac{1}{2} \times \text{Density} \times \text{Area} \times \text{Drag Coefficient} \times (\text{Velocity})^2 \\
\text{Position} = \int \text{Velocity} \\
$$

**Input:**
- Thrust
- TVC Misalignment Angle
- Moment Arm
- Inertia

**Actuator Subsystem:**\
\
$$
F_x = \text{Thrust} \times \sin(\theta_{\text{input}}) \\
F_z = \text{Thrust} \times \cos(\theta_{\text{input}}) \\
M_y = \text{Thrust} \times \sin(\theta_{\text{input}}) \times \text{Moment Arm} \\
$$

## 3 Degree of Freedom Equations

We obtain 3 DoF equations from 6 DoF equations following these assumptions:

1. No Roll i.e.  $\phi = 0$. As we do not have roll control, it is a reasonable assumption. 
2. No motion in Y axis i.e. v = 0, zero lateral velocity.

Zero roll angle ( $\phi = 0$) leads to decoupling of flat earth equations. Decoupling implies that the equations of motion separate into two independent sets. One set is longitudinal motion (pitching and translating in X-Z plane) and the other set describes lateral-directional motion (rolling, yawing and sideslipping).

The equations modeling the forces and moments on the rocket, as well as the transformation matrix for the angular rates, are given as:

$$
\begin{aligned}
\begin{bmatrix}
F_x - mg\sin(\theta) \\
F_y + mg\sin(\phi)\cos(\theta) \\
F_z + mg\cos(\phi)\cos(\theta) \\
\end{bmatrix}
=
m
\begin{bmatrix}
\dot{u} + qw - rv \\
\dot{v} + ru - pw \\
\dot{w} + pv - qu \\
\end{bmatrix}
\end{aligned}
\quad (46)
$$

$$
\begin{aligned}
\begin{bmatrix}
\dot{\phi} \\
\dot{\theta} \\
\dot{\psi} \\
\end{bmatrix}
=
\begin{bmatrix}
1 & \sin(\theta)\tan(\phi) & \cos(\theta)\tan(\phi) \\
0 & \cos(\phi) & -\sin(\phi) \\
0 & \sin(\theta)\sec(\phi) & \cos(\theta)\sec(\phi) \\
\end{bmatrix}
\cdot
\begin{bmatrix}
p \\
q \\
r \\
\end{bmatrix}
\end{aligned}
\quad (47)
$$

Substituting  $\phi = 0$  and \( v = 0 \) in equations (46) and (47), we get:

$$
\begin{aligned}
A_{xb} &= \dot{u} = \frac{F_x}{m} - qw - g\sin(\theta), & A_{xe} &= \dot{w} = \frac{F_x}{m} + \sin(\theta), \\
A_{zb} &= \dot{w} = \frac{F_z}{m} + qu + g\cos(\theta), & A_{ze} &= \frac{F_z}{m} + \cos(\theta)
\end{aligned}
\quad (48)
$$

$$
\dot{q} = \frac{M_y}{I_{yy}}, \quad \dot{\theta} = q, \quad \theta = \int \dot{\theta} \, dt \\
$$

In our case, the 3DoF results in $x, z$ translation motions and $\theta$ rotational motion.

## Control

The control algorithm is defined by the following equations:

$$
\text{Error} = \theta_{\text{Setpoint}} - \theta_{\text{Rocket Angle}} \quad (49)
$$

$$
\theta_{\text{input}} = K_p \times \text{Error} + K_d \times \frac{d(\text{Error})}{dt} + K_I \times \int \text{Error} \, dt \quad (50)
$$

## Output

The outputs of the system are the accelerations, trajectory, and orientation of the rocket:

- Accelerations $A_x$ and $A_z$
- Rocket Trajectory
- Orientation

![Thrust Test](/images/Thrust_Test_1.mp4 "Thrust Test")

![Thrust Test](/images/mr_thrust_curve.png "Thrust Curve")

<div style="text-align:center">
    <img src="/images/flowchart3.jpeg" alt="Flow Chart" title="Flow Chart" />
</div>
