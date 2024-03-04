---
tags: []
created: 2024-02-24 21:48
modified: 2024-02-27 18:30
---
See [[Types of Stability]] and [[Lyapunov Function]]
## Lyapunov's Theorem
- If the linearized system ($\dot{\underline{x}}=\underline{A}\underline{x}$) is strictly stable (i.e., if all eigenvalues of $A$ are strictly in the left-half complex plane), then the equilibrium point is asymptotically stable (for the actual nonlinear system).
- If the linearized system is unstable (i.e., if at least one eigenvalue of $A$ is strictly in the right-half complex plane), then the equilibrium point is unstable (for the actual nonlinear system) .
- If the linearized system is marginally stable (i.e., all eigenvalues of $A$ are in the left-half complex plane, but at least one of them is on the imaginary axis), then one cannot conclude anything from the linear approximation for the EP of the actual nonlinear system

	Given $\dot{x}=f(x)$ and $V(x)$ defined on $\Omega$
	1. $V(x) = 0$ when $x=x^*$
	2. $V(x)>0$, for all $x$ in $\Omega$ except $x=x^*$
	3. $\dot{V}(x)=\nabla V(x)\cdot f(x) \leq 0$ for all $x$ in $\Omega$
	$\implies x^*$ is stable
	If also 
	4. $\dot{V}(x)<0$ for all $x$ in $\Omega$ (except $x^*$)
	$\implies x^*$ is locally asymptotically stable (L.A.S)
	If also 
	5. $\Omega = \mathbb{R}^n$ 
	6. $V(x)\to \infty$ as $\sqrt{ x_{1}^2+\dots+x_{n}^2 } \to \infty$
	$\implies x^*$ is globally asymptotically stable (G.A.S)
[Source](https://www.youtube.com/watch?v=td-d4Yi-81c&list=PLBYGwR1BU9CFZarhZnAn3wkMdf4FsmJdD&index=23)

This can be solved for using two methods:
1. [[Lyapunov's Indirect (Linearization) Method]]
2. [[Lyapunov's Direct Method]]

# Useful References
https://underactuated.mit.edu/lyapunov.html