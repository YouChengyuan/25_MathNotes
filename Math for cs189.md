#LinearAlgebra #RealAnalysis #ML
# 1. linear algebra
> [!NOTE] The bound of rank(AB)
> ![[Pasted image 20250626025004.png]]
> $proof.$
> see [[rank-nullity theorem#^202506290148]]

> [!NOTE] A new way to prove that column rank equals row rank
> ![[Pasted image 20250626023652.png]]
> $proof.$
> by the given fact, there exist a matrix $M$ in somewhere of $A$, without loss of generalty, suppose
> $$A=
\begin{pmatrix}
M & A_1\\
A_2 & A_3\\
\end{pmatrix}
>$$
<span style="color:rgb(242, 7, 19)">since $M$ has none-zero deternimant, thus $M$ is an isomorphism, then columns of $M$ as vectors are linearly independent</span>,then the $k$ amount of column vectors of $\left(\begin{array}{c} M\\ A_2 \end{array}\right)$ are linearly independent $\Longrightarrow$ the dimension of column space of $\left(\begin{array}{cc} M & A_1 \\ A_2 & A_3 \end{array}\right)$ is at least $k$. Similar proof for the case of row space of $A$. $\Box$

> [!NOTE] $rank(A^TA)=rank(A)$
> ![[Pasted image 20250626041611.png]]
> $proof.$
> suppose $rank(A^TA)<rank(A)$ for contradiction, then some non-zero vectors in $range(A)$ is in $null(A^T)$, hence $range(A)\cap null(A^T) \ne {\vec{0}}$, however, by [[transpose decomposition#^2507092033]], $W=range(A)\oplus null(A^T)$, which means that $range(A)\cap null(A^T) = {\vec{0}}$, a contradiction. Thus, $rank(A^TA) \ge rank(A)$, and since $rank(A^TA) \le rank(A)$ by [[rank-nullity theorem#^202506290148]], we have $rank(A^TA)=rank(A)$. $\Box$
> one way of using $A^TA$ is [[singular value decoposition]]
> ^2508041138

> [!NOTE] $A^TA{\mathbb{R}^n}=range(A^T)$ 
> ![[Pasted image 20250710113412.png]]
> $A\mathbb{R}^n=range(A)$
> $A^TA{\mathbb{R}^n}=A^T range(A)$, which is a subspace of $range(A^T)$, and since it has been proved that $rank(A^TA)=rank(A^T)=rank(A)$, thus $A^TA{\mathbb{R}^n}=range(A^T)$ 

> [!NOTE] equivalent definition of positive semidefinite(PSD) 
> ![[Pasted image 20250710143838.png]]
> <span style="color:rgb(242, 7, 19)">$A$ is symmetric</span>
> $proof.$
> $(a)\rightarrow(b)$ suppose (a) holds, then for each eigenvalue $\lambda_i$ and the corresponding eigenvector $x_i$ of $A$, we have $x_i^TAx_i\ge0$ $\Longrightarrow$ $x_i^T\lambda_i x_i=\lambda_ix_i^Tx_i\ge0$ $\Longrightarrow$ $\lambda_i\ge0$;
> $(b)\rightarrow(c)$ since $A$ is symmetric, then by [[spectual theorem]], there exists an orthonormal matrix $Q$ of eigenvectors of $A$ and the  matrix $\Lambda$ of corrsponding eigenvalues, s.t. $A=Q\Lambda Q^T$, and <span style="color:rgb(242, 7, 19)">since all of the eigenvalues are non-negative, then $\sqrt{\Lambda}$ exists</span>, hence we have $A=(Q\sqrt{\Lambda})(\sqrt{\Lambda}Q)^T$, thus $U=Q\sqrt{\Lambda}$;
> $(c)\rightarrow(a)$ suppose (c) holds, then for $\forall x\in \mathbb{R}^n$, $x^TAx=x^TUU^Tx=(U^Tx)^T(U^Tx)= ||U^Tx||^2 \ge 0$ ; $\Box$

the form $x^TAx$ is quite alike the matrix representation of a bilinear map $B(x,x)$

> [!def] The Frobenius inner product
> ![[Pasted image 20250712144656.png]]
><span style="color:rgb(242, 7, 19)"> it's different with inner product for vectors</span>
>let 
>$$
>A=
>\begin{bmatrix}
>A_{\dot~,1} & A_{\dot~,2} & \cdots & A_{\dot~,n}
>\end{bmatrix}
>$$
>$$
>B=
>\begin{bmatrix}
>B_{\dot~,1} & B_{\dot~,2} & \cdots & B_{\dot~,n}
>\end{bmatrix}
>$$
>then 
>$$
>A^T=
>\begin{bmatrix}
>A_{\dot~,1}^T \\
> A_{\dot~,2}^T \\
> \vdots \\
>A_{\dot~,n}^T \\
>\end{bmatrix}
>$$
>then we have 
>$$
>\begin{align}
>trace(A^TB) &= trace(
>\begin{bmatrix}
>A_{\dot~,1}^T \\
> A_{\dot~,2}^T \\
> \vdots \\
>A_{\dot~,n}^T \\
>\end{bmatrix}
> \begin{bmatrix}
>B_{\dot~,1} & B_{\dot~,2} & \cdots & B_{\dot~,n}
>\end{bmatrix} 
>) \\
>&= A_{\dot~,1}^TB_{\dot~,1} + A_{\dot~,2}^TB_{\dot~,2} + \cdots + A_{\dot~,n}^TB_{\dot~,n}
>\end{align}
>$$

> [!def] The Frobenius norm
> ![[Pasted image 20250712144948.png]]

> [!NOTE] 
> ![[Pasted image 20250712145412.png]]
> $proof.$
> (a) just some matrix calculation
> (b) suppose $A,B \in \mathcal{L}(\mathbb{R}^n)$ ,
> since $A$ and $B$ are symmetric,thne $trace(AB)=trace(BA)$, and by [[positive semidefinite]], there exists matrix $M$ and $L$ s.t. $A=MM^T$, $B=LL^T$, then 
>$$
\begin{align*}
>trace(AB) &= trace(BA) \\
>&=trace(MM^TLL^T) \\
>&= trace(M^TLL^TM) \\
>&= trace[(L^TM)^T(L^TM)]
>\end{align*}
>$$
>where the third equation is by [[trace#^2507122226]]. Let $C=L^TM$, then 
>$$
>\begin{align*}
>trace(AB) &= trace(C^TC) \\
>&= trace(C^TC) \\
>&= \sum_{i=1}^n ||C_{.,i}|| \\
>&\ge 0
>\end{align*} 
>$$
>(c) 
> 

> [!NOTE] a way to calculate the maximum singular value
> ![[Pasted image 20250712231211.png]]

# 2. Matrix\Vector calculus and norms
> [!NOTE] matrix calculus
> ![[Pasted image 20250713205604.png]]
> $answer$
> let
> $$
> g(A):=sin(A^2_{11}+e^{A_{11}+A_{22}})
> $$
> $$
> h(A):=x^TAy
> $$
> then
> $$
> \begin{align*}
> f(A) &= sin(A^2_{11}+e^{A_{11}+A_{22}}) + x^TAy\\
> &= g(A) + h(A)
> \end{align*}
> $$
> then
> $$
> \begin{align*}
> \nabla f = 
> \frac{\partial f}{\partial A} &= 
> \frac{\partial g}{\partial A}+\frac{\partial h}{\partial A} \\
> &=
> \begin{bmatrix}
> \frac{\partial g}{\partial A_{11}} & \frac{\partial g}{\partial A_{12}} \\
> \frac{\partial g}{\partial A_{21}} & \frac{\partial g}{\partial A_{22}} \\
> \end{bmatrix}
> + xy^T
> \end{align*}
> $$
> where 
> $$
> \frac{\partial g}{\partial A_{11}}= cos(A^2_{11}+e^{A_{11}+A_{22}})(2A_{11}+e^{A_{11}+A_{22}})
> $$
> $$
> \frac{\partial g}{\partial A_{22}}= cos(A^2_{11}+e^{A_{11}+A_{22}})e^{A_{11}+A_{22}}
> $$
> $$
> \frac{\partial g}{\partial A_{12}}=\frac{\partial g}{\partial A_{21}}=0
> $$
> $\Box$

> [!NOTE] induced norm
> ![[Pasted image 20250714163952.png]]
> 
> $answer.$
> (a)
> by [[singular value decoposition]], there exists orthogonal matrices $U,V$ and a diagonal matrix $\Sigma$ s.t. $A=U\Sigma V^T$, then 
> $$
> \begin{align*}
> \|A\|_2 &= \sup\limits_{x \ne 0} \frac{\|U\Sigma V^T x\|_2}{\|x\|_2}\\
> &= \sup\limits_{x \ne 0} \frac{\|\Sigma V^T x\|_2}{\|x\|_2}\\
> &= \sup\limits_{x \ne 0} \frac{\|\Sigma V^T x\|_2}{\|V^T x\|_2}\\ 
> \end{align*} 
> $$
> where the second and third equations hold because [[orthogonal matrix#^2507161655]]
> Let $y=V^T x$, then 
> $$
> \|A\|_2 = \sup\limits_{x \ne 0} \frac{\|\Sigma y\|_2}{\|y\|_2} = \sup\limits_{x \ne 0} \frac{y^T\Sigma^2 y}{y^Ty}
> $$
> to find $y$ s.t. $\frac{y^T\Sigma^2 y}{y^Ty}$ reaches its supremum, since 
> $$
> \frac{y^T\Sigma^2 y}{y^Ty} = \frac{\sum_{i=1}^n \sigma_i^2y_i^2}{\sum_{i=1}^n y_i^2}
> $$
> then by [[weighted sum#^2507190123]], let $k$ be the index s.t. $\sigma_k = max\{\sigma_i\}$ , then 
> $$\sup\limits_{x \ne 0} \frac{y^T\Sigma^2 y}{y^Ty}= \max\{\alpha_i\}$$ 
> 
> $answer.$
> (b) 
> suppose $A \in \mathcal(\mathbb{R}^s, \mathbb{R}^t)$
> $$
> \begin{align}
> \|A\|_\infty &= \sup\limits_{x \ne 0}\frac{\max\limits_{j\in\{1,2,...,t\}} |(Ax)_i|}{\max\limits_{i\in\{1,2,...,s\}}|x_i|} \\
> &= \sup\limits_{x \ne 0}\frac{\max\limits_{j\in\{1,2,...,t\}} |\sum_{k=1}^s A_{jk}x_k|}{\max\limits_{i\in\{1,2,...,s\}}|x_i|} \\
> &\le \sup\limits_{x \ne 0}\frac{\max\limits_{j\in\{1,2,...,t\}} \sum_{k=1}^s |A_{jk}|\cdot|x_k|}{\max\limits_{i\in\{1,2,...,s\}}|x_i|} \\
> &\le \sup\limits_{x \ne 0}\frac{\max\limits_{j\in\{1,2,...,t\}} \sum_{k=1}^s \{|A_{jk}|\cdot\max\limits_{k\in\{1,2,...,s\}}|x_k|\}}{\max\limits_{i\in\{1,2,...,s\}}|x_i|} \\
> &= \max\limits_{j\in\{1,2,...,t\}}\sum_{k=1}^s |A_{jk}|
> \end{align}
> $$
> i.e., the **maximum absolute row sum** of $A$. $\Box$
> 

> [!NOTE] vector calculus
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
>

# 3. Linear neural networks

> [!NOTE] $\nabla_W RSS(W)$
> ![[Pasted image 20250720181352.png]]
> $proof.$
> $$
> \begin{align}
> RSS(W) &= \|XW^T - Y\|_F^2 \\
> &= tr\{(WX^T - Y^T)(XW^T-Y)\} \\
> &= tr\{WX^TXW^T - WX^TY - Y^TXW^T + Y^TY\} \\
> &= tr(WX^TXW^T) - tr(WX^TY) - tr(Y^TXW^T) + tr(Y^TY) \\
> &= tr(WX^TXW^T) - 2tr(X^TYW) + tr(Y^TY) \\
\end{align}
> $$
> the last eqution is by [[trace#^2507211415]], [[trace#^2507122226]]
> then by [[matrix & vector calculus#^2507211515]]
> $$
> \begin{align}
> \frac{\partial RSS(W)}{\partial W} &= \frac{\partial tr(WX^TXW^T)  }{\partial W}- 2\frac{\partial tr(X^TYW)}{\partial W}  + \frac{\partial tr(Y^TY)}{\partial W} \\
> &= W(X^TX + X^TX) -2 Y^TX \\
> &= 2(WX^T-Y^T)X
\end{align}
> $$
> then 
> $$
> \begin{align}
>\nabla_W RSS(W) = \frac{\partial RSS(W)}{\partial W} = 2(WX^T-Y^T)X
\end{align}
> $$
> $\Box$
> 

> [!NOTE] directional derivative of $RSS(W)$
> ![[Pasted image 20250721152214.png]]
> we regulate $\Delta W$ as a unit vector
> we claim that 
> $$
> \begin{align}
> RSS'_{\Delta W}(W) &= \langle \nabla_W RSS(W), \Delta W \rangle_F \\
> &= \langle 2(WX^T-Y^T)X, \Delta W \rangle_F \\
> &= 2\langle WX^TX-Y^TX, \Delta W \rangle_F \\
> \end{align}
> $$
>
$proof.$
>$$
>\begin{align}
> RSS'_{\Delta W}(W) &= \lim\limits_{t \rightarrow 0} \frac{RSS(W+ t\Delta W)-RSS(W)}{t} \\
> &= \lim\limits_{t \rightarrow 0} \frac{\|X(W+ t\Delta W)^T-Y\|^2_F - \|XW^T-Y\|^2_F }{t} \\
> &= \lim\limits_{t \rightarrow 0} \frac{\|XW^T+ tX(\Delta W)^T-Y\|^2_F - \|XW^T-Y\|^2_F }{t} \\
>  &= \lim\limits_{t \rightarrow 0} \frac{\|XW^T-Y + tX(\Delta W)^T\|^2_F - \|XW^T-Y\|^2_F }{t} \\
> &= \lim\limits_{t \rightarrow 0} \frac{\|XW^T-Y\|^2_F + 2t\langle XW^T-Y, X(\Delta W)^T\rangle_F + \|tX(\Delta W)^T\|^2_F- \|XW^T-Y\|^2_F }{t} \\
> &= \lim\limits_{t \rightarrow 0} \frac{ 2t\langle XW^T-Y, X(\Delta W)^T\rangle_F +t^2 \|X(\Delta W)^T\|^2_F}{t} \\
> &=   2\langle XW^T-Y, X(\Delta W)^T\rangle_F + \lim\limits_{t \rightarrow 0} t  \|X(\Delta W)^T\|^2_F \\
> &= 2\langle XW^T-Y, X(\Delta W)^T\rangle_F \\
> &= 2tr[(WX^T-Y)X(\Delta W)^T] \\
> &= 2\langle WX^TX-Y^TX, \Delta W \rangle_F  \\
>\end{align}
>$$
>$\Box$

> [!NOTE] directional derivative  $\mu'_{\Delta \theta}(\theta)$
> ![[Pasted image 20250722223833.png]]
>
>$proof.$
>we regulate $\Delta \theta$ as a unit vector
>$$
>\begin{align}
> \mu'_{\Delta \theta}(\theta) &= \lim\limits_{t \rightarrow 0} \frac{\mu(\theta+  t\Delta\theta)-\mu(\theta)}{t} \\
> &= \lim\limits_{t \rightarrow 0} \frac{(W_L+t\Delta W_L)(W_{L-1}+t\Delta W_{L-1})\cdots(W_1+t\Delta W_1) - W_LW_{L-1}\cdots W_1}{t} \\
> &= \lim\limits_{t \rightarrow 0} \frac{[W_LW_{L-1}\cdots W_1 + t\sum_{j=1}^LW_{>j}\Delta W_j W_{<j} + o(t) ]- W_LW_{L-1}\cdots W_1}{t} \\
>  &= \lim\limits_{t \rightarrow 0} \frac{ t\sum_{j=1}^LW_{>j}\Delta W_j W_{<j} + o(t)}{t} \\
>  &= \lim\limits_{t \rightarrow 0} \sum_{j=1}^LW_{>j}\Delta W_j W_{<j} + o(t) \\
>  &= \sum_{j=1}^LW_{>j}\Delta W_j W_{<j}
>\end{align}
>$$
>$\Box$
>

> [!NOTE] directional derivative of $RSS\circ \mu$
> ![[Pasted image 20250723105437.png]]
> ![[Pasted image 20250723105453.png]]
> 
> $answer.$
> we regulate $\Delta \theta$ as a unit vector, let $u = \mu(\theta_0 + t\Delta\theta) - \mu(\theta_0)$
> $$
> \begin{align}
> J'_{\Delta \theta}(\theta)|_{\theta = \theta_0} &= \lim\limits_{t \rightarrow 0} \frac{J(\theta_0 + t\Delta\theta) - J(\theta_0)}{t} \\
> &= \lim\limits_{t \rightarrow 0} \frac{(RSS\circ \mu)(\theta_0 + t\Delta\theta) - (RSS\circ \mu)(\theta_0)}{t} \\
> &= \lim\limits_{t \rightarrow 0} \frac{RSS(\mu(\theta_0 + t\Delta\theta)) - RSS(\mu(\theta_0))}{t} \\
> &= \lim\limits_{t \rightarrow 0} \frac{RSS(\mu(\theta_0) + u) - RSS(\mu(\theta_0))}{t} \\
> &= \lim\limits_{t \rightarrow 0} \frac{RSS(\mu(\theta_0)) + D(RSS)_{\mu(\theta_0)}u + R_1(u)- RSS(\mu(\theta_0))}{t} \\
> &= \lim\limits_{t \rightarrow 0} \frac{D(RSS)_{\mu(\theta_0)}u + R_1(u)}{t} \\
>  &= \lim\limits_{t \rightarrow 0} \frac{D(RSS)_{\mu(\theta_0)}(\mu(\theta_0 + t\Delta\theta) - \mu(\theta_0)) + R_1(u)}{t} \\
>  &= \lim\limits_{t \rightarrow 0} \frac{tD(RSS)_{\mu(\theta_0)}((D\mu)_{\theta_0})\Delta\theta + D(RSS)_{\mu(\theta_0)}R_2(t\Delta\theta)+R_1(u)}{t} \\
>  &= D(RSS)_{\mu(\theta_0)}((D\mu)_{\theta_0})\Delta\theta\\
>  &= \nabla RSS_{\mu(\theta_0)}\mu'_{\Delta \theta}(\theta_0) \\
>  &= RSS'_{\mu'_{\Delta \theta}(\theta_0)}(\mu(\theta_0)) \tag{1}
\end{align}
> $$
> where $\mu'_{\Delta \theta}(\theta_0)$ in (1) is the direction of derivative,$\mu(\theta_0)$ is the position of derivative.
> $\Box$
> ^2507231623

> [!NOTE] $\nabla_\theta J(\theta)$
> ![[Pasted image 20250723162922.png]]
> 
> $proof.$
> $$
> \begin{align}
>J'_{\Delta \theta}(\theta) &= 2\langle \mu(\theta)X^TX-Y^TX, \mu'_{\Delta \theta}(\theta) \rangle_F  \\
>&= 2\langle \mu(\theta)X^TX-Y^TX, \sum_{j=1}^LW_{>j}\Delta W_j W_{<j}\rangle_F  \\
>&= 2tr\{ (\mu(\theta)X^T-Y^T)X(\sum_{j=1}^LW_{>j}\Delta W_j W_{<j})^T\}  \\
>&= \sum_{j=1}^L2tr\{ (\mu(\theta)X^T-Y^T)XW_{<j}^T(\Delta W_j)^T W_{>j}^T\}  \\
>&= \sum_{j=1}^L2tr\{ (W_{>j}^T\mu(\theta)X^T-Y^T)XW_{<j}^T(\Delta W_j)^T \}  \\
>&= tr\{ \sum_{j=1}^L 2(W_{>j}^T\mu(\theta)X^T-Y^T)XW_{<j}^T(\Delta W_j)^T \}  \\
>&= tr\{ 
>\begin{bmatrix}
>2(W_{>1}^T\mu(\theta)X^T-Y^T)XW_{<1}^T &
>2(W_{>2}^T\mu(\theta)X^T-Y^T)XW_{<2}^T &
>\cdots &
>2(W_{>n}^T\mu(\theta)X^T-Y^T)XW_{<n}^T 
>\end{bmatrix}
>\begin{bmatrix}
>(\Delta W_1)^T \\
>(\Delta W_2)^T \\
>\vdots \\
>(\Delta W_n)^T
>\end{bmatrix}
>\} \\
>&= tr\{ 
>\begin{bmatrix}
>2(W_{>1}^T\mu(\theta)X^T-Y^T)XW_{<1}^T &
>2(W_{>2}^T\mu(\theta)X^T-Y^T)XW_{<2}^T &
>\cdots &
>2(W_{>n}^T\mu(\theta)X^T-Y^T)XW_{<n}^T 
>\end{bmatrix}
>\begin{bmatrix}
>\Delta W_1 &
>\Delta W_2 &
>\cdots &
>\Delta W_n 
>\end{bmatrix}^T
>\}  \tag{1} \\
>
\end{align}
> $$
> for convinience, let 
> $$
> \begin{align}
> h(\theta) := \begin{bmatrix}
>2(W_{>1}^T\mu(\theta)X^T-Y^T)XW_{<1}^T &
>2(W_{>2}^T\mu(\theta)X^T-Y^T)XW_{<2}^T &
>\cdots &
>2(W_{>n}^T\mu(\theta)X^T-Y^T)XW_{<n}^T 
>\end{bmatrix}
\end{align}
> $$
> $$
> \begin{align}
> \Delta \theta :=\begin{bmatrix}
>\Delta W_1 &
>\Delta W_2 &
>\cdots &
>\Delta W_n 
>\end{bmatrix}
\end{align}
> $$
> 
> then by equation (1)
> $$
> \begin{align}
>J'_{\Delta \theta}(\theta) &= \langle h(\theta), \Delta \theta \rangle_F
\end{align}
> $$
> and by multivariable calculus, $J'_{\Delta \theta}(\theta) = \langle \nabla_\theta J(\theta), \Delta \theta \rangle_F$, hence $\nabla_\theta J(\theta) = h(\theta)$, complete the proof. $\Box$
> 
> 
> 
> 


# 4. Probability Potpourri

> [!NOTE] covariance matrix is PSD
> ![[Pasted image 20250724230233.png]]
>
>$proof.$
>$$
\begin{align}
x^T\Sigma x &= x^T\mathbb{E}[(Z-\mu)(Z-\mu)^T]x \\
&= x^T\mathbb{E}[YY^T]x \\
&= \mathbb{E}[x^TYY^Tx] \\
&= \mathbb{E}[(Y^Tx)^TY^Tx]
\end{align}
>$$
>since $(Y^Tx)^TY^Tx \ge 0$, hence $x^T\Sigma x \ge 0$, then by [[positive semidefinite#^2507251220]], $\Sigma$ is positive semidefinite. $\Box$

> [!NOTE] conditional probability and Beysian equation
> ![[Pasted image 20250725002829.png]]
>
>$answer.$
> since $P(Disease) = 0.001, P(Positive|Disease)=x, P(Posivie|No Disease)=y$, then
>$$
>\begin{align}
> P(Disease | Positive) &= \frac{P(Positive|Disease)\cdot P(Disease)}{P(Positive)} \\
> &= \frac{P(Positive|Disease)\cdot P(Disease)}{P(Positive|No Disease)\cdot P(No Disease)} \\
> &= \frac{0.001x}{0.999y}
>\end{align}
>$$
>let $P(Disease | Positive) > 0.5$, then $\frac{0.001x}{0.999y}>0.5 \Longrightarrow x>\frac{999}{2}y$. $\Box$
>


# 5. Multivariable Normal Distribution

![[Pasted image 20250725131448.png]]

> [!NOTE] $\mathbb{E}[X] = \mu$
> ![[Pasted image 20250725131952.png]]
> 
> $proof.$
> $$
> \begin{align}
> \mathbb{E}[X]  &= \int_{\mathbb{R}^d} xf(x)dx \\
> &= \int_{\mathbb{R}^d} \frac{x}{\sqrt{(2\pi)^d |\Sigma|}} \exp\left\{-\frac{1}{2}(x - \mu)^T \Sigma^{-1}(x - \mu)\right\} \, dx \\
> &= \int_{\mathbb{R}^d} \frac{x-\mu + \mu}{\sqrt{(2\pi)^d |\Sigma|}} \exp\left\{-\frac{1}{2}(x - \mu)^T \Sigma^{-1}(x - \mu)\right\} \, dx \\
> &= \int_{\mathbb{R}^d} \frac{x-\mu + \mu}{\sqrt{(2\pi)^d |\Sigma|}} \exp\left\{-\frac{1}{2}(x - \mu)^T \Sigma^{-1}(x - \mu)\right\} \, dx \\
> &= \int_{\mathbb{R}^d} \frac{x-\mu }{\sqrt{(2\pi)^d |\Sigma|}} \exp\left\{-\frac{1}{2}(x - \mu)^T \Sigma^{-1}(x - \mu)\right\} \, dx +\int_{\mathbb{R}^d} \frac{\mu} {\sqrt{(2\pi)^d |\Sigma|}} \exp\left\{-\frac{1}{2}(x - \mu)^T \Sigma^{-1}(x - \mu)\right\} \, dx \\
> &= \int_{\mathbb{R}^d} \frac{x-\mu }{\sqrt{(2\pi)^d |\Sigma|}} \exp\left\{-\frac{1}{2}(x - \mu)^T \Sigma^{-1}(x - \mu)\right\} \, d(x-\mu)+\mu\int_{\mathbb{R}^d} \frac{1} {\sqrt{(2\pi)^d |\Sigma|}} \exp\left\{-\frac{1}{2}(x - \mu)^T \Sigma^{-1}(x - \mu)\right\} \, dx \tag{1} \\
> &= 0 + \mu \cdot 1
\end{align}
> $$
> the first integration of (1) equals 0 because $\frac{x-\mu }{\sqrt{(2\pi)^d |\Sigma|}} \exp\left\{-\frac{1}{2}(x - \mu)^T \Sigma^{-1}(x - \mu)\right\}$ is odd w.r.t $x-\mu$, then its integration on symmetric region $\mathbb{R}^d$ is 0. $\Box$
> 

> [!NOTE] $Var(X)=\Sigma$
> ![[Pasted image 20250725160858.png]]

$$
\begin{align}
Z &=\Sigma^{-\frac{1}{2}}(X-\mu)\\
&= 
\end{align}
$$

let , then $X=\Sigma^{\frac{1}{2}}Z+\mu$, let $A=\Sigma^{\frac{1}{2}}$ for convinience, then 
$$
\begin{align}
Var(X) &= \mathbb{E}[AZ(AZ)^T]\\
&= \mathbb{E}[AZZ^TA^T]\\
&= A\mathbb{E}[ZZ^T]A^T\\
\end{align}
$$

> [!NOTE] MGF of multivariate normal distribution
> ![[Pasted image 20250727092624.png]]
> 
$proof.$
>$$
\begin{align}
M_x(\lambda) &= \mathbb{E}[e^{\lambda^Tx}] \\
&=\int_{\mathbb{R}^d} e^{\lambda^Tx}\frac{1}{\sqrt{(2\pi)^d |\Sigma|}} \exp\left\{-\frac{1}{2}(x - \mu)^T \Sigma^{-1}(x - \mu)\right\} \, dx \\
&= \int_{\mathbb{R}^d} \frac{1}{\sqrt{(2\pi)^d |\Sigma|}} \exp\left\{\lambda^Tx-\frac{1}{2}(x - \mu)^T \Sigma^{-1}(x - \mu)\right\} \, dx \\
&= \int_{\mathbb{R}^d} \frac{1}{\sqrt{(2\pi)^d |\Sigma|}} \exp\left\{\lambda^Tx-\frac{1}{2}x^T\Sigma^{-1}x + \mu^T\Sigma^{-1}x - \frac{1}{2}\mu^T\Sigma^{-1}\mu\right\} \, dx \\
&= \int_{\mathbb{R}^d} \frac{1}{\sqrt{(2\pi)^d |\Sigma|}} \exp\left\{(\lambda^T+\mu^T\Sigma^{-1})x-\frac{1}{2}x^T\Sigma^{-1}x - \frac{1}{2}\mu^T\Sigma^{-1}\mu\right\} \, dx \tag{*}\\
\end{align}
>$$
>let $\mu_\lambda=\mu+\Sigma\lambda$, then 
>$$
\begin{align}
(*)&=  \int_{\mathbb{R}^d} \frac{1}{\sqrt{(2\pi)^d |\Sigma|}} \exp\left\{ - \frac{1}{2} (x - \mu_{\lambda})^{T} \Sigma^{-1} (x - \mu_{\lambda}) + \frac{1}{2} \lambda^{T} \Sigma \lambda + \lambda^{T} \mu\right \} \, dx \\
&= \exp\left\{  \frac{1}{2} \lambda^{T} \Sigma \lambda + \lambda^{T} \mu\right\}\int_{\mathbb{R}^d} \frac{1}{\sqrt{(2\pi)^d |\Sigma|}}\exp\left\{ - \frac{1}{2} (x - \mu_{\lambda})^{T} \Sigma^{-1} (x - \mu_{\lambda})\right\}\,d(x-\mu_\lambda) \\
&= \exp\left\{  \frac{1}{2} \lambda^{T} \Sigma \lambda + \lambda^{T} \mu\right\} \cdot 1
\end{align}
>$$
>hence
>$$
\begin{align}
M_x(\lambda) &=\exp\left\{  \frac{1}{2} \lambda^{T} \Sigma \lambda + \lambda^{T} \mu\right\}
\end{align}
>$$
>
>complete the proof.$\Box$

> [!NOTE] using MGF to find distribution
> ![[Pasted image 20250727111600.png]]
> 
> $answer.$
> let $y=Ax+b$, then
> $$
> \begin{align}
> M_y(\lambda) &= \mathbb{E}[e^{\lambda^Ty}] \\
> &= \mathbb{E}[e^{\lambda^T(Ax+b)}] \\
> &= \mathbb{E}[e^{\lambda^TAx+\lambda^Tb}] \\
> &= e^{\lambda^Tb}\mathbb{E}[e^{\lambda^TAx}] \\
> &= e^{\lambda^Tb}\mathbb{E}[e^{(A^T\lambda)^Tx}] \\
> &= e^{\lambda^Tb}\mathbb{E}[e^{(A^T\lambda)^Tx}] \\
> &= e^{\lambda^Tb}\exp\left\{\frac{1}{2} (A^T\lambda)^T\Sigma (A^T \lambda) + (A^T\lambda)^T\mu \right\} \\
> &= \exp\left\{\lambda^Tb+\frac{1}{2} (A^T\lambda)^T\Sigma (A^T \lambda) + (A^T\lambda)^T\mu \right\} \\
> &= \exp\left\{  \frac{1}{2} \lambda^T A\Sigma A^T \lambda + \lambda^{T} (A\mu + b)\right\} \\
>\end{align}
> $$
> and since 
> $$
> \begin{align}
> \mathbb{E}[y] &= \mathbb{E}[Ax+b] \\
> &= A\mu + b
\end{align}
> $$
> 
> $$
> \begin{align}
> Var(y) &=  \mathbb{E}[(y-\mathbb{E}[y])(y-\mathbb{E}[y])^T] \\
> &= \mathbb{E}[A(x-\mu)(x-\mu)^TA^T] \\
> &= \mathbb{E}[A(x-\mu)(x-\mu)^TA^T] \\
> &= A\mathbb{E}[(x-\mu)(x-\mu)^T] A^T\\
> &= A\Sigma A^T
\end{align}
> $$
> thus 
> $$
> \begin{align}
>M_y(\lambda) &= \exp\left\{  \frac{1}{2} \lambda^T \Sigma_y \lambda + \lambda^{T} \mu_y\right\} \\
\end{align}
> $$
> hence $y$ is of multivariate normal distribution. $\Box$
> ^2507271303

> [!NOTE] standard multivariate normal distribution
> ![[Pasted image 20250727125622.png]]
> 
> $answer.$
> let $Z=\Sigma^{-\frac{1}{2}}(X-\mu)$, then by [[Math for cs189#^2507271303]], $Z$ is of multivariate normal distribution, and 
> $$
> \begin{align}
> M_z(\lambda) &= \exp\left\{  \frac{1}{2} \lambda^T \Sigma^{-\frac{1}{2}}\Sigma (\Sigma^{-\frac{1}{2}})^T \lambda + \lambda^{T} (\Sigma^{-\frac{1}{2}}\mu -\Sigma^{-\frac{1}{2}}\mu)\right\} \\
> &= \exp\left\{  \frac{1}{2} \lambda^T I \lambda \right\} \\
\end{align}
> $$
> thus, $\mu_z = 0,\Sigma_z =I$. $\Box$
> 






