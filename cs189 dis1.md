#ML #StatNProb 

problem sheet [[cs189_dis1.pdf#page=1|cs189_dis1, p.1]]

> [!NOTE] 1.c 
> ![[Pasted image 20250802224935.png]]
> $remark.$
> let $q(r_i) := \begin{bmatrix} \delta_{1}(r_i) &  \delta_{2}(r_i) & \delta_{3}(r_i) & \delta_{4}(r_i)  \end{bmatrix}^T$ , where
> $$
> \begin{align}
> \delta_k(r_i) = \left\{ \begin{array}{rcl} 1 & \mbox{for} & r_i = k \\ 0 & \mbox{for} & r_i \ne k \end{array}\right. ~~~~~~~~~~~~k= 1,2,3,4
\end{align}
> $$
> then $\|q(r_i)\|_1 = 1$, $q(r_i)$ is a valid vector of probability per class.
> Then the cross-entropy ([[Kullback-Leibler (KL) divergence]]) based  on raw observations mentioned in the problem is actually expressed as:
> $$
> \begin{align}
> D_{\text{KL}}(q \parallel p) &= \sum_{i=1}^n  q(r_i)^T \log \left(q(r_i) \right) - \sum_{i=1}^n q(r_i)^T \log (p) \\
> &= \sum_{i=1}^n\left \{ q(r_i)^T \cdot  \begin{bmatrix} 
\log \delta_{1}(r_i) \\  
\log \delta_{2}(r_i) \\ 
\log \delta_{3}(r_i) \\ 
\log \delta_{4}(r_i)  
\end{bmatrix} \right\} - \sum_{i=1}^n\left\{ q(r_i)^T  \cdot  \begin{bmatrix} 
\log p_1 \\  
\log p_2 \\ 
\log p_3\\ 
\log p_4  
\end{bmatrix}\right\} \tag{*} \\
\end{align}
> $$
> since the first monomial in $(*)$ is a constant, therefore, to minimize $D_{\text{KL}}(q \parallel p)$ only needs to minimize the second monomial in $(*)$, which is exactly the function $-\sum_{i=1}^n \sum_{y \in B} \delta_{r_i y} \log p_y$ given in the problem.
> 
> $proof.$
> let $D(p)$ denotes $-\sum_{i=1}^n \sum_{y \in B} \delta_{r_i y} \log p_y$, by remark, we have:
> $$
> \begin{align}
> D(p) &= -\sum_{i=1}^n q(r_i)^T \log (p) \\
> &= -\left(\sum_{i=1}^n q(r_i)^T \right)\log (p)\\
> &= - Q^T\log (p) \\
> &= - \sum_{k=1}^4 Q_k\log (p_k)
\end{align}
> $$
> where $Q:=\sum_{i=1}^n q(r_i)=  (Q_1,Q_2,Q_3,Q_4)^T\in \mathbb{R}^4$, and $D(p)$ is indeed a function w.r.t. $p$, then we can calculate the gradient of $D$ w.r.t. $p$. 
> $$
> \begin{align}
> \nabla_pD(p) &= -
> \begin{bmatrix}
> \frac{\partial Q^T\log (p)}{\partial p_1} \\
> \frac{\partial Q^T\log (p)}{\partial p_2} \\
> \frac{\partial Q^T\log (p)}{\partial p_3} \\
> \frac{\partial Q^T\log (p)}{\partial p_4} \\
> \end{bmatrix} \\
> &= -
> \begin{bmatrix}
> \frac{Q_1}{p_1} \\
> \frac{Q_2}{p_2} \\
> \frac{Q_3}{p_3} \\
> \frac{Q_4}{p_4} \\
> \end{bmatrix} \\
> \end{align}
> $$
> since by definition of $q(r_i)$, $Q_k \ge 0$ and the equality will not hold simultaneously for $k=1,2,3,4$ , thus $\nabla_pD(p) < 0$ on $\mathbb{R}_+^4$

$\arg\min\limits_{p\in \mathbb{R}^4_+, \sum_{i=1}^4 p_i=1}\sum_{i=1}^4a_i\log(p_i)$

$a_i >0$ $(i=1,2,3,4)$




> [!NOTE] 2.(a) uncorrelation can not universally infer independence
> ![[Pasted image 20250803135645.png]]
> $P(Y=1|X=0) = P(Y=-1|X=0)=0.5$, $P(X=1|Y=0) = P(X=-1|Y=0)=0.5$
> $P(Y=1,X=0) = P(Y=-1,X=0) = 0.25$
> $P(Y=0,X=1) = P(Y=0,X=-1) = 0.25$
> thus
> $$
\begin{pmatrix}
 & X=-1 & X=0 & X=1 \\
Y=-1 & 0 & 0.25 & 0 \\
Y=0 & 0.25 & 0 & 0.25 \\
Y=1 & 0 & 0.25 & 0 \\
\end{pmatrix}
>$$
>$$
> \begin{align}
> Cov(X,Y) = \sum_{X,Y\in\{-1,0,1\}} X\cdot Y\cdot P(X,Y) = 0
\end{align}
> $$
> hence, $X$ and $Y$ are uncorrelated, however, since 
> $$
> \begin{align}
> P(X=0, Y=0) = 0 \ne 0.25 = P(X=0)\cdot P(Y=0)
\end{align}
> $$
> hence, $X$ and $Y$ are dependent.
> ^2508031619

> [!NOTE] 2.(b)
> ![[Pasted image 20250803142404.png]]
> $proof.$
> since $X_i,X_j$ are independent for all $i\ne j$, then $p(x_i,x_j) = p(x_i)p(x_j)$, hence for all $i\ne j$:
> $$
> \begin{align}
> Cov(X_i,X_j) &= 
> \int_{\mathbb{R}}\int_{\mathbb{R}}x_ix_jp(x_i)p(x_j)\,dx_i\, dx_j  - \mu_i\mu_j\\
>  &= \int_{\mathbb{R}}x_ip(x_i)\,dx_i\int_{\mathbb{R}}x_jp(x_j)\, dx_j  - \mu_i\mu_j\\
>  &= \mu_i\mu_j - \mu_i\mu_j \\
>  &= 0
\end{align}
> $$
> and for all entries on the diagonal:
> $$
> \begin{align}
> Cov(X_i,X_i) = Var(X_i) \ge 0
\end{align}
> $$
> thus $\Sigma$ is a diagonal matrix.$\Box$
> 










