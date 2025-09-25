#ML 


> [!tip] different types of RNN
> ![[Pasted image 20250910153358.png]]

> [!NOTE] Backpropagation Through Time (BPTT) in RNNs
> explain it in the case of a many-to-one RNN model:
> 
> ![[Pasted image 20250910150635.png]]
> - **1. calculate** $\frac{\partial \mathcal{L}}{\partial W}$
>  $$
>  \begin{align}
>  \frac{\partial \mathcal{L}}{\partial W} &= \frac{\partial \mathcal{L}}{\partial h_t}\cdot \frac{\partial h_t}{\partial W}
\end{align}
>  $$
> let $f(W,h_t):= \phi(Wh_{t-1} + Ux_t + b)$ , where $\phi$ can be activate function like $\tanh$, then when conducting $\frac{\partial \mathcal{L}}{\partial W}$, $h_t$ can be deemed as:
> $$h_t = f(W, h_{t-1})$$
> then by [[multivariable chain rule]], 
> $$
> \begin{align}
> \frac{\partial h_t}{\partial W} &= \frac{\partial h_t^+}{\partial W}\cdot\frac{\partial W}{\partial W} + \frac{\partial h_t}{\partial h_{t-1}}\cdot\frac{\partial h_{t-1}}{\partial W} \\
>  &= \frac{\partial h_t^+}{\partial W} + \frac{\partial h_t}{\partial h_{t-1}}\cdot\frac{\partial h_{t-1}}{\partial W} \\
>  &= \frac{\partial h_t^+}{\partial W} + \frac{\partial h_t}{\partial h_{t-1}}\cdot \left( \frac{\partial h_{t-1}^+}{\partial W} + \frac{\partial h_{t-1}}{\partial h_{t-2}}\cdot\frac{\partial h_{t-2}}{\partial W} \\ \right) \\
>  &= \frac{\partial h_t^+}{\partial W} + \frac{\partial h_t}{\partial h_{t-1}}\cdot \frac{\partial h_{t-1}^+}{\partial W} + \frac{\partial h_{t}}{\partial h_{t-2}}\cdot\frac{\partial h_{t-2}}{\partial W} \\
>  &= \frac{\partial h_t^+}{\partial W} + \frac{\partial h_t}{\partial h_{t-1}}\cdot \frac{\partial h_{t-1}^+}{\partial W} + \frac{\partial h_{t}}{\partial h_{t-2}}\cdot  \left( \frac{\partial h_{t-1}^+}{\partial W} + \frac{\partial h_{t-1}}{\partial h_{t-2}}\cdot\frac{\partial h_{t-2}}{\partial W} \\ \right) \\
>  &= \cdots \\
>  &= \sum_{i=1}^t \frac{\partial h_{t}}{\partial h_{i}}\cdot \frac{\partial h_{i}^+}{\partial W}
\end{align}
> $$
> Thus 
> $$
> \begin{align}
>\frac{\partial \mathcal{L}}{\partial W} &= \frac{\partial \mathcal{L}}{\partial h_t}\cdot \sum_{i=1}^t \frac{\partial h_{t}}{\partial h_{i}}\cdot \frac{\partial h_{i}^+}{\partial W}
\end{align}
> $$
> 
> - **2. calculate** $\frac{\partial \mathcal{L}}{\partial U}$
> $$
> \begin{align}
>\frac{\partial \mathcal{L}}{\partial U} = \frac{\partial \mathcal{L}}{\partial h_t}\cdot \frac{\partial h_t}{\partial U}
\end{align}
> $$
> now deem $h_t$ as 
> $$
> \begin{align}
>h_t = f(U, h_{t-1})
\end{align}
> $$
> then 
> $$
> \begin{align}
> \frac{\partial h_t}{\partial U} &= \frac{\partial h_t^+}{\partial U}\cdot\frac{\partial U}{\partial U} + \frac{\partial h_t}{\partial h_{t-1}}\cdot\frac{\partial h_{t-1}}{\partial U} \\
> &= \cdots \\
> &= \sum_{i=1}^t \frac{\partial h_{t}}{\partial h_{i}}\cdot \frac{\partial h_{i}^+}{\partial U}
\end{align}
> $$
> Thus 
> $$
> \begin{align}
>\frac{\partial \mathcal{L}}{\partial U} &= \frac{\partial \mathcal{L}}{\partial h_t}\cdot \sum_{i=1}^t \frac{\partial h_{t}}{\partial h_{i}}\cdot \frac{\partial h_{i}^+}{\partial U}
\end{align}
> $$


> [!tip] gradient descent and gradient explosion
> ![[Pasted image 20250923053326.png]]
