
##### Steepest Descent Direction:
Go in the direction along which f decreases most rapidly:
$$
p_k=-\nabla f_k
$$

##### Newton Direction:
$$
p_k^N=-(\nabla^2f_k)^{-1}\nabla f_K
$$
Can only be used if $\nabla^2f_k$ is positive definite. This way, we ensure that $(\nabla^2f_k)^{-1}$ exists.

##### Quasi-Newton Search Direction:
Replace $\nabla^2f_k$ with $B_k$:
$$
p_k=-B_k^{-1}\nabla f_k
$$
Then either approximate $B_k$, or use $B_k^{-1}=H_k$ and approximate $H_k$.


### 2.1 Deciding Step Length. The Wolfe conditions
$\alpha_k$ must satisfy the two conditions:
1: Sufficient decrease:
$$
f(x_k+\alpha p_k)\leq f(x_k)+c_1\alpha\nabla f_k^{\top}p_k,\;c_1\in(0,1)
$$
2: Curvature conditions:
$$
\nabla f(x_k+\alpha_kp_k)^{\top}p_k \geq c_2\nabla f_k^{\top}p_k,\;c_2\in(c_1,1)
$$

### 2.3 The BFGS method
![[Pasted image 20230730131409.png]]

We want to use BFGS over Newton when we don't have the capacity to calculate the Hessian matrix. To implement efficiently, the line search should:
- Either satisfy the Wolfe conditions or the string Wolfe conditions.
- Always try a step length of $\alpha_k=1$ first, because this step length will eventually always be accepted.

##### Good Hessian Approximations
- $B_k>0$ ensures descent direction.
- $B_k\approx\nabla^2f_k$ ensures fast convergence.
- Cheap computation: Only use gradients to compute $B_k$.
To determine if $B_{k+1}$ is a good approximation it must fulfill the secant condition:
$$
B_{k+1}s_k=y_k
$$
![[Pasted image 20230730131951.png]]

##### The Maratos Effect
Some algorithms based on merit functions may converge slowly because they reject steps that make good progress toward a solution.
Steps to avoid the Maratos effect:
- Use a merit function that does not suffer from the Maratos effect, for example Fletcher's augmented Lagrangian.
- Use second-order correction
- Allow the merit function to increase on certain iterations. A nonmonotone strategy.

### 3.3 Sequential Quadratic Programming
i.e. Active-Set methods for nonlinear programming. At each iterate, we model the nonlinear problem as a quadratic programming problem and define the search direction to be the solution of this subproblem.

##### 3.3.1 Local SQP method
Assumptions:
- Constraint Jacobian $A(x)$ has full rank.
- The matrix $\nabla^2\mathcal{L}(x,\lambda)$ is positive definite on the tangent space of the constraints.

##### Equality-constrained QP approach
$$
min f(x),\;st:c(x)=0
$$
We model this using the quadratic program:
$$
min f_k+\nabla f_k^{\top}p+\frac{1}{2}p^{\top}\nabla^2\mathcal{L}_kp
$$
s.t:
$$
A_kp+c_k=0
$$

##### 3.3.3 Merit functions in SQP methods
SQP methods often use a merit function to decide if a step should be accepted. This is because the optimal solution may lie outside of the feasible area. **The merit function measures progress both in terms of the objective function and in terms of the constraints**. In line search, the merit function controls the step size. 
Inequality constraints are often altered using a vector of slack variables:
$$
\bar{c}(x,s)=c(x)-s=0,\;s\geq0
$$

