
> [!NOTE] The first characterization in $\mathbb{R}^2$
> ![[cs189_hw2.pdf#page=2&rect=104,454,561,547|cs189_hw2, p.2]]
> $proof.$

> [!NOTE] The second characterization in $\mathbb{R}^2$
> ![[cs189_hw2.pdf#page=2&rect=104,417,562,447|cs189_hw2, p.2]]
> i.e. The linear combo of i.i.d. standard Gaussian RVs is jointly MVG
> 
> $proof.$

> [!tip] Excercise
> ![[cs189_hw2.pdf#page=2&rect=103,216,563,414|cs189_hw2, p.2]]
> 
> $answer.$
> (1)
> (i) **$Z_1,Z_2$ are jointly MVG:** since $X_1$ and $X_2$ are independent, then both $X_1|X_2=X_1$ and $X_2|X_1=X_2$. Plus, $X_1$ and $X_2$ are of Gaussian distrbution, then by the first characterization, $Z_1,Z_2$ are jointly MVG. $\blacksquare$ 
> 
> (ii) **$Z_1,Z_2$ are jointly MVG:** since $Z=[Z_1,Z_2]^T=A[X_1,X_2]^T$, where $A=\left( \begin{array}{c} 1 & 0\\ 1 & 2  \end{array} \right)$, then by the second characterization, complete the proof. $\blacksquare$
> 
> (iii) **$Z_1,Z_2$ are jointly MVG:** since $Z=[Z_1,Z_2]^T=A[X_1,X_2]^T$, where $A=\left( \begin{array}{c} 1 & 0\\ -1 & 0  \end{array} \right)$, then by the second characterization, complete the proof. $\blacksquare$
> 
> (iv) **$Z_1,Z_2$ are not jointly MVG:** since $P(UX_1=x)=0.5\cdot P(UX_1=x|U=1)+0.5\cdot P(UX_1=x|U=-1)=0.5\cdot P(X_1=x)+0.5\cdot P(-X_1=x)$, hence $Z_2=0.5X_1-0.5X_1$<span style="color:rgb(242, 7, 19)"> this is wrong</span>
> 
> > [!warning] Analysis of the Incorrect Inference about $UX_1$
> > 
> > ### Given:
> > - $U$ is uniform: $P(U = 1) = 0.5$, $P(U = -1) = 0.5$.
> > - $X_1$ is a random variable (independent of $U$).
> > 
> > ### Correct Distribution of $UX_1$:
> > $$
> > P(UX_1 = x) = 0.5 \cdot P(X_1 = x) + 0.5 \cdot P(-X_1 = x).
> > $$
> > This is because:
> > - When $U = 1$, $UX_1 = X_1$.
> > - When $U = -1$, $UX_1 = -X_1$.
> > 
> > ### Incorrect Claim:
> > The inference states:
> > $$
> > Z_2 = 0.5 X_1 - 0.5 X_1,
> > $$
> > which wrongly simplifies to **0**. This is incorrect because:
> > 1. $UX_1$ is a **mixture** of $X_1$ and $-X_1$, not an arithmetic combination.
> > 2. The expression $0.5 X_1 - 0.5 X_1$ is deterministically zero, contradicting the actual randomness of $UX_1$.
> > 
> > ### Why It Fails:
> > - The correct interpretation is probabilistic:  
> >   $$
> >   UX_1 = \begin{cases} 
> >   X_1 & \text{(probability 0.5)}, \\
> >   -X_1 & \text{(probability 0.5)}.
> >   \end{cases}
> >   $$
> > - This describes **two possible outcomes**, not a weighted sum.
> > 
> > ### Key Insight:
> > - **Mixture distributions** (probabilistic selections) ≠ **linear combinations** (arithmetic operations).
> > - $UX_1$ retains the variability of $X_1$ and $-X_1$, while $0.5 X_1 - 0.5 X_1$ collapses to zero.
> > 
> > ### Final Answer:
> > The claim $Z_2 = 0.5 X_1 - 0.5 X_1$ is **invalid** because it misrepresents $UX_1$ as a deterministic zero instead of a random mixture of $X_1$ and $-X_1$.
> 
> 
> correct version:
> $$
> \begin{align}
>P(UX_1=x) &= 0.5\cdot P(UX_1=x|U=1)+0.5\cdot P(UX_1=x|U=-1)\\
> &=0.5\cdot P(X_1=x)+0.5\cdot P(-X_1=x) \\
> &= 0.5\cdot P(X_1=x)+0.5\cdot P(X_1=-x) \\
> &= 0.5\cdot P(X_1=x)+0.5\cdot P(X_1=x) \tag{*} \\
> &= P(X_1=x) 
\end{align}
> $$
> the equality of $(*)$ is by the symmetry of Gaussian distribution, thus, we proved that $UX_1$ is Gaussian distributed. However, since neither $X_1U|X_1$ nor $X_1|X_1U$ are Gaussian distributed, hence they are not jointly Gaussian distributed. $\blacksquare$
> 
> (2)
> (i) $\Sigma = \left( \begin{array}{c} 1 & 0\\ 0 & 1  \end{array} \right)$
> (ii)  Since
> $$
> \begin{align}
> Cov(Z_1,Z_2) &= \mathbb{E}[Z_1Z_2] - \mathbb{E}[Z_1]\mathbb{E}[Z_2]\\
> &= \mathbb{E}[X_1^2 + 2X_1X_2] - 0 \\
> &= \mathbb{E}[X_1^2] + 2\mathbb{E}[X_1X_2] \\
> &= Var(X_1) + 2Cov(X_1,X_2) \\
> &= 1 + 2\cdot0 \\
> &= 1
\end{align}
> $$
> $$
> \begin{align}
> Var(Z_2) &= \mathbb{E}[Z_2^2] - (\mathbb{E}[Z_2])^2 \\
> &= \mathbb{E}[X_1^2 + 4X_1X_2 + 4X_2^2] - (\mathbb{E}[X_1+2X_2])^2 \\
> &= \mathbb{E}[X_1^2] + \mathbb{E}[4X_1X_2] + \mathbb{E}[4X_2^2] - 0 \\
> &= Var(X_1) + 4Cov(X_1,X_2) + 4Var(X_2) \\
> &= 1 + 4\cdot0 + 4 \\
> &= 5
\end{align}
> $$
> therefore, $\Sigma= \left( \begin{array}{c} 1 & 1\\ 1 & 5  \end{array} \right)$
> (iii) Since 
> $$Cov(X_1, -X_1)= -\mathbb{E}[X_1^2] = -1$$
> $$
> \begin{align}
> Var(-X_1) = Var(X_1) = 1
\end{align}
> $$
> thus $\Sigma = \left( \begin{array}{c} 1 & -1\\ -1 & 1  \end{array} \right)$
> (iv) since we've already proved that $p(UX_1) = p(X_1)$ in (1).(iv), then 
> $$
> \begin{align}
> Cov(X_1, UX_1) &= \mathbb{E}[X_1UX_1] - \mathbb{E}[X_1]\mathbb{E}[UX_1] \\
> &= \mathbb{E}[X_1X_1] - \mathbb{E}[X_1]\mathbb{E}[X_1] \\
> &= Var(X_1)\\
> &= 1
\end{align}
> $$
>  $$
>  \begin{align}
>  Var(UX_1) = Var(X_1) = 1
\end{align}
>  $$
>  thus $\Sigma=\left( \begin{array}{c} 1 & 1\\ 1 & 1  \end{array} \right)$

> [!NOTE] $\Sigma = VV^T$ for linear combo of standard MVG
> suppose $X_1, \cdots, X_d$ are independent standard Gaussian RVs, and $\mathbf{X}=[X_1, \cdots, X_d]^T$, $V \in \mathbb{R}^{d\times d}$, then for $\mathbf{Z}= V\mathbf{X}$, the covariance matrix $\Sigma_Z$ is 
> $$
> \begin{align}
> \Sigma_Z = VV^T
\end{align}
> $$
> 
> $proof.$
> since $Z_i = \sum_{k=1}^d V_{ik}X_k$, then for all $i,j\in\{1,\cdots,d\}$:
> $$
> \begin{align}
> Cov(Z_i, Z_j) &= \mathbb{E}[Z_iZ_j] - \mathbb{E}[Z_i]\mathbb{E}[Z_j] \\
> &= \mathbb{E}[(\sum_{k=1}^d V_{ik}X_k)(\sum_{k=1}^d V_{jk}X_k)] - \mathbb{E}[\sum_{k=1}^d V_{ik}X_k]\mathbb{E}[\sum_{k=1}^d V_{jk}X_k)] \\
> &= \mathbb{E}[(\sum_{k=1}^d V_{ik}X_k)(\sum_{k=1}^d V_{jk}X_k)] - 0 \\
> &= \mathbb{E}[\sum_{k=1}^d V_{ik}V_{jk}X_k^2 + \sum_{1 \le k\ne l \le d}V_{ik}V_{jl}X_kX_l ] \\
> &= \sum_{k=1}^d V_{ik}V_{jk}\mathbb{E}[X_k^2] + \sum_{1 \le k\ne l \le d}V_{ik}V_{jl}\mathbb{E}[X_kX_l ] \\
> &= \sum_{k=1}^d V_{ik}V_{jk}\cdot Var(X_k) + \sum_{1 \le k\ne l \le d}V_{ik}V_{jl}Cov(X_i,X_j) \\ 
> &= \sum_{k=1}^d V_{ik}V_{jk} + 0 \\ 
> &= \sum_{k=1}^d V_{ik}V_{jk} \\
> &= V_{i,.} V_{j,.}^T \in \mathbb{R}
\end{align}
> $$
> hence
> $$
> \begin{align}
> \Sigma_Z = VV^T
\end{align}
> $$
> $\blacksquare$
> ^2508072156
>

> [!NOTE] $\Sigma = VV^T$ for linear combo of any standard multivariate distribution
> suppose $\mathbf{X}=[X_1, \cdots, X_d]^T$ is a standard multivariate distribution, i.e. $\mu=\vec{0}_d$, $\Sigma=I_{d\times d}$.Then for $V \in \mathbb{R}^{d\times d}$, the covariance matrix $\Sigma_Z$ of  $\mathbf{Z}= V\mathbf{X}$ is 
> $$
> \begin{align}
> \Sigma_Z = VV^T
\end{align}
> $$
> 
>$proof.$
>totally the same as that of [[multivariate Gaussian (MVG)#^2508072156]]


> [!NOTE] Title
> ![[cs189_hw2.pdf#page=3&rect=85,615,565,738|cs189_hw2, p.3]]
> 

> [!NOTE] Title
> $$
> \begin{align}
> P(Z_1,Z_2) &= \frac{1}{(2\pi)|\boldsymbol{\Sigma}|^{1/2}} 
\exp\left( -\frac{1}{2} (\mathbf{z} - \boldsymbol{\mu})^T \boldsymbol{\Sigma}^{-1} (\mathbf{z} - \boldsymbol{\mu}) \right) \\
> &= \frac{1}{(2\pi) |\boldsymbol{\Sigma}|^{1/2}} 
\exp\left( -\frac{1}{2} (\mathbf{z} - \boldsymbol{\mu})^T LD^{-1}L^T(\mathbf{z} - \boldsymbol{\mu}) \right) \\
 &= \frac{1}{(2\pi) |\boldsymbol{\Sigma}|^{1/2}} 
\exp\left( -\frac{1}{2} [L^T(\mathbf{z} - \boldsymbol{\mu})]^T D^{-1}[L^T(\mathbf{z} - \boldsymbol{\mu})] \right)\\ 
>&= \frac{1}{(2\pi) |\boldsymbol{\Sigma}|^{1/2}} 
\exp\left( -\frac{1}{2} [L^T(\mathbf{z} - \boldsymbol{\mu})]^T D^{-1}[L^T(\mathbf{z} - \boldsymbol{\mu})] \right)\\
>&= 
\end{align}
> $$
> $$
> \begin{align}
> P(Z_2 = z_2) &= \frac{1}{\sqrt{2\pi}(\Sigma_{22})^{1/2}} \exp\left\{-\frac{1}{2\Sigma_{22}}z_2^2 \right\} \\
> 
\end{align}
> $$
> 





