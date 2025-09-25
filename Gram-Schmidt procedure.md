#LinearAlgebra 

The foundamental theorem as a lemma for Gram-Schimidt procedure:
> [!NOTE] The orthogonal decomposition for a vector
> Fix $\vec{v} \in V$, for $\forall \vec{w} \in V$, let
> $$
> \vec{u}= \vec{v}-\frac{<\vec{w},\vec{v}>}{<\vec{w},\vec{w}>}\vec{w}
> $$
> then $\vec{v}=\vec{u}+\frac{<\vec{w},\vec{v}>}{<\vec{w},\vec{w}>}\vec{w}$, and $<\vec{w},\vec{u}> =0$
> $proof.$
> the diea is that we firstly scale the arbitarily chosed $\vec{w}$ by multiplying it with a scalor $\alpha$, to let $\alpha \cdot \vec{w}$ with the geometric relationship with $\vec{v}$ as shown below:
> ![[Pasted image 20250708122334.png]]
> then we have $\vec{v}=\alpha \cdot \vec{w}+\vec{u}$ and $<\alpha \cdot \vec{w},\vec{u}> =0$ $\Longrightarrow$ $\alpha =\frac{<\vec{w},\vec{v}>}{<\vec{w},\vec{w}>}$, complete the proof. $\Box$

The Gram-Schimidt procedure is actually applying the method above several times on a list of vectors.
> [!NOTE] Gram-Schmidt procedure
> for a basis $v_1, v_2, ..., v_n$ of $V$, let 
> $$
> \begin{align*}  
>u_1 &= v_1 \\  
>u_2 &= v_2 - \frac{\langle v_2, u_1 \rangle}{\langle u_1, u_1 \rangle} u_1  \\
>u_3 &= v_3 - \frac{\langle v_3, u_1 \rangle}{\langle u_1, u_1 \rangle} u_1 -\frac{\langle v_3, u_2 \rangle}{\langle u_2, u_2 \rangle} u_2 \\
>\vdots \\
\end{align*}
> $$
> ![[Pasted image 20250708173745.png]]
> by this fashion we get $u_1, u_2,... ,u_n$, which is an orthogonal basis of $V$, then from which we can easily derive an orthonormal basis of $V$ by $e_k=\frac{u_k}{\langle u_k, u_k\rangle}$
