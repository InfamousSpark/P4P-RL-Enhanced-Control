---
tags: []
created: 2024-02-22 13:10
modified: 2024-02-27 21:36
---
Equilibrium points (a.k.a. stationary points, operating points, fixed points, critical points, steady-state points, trim points) of a nonlinear system are the values of $\underline{x}^*, \underline{y}^*, \underline{u}^*$ when the nonlinear system is in equilibrium. 

Equilibrium implies that $\dot{\underline{x}}=\underline{0} \implies \underline{x}$ is constant.
![[Equilibrium Points.png]]


A state $x^*$ is a equilibrium point (or state) of the system $\dot{x}=f(x)$ if once $x(t)$ is equal to $x^*$, it remains equal to $x^*$ for all future time. Given a EP $x^*$ there always exists a coordinate transformation $y^*=x-x^*$ such that $$
\begin{cases}
\dot{y}=\dot{x}=g(x)=g(y+x^*)=f(x) \\
f(0)=0
\end{cases}
$$
Mathematically this means the [[Vectors|vector]] $x^*$ satisfies $$
0=f(x^*)
$$Equilibrium points can be found by solving the above nonlinear equation.

# State-Space Models
Considering the nonlinear [[State-Space Models]] the equilibrium equations satisfy $$
\begin{cases}
\underline{0}=\underline{f}(\underline{x}^*,\underline{u}^*) \\
\underline{y}^*=\underline{h}(\underline{x}^*,\underline{u}^8)
\end{cases}
$$
There may be more than one equilibrium point for a particular nonlinear system. To exactly define a particular equilibrium point, typically we have some information on $(\underline{x}^*, \underline{y}^*, \underline{u}^*)$ but need to find the rest by solving the above equations. The process of finding all the information for an equilibrium point is often called [[Trimming]], from its use in vehicle flight dynamics

There is [[MATLAB Functions]] to find unknown equilibrium point from a non linear model `trim`

An EP is closely related to stability, see [[Types of Stability]]