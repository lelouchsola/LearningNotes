# Notes for Paper 3
### Title:Optimisation of demand response in electric power systems, a review 
### Authors:A. Rezaee Jordehi
### Journal:Renewable and Sustainable Energy Reviews 
### Tags: Demand response; Demand side management; Optimization; Power System
## Notes
### 0. Summary
This paper introduced many concepts related to demand response, such as what is the definition of demand response, or what does the demand response use for. Then, different objectives and categories were introduced. For realizing optimization on these objectives, many kinds of algorithms were presented, including classic algorithms (LP, NLP) and metaheuristic algorithms (GA, SA, TLBO). Finally, some research directions were proposed by the author.
### 1. Definition of demand response
Changes in electric usage by end-use customers from their normal consumption patterns in response to changes in the price of electricity use at times of high wholesale market prices or when system reliability is jeopardized.  
DR programs mainly aim to help power systems during peak demand hours or contingencies.
### 2. Classification
#### 2.1 Incentive-based DR programs
Consumers are awarded incentives for changing their consumption patterns as per the desire of the supply-side.  
Including:  
1. __Direct load control (DLC) programs:__ allow the utility to shut down or cycle them when needed.
2. __Load curtailment programs:__ registered consumers are paid incentives for curtailing their consumption as the wish of utility.
3. __Demand bidding programs:__ the cibsumers are bid to curtail part of their consumption at a certain bid price.
4. __Emergency demand reduction programs__

#### 2.2 Price-based DR programs
Consumers are charged with different prices at different times of consumption, according to the supply cost of electricity.
1. __Times of use (TOU) pricing__: the electricity price for consumers depends on the time interval that the electricity is used.
2. __Critical peak pricing (CPP)__: the normal peak price is replaced by a very higher price when the reliability of power system is jeopardized.
3. __Real-time pricing (RTP)__: electricity tariffs typically change hourly.
4. __Inclining block rate (IBR)__: electricity price goes to a higher level if the consumption reaches a threshold. 

### 3. Advantages of demand response programs
1. reduce peak to average ratio of demand
2. decrease of amount of emissions
3. improve reliability of power system
4. decrease the occurrence probability of price spikes in electricity market
5. increase market efficiency
6. nire effuecuebr usage of resources in power system.
7. help power system to overcome difficulties arising from uncertain nature of intermittent renewable energy resources
8. bill saving for consumers

### 4. Demand response optimization
DR optimization problem formulated as a constrained optimization problem, including binary decision variables.
#### 4.1 Classic optimization algorithms
Linear programming or nonlinear programming. The on-off status must be determined, which represent binary decision variables.
##### 4.1.1 LP or MILP
__Objective:__ minimize the household's bill payment and appliances's waiting time; minimize peak demand and find the optimal number of user participarting in DLC program; minimize peak hourly load of household; day-ahead operation cost minimization.
##### 4.1.2 NLP or MINLP
1. convenience function, non-decreasing function.
2. Uncertainty of load and price can be modeled by normal probability density functions
#### 4.2 Metaheuristic optimization algorithms
##### 4.2.1 Particle swarm optimization (PSO)
A swarm with $N_p$ particles search for a near-global solution. The particles are randomly initialised. The position with the best objective is set as the global best.  
In binary PSO (with binary decision varibales), after updating velocities, sigmoid function is used to map velocities into interval [0, 1] (velocity represents the probability that variable $X_{id}$ takes the 1 value).
##### 4.2.2 Genetic algorithm (GA) 
It is inspired of the evolution of human beings from generation to generation. At each iteration, crossover and mutation operators produce new individuals  and a stochastic-based selection operator is used to select fitter individuals.
##### 4.2.3 Simulated annealing algorithm (SA)
It is used to find optimal set of the real time prices and optimal scheduling of residential appliances.
##### 4.2.4 Teaching learning-based optimization (TLBO)

### 5. Directions for future research
1. Comparison among different DR programs on different ibjectives (such as peak to average ratio (PAR) minimisation, reliability enhancement)
2. Consider the uncertainties (loads, generated powers, consumers)
3. More effort on DR programs for commercial and industrial consumers.
4. More effort on strategies for setting real-time prices.
5. Investigate the environmental implications of DR programs
6. Putting more effort on mathematical formulation of the comfort.
7. Considering PHEV (Plug-in hybrid electric vehicle) in optimization.