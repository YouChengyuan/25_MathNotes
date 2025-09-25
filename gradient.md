#RealAnalysis 

**only scalor function may have gradient, on condition that it's also differentiable**

> [!def] gradient; $\nabla$
> we use **standard basis** $x_1, ..., x_n$ for $\mathbb{R}^n$, and suppose $f:\mathbb{R}^n \rightarrow \mathbb{R}$ is **differentiable scalor function**, then define the gradient $\nabla f: \mathbb{R}^n \rightarrow \mathbb{R}^n$ of $f$ at the point $p=(p_1, ..., p_n)$ as
> $$
> \nabla f(p)=
> \begin{bmatrix}
> \frac{\partial f}{\partial x_1} (p) \\
> \vdots \\
> \frac{\partial f}{\partial x_n} (p) \\
> \end{bmatrix}
> $$
> <span style="font-weight:bold; color:rgb(242, 7, 19)">Notice: The gradient is a vector!</span>

> [!thr] the gradient is the transpose of Jacobian matrices
> If $f$ is a differentiable **<span style="color:rgb(242, 7, 19)">scalor function</span>**, then $\nabla f(P)$ exists, and $(Df)_p$ is the **dual** of $\nabla f(P)$, i.e. $(Df)_p = [\nabla f(P)]^T$
> 
> $proof.$
> $$
> (Df)_p = \begin{bmatrix}
> \frac{\partial f}{\partial x_1} (p) & \cdots & \frac{\partial f}{\partial x_n} (p)
> \end{bmatrix}
> \in (\mathbb{R}^n)' 
> $$
> $$
> \nabla f(p)=
> \begin{bmatrix}
> \frac{\partial f}{\partial x_1} (p) \\
> \vdots \\
> \frac{\partial f}{\partial x_n} (p) \\
> \end{bmatrix}
> \in \mathbb{R}^n
> $$
> where $(\mathbb{R}^n)'$ is the dual space of $\mathbb{R}^n$, complete the proof. $\Box$

> [!tip] represent  $(Df)_p(\vec{v})$ by $\nabla f$
> let $(Df)_p$ be the derivative of $f:\mathbb{R}^n \rightarrow \mathbb{R}$ at point $p \in \mathbb{R}^n$, then for $\vec{v}=(v_1, ...,v_n)^T \in \mathbb{R}^n$
> $$(Df)_p(\vec{v})=\langle \nabla f(p), \vec{v} \rangle =
> \begin{bmatrix}
> \frac{\partial f}{\partial x_1} (p) \\
>  \vdots \\
>   \frac{\partial f}{\partial x_n} (p) \\
> \end{bmatrix}^T
> \begin{bmatrix}
> v_1 \\
> \vdots \\
> v_n \\
> \end{bmatrix}\\
> =
> \begin{bmatrix}
> \frac{\partial f}{\partial x_1} (p) & \cdots & \frac{\partial f}{\partial x_n} (p)
> \end{bmatrix}
> \begin{bmatrix}
> v_1 \\
> \vdots \\
> v_n \\
> \end{bmatrix}
> $$
> 

> [!NOTE] represent the direction derivative by gradient
> Suppose $u$ is a unit vector, then the direction derivative $(D_uf)_p$ at point $p$ with the direction of $u$ can be represented by:
> $$
> \begin{align}
>(D_uf)_p = \nabla f(p) \cdot u
\end{align}
> $$
> 
> $proof.$
> ![[Pasted image 20250902211449.png]]
> ^2509022115

> [!thr] The gradient & derivative of functions w.r.t a matrix 
> suppose a differentiable scalor function $f: \mathcal{L}(\mathbb{R}^m, \mathbb{R}^n) \rightarrow \mathbb{R}$, let $\{X_{ij}\}$ be the set of standard basis of $\mathcal{L}(\mathbb{R}^m, \mathbb{R}^n)$, then the gradient of $f(X)$ w.r.t. the matrix $X$ at the point $P \in \mathcal{L}(\mathbb{R}^m, \mathbb{R}^n)$ is 
> $$
> \nabla f(P)=
> \begin{bmatrix}
\frac{\partial f}{\partial  X_{11}}(P) & \cdots & \frac{\partial f}{\partial X_{1n}}(P) \\
\vdots & \ddots & \vdots \\
\frac{\partial  f}{\partial  X_{m1}}(P) & \cdots & \frac{\partial  f}{\partial  X_{mn}}(P)  \\
\end{bmatrix} 
= (Df)_p
> $$
> for an arbitary $A\in \mathcal{L}(\mathbb{R}^m, \mathbb{R}^n)$ the $A$-directional derivative of $f(X)$ w.r.t. the matrix $X$ at the point $P \in \mathcal{L}(\mathbb{R}^m, \mathbb{R}^n)$ is 
>$$
>(Df)_P(A) = \langle \nabla f(P), A \rangle_F = trace([\nabla f(P)]^TA)
>$$
>where $\langle , \rangle_F$ is the [[Frobenius inner product]].
>
>$proof.$

> [!thr] the geometric meaning of the gradient
> The gradient $\nabla_x f(p)$ at point $p$ direct to the direction that $f(x)$ has the greatest speed to increase.
> 
> $proof.$
> By [[gradient#^2509022115]], the direction derivative $(D_uf)_p$ can be represented by  
> $$
> \begin{align}
> (D_uf)_p &= \nabla f(p) \cdot u \\
> &= \|f(p)\| \cdot \|u\| \cdot \cos(\theta) \\
> &= \|f(p)\| \cdot \cos(\theta) \\
\end{align}
> $$
> thus $0=\arg\max\limits_{\theta}(D_uf)_p$, i.e. $u$ should has the same direction as $\nabla f(p)$ to reach the maximum of $(D_uf)_p$. $\blacksquare$

