# Safe Reinforcement Learning
## This note is based on the slides of Philip S. Thomas from CMU
### Definition of Safe Reinforcement Learning
1. I guarantee that with probability at least $1-\delta$, I will not change your policy to one that is worse than the current policy.
2. The assumption is restrictive, as well as difficult to uphold in the control case, where the target policy is greedy with respect to the current Q-function. In that sense this algorithm is not safe: it does not handle the case of arbitrary "off-policyness".
3. Guarantee that with probability at least $1-\delta$ the policy (or q-function) will be within $\delta$ of optimal after n episodes.

### Three steps towards a safe algorithm
#### A. Off-Policy Policy Evaluation (OPE)
1. Use a behavior policy produces historical data D;
2. given a new policy $\pi_e$; 
3. predict the performance $J(\pi_e)$ of the evaluation policy; 
![OPE](./images/SafeRL/OPE.PNG)
#### B. High Confidence Off-Policy Policy Evaluation (HCOPE)
1. Use a behavior policy produces historical data D;
2. given a new policy $\pi_e$; 
3. given a probabilty $1-\delta$;
4. Lower bound the performance $J(\pi_e)$ with probabilty $1-\delta$
![HCOPE](./images/SafeRL/HCOPE.PNG)
#### C. Safe Policy Improvement (SPI)
1. Use a behavior policy produces historical data D;
2. given a probabilty $1-\delta$;
3. Produce a policy $\pi$ that satisfies:
$
P(J(\pi) \geq J(\pi_b)) \geq 1 - \delta
$
![SPI](./images/SafeRL/SPI.PNG)

# Safe Reinforcement Learning for cyber-physical systems (CPS)
## This paragraph is based on the paper "Safe AI for CPS" by Nathan Fulton from CMU
### Definition


