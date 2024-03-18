---
title: 'Controllability'
date: 2024-03-18
permalink: /posts/2024/03/Controllability/
collections: posts
tags:
  - duality
  - observability
  - controllability
  - stabilizability
  - reachability
  - control-system-analysis
---

![Illustration](/images/ctrb.jpeg "Illustration")

<details>
  <summary><strong>Table of Contents</strong></summary>
  <ul>
    <li><a href="#what-is-controllability">What is controllability?</a>
      <ul>
        <li><a href="#how-to-test-for-controllability">How to test for controllability?</a></li>
        <li><a href="#where-does-this-fit-in-control-theory">Where does this fit in control theory?</a></li>
      </ul>
    </li>
    <li><a href="#what-are-its-limitations">What are its limitations?</a></li>
    <li><a href="#references">References</a></li>
  </ul>
</details>

## What is controllability?

Controllability is a property of a dynamical system that determines whether it can be steered from any initial state to any desired final state within a finite time by applying appropriate control inputs. For a linear time-invariant (LTI) system described by, 

$$ 
\dot x(t) = Ax(t) + Bu(t)
$$

where $x(t)$ is the state vector and $u(t)$ is the control input vector, controllability ensures that the system can be fully controlled.

**Is controllability independent of initial state?**

Yes. It can transition the state from any arbitrary initial state to desired final state in finite time.

### How to test for controllability?

For a LTI system, to test for controllability, we construct the controllability matrix 

$$C_c = [B \quad AB \quad A^2B \quad ... \quad A^{(n-1)}B]$$

where $A$ is the state matrix, $B$ is the input matrix, and $n$ is the dimension of the state vector. The system is controllable if and only if the controllability matrix $C_c$ has full row rank, i.e., $\text{rank}(C_c) = n$.

### Where does this fit in control theory?

In the broader context of control theory, controllability is a fundamental concept that plays a crucial role in various aspects of control system analysis and design. It is closely related to other key concepts such as observability, stability, and optimal control. Controllability is essential for analyzing system behavior, designing effective control strategies, ensuring system stability, and solving optimal control problems. It is also relevant in system identification, fault diagnosis, and tolerant control.

Controllability is assessed during the early stages of control system design to determine the feasibility of controlling the system and to guide the selection of appropriate control strategies. It finds applications in various domains, including robotics, aerospace systems, process control, power systems, and transportation systems. Whenever there is a need to control and regulate the behavior of a dynamical system, controllability becomes a fundamental consideration. 

## What are its limitations?

Controllability has some limitations:
1. It assumes a perfect model of the system, which may not always be available in practice.
2. It does not consider physical constraints on the control inputs or system states.
3. It is primarily defined for linear systems, and extending the concept to nonlinear systems can be challenging.
4. It does not address the issue of control effort or energy required to steer the system to the desired state.
5. Controllability tests, such as the rank condition of the controllability matrix, are well-defined for LTI systems. However, for linear time-varying (LTV) systems, where the system matrices A(t) and B(t) are functions of time, the controllability tests are more complex and less straightforward. The controllability matrix for LTV systems involves the state transition matrix, which can be difficult to compute analytically. As a result, controllability analysis for LTV systems often relies on numerical simulations or approximate methods.

## References

1. Hespanha, Joao P. *Linear Systems Theory*. Princeton University Press, 2018.
2. Brockett, Roger W. *Finite Dimensional Linear Systems*. Society for Industrial and Applied Mathematics, 2015.
