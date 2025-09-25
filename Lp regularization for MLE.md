#ML 

> [!tip] understand $L_p$ regularized linear regressions in the perspective of optimization problem
> ![[L5.LinearRegression2.9.12.2024.pdf#page=22&rect=190,24,450,603|L5.LinearRegression2.9.12.2024, p.22]]
> The graph above illustrates the mathematical rationale of $L_p$ regularized linear regression in the perspective of optimization, the first image is Ridge regression, the second is Lasso regression, the third is Elastic Net regression.
> For example, in Lasso regression, adding $\|w\|_1$ to the objective function is actually adding a constraint $\|w\|_1=\sum_{i=1}^d |w_i| \le C$ to the optimization problem $\arg\min\limits_{w}\,(\vec{y}-X\vec{w})^T(\vec{y}-X\vec{w})$, in $\mathbb{R}^2$ case, the constraint forms a square feasible region, as shown in the first image above, and the optimization problem is to find a point in the square to minimize the error function, which is a convex function in $\mathbb{R}^2$, as shown in the image by the blue color-shaded map, the deeper the color is , the smaller the error function values.


![[Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library).pdf#page=30&rect=28,351,480,661&color=yellow|Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library), p.10]]
> [!thr] improper feature selection in OLS may cause explosion of magnitude of $w^*$ 
> In [[OLS regression]], the magnitude $\|w^*\|_2$ of estimated $w^*$ may explode if a new feature we added to $X$ contributes a nearly zero eigenvalue $\lambda_{j}$ to $X^TX$
> 
> $proof.$
> First we calculate the $\|w_{OLS}^*\|_2$:
>  Notice that $X^TX$ is a PSD([[positive semidefinite]]) matrix because for all vector $v$ in the domain of $X$ : $v^T(X^TX)v = (Xv)^T(Xv) \ge 0$, hence the eigenvalues of $X^TX$ are all non-negative, and since $X^TX$ is also symmetric, then by [[spectual theorem]], the matrix $Q$ of $X^TX$'s eigenvectors is orthogonal, then let $\Lambda = diag(\lambda_1,\lambda_2, \cdots, \lambda_m)$ be the matrix of distinct and positive proportion of all eigenvalues of $X^TX$ ($m\le rank(X^TX)$), then $X^TXQ = Q\Lambda$, and consequently $X^TX=Q\Lambda Q^T$, then $(X^TX)^{-1}=Q\Lambda^{-1}Q^T$, hence 
> $$
>\begin{align}
>\|w_{OLS}^*\|_2 &= \sqrt{y^TX(X^TX)^{-1}(X^TX)^{-1}X^Ty} \\
> &= \sqrt{y^TXQ\Lambda^{-2}Q^TX^Ty} \\
> &= \sqrt{z^T\Lambda^{-2}z} \\
> &= \sqrt{\sum_{i=1}^m \frac{z_i^2}{\lambda_i^2}} \tag{*}
>\end{align}
>$$
>where $z=Q^TX^Ty$, and it's clear by $(*)$ that if the newly added column to $X$ contributes a nearly zero eigenvalue $\lambda_{j}$ to $X^TX$, then $\frac{z_j^2}{\lambda_j^2}$ may explode and so does $\|w_{OLS}^*\|_2$. $\blacksquare$
>
>
> An example in polynomial linear regression:
> ![[Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library).pdf#page=32&rect=67,92,495,260&color=yellow|Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library), p.12]]
>


> [!tip] $L_2$ regularization for OLS (Ridge regression)
> To prevent the explosion of $\|w^*\|_2$, we introduce the adjusted MLE with regularizer $\frac{\lambda}{2}\|w\|_2^2$ added :
> ![[Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library).pdf#page=33&rect=196,401,397,447&color=yellow|Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library), p.13]]
> since now there are two optimizing objectives in the error function, we need to weigh such two objectives, then we introduce $\lambda \in(0,1]$ to controls the relative importance of minimizing $\|w^*\|_2$. 
> 
> the result $w_r^*$ of MLE with regularizer added :
> ![[Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library).pdf#page=137&rect=114,119,478,272&color=yellow|Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library), p.118]]
> 
> See the difference of choosing different $\lambda$ in the example bellow:
> ![[Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library).pdf#page=33&rect=20,487,483,668&color=yellow|Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library), p.13]]

> [!warning] $w_0$ in the regularizer is usually ommited
> The coefficient $w_0$ (the bias term) is often omitted from the regularization term in the error function for the following reasons:
>1. **Dependence on the Origin of the Target Variable**:  
The bias term $w_0$​ represents the offset or intercept in the model. Regularizing $w_0$​ would penalize its magnitude, effectively tying the model's performance to the origin (zero point) of the target variable $t_n$​. This is undesirable because shifting the target variable (e.g., adding a constant to all $t_n$​) should not change the model's predictions, but regularizing $w_0$​ would make the results dependent on such shifts. Omitting $w_0$ from regularization ensures the model is invariant to translations of the target variable. 
>2. **Preserving Model Flexibility**:  
The bias term $w_0$ allows the model to fit data that is not centered around zero. Penalizing $w_0$ would restrict this flexibility, potentially degrading the model's ability to fit the data well. By excluding $w_0$​ from regularization, the model retains the freedom to adjust the baseline prediction without penalty.   
>3. **Practical Considerations**:  
Regularizing $w_0$ could lead to unnecessary complications, such as requiring a separate regularization coefficient for $w_0$​. Omitting it simplifies the implementation and aligns with the common practice in many machine learning frameworks.


> [!tip] regularization can reduce overfitting
> The regularization can reduce the problem of model's overfitting to training data and consequently increase the prediction performance on test data.
> ![[Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library).pdf#page=34&rect=222,545,488,663&color=yellow|Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library), p.14]]
> where y-axis is the root mean square error of the model , while x-axis is $\ln\lambda$, which increase as the weight $\lambda$ of regularizer tend to 1 from 0. The graph shows that the model's performance on test data is boosted as we increase $\lambda$ from $e^{-30}$ to $e^{-20}$, then holds when $e^{-20} \lambda \le e^{-10}$, and when $e^{-0}$ to $e^{-10}$, the performance eventually turn to bad as the error increase both on training data and test data. 
> 
> <span style="font-weight:bold; color:rgb(242, 7, 19)">Therefore, the hyperparameter $\lambda$ is not "The bigger, the better", </span><span style="color:rgb(242, 7, 19)">it also needs to be manually selected properly between the interval $(0,1]$ when minimizing the error function, but notice that it is fixed when solving the optimization problem, and is by such called "hyperparameter"</span>
> > [!PDF|yellow] [[Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library).pdf#page=34&selection=67,2,90,23&color=yellow|Deep Learning Foundations and Concepts (Christopher M. Bishop, Hugh Bishop) (Z-Library), p.14]]
> > We cannot simply determine the value of λ by minimizing the error function jointly with respect to w and λ since this will lead to λ → 0 and an over-fitted model with small or zero training error.
> 
> 

> [!thr] regularization can solve numerical instability of OLS
> see [[ridge regression#^2508051756]]


