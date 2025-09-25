#LinearAlgebra 

from [[SVD_MITresource.pdf]]

[[orthogonal decomposition]] only works for square matrix, however, singular value decomposition can handle all kinds of matrices.

> [!tip] The basic idea of SVD
> for $A \in \mathcal{L}(V,W)$, suppose $rank(A)=r$, we're going to find an orthogonal basis $v_1,v_2,...,v_r$ of $Row(A)$, an orthogonal basis $u_1, u_2,...,u_r$ of $Col(A)$, s.t. for $i=1,2,...,r$:
> $$
> Av_i = \sigma_iu_i
> $$
> where $\sigma_1,\sigma_2, ..., \sigma_r$ are real numbers.
> then we have
> $$
> A
> \begin{bmatrix}
> \vec{v_1} & \vec{v_2} & ... & \vec{v_r}
> \end{bmatrix}
> = 
> \begin{bmatrix}
> \vec{u_1} & \vec{u_2} & ... & \vec{u_r}
> \end{bmatrix}
> \begin{bmatrix}
\sigma_1 & & & \\
& \sigma_2 & & \\
& & \ddots & \\
& & & \sigma_r
\end{bmatrix} 
> $$
> Let 
> $$
> \begin{align*}
> V=
> \begin{bmatrix}
> \vec{v_1} & \vec{v_2} & ... & \vec{v_r}
> \end{bmatrix}\\
> U=
> \begin{bmatrix}
> \vec{u_1} & \vec{u_2} & ... & \vec{u_r}
> \end{bmatrix} \\
> \Sigma=
> \begin{bmatrix}
\sigma_1 & & & \\
& \sigma_2 & & \\
& & \ddots & \\
& & & \sigma_r
\end{bmatrix} 
> \end{align*}
> $$
> then since $V$ is orthogonal matrix, we enventually have:
> $$
> A=U\Sigma V^T
> $$
> where $\Sigma$ is diagonal, and notice that $V$ and $U$ are [[orthogonal matrix]], thus $$A^TA=V \Sigma U^TU \Sigma V^T=V \Sigma ^2 V^T$$
> which is similar to the good attribute of orthogonal decomposition of a matrix.

> [!NOTE] Calculation of parameters of SVD
> **First we calculate $V$ and $\Sigma$.** 
> since
> $$
> \begin{align*}
A^TA &= V \Sigma U^TU \Sigma V^T \\
&= V \Sigma^2 V^T \\
&= V 
\begin{bmatrix}
\sigma_1^2 & & & \\
& \sigma_2^2 & & \\
& & \ddots & \\
& & & \sigma_r^2
\end{bmatrix} 
V^T
\end{align*}
> $$
> then, by [[eigen decomposition]], $V$ is the matrix of eigenvectors of $A^TA$, and $\Sigma^2$ is the matrix of eigenvalues of $A^TA$, thus we can calculate $V$ and $\sigma_1,\sigma_2, ..., \sigma_r$ by calculate the eigenvalues and the corresponding eigenvectors of $A^TA$.
> **Second, we calculate $U$ in the same fashion:**
> $$
> \begin{align*}
AA^T &= U \Sigma V^TV \Sigma U^T \\
&= U \Sigma^2 U^T \\
&= U 
\begin{bmatrix}
\sigma_1^2 & & & \\
& \sigma_2^2 & & \\
& & \ddots & \\
& & & \sigma_r^2
\end{bmatrix} 
U^T
\end{align*}
> $$
> then $U$ is the matrix of eigenvectors of $AA^T$

> [!NOTE] The reason that we define $U$,$V$ to be the basis matrix of $Col(X)$ and $Row(X)$, rather than the basis of $\mathbb{R}^n$,$\mathbb{R}^d$
> ![[cs189_hw2.pdf#page=4&rect=81,78,562,219|cs189_hw2, p.4]]
> ![[cs189_hw2.pdf#page=5&rect=104,682,486,743|cs189_hw2, p.5]]
> $proof.$
> - (i)
> Suppose that $\tilde{U}=\{u_i:\sigma_i > 0\}$, then we claim that $\tilde{U}$ is a basis for the column space of $X$:
> For any vector $w$ in the column space of $X$, there exists a scaler vector $\alpha \in \mathbb{R}^d$ s.t. $w=X\alpha$, and since
> $$
> \begin{align}
> X\alpha &= \sum_{i:\sigma_i>0} \sigma_iu_iv_i^T\alpha \\
> &= \sum_{i:\sigma_i>0} \beta_i u_i
\end{align}
> $$
> where $\beta_i=\sigma_iv_i^T\alpha \in \mathbb{R}$, hence $Col(X)\subseteq span(\tilde{U})$.
> For $\forall \beta_i\in \mathbb{R}$ ($i:\sigma_i>0$):
> there exists $\alpha \in \mathbb{R}^d$ s.t. the following system of equations holds
> $$
> \begin{align}
> \left\{
> \begin{array}{rcl}
> v_i^T\alpha = \frac{\beta_i}{\sigma_i} ~~~ (i:\sigma_i>0)
> \end{array}
> \right.
\end{align}
> $$
> i.e. $X\alpha = \sum_{i:\sigma_i>0} \beta_i u_i$, thus $span(\tilde{U})\subseteq Col(X)$.
> Therefore, $span(\tilde{U})= Col(X)$, and since vectors in $\tilde{U}$ are linearly independent, thus $\tilde{U}$ is a set of basis vectors for $Col(X)$;
> Then since $\tilde{U}\subseteq \{u_i\}_{i=1}^n$ is a set of orthonormal vectors by definition, thus complete the proof.$\blacksquare$
> - (ii)
> Similar to (i).$\blacksquare$


