---
tags: []
created: 2024-02-24 21:48
modified: 2024-02-27 21:35
---
First goal is to design a control objective to drive all states to 0,  $x(t) \underset{ n \to \infty }{ \to } 0$  - closed loop system is stable

This is called state regulation - different from [[Reference Tracking]] where we wish to drive the output to a known function of time $y(t) \underset{ t \to \infty }{ \to } y_{r}(t)$


FSFB Control law:
$$
u(t) = -Kx(t), K \in \mathbb{R}^{n\cdot m}
$$

Or

$$
\begin{align}
&u_{1} = -k_{11}x_{1}-k_{12}x_{2}+\dots-k_{1n}x_{n}\\
&\dots\\
&u_{m} = -k_{m1}x_{1}-k_{m2}x_{2}+\dots-k_{mn}x_{n}\\
&\end{align}
$$

The closed loop state equation is then
$$
\begin{align}
\dot{\underline{x}} & = A\underline{x}- BK\underline{x} \\
&=(A-BK)\underline{x}
\end{align}
$$
where $A-BK$ is a new matrix which can be modified to change poles, transient response etc.  and is a new $n\cdot m$ state matrix of the CL system

**Arbitrary pole placement:**
Find $K \in \mathbb{R}^{m\cdot n} \ni \text{det}(\lambda I-(A-BK)) = (\lambda-\lambda_{1}^d)(\lambda-\lambda_{n}^d)\dots(\lambda-\lambda_{n}^d)$
where $\lambda_{1}^D,\lambda_{2}^{D}..,\lambda_{n}^D$ are the desired pole locations of the CL system. Allowing for complex conjugate pairs

To move poles from $(x_{1},x_{2})$ to $(y_{1},y_{2})$ solve $A-BK$ where $A =$ matrix which $(x_{1},x_{2})$ is the eigenvalues of, $$B=\begin{bmatrix}
 y_{1}\\ y_{2}
\end{bmatrix}$$ and $K = [k_{1},k_{2}]$ (gains) and solve $K\in\mathbb{R}^{m\cdot n} \ni \dots$

Cannot always place poles where desired. There needs to be $K \in u-K\underline{x}$ to be possible.

**DEF**:
	The linear system $\dot{\underline{x}} = A\underline{x}+B\underline{u}$ is *Controllable* means that there exists a control signal $\underline{u}(t)$ to drive the system from any initial state $\underline{x}_{0}$ to any final state $\underline{x}_{f}$ in finite time
	Abbreviated as ($A,B$) Controllable

To test for controllability can use the rank test
	$(A_{n\cdot n},B_{n\cdot m})$ controllable $\equiv$ rank$(M_c) = n$
	where $M_{c} = [B, AB, A^2B, \dots, A^{n-1}B]$
For single input, B is a column [[Vectors|vector]] and $M_c$ is square so we can use det$(M_{c})$ to test rank$(M_{c}) = n$


See relevant [[MATLAB Functions]] for methods of solving

**Notes**
1. If a system is controllable, we are able to arbitrarily place poles when $\underline{u} = 0K\underline{x}$. However if a system is uncontrollable, we are still able to move the poles, the location just cannot be arbitrary
2. Controlling [[Nonlinear Systems]] with a linear controller requires consideration of the [[Equilibrium Point]] about which the linear model is defined.