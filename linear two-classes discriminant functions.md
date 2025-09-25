#ML 

see full content in [[Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library).pdf#page=152|Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library), p.133]]

> [!def] linear two-classes discriminant functions
> We introduce $$y(x) = w^Tx+w_0 $$
> and an input vector $x$ is assigned to class I if $y(x) \ge 0$ and to class II ortherwise.

> [!NOTE] the decision boundary $L_{y=0}$ is perpendicular to $w$
> ![[Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library).pdf#page=151&rect=237,155,366,183|Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library), p.132]]
> ![[Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library).pdf#page=152&rect=20,447,480,664|Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library), p.133]]
> Though we can simply prove this claim if we notice that the $w_0$ in $w^Tx + w_0 = 0$ only does translation to the line or hyper plane $w^Tx=0$, thus we can deem $w^Tx + w_0 = 0$ as $w^Tx =0$ in this situation, and it's obvious that $\forall x \in \{x\in \mathbb{R}^n | w^Tx =0\}$ is perpendicular to $w$.
> However, I made another proof for dim-2 case, anyway, for fun.
> $proof.$
> $L_{y=0}:=\{x\in \mathbb{R}^2 | y(x)=w^Tx + w_0 = 0\}$, this line can also be represented by $\{ t\cdot \vec{v} + \vec{p},t\in \mathbb{R}\}$, where $\vec{v}$ and $\vec{p}$ derives from:
$$w_1x_1^* + w_0 = 0$$
$$w_2x_2^* + w_0 = 0$$
$$x_1^* = \frac{-w_0}{w_1}$$
$$x_2^* = \frac{-w_0}{w_2}$$
>$$
>\vec{v} = 
>\begin{pmatrix}
>x_1^* \\
>0
>\end{pmatrix}
>-
>\begin{pmatrix}
>0 \\
>x_2^*
>\end{pmatrix}
>=\begin{pmatrix}
>x_1^* \\
>-x_2^*
>\end{pmatrix}
>$$
>$$
>\vec{p} = 
>\begin{pmatrix}
>x_1^* \\ 0
>\end{pmatrix}
>$$
>then the line $L_{y=0}=\{\begin{pmatrix}(t+1)\cdot x_1^* \\ -x_2^* \end{pmatrix}, t\in \mathbb{R}\}$, and since for $\forall t \in \mathbb{R}$: 
>$$
>\begin{align}
> w^T\begin{pmatrix}(t+1)\cdot x_1^* \\ -x_2^* \end{pmatrix} &= (t+1)\cdot x_1^*w_1 -x_2^*w_2 \\
>  &= \frac{-w_0}{w_1}w_1 - \frac{-w_0}{w_2}w_2 \\
>  &= 0
>\end{align}
>$$
>Thus $L_{y=0} \perp w$. $\blacksquare$
>Another smart one:
>![[Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library).pdf#page=152&rect=116,402,474,441|Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library), p.133]]


> [!tip] the distance $r$ in this model is not the normal distance
> ![[Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library).pdf#page=152&rect=116,172,489,307|Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library), p.133]]
> compare this $r$ to $d$ in [[normal distance in Euclidian spaces#^2508300157]], notice that $r$ is actually $d$ with a sign.
