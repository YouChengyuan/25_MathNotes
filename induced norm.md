#RealAnalysis 

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
> Let $y=V^T x \in \mathbb{R}^n$, then by [[Lp norm]], we have
> $$
> \|A\|_2 = \sup\limits_{x \ne 0} \frac{\|\Sigma y\|_2}{\|y\|_2} = \sup\limits_{x \ne 0} \frac{y^T\Sigma^2 y}{y^Ty}
> $$
> to find $y$ s.t. $\frac{y^T\Sigma^2 y}{y^Ty}$ reaches its supremum, since 
> $$
> \frac{y^T\Sigma^2 y}{y^Ty} = \frac{\sum_{i=1}^n \sigma_i^2y_i^2}{\sum_{i=1}^n y_i^2}
> $$
> then by [[weighted sum#^2507190123]], let $k$ be the index s.t. $\sigma_k = max\{\sigma_i\}$ , then 
> $$\sup\limits_{x \ne 0} \frac{y^T\Sigma^2 y}{y^Ty}= \max\{\alpha_i\}$$ 

I tried another way to find $\sup\limits_{x \ne 0} \frac{y^T\Sigma^2 y}{y^Ty}$, but somehow I didn't make it
>[!tip] another way 
> let $u=y^T\Sigma^2 y$, $v=y^Ty$ then 
> $$
> \begin{align*}
> \frac{d~\frac{y^T\Sigma^2 y}{y^Ty}}{d~y} &= \frac{d~\frac{u}{v}}{d~y} \\
> &= \frac{v}{v^2}\cdot \frac{du}{dy} - \frac{u}{v^2}\cdot \frac{dv}{dy} \\
>\end{align*}
> $$
> for $\frac{du}{dy}$, since $\frac{du}{dy}= \frac{d~y^T\Sigma^2 y}{d~y}$, let $B= \Sigma^2$, then 
> $$
> y^TBy=\sum_{i=1}^n \sum_{j=1}^n y_iB_{ij}y_j
> $$ 
> for each $k$:
> $$
> \begin{align*}
> \frac{\partial y^T\Sigma^2 y}{\partial y_k} &= \frac{\partial \sum_{i=1}^n \sum_{j=1}^n y_iB_{ij}y_j}{\partial y_k} \\
> &= \sum_{i\in\{1,2,...,n\}/\{k\}}y_iB_{ik} + \sum_{j\in\{1,2,...,n\}/\{k\}}B_{kj}y_j + 2y_kB_{kk}\\
> &= \sum_{i\in\{1,2,...,n\}/\{k\}}2y_iB_{ik} + 2y_kB_{kk}\\
> &= \sum_{i=1}^n2y_iB_{ik} \tag{1}\\ 
> \end{align*}
> $$
> the third equation holds because $B$ is symmetric, then $B_{ik}=B_{ki}$, hense $\sum_{i\in\{1,2,...,n\}/\{k\}}y_iB_{ik} = \sum_{j\in\{1,2,...,n\}/\{k\}} B_{kj}y_j$.
> Then by (1), we have 
> $$
> \frac{d~y^T\Sigma^2 y}{d~y} = 
> \begin{bmatrix}
> \sum_{i=1}^n2y_iB_{i1} \\
> \sum_{i=1}^n2y_iB_{i2} \\
> \vdots \\
> \sum_{i=1}^n2y_iB_{in} \\
> \end{bmatrix}
> =
> \begin{bmatrix}
> \sum_{i=1}^n2y_iB_{1i} \\
> \sum_{i=1}^n2y_iB_{2i} \\
> \vdots \\
> \sum_{i=1}^n2y_iB_{ni} \\
> \end{bmatrix}
> = 2By
> $$
> hense, $\frac{d~u}{d~y}=2By$
> For $\frac{d~v}{d~y}$, 
> $$
> \frac{d~v}{d~y} = \frac{d~y^Ty}{d~y} = 
> \begin{bmatrix}
> \frac{\partial y^Ty}{\partial y_1} \\
> \frac{\partial y^Ty}{\partial y_2} \\
> \vdots \\
> \frac{\partial y^Ty}{\partial y_n} \\
> \end{bmatrix}
> = 
> \begin{bmatrix}
> 2y_1 \\
> 2y_2 \\
> \vdots \\
> 2y_n \\
> \end{bmatrix}
> = 2y
> $$
> then 
> $$
> \begin{align}
> \frac{d~\frac{y^T\Sigma^2 y}{y^Ty}}{d~y} &= \frac{2By}{y^Ty} - \frac{y^T\Sigma^2 y}{(y^Ty)^2}2y \\
> \end{align}
> $$
> let $\frac{d~\frac{y^T\Sigma^2 y}{y^Ty}}{d~y}=0$, then $\frac{2By}{y^Ty} - \frac{y^T\Sigma^2 y}{(y^Ty)^2}\cdot2y=0$ $\Longrightarrow$ $By-\frac{y^T\Sigma^2 y}{y^Ty}y=0$ $\Longrightarrow$ $(B-\frac{y^T\Sigma^2 y}{y^Ty}I)y=0$
<span style="color:rgb(68, 255, 0)">the issue is that I can't solve this equation</span>


> [!NOTE] induced norm
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




