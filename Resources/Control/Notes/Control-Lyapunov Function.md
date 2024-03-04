---
tags: []
created: 2024-02-27 18:19
modified: 2024-02-27 18:19
---
A control-Lyapunov function (CLF) is an extension of the idea of [[Lyapunov Function]] $V(x)$ to systems with control inputs. A control-Lyapunov function is used to test whether a system is asymptotically stabilizable, that is whether for any state $x$ there exists a control $u(x,t)$ such that the system can be brought to the zero state asymptotically by applying the control $u$

Consider an autonomous dynamical system with inputs: $$
\dot{x}=f(x,u)
$$where $x \in \mathbb{R}^n$  is the state vector and $u \in \mathbb{R}^n$ is the control vector. Suppose out goal is to drive the system to an equilibrium $x^* \in \mathbb{R}^n$  from every initial state in some domain $D \subset \mathbb{R}^n$. Suppose the equilibrium is at $x^*=0$

**Def:** A control-Lyapunov function is a function $V:D\to \mathbb{R}$ that is continuously differentiable, positive-definite, and such that for all $x\in\mathbb{R}^n(x\ne0)$, there exist $u\in\mathbb{R}^m$ such that $$
\dot{V}(x,u):=\langle \nabla V(x),f(x,u)\rangle<0,
$$where $\langle u,v\rangle$ denotes the [[Inner Product]] of $u,v\in \mathbb{R}^n$ 

The last condition is for each $x$ we can find a control $u$ that will reduce the "energy" $V$. Intuitively, if in each state we can always find a way to reduce the energy, we should eventually be able to bring the energy asymptotically to zero, that is to bring the system to a stop. 

Some results apply only to [[Control-Affine Systems]] i.e. control systems in the following form:$$
\dot{x}=f(x)+\sum^m_{i=1}g_i(x)u_{i}
$$where $f:\mathbb{R}^n\to \mathbb{R}^n$ and $g_{i}:\mathbb{R}^n\to \mathbb{R}^n$ for all $i=1,\dots,m$

## Constructing the Stabilizing Input
It is often difficult to find a control-Lyapunov function for a given system, but if one is found, then the feedback stabilization problem simplifies considerably.

For the control-affine system [Sontag's formula](http://www.sontaglab.org/FTPDIR/sontag_mathematical_control_theory_springer98.pdf | 5.5.6) gives the feedback law $k:\mathbb{R}^n\to \mathbb{R}^n$ directly in terms of the derivatives of the CLF. In the special case of a single input system $m=1$ the formula can be written as: $$
k(x) = \begin{cases}
- \frac{L_{f}V(x)+\sqrt{ [L_{f}V(x)]^2+[L_{g}V(x)]^4 }}{L_{g}V(x)} & \text{if } L_{g}V(x)\ne0 \\
0 & \text{if } L_{g}V(x)=0
\end{cases}
$$where $L_{f}V(x):=\langle \nabla V(x),f(x)\rangle$ and $L_{g}V(x):=\langle \nabla V(x),g(x) \rangle$ are the [[Lie Derivatives]] of $V$ along $f$and $g$ respectively.

For a general nonlinear system, the input $u$ can be found by solving a static nonlinear programming problem:$$
u^* = \arg\min\nabla V(x)\cdot f(x,u)
$$for each state $x$

Source: https://en.wikipedia.org/wiki/Control-Lyapunov_function