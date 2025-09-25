#ConvexOpt 

> [!def] convex set
> A set $S$ is convex if for $\forall x,y\in S$: $x + (1-t)y \in S$ for $\forall t \in \mathbb{R}$.

> [!def] convex function Ver.1
>![[convex_optimization_textbook.pdf#page=81&rect=101,376,477,437|convex_optimization_textbook, p.67]]
> <span style="color:rgb(242, 7, 19)">Notice that the domain of $f$ also has to be a convex set!</span>
> 

> [!def] convex function-Ver.2
> ![[Pasted image 20250801145207.png]]
> the reason that $t \ne 0,1$ and $x_1 \ne x_2$ can be 
> 1. for the need to expend such definition to functions on $\mathbb{R}\cup\{-\infty,\infty\}$, because if $t=0$, then for $x$ s.t. $|f(x)|= \infty$, $t\cdot f(x) = 0\cdot \infty$ is undefined.
> 2. if $t=0,1$ or $x_1 = x_2$, then $\le$ is satisfied for all functions, which is consequently redundant.

> [!def] concave function
> just change the $\le$ into $\ge$ in the definition of convex funtion.

> [!NOTE] a convex function is convex along any line within its domain
> A function is convex if and only if it is convex when restricted to any line that intersects its domain. i.e. for all $v$, the function $g(t) = f (x + tv)$ is convex (on its domain, $\{t | x + tv \in dom \,f \}$)
> 
> $proof.$
> Suppose a convex set $A\in \mathbb{R}^n$, and a function $f: A \rightarrow \mathbb{R}$.
> $(\Rightarrow)$
>  If $f$ is convex, then $g(t) = f(x + tv)$ is convex for any $x$ and $v$.  
> Assume $f$ is convex. Then for any $x, y \in A$ and $\theta \in [0, 1]$:  
> $$
> f(\theta y + (1 - \theta) x) \leq \theta f(y) + (1 - \theta) f(x).
> $$
> Fix $x \in A$ and $v \in \mathbb{R}^n$, and define $g(t) = f(x + tv)$ for $t$ where $x + tv \in A$.  
> For $t_1, t_2$ in $g$'s domain and $\theta \in [0, 1]$:  
> $$
> g(\theta t_1 + (1 - \theta) t_2) = f(x + (\theta t_1 + (1 - \theta) t_2) v) = f(\theta (x + t_1 v) + (1 - \theta) (x + t_2 v)).
> $$
> By convexity of $f$:  
> $$
> f(\theta (x + t_1 v) + (1 - \theta) (x + t_2 v)) \leq \theta f(x + t_1 v) + (1 - \theta) f(x + t_2 v) = \theta g(t_1) + (1 - \theta) g(t_2).
> $$
> Thus:  
> $$
> g(\theta t_1 + (1 - \theta) t_2) \leq \theta g(t_1) + (1 - \theta) g(t_2),
> $$
> proving $g$ is convex.
> $(\Leftarrow)$ 
> If all $g(t) = f(x + tv)$ are convex, then $f$ is convex.  
> Take any $x, y \in A$ and $\theta \in [0, 1]$. Let $v = y - x$.  
> Define $g(t) = f(x + t(y - x))$, which is convex by assumption.  
> Evaluating at $t=0$ and $t=1$:  
> - $g(0) = f(x)$  
> - $g(1) = f(y)$  
> By convexity of $g$:  
> $$
> g(\theta) \leq \theta g(1) + (1 - \theta) g(0)
> $$
> Substituting:  
> $$
> f(x + \theta (y - x)) \leq \theta f(y) + (1 - \theta) f(x),
> $$
> which is the definition of convexity for $f$.
> $\blacksquare$

> [!NOTE] convexity test for differentiable functions
> A differentiable function $f: \mathbb{R}^n \rightarrow \mathbb{R}$ defined on a convex domain is convex if and only if 
$$ f(x) \geq f(y) + (\nabla f(y))^T \cdot (x - y) $$ 
>holds for all $x, y$ in the domain.
![[convex_optimization_textbook.pdf#page=83&rect=114,524,485,679|convex_optimization_textbook, p.69]]
>![[Pasted image 20250801160208.png]]
>
 $proof.$
> suppose $f$ is convex, then fix an arbitrary $y \in \mathbb{R}^n$, for $\forall x\in \mathbb{R}^n$ ,$0<t<1$, we have
> $$
> \begin{align}
> f(tx + (1-t)y) \le tf(x) + (1-t)f(y)
>\end{align}
> $$
> which is equivalent to
> $$
> \begin{align}
> f(y+t(x-y)) \le f(y)+t(f(x) -f(y))
\end{align}
> $$
> which is equivalent to
> $$
> \begin{align}
> \frac{f(y+t(x-y)) - f(y)}{t} \le f(x) -f(y)
\end{align}
> $$
> since $f$ is differentiable, then it is equivalent to
> $$
> \begin{align}
> (\nabla f(y))^T \cdot (x - y) = \lim\limits_{t\rightarrow 0}\frac{f(y+t(x-y)) - f(y)}{t} \le \lim\limits_{t\rightarrow 0}[f(x) -f(y)] = f(x) -f(y)
\end{align}
> $$
> complete the proof.  $\Box$
> ^2508131719

> [!NOTE] convex test for twice-differentiable functions
> ![[convex_optimization_textbook.pdf#page=85&rect=101,518,470,646|convex_optimization_textbook, p.71]]
> $proof.$
> suppose

> [!tip] example of convexity test
> ![[cs189_note2.pdf#page=6&rect=71,580,575,739|cs189_note2, p.6]]

> [!NOTE] The finite intersection of convex sets in finite-dimensional real vector space is also a convex set
> Suppose $C_1, C_2 , \cdots, C_n$ ($n < \infty$) are convex subsets of a finite-dimensional real vector space, and $A = \cap_{i=1}^nC_i \ne \varnothing$, then $A$ is also a convex set.
> 
> $proof.$
> Since for $\forall x,y \in A$：$x,y \in C_i$ ($i=1,\cdots, n$), thus $tx + (1-t)y \in C_i$ holds for any $0 \le t \le 1$ and $i=1,\cdots, n$, which implies that $tx + (1-t)y \in \cap_{i=1}^nC_i = A$, hence $A$ is a convex set. $\blacksquare$
>^2508141643

> [!NOTE] The finite sum of convex functions preserves convexity
> Suppose $\{C_i\}_{i=1}^n$ ($n < \infty$) is a set of convex subsets of $\mathbb{R}^m$ ($m < \infty$),and $A:=\cap_{i=1}^nC_i \ne \varnothing$, then for a set $\{f_i:C_i \rightarrow \mathbb{R}\}_{i=1}^n$ of convex functions defined on those convex sets:
> $$
> \begin{align}
> g = \sum_{i=1}^n f_i
\end{align}
> $$
> is also a convex function on $A$.
> 
> $proof.$
> Since $f_i$'s are convex functions on $C_i$'s, then for $\forall x,y \in A$ and $0 \le t \le 1$ and $i=1,\cdots,n$: 
> $$
> \begin{align}
> f_i(tx + (1-t)y) \le tf_i(x) + (1-t)f_i(y)
\end{align}
> $$
> hence
> $$
> \begin{align}
> \sum_{i=1}^n f_i(tx + (1-t)y) \le \sum_{i=1}^n \left[tf_i(x) + (1-t)f_i(y)\right]
\end{align}
> $$
> which is equivalent to 
> $$
> \begin{align}
> g(tx + (1-t)y) \le tg(x) + (1-t)g(y)
\end{align}
> $$
> thus $g$ is a convex function on $A$. $\blacksquare$
> ^2508121918

> [!NOTE] A linear combo with non-negative scalers of finite convex functions preserves convexity
> Suppose $\{C_i\}_{i=1}^n$ ($n < \infty$) is a set of convex subsets of $\mathbb{R}^m$ ($m < \infty$),and $A:=\cap_{i=1}^nC_i \ne \varnothing$, $\{a_i\}_{i=1}^n$ is a set of real **<span style="color:rgb(242, 7, 19)">non-negative</span>** numbers. Then for a set $\{f_i:C_i \rightarrow \mathbb{R}\}_{i=1}^n$ of convex functions defined on those convex sets:
> $$
> \begin{align}
> g = \sum_{i=1}^n a_if_i
\end{align}
> $$
> is also a convex function on $A$. 
> 
> $proof.$
> Quite the same as the proof of [[convexity#^2508121918]]

> [!NOTE] $1/m$ power with $m \ge 1$ on positive convex functions preserves convexity
> If $f: C\rightarrow \mathbb{R}_+$ ($C \subseteq \mathbb{R}^n$) is a convex positive function, then $g:=f^{1/m}$ with $m\ge1$ is also a convex function.
> 
> $proof.$
> Since
> $$
> \begin{align}
> \nabla g(p) &= \frac{1}{m} f(p)^{1/m-1} \nabla f(p)
\end{align}
> $$
> $$
> \begin{align}
>\nabla^2 g(p) &= \frac{1}{m}\left[ (\frac{1}{m} -1)f(p)^{1/m-2} (\nabla f(p))(\nabla f(p))^T + f(p)^{1/m-1} (\nabla^2 f(p)) \right]\\
> &= \frac{1}{m}f(p)^{1/m-2}\left[ (\frac{1}{m} -1) (\nabla f(p))(\nabla f(p))^T + f(p) (\nabla^2 f(p)) \right]\\
\end{align}
> $$
> then for $x \in C$:
> $$
> \begin{align}
> x^T[\nabla^2 g(p)]x &= x^T\left\{\frac{1}{m}f(p)^{1/m-2}\left[ (\frac{1}{m} -1) (\nabla f(p))(\nabla f(p))^T + f(p) (\nabla^2 f(p)) \right]\right\}x \\
> &= \frac{1}{m}f(p)^{1/m-2}\left[ (\frac{1}{m} -1) x^T(\nabla f(p))(\nabla f(p))^Tx + f(p) x^T(\nabla^2 f(p))x \right] \\
> &= \frac{1}{m}f(p)^{1/m-2}\left[ (\frac{1}{m} -1) [(\nabla f(p))^Tx]^T(\nabla f(p))^Tx + f(p) x^T(\nabla^2 f(p))x \right] 
\end{align}
> $$
> notice that for $\forall x,p \in C$:
> $$[(\nabla f(p))^Tx]^T(\nabla f(p))^Tx \ge0 $$
> $$x^T(\nabla^2 f(p))x \ge 0$$
> $$f(p) > 0$$
> thus $x^T[\nabla^2 g(p)]x \ge 0$ holds for $\forall x,p \in C$, and $g$ is consequently a convex function on $C$ by [[convexity#^2508131719]]. $\blacksquare$
>  

> [!NOTE] $|x|^p$ is convex on $\mathbb{R}$ for $p\ge1$
> ![[convex_optimization_textbook.pdf#page=85&rect=127,112,386,132|convex_optimization_textbook, p.71]]
> $proof.$
> Since $\mathbb{R}$ is a convex set, and for $\forall x, y \in \mathbb{R}$ and $0 \le t \le 1$ :
> (i) if either $x$ or $y$ is $0$:
> without loss of generality, let $y=0$, then
> $$
> |tx+(1-t)y|^p  = \left(|tx| \right) ^p = t^p|x|^p \le t|x|^p
> $$
> (ii) if $x$ and $y$ are both positive or both negative:
> without loss of generality, let $x,y < 0$, then $|x|^p = (-1)^px^p$ and its twice derivative is $(-1)^pp(p-1)x^{p-2}$, which is non-nagative for $\forall x \in \mathbb{R}$, thus $|x|^p$ is convex on $\mathbb{R}_-$, then for $\forall x,y <0$:
> $$
> \begin{align}
> |tx+(1-t)y|^p \le t|x|^p + (1-t)|y|^p
\end{align}
> $$
> similar proof for $x,y>0$.
> (iii) for $x$ and $y$ that are with opposite signs:
> without loss of generality, let $x>0$ and $y<0$,let $z = -y$, then
> $$
> \begin{align}
>|tx+(1-t)y|^p &= |tx-(1-t)z|^p \\
> &\le |tx|^p + |(1-t)z|^p \\
> &\le t|x|^p + (1-t)|z|^p \\
> &= t|x|^p + (1-t)|y|^p \\
> \end{align}
> $$
> Then by (i)(ii)(iii), $|tx+(1-t)y|^p \le t|x|^p + (1-t)|y|^p$ for $\forall x,y \in \mathbb{R}$, thus $|x|^p$ is convex on $\mathbb{R}$. $\blacksquare$
> 
> 

> [!NOTE] $L_p$ norm is a convex function on any convex set not containing the origin point.
>$proof.$
>Directly proved by the theorems above.

> [!NOTE] some convex functions on $\mathbb{R}^n$
> ![[convex_optimization_textbook.pdf#page=86&rect=168,108,521,303|convex_optimization_textbook, p.72]]
> $proof.$
> - **$L_2$ norms**
> suppose $f: \mathbb{R}^n \rightarrow \mathbb{R}$ s.t. $f(x) = \sqrt{\sum_{i=1}^n x_i^2}$, for $\forall x,y\in \mathbb{R}^n$ and $0 \le t \le 1$ :
> $$
> \begin{align}
> f(tx + (1-t)y) &= \sqrt{\langle tx + (1-t)y, tx + (1-t)y\rangle} \\
> &= \sqrt{\langle tx , tx \rangle + \langle tx ,(1-t)y\rangle+ \langle (1-t)y, tx \rangle + \langle (1-t)y,(1-t)y\rangle} \\
> &= \sqrt{\langle tx , tx \rangle + 2\langle tx ,(1-t)y\rangle + \langle (1-t)y,(1-t)y\rangle} \\
> &\le \sqrt{\langle tx , tx \rangle + \langle (1-t)y,(1-t)y\rangle} \\
> &\le \sqrt{\langle tx , tx \rangle} + \sqrt{\langle (1-t)y,(1-t)y\rangle} \\
> &= t\sqrt{\langle x , x \rangle} + (1-t)\sqrt{\langle y,y\rangle} \\
> &= tf(x) + (1-t)f(y)
\end{align}
> $$
> $\blacksquare$
> 
> - **max function**
> suppose $f: \mathbb{R}^n \rightarrow \mathbb{R}$ s.t. $f(x) = \max\{x_1,\cdots,x_n\}$, for $\forall x,y\in \mathbb{R}^n$ and $0 \le t \le 1$ :
> $$
> \begin{align}
> f(tx + (1-t)y) &= \max\{tx_1+(1-t)y_1, \cdots, tx_n+(1-t)y_n\} \\
>  &\le t\max\{x_1, \cdots, x_n\} + (1-t)\max\{y_1, \cdots, y_n\} \\
>  &= tf(x) + (1-t)f(y)
\end{align}
> $$
> $\blacksquare$
> 
> - **quadratic-over-linear function**
> suppose $f: C \rightarrow \mathbb{R}$ s.t. $f(x) = \frac{x_1^2}{x_2}$, and $C:= \{(x_1, x_2) \in \mathbb{R}^2 | x_2 > 0\}$,then:
> $$
> \begin{align}
> \nabla f(x) = \begin{bmatrix} 2x_1/x_2 \\ -x_1^2/x_2^2 \end{bmatrix}
\end{align}
> $$
> $$
> \begin{align}
>\nabla^2 f(x) = 
>\begin{bmatrix} 
>2/x_2 & -2x_1/x_2^2 \\
> -2x_1 /x_2^2 & 2x_1^2/x_2^3 \\
>\end{bmatrix}
> =
> \frac{2}{x_2^3} 
> \begin{bmatrix} 
>x_2^2 & -x_1x_2\\
> -x_1x_2  & x_1^2 \\
>\end{bmatrix}
> = 
> \frac{2}{x_2^3} 
> \begin{bmatrix} 
>x_2 \\
> -x_1 \\
>\end{bmatrix}
>\begin{bmatrix} 
>x_2 & -x_1 
>\end{bmatrix}
\end{align}
> $$
> then for $\forall v \in \mathbb{R}^2$, $\forall x \in C$:
> $$
> \begin{align}
> v^T\nabla^2 f(x)v &= 
> \frac{2}{x_2^3} 
> v^T
> \begin{bmatrix} 
>x_2 \\ -x_1 
>\end{bmatrix}
>\begin{bmatrix} 
>x_2 & -x_1 
>\end{bmatrix}
>v \\
> &=
> \frac{2}{x_2^3} 
> \left\{
> \begin{bmatrix} 
>x_2 & -x_1 
>\end{bmatrix}
>v
>\right \}^T
>\begin{bmatrix} 
>x_2 & -x_1 
>\end{bmatrix}
>v \\
> &\ge 0
> \end{align}
> $$
> $\blacksquare$
> - **log-sum-exp**
> The Hessian of the log-sum-exp function is
> $$\nabla^2 f(x) = \frac{1}{(1^T z)^2} \left((1^T z) \text{ diag}(z) - zz^T\right)$$
> where $( z = (e^{x_1}, \ldots, e^{x_n}) )$. To verify that $(\nabla^2 f(x) \geq 0$ we must show that for all $(v, v^T \nabla^2 f(x) v \geq 0$, i.e.,
> $$v^T \nabla^2 f(x) v = \frac{1}{(1^T z)^2} \left(\left(\sum_{i=1}^n z_i \right) \left(\sum_{i=1}^n v_i^2 z_i \right) - \left(\sum_{i=1}^n v_i z_i \right)^2 \right) \geq 0.$$
> But this follows from the Cauchy-Schwarz inequality $((a^T a)(b^T b) \geq (a^T b)^2$ applied to the vectors with components $(a_i = v_i \sqrt{z_i})$, $(b_i = \sqrt{z_i})$. $\blacksquare$

> [!NOTE] some concave functions on $\mathbb{R}^5$
> ![[convex_optimization_textbook.pdf#page=87&rect=116,379,478,440|convex_optimization_textbook, p.73]]
> 
> $proof.$
> [[convex_optimization_textbook.pdf#page=88|convex_optimization_textbook, p.74]]


