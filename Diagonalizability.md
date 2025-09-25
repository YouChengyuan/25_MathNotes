#LinearAlgebra

# 1. minimal poly
>[!note] eigenvalues are roots of the minimal polynomial
>![[Pasted image 20250618000541.png]]
><span style="color:rgb(242, 7, 19)">this can be used for calculating the eigenvalues of a matrix</span><span style="color:rgb(68, 255, 0)">(but the challege is how to find the minimal poly)</span>
>

> [!NOTE] the upper bound of the degree of minimal poly
> ![[Pasted image 20250618213912.png]]
> $proof$
> Let $m(T)$ denote the minimal poly of $T$.  If $V=\{0\}$, then $m(T)=1$, which has degree 0 = dimV by definition. For the case that $dimV>0$, suppose the desired result is true for all operator on all vector spaces of dimension less than $dimV$.
> Notice that $T$ is invariant under $span(T^0v=v, T^1v, T^2v, ...)$, let $m$ be the smallest integer s.t. $T^mv \in span(T^0v=v, T^1v, T^2v, ..., T^{m-1}v)$, then $v, Tv, ..., T^{m-1}$ is linearly independent, hense the dimension of $X:=span(v, Tv, ..., T^{m-1})$ is $m$, moreover, $T$ is invariant under $X$ (proof: we are going to prove that for $\forall k \in \{m+1, m+2, ...\}$ : $T^kv \in X$. Since $T^mv \in span(T^0v=v, T^1v, T^2v, ..., T^{m-1}v)$, then $\exists n \le m-1,\alpha \in \mathbb{F}$ s.t.$$  \alpha T^nv = T^mv \tag{1}$$ then $T^{m+2}v=\alpha T^{n+1}v$, notice that $n+1\le m$, if $n+1=m$, then we can apply $(1)$ again to keep the exponential of $T$ less or equal to m-1, therefore, for $\forall k\ge m$, we can apply $(1)$ several times to reduce the exponential to $\le m-1$, complete the proof). Since $T^mv \in span(T^0v=v, T^1v, T^2v, ..., T^{m-1}v)$, then there exist an nonetrivial list of number $a_0,a_1,a_2,...,a_m$ s.t. 
> $$T^mv = a_0v+a_1T^1v+a_2T^2v+\cdots +a_mT^{m-1}v \tag{2}$$ 
> Let $$q(T):=a_0I+a_1T^1+a_2T^2+\cdots +a_mT^{m-1}-T^m \tag{3}$$ 
> then by (2) we have $$q(T)v=(a_0I+a_1T^1+a_2T^2+\cdots +a_mT^{m-1}-T^m)v=0 \tag{4}$$
> thus $q(T)$ is a zero map on $X$, as you may check, then $nullityT \ge dimX=m$, then $$rank~q(T)=dimV-nullity~T \le dimV - m$$
> Since $range~q(T)$ is invariant under $T$, thus by the hypothesis to $T|_{range~q(T)}$ on $range~q(T)$, the minimal poly $s$ of $T|_{range~q(T)}$ is of $deg~s \le dimV-m$ and $s(T|_{range~q(T)})=0$ .Thus for $\forall v \in V:$
> $$(sq)(T)v=s(T)q(T)v=0$$
> notice that $sq$ is a monic poly satisfied by $T$, thus the degree of the minimal poly of $T$ is less than or equal to $deg~sq=deg~s+deg~q \le dimV-m + m=dimV$, complete the proof. $\Box$

# 2. Upper-triangular matrix

> [!NOTE] a monic poly of the upper-triangular matrix
>![[Pasted image 20250620203947.png]]
> $proof.$
> Let the upper-triangular matrix be 
>$$
\begin{bmatrix}
\lambda_1 & a_{12}   & a_{13}   & \cdots  & a_{1n}   \\
0         & \lambda_2 & a_{23}   & \cdots  & a_{2n}   \\
0         & 0         & \lambda_3 & \cdots  & a_{3n}   \\
\vdots    & \vdots    & \vdots   & \ddots  & \vdots   \\
0         & 0         & 0        & \cdots  & \lambda_n
\end{bmatrix}
\tag{1}
>$$
>suppose the basis that the matrix above w.r.t is $v_1, v_2, ..., v_n$, then for each $v_i$: $(T-\lambda_iI)v_i=a_{1,i}~v_1+a_{2,i}~v_2+\cdots+a_{i-1,i}~v_{i-1}$ 
>$$
>\begin{aligned}
>(T-\lambda_1I)(T-\lambda_2I)\cdots(T-\lambda_nI)v_i &=(T-\lambda_1I)(T-\lambda_2I)\cdots(T-\lambda_{n-1}I)(T-\lambda_iI)v_i \\
>&=(T-\lambda_1I)(T-\lambda_2I)\cdots(T-\lambda_{n-1}I)\sum\limits_{k=1}^{i-1} (a_{k,i}\vec{v_k})\\
>&=\sum\limits_{k=1}^{i-1}[(T-\lambda_1I)(T-\lambda_2I)\cdots(T-\lambda_{n-1}I)(a_{k,i}\vec{v_k})]\\
>&=\sum\limits_{k=1}^{i-1}E_k
>\end{aligned}
>\tag{2}
>$$
>where $E_k$ denotes $(T-\lambda_1I)(T-\lambda_2I)\cdots(T-\lambda_{n-1}I)(a_{k,i}\vec{v_k})$ for each $k=1,2,...,i-1$ , then apply the same fashion as (2) inductively untill $E_k$ was reduced to $(T-\lambda_1)(c\cdot \vec{v_1})=\vec{0}$,where $c$ is a constant, and the second equality is by (1), thus $\sum\limits_{k=1}^{i-1}E_k=\sum\limits_{k=1}^{i-1}\vec{0}$
>Since (2) applies for $\forall~i \in {1, 2,..., n}$, thus $(T-\lambda_1I)(T-\lambda_2I)\cdots(T-\lambda_nI)$ is a zero map on $V$, complete the proof. $\Box$
>^2506212318


