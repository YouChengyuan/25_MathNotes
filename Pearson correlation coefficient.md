#StatNProb

[for reference](obsidian://open?vault=math&file=textbook%2Fcorrelation.pdf)

> [!warning] Pearson correlation may tells wrong information when there are highly concentrated points along with several outliers
> ![[Pasted image 20250810045825.png]]
> there are many points at the left down conner with the same coordinate $(1.5,0)$ , and an outlier point at the right up conner, which causes $\rho = 1$, though we shouldn't say $x$ and $y$ are correlated.

> [!warning] Ecological correlation should be interpreted with care
> 用宏观数据进行相关性分析要慎重
> ![[Pasted image 20250730164059.png]]
> [[correlation.pdf#page=15|correlation, p.15]]
> mathematical proof see [[ecological fallacy#^2507301818]]

> [!def] pearson correlation coefficient; $\rho_{xy}$
>for two dim-1 random variables $x,y$:
> $$
> \begin{align}
> \rho_{xy} &= \frac{Cov(x,y)}{\sigma_x \sigma_y} \\
> &= \frac{\mathbb{E}[(x-\mu_x)(y-\mu_y)]}{\sigma_x \sigma_y} \\
> &= \mathbb{E}[(\frac{x-\mu_x}{\sigma_x})(\frac{y-\mu_y}{\sigma_y})] \\
> &= \mathbb{E}[z_xz_y]
\end{align}
> $$
> where $\sigma_x,\sigma_y$ are standard derivations of $x$ and $y$, $z_x,z_y$ are standard forms of the x and y's distributions. When it comes to a sample with $n$ elements, the non-bias estimiation $r_{xy}$ of $\rho_{xy}$ is 
> $$
> \begin{align}
> r_{xy} &= \frac{
> \frac{1}{n-1}\sum_{i=1}^n [(x_i-\bar{x})(y_i-\bar{y})]
> }
> {
> \sqrt{
> \frac{1}{n-1}\sum_{i=1}^n(x_i-\bar{x})^2
> }
> \sqrt{
> \frac{1}{n-1}\sum_{i=1}^n(y_i-\bar{y})^2
> }
> } \tag{1}\\ 
> &= \frac{
> \sum_{i=1}^n [(x_i-\bar{x})(y_i-\bar{y})]
> }
> {
> \sqrt{
> \sum_{i=1}^n(x_i-\bar{x})^2
> }
> \sqrt{
> \sum_{i=1}^n(y_i-\bar{y})^2
> }
> } \\
> 
\end{align}
> $$
> (1) can also be rewritten as 
> $$
> \begin{align}
> r_{xy} &= \frac{
> \frac{1}{n-1}\sum_{i=1}^n [(x_i-\bar{x})(y_i-\bar{y})]
> }
> {
> s_x
> s_y
> } \\
> &= \frac{1}{n-1}\sum_{i=1}^n [\frac{(x_i-\bar{x})}{s_x}\frac{(y_i-\bar{y})}{s_y}]
\end{align}
> $$
> 

> [!NOTE] $-1 \le \rho_{xy} \le 1$
> $proof.$
> let $f(x,y)$ be the joint pdf of $x,y$, then by [[properties of E#^2507292050]]
> $$
> \begin{align}
> 	|\rho_{xy}| &= |\mathbb{E}[z_xz_y]| \le \sqrt{\mathbb{E}[z_x^2]\mathbb{E}[z_y^2]} = \sqrt{Var(z_x)Var(z_y)} = 1
\end{align}
> $$
> complete the proof.
>   

> [!tip] $\rho_{xy}$ actually tells whether there is a "single trend" between $x$ and $y$
> since the estimation $r_{xy}$ of $\rho_{xy}$ is :
> $$
> \begin{align}
>  r_{xy} = \frac{1}{n-1}\sum_{i=1}^n [\frac{(x_i-\bar{x})}{s_x}\frac{(y_i-\bar{y})}{s_y}]
\end{align}
> $$
> notice that $\frac{(x_i-\bar{x})}{s_x}$ and $\frac{(y-\bar{y})}{s_y}$ measures the standardized offset of $x$ and $y$ from their own mean values, then if there is a positive correlation(trend) between $x$ and $y$, then each $\frac{(x_i-\bar{x})}{s_x}\cdot\frac{(y_i-\bar{y})}{s_y}$ shall be positive, and their mean value $r_{xy}$ shall be positive. Reversely, if there is a negative correlation between $x$ and $y$, then $r_{xy}$ shall be negative by similar rationale.
> ![[Pasted image 20250730160828.png]]
> ![[Pasted image 20250730160835.png]]
> ![[Pasted image 20250730160904.png]]
> However, if the association between $x$ and $y$ is not single direction, $y =  x^2$ for instance, then $r_{xy}$ fails to tell the association, because signs of each $\frac{(x_i-\bar{x})}{s_x}\cdot\frac{(y_i-\bar{y})}{s_y}$ are not uniformly positive or negative, then such term will cancel each other, make their sum tend to be 0.
> ![[Pasted image 20250730161743.png]]
> ^2507301620

> [!NOTE] $\rho_{xy}$ measures only linear or linear-alike association
> has been illustrated in [[Pearson correlation coefficient#^2507301620]]
> 
> 

> [!NOTE] $r_{xy}$ is highly affected by outliers
> since 
> $$
> \begin{align}
>  r_{xy} = \frac{1}{n-1}\sum_{i=1}^n [\frac{(x_i-\bar{x})}{s_x}\frac{(y_i-\bar{y})}{s_y}]
\end{align}
> $$
> thus each point $i$ has the same weight in $r_{xy}$, hence they have the same affect to the value of $r_{xy}$, thus if $n$ is small, and there is a big outlier in the data, then $r_{xy}$ are highly affected.
> ![[Pasted image 20250730162842.png]]

