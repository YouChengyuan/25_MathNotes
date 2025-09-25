
> [!def] orthogonally diagonalizable
> An $n \times n$ matrix $A$ is said to be orthogonally diagonalizable if there exists an orthogonal matrix $Q$ such that:
$$ Q^{-1}AQ = Q^T AQ = D $$
where $D$ is a diagonal matrix.
><span style="color:rgb(0, 179, 255)">This is a special occasion of [[Diagonalizability#^2507101646]] where the matrix of linear independent eigenvectors is also an orthogonal matrix.</span>

> [!NOTE] Lemma1. eigenvectors of a real symmetric matrix are always orthogonal
> suppose $S \in \mathcal{L}(V)$ is a symmetric matrix, and $x_1, ..., x_k$ are eigenvectors of $S$ corresponding to different $\lambda$'s, then the matrix $X$ of such eigenvectors is an orthogonal matrix.
> $proof.$
> we only need to prove that for an arbitrary pair of distinct eigenvectors $x_i,x_j$ are orthogonal, then $X$ is an orthogonal matrix. since $Sx_i=\lambda_ix_i$, then $(Sx_i)^T=(\lambda_ix_i)^T$ $\Longrightarrow$ $x_i^TS^T=\lambda_ix_i^T$, and since $S$ is symmetric, i.e. $S^T=S$, thus $$x_i^TS=\lambda_ix_i^T \tag{1}$$
> moreover, since $Sx_j=\lambda_jx_j$, then we have
> $$
> x_i^TSx_j=\lambda_ix_i^Tx_j \tag{2}
> $$ 
> Similarly, we have
> $$
> x_i^TSx_j=\lambda_jx_i^Tx_j \tag{3}
> $$ 
> hense,by (2)(3), we have
> $$
> \lambda_ix_i^Tx_j=\lambda_jx_i^Tx_j
> $$
> then since $\lambda_i \ne \lambda_j$, $x_i^Tx_j$ must be zero, hence $x_i$ and $x_j$ are orthogonal. $\Box$

> [!NOTE] Lemma2. $A$ can be orthogonally diagonalizable if and only if $A$ has an orthonormal set of eigenvectors.
> $proof.$ 
> $(\rightarrow)$: suppose $A$ can be orthogonal diagonalizable, then there exists an orthogonal matrix $Q$ s.t. $A=Q\Lambda Q^{-1}$, where $\Lambda$ is a diagonal matrix. Then $AQ=Q\Lambda$, which means for each column vector $Q_i$ in $Q$, there is a corresponding $\lambda_i$ in the diagonal of $\Lambda$, s.t. $AQ_i=\lambda_iQ_i$, hence, $Q_i$ is an eigenvector of $A$ for $i=1,2,...,n$. Moreover, since $Q$ is orthogonal, then each column vectors in $Q$ are orthogonal, complete the proof of this direction. 
> $(\leftarrow)$: suppose $A$ has an orthonormal set of eigenvectors, then by [[singular value decoposition]], complete the proof.

> [!NOTE] Thr. spectual theorem
> If $A\in \mathcal{L}(V)$ and $A$ is **symmetric**, then 
> $$
> A=Q\Lambda Q^{-1}
> $$
> where $Q$ is the matrix of orthonormal eigenvectors of $A$ and $\Lambda$ is the matrix of corresponding eigenvalues.
> Moreover, since $Q$ is orthonormal, then $Q^{-1}=Q^T$, hense
> $$
> A=Q\Lambda Q^{-1}=Q\Lambda Q^T
> $$
> $proof.$
> suppose $A$ has $r$ linearly independent eigenvectors, let $Q$ be the matrix of such eigenvectors, and $\Lambda$ is the corresponding eigenvalues then we have 
> $$
> AQ=Q\Lambda
> $$
> since $A$ is symmetric, then $Q$ is an orthogonal matrix, hense $Q^TQ=QQ^T=I$ $\Longrightarrow$ $A=Q\Lambda Q^T$, complete the proof. $\Box$
> <span style="color:rgb(242, 7, 19)">**this theorem actually shares the same idea of singular vector decomposition**, both of which find an orthogonal matrix, however, thanks for the property of symmetry, we already have the orthogonal eigenvector matrix of the symmetric matrix.</span>



