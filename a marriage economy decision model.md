
# 1. Definitions
suppose the time line of a marriage is $[t_0,t_1]$, where $t_0$ is the time of the wedding, $t_1$ is the end time of this marriage (by death or divorce).
## 1.1 value 
Suppose there are $d$ features of major concern in a marriage decision process, then such features during a candidate's life-long journey is  measured by a $d$-dimensional stochastic process
$$X(t):=[ x_1(t) , \cdots ,x_d(t)]^T$$

## 1.2 weight of the value 
Suppose the weight of value for a person is 
$$
\begin{align}
W(t):=[w_1(t),\cdots,w_d(t)]^T
\end{align}
$$
where $\sum_{i=1}^d w_i(t) = 1$ given $\forall t \in [t_0,t_1]$


# 2. assumption
## 2.1 fare trading 

We assume that a couple $P_1$ and $P_2$ make a fare trading in a marriage, i.e. their perceptual utilization to each other are equal, at least at a short time period when they just consent to marry:

$$\frac{|U_1(X_2)  - U_2(X_1)|}{U_1(X_2)} + \frac{|U_1(X_2)  - U_2(X_1)|}{U_2(X_1)} \le d$$
## 2.2 age constraint

$$\begin{cases}
t_0 \ge 22 \space \space \text{if male}\\
t_0 \ge 20 \space \space \text{if female}\\
\end{cases}$$

## 2.3 divorce constraint

t.b.d

# 3. model 


## 3.1 perceptual utilization
we define the perceptual utilization 
$$
\begin{align}
U_i(X_j,t):= W_i(t)^TX_j(t)
\end{align}
$$

## 3.2 objective function

suppose the accumulated comprehensive value along a marriage is 
$$
\begin{align}
\mathcal{V} := \int_{t_0}^{t_1} W(t)^TX(t)\,d\,t
\end{align}
$$
then our goal is to maximize our $\mathcal{V}$ .

# 3. variation









