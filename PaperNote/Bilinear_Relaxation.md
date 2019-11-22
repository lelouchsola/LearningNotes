# Codes and remarks for Bilinear relaxation methods
## This work is based on the paper "Global optimization of bilinear programs with a multiparametric disaggregation technique." 
### 0. Bilinear Programming
#### 0.1 objective function
![1](./images/Bilinear_Relaxation/1.png)
#### 0.2 constraints
![2](./images/Bilinear_Relaxation/2.png)

### 1. Multiparametric disaggregation technique (MDT)
#### 1.1  discretize variable $v$
![3](./images/Bilinear_Relaxation/3.png)  
![4](./images/Bilinear_Relaxation/4.png)  
![5](./images/Bilinear_Relaxation/5.png)  
Remarks:  
1. v is discretized that selects one digit $k \in K = \{0,1,2,...,9\}$ for each power $l \in Z$
2. because each power can only contain one digit $k$, so $\Sigma_{k=0}^9 z_{k,l}=1$
#### 1.2 discretize $w$
Substitute disretized $v$ into $w=uv$, we can get:  
![6](./images/Bilinear_Relaxation/6.png)  
where $u_{k,l}=uz_{k,l}$.  
Two constraints will be introduced:  
![7](./images/Bilinear_Relaxation/7.png)  
![8](./images/Bilinear_Relaxation/8.png)  
Remarks:  
a. $u^U,u^L$ are the upper and lower bounds of $u$  
b. multiply $\Sigma_{k=0}^9 z_{k,l}=1$ by $u$ we can get the second constraint
#### 1.3 Relaxation on $L$
It is infeasible to compute the infinite sums over all integers, we represent $v$ to a finite level of precision $v'$ leading to a continuous but approximate representation of the bilinear term $w'$.  
![9](./images/Bilinear_Relaxation/9.png)  
where $l \in L = \{p, p+1,..., P\}$
#### 1.4 Lower bounding
Introduce a slack variable $\delta$
### 2. Piecewise McCormick envelopes (PCM)