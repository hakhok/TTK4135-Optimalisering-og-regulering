### Theorem 1: First order necessary conditions
_Assume that $z^*$ is a local solution and that $f$ and all $c_i$ are differentiable, and their derivatives are continuous. Further, assume that all the active constraint gradients are linearly independent at  $z^*$ ( #LICQ holds). Then there exists Lagrange multipliers $\lambda^*$ for $i\in \mathcal{E} \cup \mathcal{I}$ such that the following conditions #KKT holds at $(x^*,\lambda^*)$:_
$$
\begin{aligned}
\nabla_z \mathcal{L}\left(z^*, \lambda^*\right) & =0 & & \\
c_i\left(z^*\right) & =0, & & i \in \mathcal{E} \\
c_i\left(z^*\right) & \geq 0, & & i \in \mathcal{J} \\
\lambda_i^* & \geq 0, & & i \in \mathcal{J} \\
\lambda_i c_i\left(z^*\right) & =0, & & i \in \mathcal{J}
\end{aligned}
$$
The KKT conditions are necessary conditions for a local solution.


#riccati 
### Theorem 3: LQ control and the Riccati equation
_The solution of  [[4.3 Linear Quadratic control#Finite horizon LQ control]] with $Q_t\geq0$ and $R_t$>0 is given by:_

$$
u_t=-K_tx_t
$$
where the feedback gain matrix is derived by:
$$
\begin{align}
	K_t &= R_t^{-1}B_t^{\top}P_{t+1}(I+B_tR_t^{-1}B_t^{\top}P_{t+1})^{-1}A_t\\
	
	P_t &= Q_t + A_t^{\top}P_{t+1} (I+B_tR_t^{-1}B_t^{\top}P_{t+1})^{-1}A_t\\
	
	P_N &= Q_N 
\end{align}
$$

#riccati 
### Theorem 5
_The solution of a infinite horizon problem is given by:_
$$
u_t = -Kx_t, \;for\;0\leq t \leq \infty
$$
where the feedback gain matrix is derived by:
$$
\begin{align}
	K&=R^{-1}B^{\top}P(I+BR^{-1}B^{\top}P)^{-1}A \\
	P&=Q+A^{\top}P(I+BR^{-1}B^{\top}P)^{-1}A \\
	P&=P^{\top}\geq0
\end{align}
$$
The infinite horizon LQ controller is often called the _Linear Quadratic Regulator_ #LQR.

