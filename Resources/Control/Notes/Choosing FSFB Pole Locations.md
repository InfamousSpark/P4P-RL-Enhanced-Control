---
tags: []
created: 2024-02-21 14:01
modified: 2024-02-28 15:47
---
The poles of the FSFB closed-loop design are generally chosen based on the desired transient response to a specified input, e.g. settling time for unit step input disturbance, or to non-zero initial conditions.

**Performance Characteristics**
Peak Time
$$
T_{p} = \frac{\pi}{\omega_{d}}
$$
2% Settling Time
$$
T_{s}\sim\frac{4}{\zeta\omega_{n}}
$$
Overshoot
$$
\%OS = e^{\frac{(\zeta \pi)}{\sqrt{ 1-\zeta^2}}} \cdot 100\%
$$

![[Control Systems - Pole Diagrams.png]]

Placing poles further into the LHP will increase the speed of response but will require a larger control effort to do so

___
Solving equations of the form$$
\dot{\underline{x}}=\begin{bmatrix}
1 & 0 \\
0 & -2
\end{bmatrix}
\underline{x} + \begin{bmatrix}
3 & - \\
1 & 1
\end{bmatrix} \underline{u}
$$ With desired poles of CL system at $$
\lambda_{i}^D=\{-2,-3\}
$$Find the gain matrix $K$ in $\underline{u} = -K\underline{x}$

1. Check if controllable - Not needed, but good in practice
2. Calculate $A-BK$ where $K$ is a 2x2 Matrix in this case
3. Use pole placement equation $\text{det}(\lambda I-(A-BK)) = (\lambda-\lambda_{1}^D)(\lambda-\lambda_{2}^D)\dots(\lambda-\lambda_{n}^D)$ from [[State Regulation]] and solve by equating coefficients