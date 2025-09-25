#StatNProb #info 

relative: [[Shannon entropy]]

> [!def] Kullback-Leibler (KL) Divergence;$D_{\text{KL}}(P \parallel Q)$
> The **Kullback-Leibler divergence** (also called relative entropy) between two probability distributions $P$ and $Q$ is defined as:
> 
> $$ D_{\text{KL}}(P \parallel Q) = \sum_{x \in \mathcal{X}} P(x) \log \left( \frac{P(x)}{Q(x)} \right) $$
> 
> for discrete distributions, or
> 
> $$ D_{\text{KL}}(P \parallel Q) = \int_{-\infty}^{\infty} p(x) \log \left( \frac{p(x)}{q(x)} \right) dx $$
> 
> for continuous distributions, where:
> - $P$, $Q$ are probability distributions
> - $p(x)$, $q(x)$ are the probability densities
> - $\mathcal{X}$ is the support of $P$
> 
> **Properties**:
> 1. Non-negative: $D_{\text{KL}}(P \parallel Q) \geq 0$ with equality iff $P = Q$
> 2. Asymmetric: $D_{\text{KL}}(P \parallel Q) \neq D_{\text{KL}}(Q \parallel P)$ in general
> 3. Not a true metric (doesn't satisfy triangle inequality)

> [!NOTE] $D_{\text{KL}}(P \parallel Q) \geq 0$ with equality iff $P = Q$
> <span style="font-weight:bold; color:rgb(242, 7, 19)">Warning: Notice that this theorem holds only when $a > 1$ in $\log_a(b)$ of $D_{\text{KL}}(P \parallel Q)$</span>
> $proof.$
> we prove it in the continuous situation.
> we are going to prove
> $$
> \begin{align}
> D_{\text{KL}}(P \parallel Q)
> &= \int_{-\infty}^{\infty} p(x) \log \left( \frac{p(x)}{q(x)} \right) dx \\
> &= \int_{-\infty}^{\infty} p(x) \log \left( p(x) \right) dx - \int_{-\infty}^{\infty} p(x) \log \left( q(x) \right) dx \\
> &= \int_{-\infty}^{\infty} p(x) \log \left( p(x) \right) dx - \int_{-\infty}^{\infty} p(x) \log \left( q(x) \right) dx \\
> &\ge 0
> \end{align}
> $$
> it's equivalent to 
> $$
> \begin{align}
>-\int_{-\infty}^{\infty} p(x) \log \left( p(x) \right) dx \le -\int_{-\infty}^{\infty} p(x) \log \left( q(x) \right) dx \tag{1}
\end{align}
> $$
> where left hand side is the [[Shannon entropy]]
> since $log_a(b) = \frac{\ln(b)}{\ln(a)}$, hence <span style="color:rgb(242, 7, 19)">for any $a> 1$</span>, to prove (1) is to multiply a positive scalor $\frac{1}{\ln(b)}$ on both sides of 
> $$
> \begin{align}
> -\int_{-\infty}^{\infty} p(x) \ln \left( p(x) \right) dx \le -\int_{-\infty}^{\infty} p(x) \ln \left( q(x) \right) dx \tag{2}
\end{align}
> $$
> which doesn't make change to the inequality.
> To prove (2), since $\ln x \le x-1$ on $\mathbb{R}$, the equality holds iff $x=1$, then 
> $$
> \begin{align}
>\int_{-\infty}^{\infty} p(x) \ln \left( \frac{p(x)}{q(x)} \right) dx 
> &= -\int_{-\infty}^{\infty} p(x) \ln \left( \frac{q(x)}{p(x)} \right) dx \\
> &\ge -\int_{-\infty}^{\infty} p(x) \left( \frac{q(x)}{p(x)} -1\right) dx\\
> &= -\int_{-\infty}^{\infty} q(x)dx+\int_{-\infty}^{\infty} p(x)dx\\
> &= -1+1 \\
> &= 0
\end{align}
> $$
> which is equivalent t (2), and the equality holds iff $\frac{q(x)}{p(x)} = 1$ ,complete the proof. $\Box$
> ^2508021911

