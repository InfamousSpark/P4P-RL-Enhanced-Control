---
tags: []
created: 2024-02-22 12:43
modified: 2024-02-27 21:35
---
# Nonlinear
Real physical systems are nonlinear. In certain cases (and ranges of system parameters) their dynamics can be described using linear approximations, i.e. linear state space models. In other cases, however, these linear approximations become inadequate and nonlinear state space models should be used.

The nonlinear state-space models use nonlinear functions to represent both state and output equations.

Generally, SS models are given by n first order differential equations, where n is the number of states $$
\begin{align}
&\dot{x_{1}}=f_{1}(t,x_{1},x_{2},\dots,x_{n},u_{1},\dots,u_{m})\\
&\dot{x_{2}}=f_{2}(t,x_{1},x_{2},\dots,x_{n},u_{1},\dots,u_{m})\\
&\vdots\\
&\dot{x_{n}}=f_{n}(t,x_{1},x_{2},\dots,x_{n},u_{1},\dots,u_{m})\\
\end{align}
$$ where $$
\begin{align}
&\{x_{1},x_{2},\dots,x_{n}\} \text{ are the state variables, and}\\
&\{u_{1},u_{2},\dots,u_{m}\} \text{ are the input variables}\\
\end{align}
$$
Or in [[Vectors|vector]] notation:$$
\dot{\underline{x}}=\underline{f}(t,\underline{x},\underline{u})
$$where $$
\underline{x}=\begin{bmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_{n}
\end{bmatrix} \text{ and } \underline{f}(t,\underline{x},\underline{u})=\begin{bmatrix}
f_{1}(t,\underline{x},\underline{u}) \\
f_{2}(t,\underline{x},\underline{u}) \\
\vdots \\
f_{n}(t,\underline{x},\underline{u})
\end{bmatrix}
$$
The output of the system is governed by another set of nonlinear equations.
For $p$ outputs $\{y_{1},y_{2},\dots,y_{p}\}$: $$
\begin{align}
&y_{1}=h_{1}(t,x_{1},x_{2},\dots,x_{n},u_{1},\dots,u_{m}) \\
&y_{2}=h_{2}(t,x_{1},x_{2},\dots,x_{n},u_{1},\dots,u_{m}) \\
&\vdots \\
&y_{p}=h_{p}(t,x_{1},x_{2},\dots,x_{n},u_{1},\dots,u_{m})
\end{align}
$$
Or in vector form $$
\underline{y}=\underline{h}(t,\underline{x},\underline{u})
$$where $$
\underline{y}=\begin{bmatrix}
y_{1} \\
y_{2} \\
\vdots \\
y_{p}
\end{bmatrix} \text{ and } \underline{h}(t,\underline{x},\underline{u}) = \begin{bmatrix}
h_{1}(t,\underline{x},\underline{u}) \\
h_{2}(t,\underline{x},\underline{u}) \\
\vdots \\
h_{p}(t,\underline{x},\underline{u})
\end{bmatrix}
$$
## Note:
- An SS equation having an explicit $t$ variable in its expression will be time varying, while an equation independent of $t$ will be time-invariant.
- **Def:** $\dot{\underline{x}}=f(\underline{x})$ is an autonomous system. (independent of time, no external input)
- The nonlinear state-space model for time-invariant systems can be expressed as $$
\begin{cases}
\underline{\dot{x}}=\underline{f}(\underline{x},\underline{u})\\
\underline{y}=\underline{h}(\underline{x},\underline{u})
\end{cases}
$$