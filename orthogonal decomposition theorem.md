#LinearAlgebra 

![[Pasted image 20250817185259.png]]

> [!NOTE] The orthogonal projection operator 
>![[Pasted image 20250817200109.png]]
>
> $proof.$
> ($\Rightarrow$)
> If $P$ is a rank-$d$ projection matrix, then $P$ is symmetric due to $P-=P^T$,then by [[spectual theorem]], there exists a orthogonal matrix $Q$ and a $d\times d$ diagonal matrix $\Sigma$ and $rank(\Sigma)=d$, s.t.  $P=Q^T\Sigma Q$, then $P = P^2$ gives that $P=Q^T\Sigma^2 Q=(Q^T\Sigma)(Q^T\Sigma)^T=UU^T$, where $U:=Q^T \Sigma$, and 
> $$
> \begin{align}
> U^TU &= (Q^T\Sigma)^T(Q^T\Sigma)\\ 
> &= \Sigma^TQQ^T\Sigma\\ 
> &=\Sigma^T\Sigma \\ 
> &= \Sigma^2  \\
> &= \begin{bmatrix}
\lambda_1^2 & 0        & \cdots & 0 \\
0        & \lambda_2^2 & \cdots & 0 \\
\vdots   & \vdots    & \ddots & \vdots \\
0        & 0         & \cdots & \lambda_d^2
\end{bmatrix} \\
> \end{align}
> $$
> notice that $P=P^2$ also proved that $\Sigma = \Sigma^2$, i.e. 
> $$
> \begin{align}
> \begin{bmatrix}
\lambda_1^2 & 0        & \cdots & 0 \\
0        & \lambda_2^2 & \cdots & 0 \\
\vdots   & \vdots    & \ddots & \vdots \\
0        & 0         & \cdots & \lambda_d^2
\end{bmatrix} 
> = 
> \begin{bmatrix}
\lambda_1 & 0        & \cdots & 0 \\
0        & \lambda_2 & \cdots & 0 \\
\vdots   & \vdots    & \ddots & \vdots \\
0        & 0         & \cdots & \lambda_d
\end{bmatrix} 
\end{align}
> $$
> hence $\lambda_i = \lambda_i^2$ $\Longrightarrow$ $\lambda_i = 0$ or $1$
> however, if $\lambda_i=0$, $rank(\Sigma)<d$, contradicting to that $rank(\Sigma)=d$, thus $\lambda_i=1$ for $i=1,\cdots, d$, complete the proof of this direction.
> 
> ($\Leftarrow$)
> If $P=UU^T$ and $U^TU=I$, then 
> $$P^T=(UU^T)^T=UU^T=P$$
> $$P^2 = P^TP = UU^TUU^T = UIU^T=UU^T = P$$
> To prove that $rank(P)=d$, suppose $rank(P)<d$ for contradiction, then
> $$
> \begin{align}
> rank(P) = rank(UU^T) = rank(U) < d
> \end{align}
> $$
> which means that there exists linear dependent column vectors in $U$, hence by [[OLS regression#^2508032019]], $U^TU$ is not invertible, contradicting to the fact that $U^TU=I$, thus $rank(P)=d$.
> Then since $P^T=P$, $P^2=P$, $rank(P)=d$, thus $P$ is a rank-$d$ projection matrix, complete the proof of this direction.
> $\blacksquare$
> ^2508221707

> [!NOTE] $X(X^TX)^{-1}X^T$ is a rank-$d$ orthogonal projection matrix
> ![[cs189_hw2.pdf#page=5&rect=86,623,565,677|cs189_hw2, p.5]]
> $proof.$
> By [[singular value decoposition]], there exists $U\in \mathbb{R}^{n\times d}$  and $V\in \mathbb{R}^{d\times d}$ s.t. $X=U\Sigma V^T$, then
> $$X=U\Sigma V^T$$
$$X^TX=V\Sigma U^TU\Sigma V^T=V\Sigma^2 V^T$$
$$(X^TX)^{-1}=V\Sigma^{-2}V^T$$
$$X(X^TX)^{-1}X^T=U\Sigma V^TV\Sigma^{-2}V^TV\Sigma U^T=UU^T$$
> and notice that $u^TU=I$, thus by [[orthogonal decomposition theorem#^2508221707]], $X(X^TX)^{-1}X^T$ is a rank-$d$ orthogonal projection matrix.$\blacksquare$
> ^2508221946

> [!NOTE] $X(X^TX)^{-1}X^T$ is a projection onto $range(X)$
> ![[cs189_hw2.pdf#page=5&rect=87,598,375,620|cs189_hw2, p.5]]
> $proof.$
> 
> Let $P$ denotes $X(X^TX)^{-1}X^T$
> - (i) $P^2=P$:
> $$
> \begin{align}
> P^2 &= X(X^TX)^{-1}X^TX(X^TX)^{-1}X^T \\
> &= X(X^TX)^{-1}X^T \\
> &= P
\end{align}
> $$
> - (ii) $range(P) = range(X)$:
> For $\forall w\in range(P)$: $\exists v\in \mathbb{R}^n$, s.t.
> $$
> \begin{align}
> w &= Pv \\
> &= X(X^TX)^{-1}X^Tv \\
> &= X\tilde{v} \in range(X)
\end{align}
> $$
> where $\tilde{v}=(X^TX)^{-1}X^Tv$, and the equation indicated that $range(P)\subseteq range(X)$;
> For $\forall w \in range(X)$: $\exists u \in \mathbb{R}^d$ s.t. 
> $$
> \begin{align}
> w=Xu
\end{align}
> $$
> and suppose $v\in \mathbb{R}^n$ s.t. $(X^TX)^{-1}X^Tv=u$ $\Longrightarrow$ $X^Tv=X^TXu$ thus $v=Xu$, then we have 
> $$
> \begin{align}
> w &= Xu \\
> &= X[(X^TX)^{-1}X^Tv] \\
> &= X(X^TX)^{-1}X^Tv \\
> &= Pv \in range(X)
\end{align}
> $$
> thus $range(X) \subseteq range(P)$;
> Therefore, $range(X) =range(P)$.
> 
> Then by [[projection#^2508221810]], (i) and (ii) implies the desired result. $\blacksquare$
> ^2508221948




 