> [!NOTE] diagonal elements of an upper-triangular matrix are nothing but eigenvalues
> **suppose $T\in \mathcal{L}(A)$ is an upper-triangular matrix, then $\lambda_1, \lambda_2, ..., \lambda_m$ are eigenvalues of $T$ if and only if they are numbers on the diagonal of $T$.**
> <span style="color:rgb(242, 7, 19)">however, remind that elements on the diagonal may not be unique, which is why the monic polynomial $(T-\lambda_1I)(T-\lambda_2I)\cdots(T-\lambda_nI)$ in [[Diagonalizability#^2506212318]] may not be the minimal poly, but it must the multiple of the minimal poly</span>
> $proof.$
> - **Lemma1. eigenvalues are contained in the diagonal of a upper-triangular matrix**
> $proof.$Since the monic polynomial $(T-\lambda_1I)(T-\lambda_2I)\cdots(T-\lambda_nI)=\tilde{0}$ in [[Diagonalizability#^2506212318]] is a multiple of the minimal poly of $T$, thus eigenvalues of the matrix, which are also the root of the minimal poly, are also roots of the minic poly. 
> - **Lemma2. each diagonal entry $\lambda_i$ is an eigenvalue of $T$**
> $proof.$ 
> By (1) in [[Diagonalizability#^2506212318]], notice that $T-\lambda_iI$ maps $span(v_1,...,v_i)$ into $span(v_1,...,v_{k-1}$, i.e, from a i-dimensional subspace of $V$ to a (i-1)-dimensional subspace of V, thus $T-\lambda_iI$ is not injective, i.e, $nullity(T-\lambda_iI)$ > 0 $\Longrightarrow$ $\exists \vec{v}\neq0$ in $V$ s.t. $(T-\lambda_iI)\vec{v}=0$, thus $\lambda_i$ is a eigenvalue of $V$ 


> [!NOTE] the sufficient and necessary condition of upper-triangularizability 
> ![[Pasted image 20250622161952.png]]
> $proof.$
> $(\Rightarrow)$ suppose the minimal poly of $T$ is $(T-\lambda_1I)(T-\lambda_2I)\cdots(T-\lambda_mI)$, where $\lambda_1, ..., \lambda_m$ are distinct numbers. Then 

# Diagonalizability


> [!def] Diagonalizability(ver1.)
> An operator $T\in \mathcal{L}(A)$ is diagonalizable if it can be represented by a diagonal matrix in some basis of $V$


> [!thr] Diagonalizability
> if $A\in \mathcal{L}(\mathbb{R}^n)$ has $n$ linearly independent eigenvectors $x_1, ..., x_n$, let $X$ be the matrix of such eigenvectors, then the eigenvalue matrix $\Lambda$ of $A$ is:
> $$
> X^{-1}AX=\Lambda=
> \begin{bmatrix}
\lambda_1 & & & \\
& \lambda_2 & & \\
& & \ddots & \\
& & & \lambda_n
\end{bmatrix} 
> $$
> $proof.$
> easy to prove by [[Diagonalizability#^2507101645]]
> ^2507101646


> [!NOTE] sufficient and necessary conditions for diagonalizability
> ![[Pasted image 20250622222355.png]]
> <span style="color:rgb(242, 7, 19)">brieffly, we only need to find $dimV$ amount of linear independent eigenvectors of $T$, then $T$ is diagonalizable</span>
> ^2507101645


> [!NOTE] condition for diagonalizability (Ver.2)
> ![[Pasted image 20250622231925.png]]
> $proof.$
> see [[110 class notes_202505211226_48940.pdf#page=193|110 class notes_202505211226_48940, p.193]]


but when can a matrix be decomposed?
![[Pasted image 20250616000328.png]]
	when a matrix is diagonolizable?
	what is the geometric multiplicity and algebraic multiplicity



