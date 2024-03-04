---
tags: []
created: 2024-02-21 15:33
modified: 2024-02-26 17:19
---
Where we want a system to follow a reference input

**Def:** *Reference Tracking Error* $$
\underline{e}_{t} = \underline{y}-\underline{y}_{r} \tag{1}
$$The goal is to drive this error $\underline{e}_{t}$ to zero asymptotically i.e. have 0 steady state error.
Different from the error $$
\underline{e}=\underline{y}_{r}-\underline{y}
$$
Assume our plant is $$
\begin{cases}
\dot{\underline{x}} = A\underline{x}+B\underline{u} \\
\underline{y}=C\underline{x}
\end{cases} \tag{2}
$$
## Internal Model Principle
States that for robust tracking and disturbance rejection we need a model of the reference (or disturbance) signal within the controller. We will use this principle to construct a tracking controller for a particular reference: a *step* signal.

A step signal satisfies the differential equation $$
\dot{\underline{y}}_{r}=\underline{0}\quad \forall t\geq 0\tag{3}
$$which is a linear differential equation of the form $h(\underline{y}_{r}) = \underline{0}$ called an *exosystem*
Define two intermediate variables, $\underline{z}$ and $\underline{w}$, which are consistent with the form of the exosystem.$$
\begin{array}
\underline{z} &= h(\underline{x}) \\
&=\dot{\underline{x}} \\
\end{array}
\quad \text{and} \quad \begin{array}
\underline{w} &= h(\underline{u}) \\
&= \dot{\underline{u}}
\end{array}\\
\implies \dot{\underline{z}} = A\underline{x} + B\underline{w}\tag{4}
$$
Taking the time derivative of (1) and using (2) & (3) gives $$
\begin{align}
 \dot{\underline{e}}_{t}  &= \dot{\underline{y}} = \dot{\underline{y}}_{r}\\
 &=C \dot{\underline{x}}-\underline{0}\\
 &=C\underline{z}
\end{align}\tag{5}
$$
Define a new state vector $$
\begin{bmatrix}
\underline{e}_{t} \\
\underline{z}
\end{bmatrix}
$$ (now in **error space**) and combine (4) & (5) into a single state equation $$
\begin{bmatrix}
\dot{\underline{e}}_{t} \\
\dot{\underline{z}}
\end{bmatrix} = \underset{ \bar{A} }{ \begin{bmatrix}
0 & C \\
0 & A
\end{bmatrix} }\begin{bmatrix}
\underline{e}_{t} \\
\underline{z}
\end{bmatrix}+ \underset{ \bar{B} }{ \begin{bmatrix}
0 \\
B
\end{bmatrix} } \underline{w}
$$
$$
\begin{align}
\bar{A}\in\mathbb{R}^{(n+p)\cdot(n+p)} \\
\bar{B}\in\mathbb{R}^{(n+p)\cdot(m+p)}
\end{align}
$$
If $(\bar{A}, \bar{B})$Controllable, then we can find gains in a full-state feedback law
$$
\begin{align}
\underline{w} &= -\bar{K}\begin{bmatrix}
\underline{e}_{t} \\
\underline{z}
\end{bmatrix} \\
&=-\begin{bmatrix}
K_{r} & K_{x}
\end{bmatrix} \begin{bmatrix}
\underline{e}_{t} \\
\underline{z}
\end{bmatrix} \\
&=-K_{r}\underline{e}_{t}-K_{x}\underline{z}
\end{align} \tag{6}
$$
Such that the CL system is stable.
If stable then $\lim_{ t \to \infty } \underline{e}_{t} = \underline{0}$ , i.e. the asymptotic reference tracking we are seeking
The control input we need is found by integrating (6)$$
\begin{align}
\underline{u}(t) &= \int_{0}^{t} \underline{w}(\tau) \, d\tau  \\
&-\underbrace{ K_{r}\int_{0}^{t} \underline{e}_{t}(\tau) \, d\tau }_{ \text{new term} } - \underbrace{ K_{x}\underline{x}(t) }_{ \text{same FSFB as before} }
\end{align}
$$
or ![[Control System - Reference Area Block Diagram.png]]
## Notes: 
1. $(A,B)$Controllable does not imply $(\bar{A},\bar{B})$Controllable
2. Recall that in the laplace domain, $\int  \, dt \to \frac{1}{s}$, so that the integrator in the controller is our internal model of the step input

The internal model method of reference tracking control introduces integral action, which can reduce the effects of:
* input disturbances
* model uncertainties, e.g. if mass or damping are difficult to measure accurately
* plant nonlinearities