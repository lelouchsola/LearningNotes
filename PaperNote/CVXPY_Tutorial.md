# Notes for learning CVXPY
## 1. Create variables
### 1.1 create scalar variables
```python
# Create two scalar optimization variables.
x = cp.Variable()
y = cp.Variable()
```
### 1.2 create Vectors and matrices variables
```python
# A scalar variable.
a = cp.Variable()

# Vector variable with shape (5,).
x = cp.Variable(5)

# Matrix variable with shape (5, 1).
x = cp.Variable((5, 1))

# Matrix variable with shape (4, 7).
A = cp.Variable((4, 7))
```

## 2. create constrains
```python
# Create two constraints.
constraints = [x + y == 1,
               x - y >= 1]
```
__Note:__
1. constraints are collected in a list
2. you can use ==, <=, and >= to construct constraints in CVXPY.
3. You cannot construct inequalities with < and >. Strict inequalities don’t make sense in a real world setting.
4. you cannot chain constraints together, e.g., 0 <= x <= 1 or x == y == 2.
5. Equality and inequality constraints are elementwise 

## 3. Form objective problem
```python
# Form objective.
obj = cp.Minimize((x - y)**2)
```
__Note:__
1. Problems are immutable, meaning they cannot be changed after they are created. To change the objective or constraints, create a new problem.

## 4. create parameters
Parameters are symbolic representations of constants.

```python
# Positive scalar parameter.
m = cp.Parameter(nonneg=True)

# Column vector parameter with unknown sign (by default).
c = cp.Parameter(5)

# Matrix parameter with negative entries.
G = cp.Parameter((4, 7), nonpos=True)

# Assigns a constant value to G.
G.value = -numpy.ones((4, 7))
```
Example 1: Disciplined Parametrized Programming
```python
import cvxpy as cp
import numpy
import matplotlib.pyplot as plt

# Problem data.
n = 15
m = 10
numpy.random.seed(1)
A = numpy.random.randn(n, m)
b = numpy.random.randn(n)
# gamma must be nonnegative due to DCP rules.
gamma = cp.Parameter(nonneg=True)

# Construct the problem.
x = cp.Variable(m)
error = cp.sum_squares(A*x - b)
obj = cp.Minimize(error + gamma*cp.norm(x, 1))
prob = cp.Problem(obj)

# Construct a trade-off curve of ||Ax-b||^2 vs. ||x||_1
sq_penalty = []
l1_penalty = []
x_values = []
gamma_vals = numpy.logspace(-4, 6)
for val in gamma_vals:
    gamma.value = val
    prob.solve()
    # Use expr.value to get the numerical value of
    # an expression in the problem.
    sq_penalty.append(error.value)
    l1_penalty.append(cp.norm(x, 1).value)
    x_values.append(x.value)
```

## 5. Use numpy to create matrices
Currently the following types may be used as constants:
1. NumPy ndarrays
2. NumPy matrices
3. SciPy sparse matrices

Example 1:
```python
# Problem data.
m = 10
n = 5
numpy.random.seed(1)
A = numpy.random.randn(m, n) # define constant values
b = numpy.random.randn(m)

# Construct the problem.
x = cp.Variable(n)
objective = cp.Minimize(cp.sum_squares(A*x - b)) # 
constraints = [0 <= x, x <= 1] # p
prob = cp.Problem(objective, constraints)

print("Optimal value", prob.solve())
print("Optimal var")
```


