#ConvexOpt 

> [!def] Jensen's inequality 
> ![[convex_optimization_textbook.pdf#page=91&rect=191,316,379,336|convex_optimization_textbook, p.77]]

> [!thr] extend Jensen's inequality to discrete multi-weighs
> If $f: C \rightarrow \mathbb{R}$ is convex on the convex set $C \subseteq \mathbb{R}^n$, then for $t_1,\cdots, t_n \in [0,1]$ s.t $\sum_{i=1}^n t_i = 1$ and $\forall x_1,\cdots,x_n \in C$:
> $$
> \begin{align}
> f(t_1x_1 + \cdots + t_nx_n) \le t_1f(x_1) + \cdots + t_nf(x_n)
\end{align}
> $$
> $proof.$
> - (i) If $\exists i \in \{1,\cdots,n\}$ s.t. $t_i = 1$:
> then
> $$
> \begin{align}
> f(t_1x_1 + \cdots + t_nx_n)  = f(x_i) 
> \le 0\cdot f(x_1) + \cdots + 1\cdot f(x_i) + \cdot 0\cdot f(x_n)
\end{align}
> $$
> which satisfies the desired inequality.
> 
> - (ii) If $t_i < 1$ for $i=1,\cdots,n$:
> Since $f$ is convex, then for $\forall x_1,\cdots,x_n \in C$, each inequality below holds
> $$
>\begin{align}
>f(t_1x_1 + \cdots + t_nx_n) & = f\left(t_1x_1+(1-t_1)(\frac{t_2}{1-t_1}x_2 + \cdots + \frac{t_n}{1-t_1}x_n )\right) \\
 &\le t_1f(x_1) + (1-t_1)f\left( \frac{t_2}{1-t_1}x_2 + \cdots + \frac{t_n}{1-t_1}x_n\right) \\
 &= t_1f(x_1) + (1-t_1)f\left( \frac{t_2}{1-t_1}x_2 + (1-\frac{t_2}{1-t_1})(\frac{t_3}{1-\frac{t_2}{1-t_1}}x_3 + \cdots + \frac{t_n}{1-\frac{t_2}{1-t_1}}x_n)\right) \\
 &\le t_1f(x_1) +  (1-t_1) \left[\frac{t_2}{1-t_1}f(x_2) + (1-\frac{t_2}{1-t_1}) f\left( \frac{t_3}{1-\frac{t_2}{1-t_1}}x_3 + \cdots + \frac{t_n}{1-\frac{t_2}{1-t_1}}x_n\right)\right] \\
 &= t_1f(x_1) + t_2f(x_2) + (1-t_1-t_2)  f\left( \frac{t_3}{1-\frac{t_2}{1-t_1}}x_3 + \cdots + \frac{t_n}{1-\frac{t_2}{1-t_1}}x_n\right) \\
 &\vdots \\
 &\le t_1f(x_1) + \cdots + t_nf(x_n)
\end{align}
> $$
> 
> (i) and (ii) imply that the desired inequality holds for $t_1,\cdots, t_n \in [0,1]$ s.t $\sum_{i=1}^n t_i = 1$ and $\forall x_1,\cdots,x_n \in C$ .$\blacksquare$
> ^2508150007

> [!thr]  extend Jensen's inequality to continuous multi-weighs
> Let $n\rightarrow \infty$ in the inequality of discrete multi-weighs occasion:
> $$
> \begin{align}
> f(\sum_{i=1}^n t_ix_i) \le \sum_{i=1}^n t_if(x_i)
\end{align}
> $$
> i.e. if $p(x) \ge 0$ on $S \subseteq \mathbf{dom} \,f$, and $\int_S p(x) \,dx = 1$, then for a convex function $f$ on $S$:
> $$
> \begin{align}
> f(\int_S p(x)x \,dx) \le \int_S p(x)f(x)\,dx
\end{align}
> $$
> which is equivalent to 
> $$
> \begin{align}
> f(\underset{S}{\mathbb{E}}[x]) \le \underset{S}{\mathbb{E}}[f(x)]
\end{align}
> $$
> 
> $proof.$

> [!NOTE] noise of inputs cannot decrease the value of a convex function
> ![[convex_optimization_textbook.pdf#page=92&rect=173,501,524,570|convex_optimization_textbook, p.78]]

