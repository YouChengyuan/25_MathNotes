# 1. Theorem

==**a square matrix $A\in \mathcal{L}(\mathbb{R}^n)$ is eigen-decomposable if $A$ has $n$ distinct eigenvalues.==**

> [!NOTE] eigen decomposition
> suppose $A \in \mathcal{L}(\mathbb{R}^n)$, $A$ has [[nondegenerate eigenvalues]] $\lambda_1, \lambda_2, ...,\lambda_n$ and corresponding **linearly independent** eigenvectors $\vec{x_1},\vec{x_2}, ..., \vec{x_n}$, which can be denoted by
> $$
> \vec{x_i}=
> \begin{bmatrix}
> x_{1i} \\
> x_{2i} \\
> \vdots \\
> x_{ni} \\
> \end{bmatrix}
> $$
> then the matrix composed of eigenvectors
> $$
> P=
> \begin{bmatrix}
> \vec{x_1} & \vec{x_2} & ... & \vec{x_n}
> \end{bmatrix}
> =
> \begin{bmatrix}
> x_{11} & \cdots & x_{1n} \\
>\vdots & \ddots & \vdots \\
> x_{n1} & \cdots & x_{nn} \\
> \end{bmatrix}
> $$
> and the diagonal matrix of eigenvalues 
> $$
D = 
\begin{bmatrix}
\lambda_1 & 0        & \cdots & 0 \\
0        & \lambda_2 & \cdots & 0 \\
\vdots   & \vdots    & \ddots & \vdots \\
0        & 0         & \cdots & \lambda_n
\end{bmatrix}
> $$
> then we have:
> $$
> \begin{align*}
> AP &=
> A
> \begin{bmatrix}
> \vec{x_1} & \vec{x_2} & ... & \vec{x_n}
> \end{bmatrix} \\
>  &= 
> \begin{bmatrix}
> A\vec{x_1} & A\vec{x_2} & ... & A\vec{x_n}
> \end{bmatrix} \\
> &= 
> \begin{bmatrix}
> \lambda_1\vec{x_1} & \lambda_2\vec{x_2} & ... & \lambda_n\vec{x_n}
> \end{bmatrix} \\
> &=
>  \begin{bmatrix}
> x_{11} & \cdots & x_{1n} \\
>\vdots & \ddots & \vdots \\
> x_{n1} & \cdots & x_{nn} \\
> \end{bmatrix}
> \begin{bmatrix}
\lambda_1 & 0        & \cdots & 0 \\
0        & \lambda_2 & \cdots & 0 \\
\vdots   & \vdots    & \ddots & \vdots \\
0        & 0         & \cdots & \lambda_n
\end{bmatrix} \\
> &= PD
> \end{align*}
> $$
> notice that $P$ is invertible, then we have:
> $$
> A=PDP^{-1}
> $$

there are some good attributes of an eigen decomposed matrix:
![[Pasted image 20250709170707.png]]

# 2. Applications
>[!note] to symplify calculation
>when we need to calculate the exponential of a matrix, if the matrix can be eigenvalue-decomposed, then it'll reduce the work if we decompose the matrix before doing the exponential calculation. 
>![[Pasted image 20250615235213.png]]
>The reason is that if we decompose a matrix $A$ into $P\Lambda P^{-1}$,  then $A^m=P\Lambda P^{-1}P\Lambda P^{-1}\cdots P\Lambda P^{-1}=P\Lambda ^m P^{-1}$ , and $\Lambda ^m$ is easy to calculate since $\Lambda$ is an diagonal matrix