---
tags: []
created: 2024-02-27 20:50
modified: 2024-02-27 20:50
---
Lyapunov functions are scalar functions that may be used to prove the [[Lyapunov's Stability Theory|Stability]] of an [[Equilibrium Point|Equilibrium]] of an ODE. 

For some classes of ODEs, the existence of a Lyapunov function is a necessary and sufficient condition for stability. Whereas there is no general technique for constructing Lyapunov functions for ODEs, in many specific cases the construction of Lyapunov functions is known.

# Definition
A Lyapunov function for a autonomous dynamical system $$
\begin{cases}
g:\mathbb{R}^n \to \mathbb{R}^n \\
\dot{y}=g(y)
\end{cases}
$$with an equilibrium point at $y=0$ is a scalar function $V:\mathbb{R}^n\to \mathbb{R}$ that is 
- Continuous
- Has continuous first derivatives
- Is strictly positive for $y\ne 0$ 
- $\dot{V}=\nabla V\cdot g$ is non-positive or written as $\nabla V\cdot g$ is locally negative definite

# Basic Theorem
Let $x^*=0$ be an EP of the autonomous system $$
\dot{x}=f(x)
$$and use the notation $\dot{V}(x)$ to denote the time derivative of the Lyapunov-candidate-function $V$: $$
\dot{V}(x)=\frac{d}{dt} V(x(t))=\frac{ \partial V }{ \partial x } \cdot \frac{dx}{dt} = \nabla V\cdot \dot{x}=\nabla V\cdot f(x)
$$
## Notes
- See [[Lyapunov's Stability Theory]] for some applications
- Is used for control purposed through [[Control-Lyapunov Function]]