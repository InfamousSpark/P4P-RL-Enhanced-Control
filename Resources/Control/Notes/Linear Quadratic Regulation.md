---
tags: []
created: 2024-02-24 21:51
modified: 2024-02-29 21:38
---
Using pole placement to calculate the full-state feedback gain K is always a trade-off between speed of regulation response and control input effort.

 A direct way of trading off various performance requirements is to introduce a cost function and minimize it, i.e. find an optimal design. This is where LQR can be used

A typical optimal control problem is formulated as follows:
Find a control input $u(t)$ that minimises
$$
\qquad J=\int_{0}^{t_{f}} h(\underline{x},\underline{u}) \, dt \qquad \text{a positive cost function} \\
$$
*subject to*$$
\qquad \dot{\underline{x}}=\underline{f}(\underline{x},\underline{u}) \qquad \text{a constraint (the dynamic plant)}
$$
# Linear Quadratic Regulation (LQR)
Given the **linear*** plant state equation $$
\dot{\underline{x}} = A\underline{x}+B\underline{u};\quad \underline{x}(0)=\underline{x}_{0}
$$
find a **regulating** control input, $\underline{u}(t)$ that minimises $$
J=\int_{0}^{\infty} (\underline{x}^TQ\underline{x}+\underline{u}^TR\underline{u}) \, dt 
$$ 
Where 
- $J$ is the scalar cost function in quadratic form
- $Q_{n\cdot n}$ is the state weighting matrix
- $Rm\cdot m$ is the input weighting matrix

## Notes:
- Can add a third term to LQR minimise function to be $$
J=\int_{0}^{\infty} (\underline{x}^TQ\underline{x}+\underline{u}^TR\underline{u} + \underline{x}^TN\underline{u}) \, dt 
$$
- We are defining a state regulation problem because $J_{min}$ is finite only when both $\underline{x}$ and $\underline{u}$ end up at zero.
- When $Q$ is ‘large in value’ and $R$ is ‘small in value’ then more weighting is being placed on state regulation compared to control effort.
- If $Q$ & $R$ are diagonal then $J = \int_{0}^{\infty}( q_{1}x_{1}^2+q_{2}x_{2}^2+\dots+q_{n}x_{n}^2 + r_{1}u_{1}^2+r_{2}u_{2}^2+\dots+r_{m}u_{m}^2)\, dt$

___
## Linear Algebra Definitions - [[Matrices]]
**Def:** Matrix $A$ is *positive-semidefinite* (written $A\geq 0$) means $A$ is square, symmetric, and all eigenvalues* of $A$ are $\geq 0$.
	\*Recall that all eigenvalues of a symmetric matrix are purely real

**Def:** Matrix $A$ is *positive-definite* (written $A > 0$) means $A$ is square, symmetric, and all eigenvalues of $A$ is $>0$ 
___

## Solution to the LQR problem (minimising $J$) by Kalman:
If:
1. $Q$ is positive-semidefinite
2. $R$ is positive-definite
3. $(A,B)$Controllable
then
- $u = -K\underline{x}$ is the optimal regulation controller
	Where $K=R^{-1}B^TP$ the optimal control gain and $P_{n\cdot n}$ is the unique positive-definite solution to the algebraic Riccati equation (ARE) $$
A^TP+PA+Q = PBR^{-1}B^TP
$$
- the closed-loop system $(A-BK)$ is always stable
- the minimum cost is $J_{min} = \underline{x}_{0}^TP\underline{x}_{0}$

## Steps to finding a LQR controllers:
1. Choose $Q$ & $R$ to trade off the refulation performance of particular state with the effort of particular control inputs. This is based on the control objectives. Typically, it is sufficient to choose $Q$ and $R$ as diagonal matrices.
	- E.g. Bryson's rule - Initially, choose diagonal elements of $Q$ and $R$ by $$
q_{i}=\frac{1}{\text{max. acceptable value of }x_{i}^2} \quad\text{and}\quad r_{i}=\frac{1}{\text{max. acceptable value of }u_{i}^2}
$$
2. Check that the 3 conditions are met for finding an optimal controller.
3. Solve the Riccati equation for $P$ (positive-definite), then calculate $K$ using $K = R^{-1}B^TP$. This process is tedious by hand but computers are efficient at it, See. [[MATLAB Functions]] for `lqr`
	