---
title: 'Control-"abilities" you should know'
date: 2024-03-17
permalink: /posts/2024/03/Control-abilities you should know/
collections: posts
tags:
  - control-system-analysis 
  - controllability
  - observability
  - duality
  - reachability
  - detectability
---

![Illustration](/images/sd.jpeg "Illustration")

**Controllability** is a stronger property that ensures the system can be steered from any initial state to any desired final state within a finite time by applying appropriate control inputs. 

**Reachability** is a local property specific to a given initial state and determines whether a specific final state can be reached from that initial state using a suitable control input.  

**Stabilizability** refers to the ability to stabilize a system using feedback control, meaning that there exists a feedback control law that can make all the unstable modes of the system stable. 

**Observability** is the dual concept of controllability and deals with the ability to determine the system's internal states based on the measured outputs. 

**Detectability** is a weaker property that ensures the ability to estimate the unstable modes of the system from the measured outputs, which is necessary for stabilization using output feedback.

**Constructability** is a concept related to the physical realizability of a control system, considering factors such as actuator and sensor placement, and the feasibility of implementing the designed control law.

The tree will show the hierarchy and connections between the properties, with the most fundamental properties at the top and the more specific properties branching out:

<div style="font-size: 100%;">
<pre>
                       System Properties
                               |
               +---------------+--------------+
               |                              |
        Stabilizability                  Detectability
               |                              |
       +-------+-------+              +-------+-------+
       |               |              |               |
Controllability  Reachability   Observability Constructability
</pre>
</div>

- Stabilizability and Detectability are the two main branches, representing the weaker properties in control theory.
- Under Stabilizability, there are two sub-properties:
    - Controllability is a stronger property that implies Reachability.
    - Reachability is a local property that is implied by Controllability but does not necessarily imply Controllability.
- Under Detectability, there are two sub-properties:
    - Observability is a stronger property than Detectability.
    - Constructability is related to the physical realizability of the control system, considering factors such as sensor and actuator placement.

**Note:**
- Controllability implies Reachability.
- Stabilizability is a weaker property than Controllability.
- Observability implies Detectability.
- Detectability is a weaker property than Observability.
- Constructability is a practical consideration related to the physical implementation of the control system and is not directly related to Observability or Controllability.

Controllability, stabilizability, and reachability are primarily concerned with the system's inputs and how they affect the system's states. These properties are related to the input-to-state behavior of the system and how the inputs can be used to control and manipulate the system's dynamics.

While, observability, detectability, and constructability are more concerned with the system's outputs and how they relate to the system's states. These properties are related to the state-to-output behavior of the system and how the outputs can be used to infer and estimate the system's internal states.

**Note:** while there is a primary focus on inputs or outputs for these properties, they are not entirely independent. The input-to-state and state-to-output behaviors are interconnected, and the properties are often analyzed together to get a comprehensive understanding of the system's characteristics.

For example:
- Controllability and observability are dual concepts, and the duality theorem relates the controllability of a system to the observability of its dual system.
- Stabilizability and detectability are related to the stability of the closed-loop system when using state feedback or output feedback, respectively.

In control system design, all these properties are considered to ensure that the system can be effectively controlled, stabilized, and monitored using available inputs and outputs. The input-related properties guide the design of control strategies, while the output-related properties guide the design of estimation and monitoring techniques.

**Duality:** Controllability and observability are dual concepts in control theory. They are mathematically related and exhibit a symmetry in their formulations. The duality arises from the fact that the roles of the input and output are interchanged when considering the dual system.
