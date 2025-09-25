#RealAnalysis 


> [!NOTE] **vector calculus**
**![[Pasted image 20250713234143.png]]**
> **<span style="color:rgb(242, 7, 19)">we usually rewrite the 4th case as a Jacobian matrix, see (b) in [[matrix & vector calculus#^2507201447]]</span>**

> [!NOTE] matrix calculus
> suppose the matrix $A \in \mathcal{L}(\mathbb{R}^m,\mathbb{R}^n)$ be like
> $$
> A=
\begin{bmatrix}
A_{11} & \cdots & A_{1n} \\
\vdots & \ddots & \vdots \\
A_{m1} & \cdots & A_{mn} \\
\end{bmatrix}
> $$
> then for a differentiable $f: \mathcal{L}(\mathbb{R}^m,\mathbb{R}^n) \rightarrow \mathbb{R}^k$, we can firstly represent $f$ by vector
> $$
> f(A)=
> \begin{bmatrix}
> f_1(A) \\
> f_2(A) \\
> \vdots \\
> f_k(A)
> \end{bmatrix}
> $$
> then the derivative of $f$ w.r.t $A$ is 
> $$
> \frac{d~f}{d~A} = 
> f_k(A) \\
> \begin{bmatrix}
> \frac{d~ f_1}{d~ A} \\
> \frac{d~ f_2}{d~ A} \\
> \vdots \\
> \frac{d~ f_k}{d~ A} \\
> \end{bmatrix}
> =
> \begin{bmatrix}
> \begin{bmatrix}
\frac{\partial f_1}{\partial  A_{11}} & \cdots & \frac{\partial f_1}{\partial A_{1n}} \\
\vdots & \ddots & \vdots \\
\frac{\partial  f_1}{\partial  A_{m1}} & \cdots & \frac{\partial  f_1}{\partial  A_{mn}}  \\
\end{bmatrix} \\
\begin{bmatrix}
\frac{\partial f_2}{\partial  A_{11}} & \cdots & \frac{\partial f_2}{\partial A_{1n}} \\
\vdots & \ddots & \vdots \\
\frac{\partial  f_2}{\partial  A_{m1}} & \cdots & \frac{\partial  f_2}{\partial  A_{mn}}  \\
\end{bmatrix} \\
\vdots \\
\begin{bmatrix}
\frac{\partial f_k}{\partial  A_{11}} & \cdots & \frac{\partial f_k}{\partial A_{1n}} \\
\vdots & \ddots & \vdots \\
\frac{\partial  f_1k}{\partial  A_{m1}} & \cdots & \frac{\partial  f_k}{\partial  A_{mn}}  \\
\end{bmatrix} \\
> \end{bmatrix}
> $$

> [!NOTE] Some examples of vector calculus
> ![[Pasted image 20250719221903.png]]
> 
> $answer.$
> (a)
> $$
> \begin{align}
> \frac{\partial\alpha}{\partial \beta_i} &= y_i \frac{e^\beta_i}{1+ e^\beta_i}
> \end{align}
> $$
> (b)
> for each $1 \le i \le n$, $1 \le j \le m$:
> $$
> \begin{align}
> \frac{\partial (Ax)_j}{\partial x_i} &= \frac{\partial\sum_{k=1}^m A_{jk}x_k}{\partial x_i} \\
> &= A_{ji}
> \end{align}
> $$
> then 
> $$
> \begin{align}
> \frac{\partial Ax}{\partial x} &= 
> \begin{bmatrix}
> \begin{bmatrix}
> A_{11} \\
> A_{21} \\
> \vdots \\
> A_{m1} \\
> \end{bmatrix} \\
> \begin{bmatrix}
> A_{12} \\
> A_{22} \\
> \vdots \\
> A_{m2} \\
> \end{bmatrix} \\
> \vdots \\
> \begin{bmatrix}
> A_{1n} \\
> A_{2n} \\
> \vdots \\
> A_{mn} \\
> \end{bmatrix} \\
> \end{bmatrix}
> = 
> \begin{bmatrix}
> A_{11} & \cdots & A_{1n} \\
\vdots & \ddots & \vdots \\
A_{m1} & \cdots & A_{mn} \\
> \end{bmatrix}
> \end{align}
> $$
> where the second equation transfer the $n \times 1$ stack of $m \times 1$ column vectors into a standard Jocobian matrix, which is more **conventional**.
> (c)
> $$
> \begin{align}
> \nabla_z(z^Tz) &= 
> \begin{bmatrix}
> 2z_1 \\
> 2z_2 \\
> \vdots \\
> 2z_m \\
> \end{bmatrix}
>  = 2z
> \end{align}
> $$
>(d)
>$$
>\begin{align}
>z^Tz = \sum_{i=1}^m z_i^2(x)
>\end{align}
>$$
>$$
>\begin{align}
>\nabla_xz^Tz &= 
>\begin{bmatrix}
>\frac{\partial z^Tz}{\partial x_1} \\
>\frac{\partial z^Tz}{\partial x_2} \\
>\vdots \\
>\frac{\partial z^Tz}{\partial x_n} \\
>\end{bmatrix}
> = 
> \begin{bmatrix}
>\sum_{i=1}^m \frac{\partial z_i^2(x)}{\partial x_1} \\
>\sum_{i=1}^m\frac{\partial z_i^2(x)}{\partial x_2} \\
>\vdots \\
>\sum_{i=1}^m\frac{\partial z_i^2(x)}{\partial x_n} \\
>\end{bmatrix}
> = 2
>\begin{bmatrix}
>\sum_{i=1}^m z_i(x)\frac{\partial z_i(x)}{\partial x_1} \\
>\sum_{i=1}^m z_i(x)\frac{\partial z_i(x)}{\partial x_2} \\
>\vdots \\
>\sum_{i=1}^mz_i(x)\frac{\partial z_i(x)}{\partial x_n} \\
>\end{bmatrix}
> = 2
> \begin{bmatrix}
\frac{\partial z_1}{\partial x_1} & \frac{\partial z_1}{\partial x_2} & \cdots & \frac{\partial z_1}{\partial x_n} \\
\frac{\partial z_2}{\partial x_1} & \frac{\partial z_2}{\partial x_2} & \cdots & \frac{\partial z_2}{\partial x_n} \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial z_m}{\partial x_1} & \frac{\partial z_m}{\partial x_2} & \cdots & \frac{\partial z_m}{\partial x_n}
\end{bmatrix}^T
>\begin{bmatrix}
>z_1 \\
>z_2 \\
>\vdots \\
>z_m \\
>\end{bmatrix}
> = 2 (\frac{\partial z}{\partial x})^Tz
>\end{align}
>$$
>(e)
>by (b) and (d), 
>$$
>\begin{align}
> \nabla_x(z^Tz) = 2A^T(Ax-y)
>\end{align}
>$$
>^2507201447

> [!NOTE] Derivatives of Trace with Respect to a Matrix
> ![[Pasted image 20250721105830.png]]
> 5.
> $$
> \begin{align}
> \frac{\partial tr(XDX^T)}{\partial X} = X(D+D^T)
\end{align}
> $$
> 
> $proof.$
> suppose $A_{m \times n}, X_{n \times p}$
> (1)
> 
> $$
> \begin{align}
>tr(AX) = \sum_{i=1}^m (AX)_{ii}= \sum_{i=1}^m \sum_{j=1}^n A_{ij}X_{ji}
\end{align}
> $$
> then
> $$
> \begin{align}
> \frac{\partial tr(AX)}{\partial X_{ij}} = A_{ji}
\end{align}
> $$
> hense 
> $$
> \begin{align}
> \frac{\partial tr(AX)}{\partial X} = A^T
\end{align}
> $$
>(2)
>$$
>\begin{align}
tr(X^TAX) = \sum_{i=1}^p (X^TAX)_{ii}= \sum_{i=1}^p \sum_{j=1}^n \sum_{k=1}^n X^T_{ij}A_{jk}X_{ki} = \sum_{i=1}^p \sum_{j=1}^n \sum_{k=1}^n X_{ji}A_{jk}X_{ki}
>\end{align}
>$$
>then for each $1 \le l \le n$, $1 \le h \le p$:
>$$
>\begin{align}
> \frac{\partial tr(X^TAX)}{\partial X_{lh}} &= \sum_{j=1}^n  X_{jh}A_{jl} +  \sum_{k=1}^n A_{lk}X_{kh}  \\
>\end{align}
>$$
>then 
>$$
>\begin{align}
> \frac{\partial tr(X^TAX)}{\partial X} &= (A^T+ A)X
>\end{align}
>$$
>(3)
> similarly
> (4)
> similarly
> (5)
> $$
> \begin{align}
>tr(XDX^T) &=  \sum_{i=1}^n (XDX^T)_{ii} \\
> &= \sum_{i=1}^n \sum_{j=1}^p \sum_{k=1}^p X_{ij}D_{jk}X^T_{ki} \\
> &= \sum_{i=1}^n \sum_{j=1}^p \sum_{k=1}^p X_{ij}D_{jk}X_{ik} \\
\end{align}
> $$
> then 
> $$
> \begin{align}
> \frac{\partial tr(XDX^T)}{\partial X_{lh}} &= \sum_{j=1}^p X_{lj}D_{jh} + \sum_{k=1}^p D_{hk}X_{lk}  \\
\end{align}
> $$
> thus 
> $$
> \begin{align}
> \frac{\partial tr(XDX^T)}{\partial X} &= X(D+D^T)
\end{align}
> $$
> 
> 
>$\Box$
>^2507211515

> [!NOTE] matrix calculus with gradient
> (a) $\nabla_x (a^Tx) = a$ and $\nabla_x (x^Ta) = a$
> (b) $\nabla_x (x^TAx) = (A+A^T)x$
>
> $proof.$
> (a)
> $$
> \begin{align}
> \nabla_x (a^Tx) = 
> \begin{bmatrix}
> \frac{\partial a^Tx}{\partial x_1} \\
> \frac{\partial a^Tx}{\partial x_2} \\
> \vdots \\
> \frac{\partial a^Tx}{\partial x_n} \\
> \end{bmatrix} 
> = 
> \begin{bmatrix}
> \frac{\partial \sum_{i=1}^n a_ix_i}{\partial x_1} \\
> \frac{\partial \sum_{i=1}^n a_ix_i}{\partial x_2} \\
> \vdots \\
> \frac{\partial \sum_{i=1}^n a_ix_i}{\partial x_n} \\
> \end{bmatrix} 
> = 
> \begin{bmatrix}
> \frac{\partial x^Ta}{\partial x_1} \\
> \frac{\partial x^Ta}{\partial x_2} \\
> \vdots \\
> \frac{\partial x^Ta}{\partial x_n} \\
\end{bmatrix} 
> = 
> \nabla_x (x^Ta)  
> =
> \begin{bmatrix}
> a_1 \\
> a_2 \\
> \vdots \\
> a_n \\
\end{bmatrix}
> 
>\end{align}
> $$
> (b)
> $$
> \begin{align}
> \nabla_x (x^TAx) = 
> \begin{bmatrix}
> \frac{\partial x^TAx}{\partial x_1} \\
> \frac{\partial x^TAx}{\partial x_2} \\ 
>  \vdots \\
>  \frac{\partial x^TAx}{\partial x_n} \\
\end{bmatrix}
> = 
> \begin{bmatrix}
> \frac{\partial \sum_{i=1}^n x_i(x^TA_{\dot,i})}{\partial x_1} \\
> \frac{\partial \sum_{i=1}^n x_i(x^TA_{\dot,i})}{\partial x_2} \\ 
>  \vdots \\
>  \frac{\partial \sum_{i=1}^n x_i(x^TA_{\dot,i})}{\partial x_n} \\
\end{bmatrix}
> = 
> \begin{bmatrix}
> \frac{\partial \sum_{i=1}^n x_i\sum_{j=1}^nx_jA_{j,i}}{\partial x_1} \\
> \frac{\partial \sum_{i=1}^n x_i\sum_{j=1}^nx_jA_{j,i}}{\partial x_2} \\ 
>  \vdots \\
>  \frac{\partial \sum_{i=1}^n x_i\sum_{j=1}^nx_jA_{j,i}}{\partial x_n} \\
\end{bmatrix}
> = \begin{bmatrix}
> \sum_{j=1}^nx_jA_{j,1} + \sum_{i=1}^nx_iA_{1,i} \\
> \sum_{j=1}^nx_jA_{j,2} + \sum_{i=1}^nx_iA_{2,i} \\ 
>  \vdots \\
>  \sum_{j=1}^nx_jA_{j,n} + \sum_{i=1}^nx_iA_{n,i} \\
\end{bmatrix} 
> = A^Tx + Ax
\end{align}
> $$
> 



