# A survey of techniques for bilinear programming

## 1. Definition [1]
![1](./images/Bilinear_Programming/1.png)  
### 1.1 SCBP
![2](./images/Bilinear_Programming/2.png)  
### 1.2 JCBP
![3](./images/Bilinear_Programming/3.png)  


## 2. Relaxation for non-convex QCQP
### 2.1 Problem description [1]
![4](./images/Bilinear_Programming/4.png)  
### 2.2 Semidefinite relaxation [1]
![5](./images/Bilinear_Programming/5.png)
### 2.3 reformulation-linearization-technique
![6](./images/Bilinear_Programming/6.png)
### 2.4 Convex envelope and relaxation [1]
![7](./images/Bilinear_Programming/7.png)
![8](./images/Bilinear_Programming/8.png)  
where $x^TQy$ is a scalar value, so $(x^TQy)^T=x^TQy$  
__Relaxation:__  
1. find the lower and upper bounds of $q^T_i(x+z)$:  
![9](./images/Bilinear_Programming/9.png)  
2. Relaxation  
![10](./images/Bilinear_Programming/10.png)  
because $(u-q^Tx)(q^T-l) \geq 0$
3. Relaxed QCQP  
![11](./images/Bilinear_Programming/11.png)  
The maximum gap should be:  
![12](./images/Bilinear_Programming/12.png)  

This kind of method is called "McCormick envelopes", details can be found in https://optimization.mccormick.northwestern.edu/index.php/McCormick_envelopes
### 2.5 Linear relaxation for Fractional Programming [2]
#### 2.5.1 Original problem
![13](./images/Bilinear_Programming/13.png)  
Where $\phi_i(x),\psi_i(x)$ are affine functions.  
Without loss of generality, we can assume:  
$\phi_i(x) \geq 0,\psi_i(x) > 0$
#### 2.5.2 find the upper and lower bounds
![14](./images/Bilinear_Programming/14.png)  
We can assume that without loss of generality:    
![15](./images/Bilinear_Programming/15.png)   
Then we can get the equivalence problem:  
![16](./images/Bilinear_Programming/16.png)
#### 2.5.3 Linear relaxation
Define a $ \widetilde{c}_i(x) \in X^0 \times D$:  
![17](./images/Bilinear_Programming/17.png)  
Then we can get the Relaxed linear programming problem:  
![18](./images/Bilinear_Programming/18.png)

### 2.6 Convex relaxation for GLMP [2]
#### 2.6.1 Problem description
![19](./images/Bilinear_Programming/19.png)
#### 2.6.2 First convex relxation method
Step 1: Get the initial variable boundary:  
![20](./images/Bilinear_Programming/20.png)  
Step 2: Get the upper and lower bounds of affine functions:  
![21](./images/Bilinear_Programming/21.png) 
Step 3: Get the upper and lower bounds of bilinear terms
![22](./images/Bilinear_Programming/22.png)
Step 4: Relax the original problem  
![23](./images/Bilinear_Programming/23.png)
#### 2.6.3 Second convex relaxtion method
Step 1-4 are the same with these in Method 1.  
Step 5: Add one more relaxation  
![24](./images/Bilinear_Programming/24.png)  
Step 6: Get the LRMP0  
![25](./images/Bilinear_Programming/25.png) 

### 2.7 With a bilinear constrait
#### 2.7.1 Original problem
![26](./images/Bilinear_Programming/26.png)  
It can be converted into a convex optimization problem (SDP)  
![27](./images/Bilinear_Programming/27.png)  

### 2.8 Improvements on McCormick envelopes
Original problem:  
![33](./images/Bilinear_Programming/33.png)  
#### 2.8.1 Uniform partitions for bilinear terms' domain [3]
A tighter mixed-integer linear programming (MILP) relaxation can be constructed by partitioning the domain of one of the variables ($x_j$) of the bilinear term into n disjoint regions, with new binary variables being added to the formulation to select the optimal partition for $x_j$. 
![28](./images/Bilinear_Programming/28.png)  
![29](./images/Bilinear_Programming/29.png) 
#### 2.8.2 Partition-dependent lower and upper bounds [4]
![30](./images/Bilinear_Programming/30.png)  
Details can be found in [4]


#### 2.8.3 convex hull reformulation [5]
![31](./images/Bilinear_Programming/31.png)  
![32](./images/Bilinear_Programming/32.png) 

### Reference
[1] 姜珊. (2015). 双线性规划问题的凸松弛求解方法研究 (Master's thesis, 清华大学).
[2] 赵营峰. (2017). 几类分式规划问题的求解方法 (Doctoral dissertation, 西安电子科技大学).
[3] Bergamini, Maria Lorena, Pio Aguirre, and Ignacio Grossmann. "Logic-based outer approximation for globally optimal synthesis of process networks." Computers & chemical engineering 29.9 (2005): 1914-1933.
[4] Castro, Pedro M. "Tightening piecewise McCormick relaxations for bilinear problems." Computers & Chemical Engineering 72 (2015): 300-311.
[5] Karuppiah, Ramkumar, and Ignacio E. Grossmann. "Global optimization for the synthesis of integrated water systems in chemical processes." Computers & Chemical Engineering 30.4 (2006): 650-673.

