---
tags: []
created: 2024-02-27 19:01
modified: 2024-02-27 19:02
---
## Stability and Instability
**Def:** The equilibrium state $x=0$ is said to be stable if, for any $R>0$, there exists $r>0$, such that if $|x(0)| <r$, then $|x(t)|<R$ for all $t\geq 0$, Otherwise, the equilibrium point is unstable.
**Clarification:** There exists a radius from [[Equilibrium Point|Equilibrium]] where initial conditions within that will always stay within a larger radius for all time.

This stability is called stability in sense of [[Lyapunov's Stability Theory|Lyapunov]] or Lyapunov stability.
![[Lyapunov Stability.png]]
$B_{R}$ denotes the spherical region defined by $|x| <R$ in state-space, and $S_{R}$ the sphere itself, defined by $|x|=R$.

Explicit stability is required in the definition because all trajectories starting within the unit disk converge to the origin. But the origin is unstable (e.g. curve C may be outside the region where the model is valid
![[Explicit Stability.png]]
## Asymptotic Stability
**Def:** An equilibrium point is asymptotically stable if it is stable, and if in addition there exists some $r>0$ such that $|x(0)|<r$ implies that $x(t)\to0$ as $t\to \infty$
**Clarification:** States approach $0$ and do not pass $R$.
![[Asymptotic Stability.png]]

An equilibrium point which is Lyapunov stable, but not asymptotically stable is called marginally stable.

The concept of exponential stability is used to estimate how fast the system trajectory approaches the EP.

If the system EP at the origin is exponentially stable, then $x(t)$ converges to the origin faster than an exponential function.
## Exponential Stability
**Def:** An equilibrium point is exponentially stable if there exists two strictly positive numbers $\alpha$ and $\lambda$ such that for all $t>0,\ |x(t)|\leq\alpha|x(0)|e^{-\lambda t}$  in some ball $B_{r}$ around the origin.
## Local and Global Stability
**Def:** If asymptotic (or exponential) stability holds for any initial states (i.e., $r = \infty$), the equilibrium point is said to be asymptotically (exponentially) stable in the large, also called globally asymptotically (exponentially) stable

Linear time-invariant systems are either asymptotically stable, marginally stable, or unstable. Linear asymptotic stability is always global and exponential. This, the refined notions of stability are explicitly needed only for nonlinear systems.