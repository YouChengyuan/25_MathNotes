#ML 

> [!tip] geometrically understanding of OLS
> ![[Pasted image 20250801222839.png]]
> ^2509091451

> [!NOTE] another way to see OLS
> Minimize OLS is equivalent to maximizing the likelihood function under a Gaussian noise distribution
>  [[Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library).pdf#page=133|Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library), p.114]]
# approaches to solve OLS
### approach 1. matrix calculus
reference: [[cs189_note2.pdf#page=2|cs189_note2, p.2]]

> [!NOTE] $w_{OLS}^* = (X^TX)^{-1}X^Ty$
> $proof.$
> [[cs189_note2.pdf#page=2|cs189_note2, p.2]]
> **Warning:** $X^TX$ is not invertible if $X$ has linear dependent columns.
> ^2509081806

> [!warning] $X^TX$ is not invertible if $X$ has linear dependent columns.
> In OLS, once we get the equation
> $$
> \begin{align}
>(X^TX)w_{OLS}^* = X^Ty
\end{align}
> $$
> if we want to solve it by multiplying $(X^TX)^{-1}$ on each side, then we firstly have to ensure that columns in $X$ are all linearly independent, otherwise $X^TX$ is not invertible, then we need to solve $w^*$ in other manner.
> Two takeaways:
> 1. make sure the number of samples is greater than the number of $x_i$
> 2. avoid linear dependence by carefully selecting the feature
> ^2508041849

> [!NOTE] $X^TX$ is not invertible if $X$ has linear dependent columns.
> $proof.$
> If $X$ has linear dependent columns, which is equivalent to that there exists a vector $v$ s.t. $Xv=\vec{0}$, then we have
> $$
> \begin{align}
> (X^TX)v = X^TXv = X^T\vec{0} = \vec{0}
\end{align}
> $$
> thus $(X^TX)$ too has linear dependent columns, and is consequently not invertible. $\blacksquare$
> ^2508032019

> [!warning] remember to check the critical point
> Let $\mathcal{J}_{SE}(w):=\|Y-Xw\|_2^2$, 
> 1. first case, if $f$ is convex(see [[convexity]]), then we will get one $w^*$ s.t. $\nabla_{w}\mathcal{J}_{SE}(w^*)=0$, which is just right to be the desired global minimum point.
> 2. second case, if $f$ is not convex, then we might get more than one $w^*$ s.t. $\nabla_{w}\mathcal{J}_{SE}(w^*)=0$, remember that $w^*$'s are just critical points, they might be a local maximum point, or local minimum point, or a saddle point, thus we have to check which one is the desired global minimum point. The critical point where the value of [[Hessian matrix]] is non-negative in any direction is a local minimum point, we detect such points and compare the value of $f$ on these points with that on boundary (is exists), then we can find the global minimum point.

### approach 2. orthogonal projection

> [!NOTE] OLS regression is actually an orthogonal projection
> ![[Pasted image 20250817183921.png]]
> 
> $proof.$
> Firstly, we can find an orthonormal basis $u_1, \cdots, u_d$ of $W$, and let the matrix $U:= \begin{bmatrix} u_1, \cdots, u_d\end{bmatrix}$ then by [[orthogonal decomposition theorem]], $P_{range(X)} = \sum_{i=1}^{d} \langle y, u_i \rangle u_i$
> thus to complete the proof,  we need to prove that 
> $$\arg\min\limits_{w \in range(X)} \|y-w\|^2 = \sum_{i=1}^{d} \langle y, u_i \rangle u_i$$
> Since for $\forall w \in range(X)$, there exists a unique $a \in \mathbb{R}^d$ s.t. $w = Ua$, then 
> $$
\begin{align}
> \arg\min\limits_{\vec{w}\in range(X)} \|y - w\|^2 &= 
\arg\min\limits_{\vec{a}\in \mathbb{R}^d} \|y - Ua\|^2  \\
&= \arg\min\limits_{\vec{a}\in \mathbb{R}^d} (y-Ua)^T(y-Ua)\\
&= \arg\min\limits_{\vec{a}\in \mathbb{R}^d} (y^T-a^TU^T)(y-Ua) \\
&= \arg\min\limits_{\vec{a}\in \mathbb{R}^d} y^Ty-y^TUa - a^TU^Ty + a^TU^TUa \\
&= \arg\min\limits_{\vec{a}\in \mathbb{R}^d} y^Ty-y^TUa - a^TU^Ty + a^TIa \\
&= \arg\min\limits_{\vec{a}\in \mathbb{R}^d} -y^TUa - a^TU^Ty + a^Ta \\
\end{align}
>$$
> let $g(a):= -y^TUa - a^TU^Ty + a^Ta$, then 
> $$
> \begin{align}
> \nabla_a g(a) &= -U^Ty - U^Ty + 2a 
\end{align}
> $$
> $$
> \begin{align}
> \nabla_a^2 g(a) &= 2 \succeq 0
 \end{align}
> $$
> 
> Then $g$ is a convex function, hence letting $\nabla_a g(a)=0$ gives $\arg\min g(a)=a^* = U^Ty = \left[ \langle u_1, y\rangle, \cdots, \langle u_d, y \rangle \right]^T$
> thus 
> $$\arg\min\limits_{\vec{w}\in range(X)} \|y - w\|^2 = Ua^* = \sum_{i=1}^{d} \langle y, u_i \rangle u_i= P_{range(X)}(y)$$. $\blacksquare$
> ^2508221941

> [!NOTE] The orthogonal projection solution for OLS regression
> ![[cs189_hw2.pdf#page=5&rect=86,511,461,594|cs189_hw2, p.5]]
> $proof.$
> by [[OLS regression#^2508221941]], $\arg\min\limits_{\tilde{w}}\|y-\tilde{w}\|_2^2=P_{range(X)}(y)$, and by [[orthogonal decomposition theorem#^2508221946]] along with [[orthogonal decomposition theorem#^2508221948]], $P_{range(X)}(y)=X(X^TX)^{-1}X^Ty$, thus complete the proof. $\blacksquare$

> [!NOTE] the interception $\beta_0 = \bar{y}$ 
> suppose a data matrix of independent variables $X_{n \times d}$ and the data vector of dependent variable $y$, then a multi-variate OLS linear regression model is represented by:
> $$
> \begin{align}
> y = \beta_0 + X\beta
\end{align}
> $$
> then $\beta_0$ is calculated by:
> $$
> \begin{align}
> \beta_0 = \bar{y} = \frac{1}{n}\sum_{i=1}^ny_i
\end{align}
> $$
> $proof.$
> let $\mathbf{1}$ be the $n\times 1$ vecor of 1s, then the regression model can be rewritten as:
> $$
> \begin{align}
> y = \begin{bmatrix} \mathbf{1} & X\end{bmatrix} 
> \begin{bmatrix} \beta_0 \\ \beta\end{bmatrix}
\end{align}
> $$
> let's just suppose $\begin{bmatrix} \mathbf{1} & X\end{bmatrix}$ is invertible, then by [[OLS regression#^2509081806]], we have
> $$
> \begin{align}
> \begin{bmatrix} \mathbf{1} & X\end{bmatrix} ^T \begin{bmatrix} \mathbf{1} & X\end{bmatrix} \begin{bmatrix} \beta_0 \\ \beta\end{bmatrix} = \begin{bmatrix} \mathbf{1} & X\end{bmatrix} ^T y
\end{align}
> $$
> which can be rewritten as 
> $$
> \begin{align}
>\begin{bmatrix} \mathbf{1} & X_1 & X_2 & \cdots & X_d\end{bmatrix} ^T \begin{bmatrix} \mathbf{1} & X_1 & X_2 & \cdots & X_d\end{bmatrix} \begin{bmatrix} \beta_0 \\ \beta_1 \\ \beta_2 \\ \vdots \\ \beta_d\end{bmatrix} = \begin{bmatrix} \mathbf{1} & X_1 & X_2 & \cdots & X_d\end{bmatrix} ^T y
\end{align}
> $$
> where $X_i$ is the $i$-th column vector of $X$. Simplify the equation then we actually get the matrix representation of a system of equations:
> $$
> \begin{align}
>\begin{bmatrix} \mathbf{1}^T \\ X_1^T \\ \vdots \\ X_d^T \end{bmatrix}
\end{align} (\beta_0\cdot \mathbf{1} + \cdots + \beta_d\cdot X_d) = \begin{bmatrix} \mathbf{1}^Ty \\ X_1^Ty \\ \vdots \\ X_d^Ty \end{bmatrix}
> $$
> notice that the first row of such system reveals the equation
> $$
> \begin{align}
> \sum_{i=1}^ny_i = n\beta_0 + \beta_1 \sum_{i=1}^nX_{i1} + \beta_2 \sum_{i=1}^nX_{i2} + \cdots + \beta_d \sum_{i=1}^nX_{id} 
\end{align}
> $$
> then if we let $\sum_{i=1}^nX_{ij} =0$ for $j=1,\cdots,d$, i.e. the samples of each independent variable are centered, then we get
> $$
> \begin{align}
>\sum_{i=1}^ny_i = n\beta_0 
\end{align}
> $$
> thus $\beta_0 = \bar{y}$. $\blacksquare$
> 
> **Remark.**
> <span style="color:rgb(0, 179, 255)">notice that this is the why the corrected degree of freedom of the coefficients is $d$,rather than $d+1$, because one of them —— $\beta_0$, is fixed by $\beta_0 = \bar{y}$.</span>
> ^2509081857

