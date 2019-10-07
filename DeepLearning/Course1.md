# Deep Learning
## This note records some important knowledges and mathematical derivations for Deep Learning Specialization provided by deeplearning.ai.
### Course 1: Neural Networks and Deep Learning
#### Week 3 
##### Derivations of Forward propagation and Back propagation
__Forward propagation:__ calculate the loss function.  
__Back propagation:__ calculate the gradients.  

__1. Logistic Regression (single sample)__  
![LR1](./images/Course1/LR1.png)
$x,w \in R^{n_x \times 1}, z,a,y,L \in R$
_Forward propagation:_  
$z = w^Tx+b$  
$a = \sigma(z) = \frac{1}{1+\exp(-z)}$
$L(a,y)=-y\log{a}-(1-y)\log{(1-a)}$  
where $L(a,y)$ can be also expressed as:  
$L(a,y)=-y\log{a}-(1-y)\log{(1-a)}$  
$\quad \quad \quad = -y\log{\frac{1}{1+\exp(-z)}}-(1-y)\log{(1-\frac{1}{1+\exp(-z)})}$  
$\quad \quad \quad = y\log\frac{1-a}{a}-\log(1-a)$  
$\quad \quad \quad = y\log \exp(-z)-\log(\frac{1}{1+\exp(z)})$  
$\quad \quad \quad = y(-z)+\log(1+\exp(z))$  
$\quad \quad \quad = -y(w^Tx+b)+\log(1+\exp(w^Tx+b))$  
_Back propagation:_  
we need to obtain the partial derivatives $\frac{\partial L}{\partial w}$ and $\frac{\partial L}{\partial b}$  
$dL = -y (dw^T)x - yw^T(dx)-ydb+d\log(1+w^Tx+b)$  
$\quad \quad \quad = -y (dw^T)x - yw^T(dx)+\frac{\exp(w^Tx+b)}{1+\exp(w^Tx+b)}d(w^Tx+b)$  
for $w$:  
$d_wL=tr(-y (dw^T)x+a(dw^T)x)=tr(x(a-y)(dw)^T)$  
we can get:
$\frac{\partial L}{\partial w}=x(a-y)$  
for $b$:
$d_bL=tr(-ydb+adb)=tr((a-y)db)$  
we can get:  
$\frac{\partial L}{\partial b} = a-y$  
__2. Logistic Regression (multiple samples)__  
We define
$$
X = [x^{(1)}, x^{(2)}, ..., x^{(m)}]
$$
where $x^{(i)} \in R^{n_x \times 1}$, so $X \in R^{n_x \times m}$ (the sample number is $m$)  
$w\in R^{n_x \times 1}$  
$Y,Z,A,b \in R^m$  
$J \in R$  
_Forward propagation:_  
$Z = X^Tw+\bm{1}b$  
$A = \sigma(Z) = \frac{1}{1+\exp(-Z)}$
$J(w,b)=\frac{1}{m}\Sigma_{i=1}^m L=\Sigma(-y_i\log{a_i}-(1-y_i)\log{(1-a_i)})$  
Similarly, we can write $J$ as:  
$J=-\frac{1}{m}Y^T(X^Tw+\bm{1}b)+\bm{1}^T\log(\bm{1}+\exp(X^Tw+\bm{1}b))$  
where $\bm{1} \in R^m$ is unit vector.  
$dJ = -\frac{1}{m}((Y^T(dX^T)w-Y^TX^T(dw)-Y^T\bm{1}(db)+\bm{1}^T\frac{\exp(X^Tw+b)}{\bm{1}^T+\exp(X^Tw+b)}((dX^T)w+X^Tdw+\bm{1}db))$  
$\quad = \frac{1}{m}(-Y^T(dX^T)w-Y^TX^T(dw)-Y^T\bm{1}(db)+ \bm{1}^T(A*((dX^T)w+X^Tdw+\bm{1}db)))$  
$\quad = \frac{1}{m}(-Y^T(dX^T)w-Y^TX^T(dw)-Y^T\bm{1}(db) + (\bm{1} * A)^T ((dX^T)w+X^Tdw+\bm{1}db))$
_Back propagation:_  
for $w$:  
$d_wJ=-\frac{1}{m}(Y^TX^T(dw)+A^TX^Tdw=tr((A^T-Y^T)X^Tdw))$  
so we can get:  
$\frac{\partial J}{\partial w}=\frac{1}{m}((A^T-Y^T)X^T)^T=\frac{1}{m}X(A-Y)$  
as for $b$:  
$\frac{\partial J}{\partial b}=\frac{1}{m}((A^T-Y^T)\bm{1})^T=\frac{1}{m}\bm{1}^T(A-Y)$  
__3. Neural Network (two layer)__  



