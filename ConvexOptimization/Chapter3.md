# Notes for "Convex Optimization"
## Chapter 3: Convex Function
### Convex Function Defination
A function: $f:R^n \rightarrow R$ is convex if $\mathbf{dom}f$ is convex set and if for all $x, y \in \mathbf{dom}f$, and $\theta$ with $0 \leq \theta \leq 1$, we have
$$
f(\theta x + (1-\theta)y) \leq \theta f(x) + (1-\theta)f(y)
$$ 
A function is convex if and only if it is convex when restricted to any line that intersects its domain.  
We can construct a line:
$$
g (t)= \{x+tv\}
$$
The intersection between g and $\mathbf{dom} f$ is $\{x+tv \in \mathbf{dom}f\}$. Then $f(x)$ is convex if and only if 
$$
g(t)=f(x+tv), x+tv \in \mathbf{dom}f
$$
is convex.

__Extended-value extensions:__  
$$
\widetilde{f}(x)= \begin{cases}  
f(x) & x \in \mathbf{f} \\
\infty & x \notin \mathbf{f}
\end{cases}$$

### First order condition
Suppose $f$ is differentiable, $f$ is convex if and only if $\mathbf{dom} f$ is convex and
$$
f(y) \geq f(x) + \nabla f(x)^T(y-x)
$$
holds for all $x,y \in \mathbf{dom}f$.

### Second order condition
Assume that $f$ is twice differentiable. Then $f$ is convex if and only if $mathbf{f}$ is convex and its Hessian is positive semidefinate: for all $x \in \mathbf{dom} f$,
$$
\nabla^2f(x) \succeq 0
$$

__Note: The separate requirement that $\mathbf{dom} f$ be convex cannot be dropped from the first- and second-order characterizations of convexity.__  

### Proof for First- and Second-order conditions
Details can be found in:  
http://yangzhou301.xyli.me/2016/03/14/826442654/

### Sublevel sets
The $\alpha$-sublevel set of a function $f: R^n \rightarrow$ is defined as
$$
C_a = \{x \in \mathbf{dom} f | f(x) \leq \alpha\}
$$
Sublevel set of a convex function is convex.

### Epigraph
Epi meas above so epigraph means above the graph
$$
\mathbf{epi} f = \{(x, f(x))|x \in \mathbf{dom} f\}
$$
A function is convex if and only if its epigraph is convex set.

### Jensen's inequality and extensions
If $f$ is convex, $x_1,..., x_k \in \mathbf{dom}f$, and $\theta_1,...,\theta_k \leq 0$ with $\theta_1 +...+\theta_k =1$, then
$$
f(\theta_1 x_1+...+\theta_k x_k) \leq \theta_1 f(x_1)+...+\theta_k f(x_k)
$$
It can extends to __integrals and probability__.

### Operations that preserve convexity
#### 1. Nonnegative weighted sums
$$
f = w_1f_1+...+w_kf_k, w_i \geq 0
$$
It can extends to __integrals and probability__.

#### 2. Composition with an affine mapping
Suppose $f:R^n \rightarrow R, A \in R^{n \times m}$ and $b \in R^n$, Define $g:R^n \rightarrow R$ by
$$g(x)=f(Ax+b)$$ with $\mathbf{dom} g = \{x|Ax+b \in  \mathbf{dom}f\}$. Then, if $f$ is convex, so is $g$.

#### 3. Pointwise maximum and supremum
If $f_1,...,f_m$ are convex, then their pointwise maximum 
$$f(x) = \max \{f_1(x),...,f_m(x)\}$$

#### 4. Composition
$h:R^k \rightarrow R$ and $g:R^n \rightarrow R^k$, guarantee convexity of their composition $f = h(g(x)):R^n \rightarrow R$, defined by 
$$
f(x)=h(g(x)), \quad \mathbf{dom} f = \{x \in \mathbf{dom}g|g(x) \in \mathbf{dom} h\}
$$
![composition](./images/Chapter3/Composition.PNG)   


