# Quick start guide and examples


## Brief Introduction

One of the major functions of BST model kit is the modeling of the concentration of metabolites in a metabolic network  as a dynamic S-system.  
For example, we need to model a metabolic network that consists of a species set $\mathcal{M}$ and a reaction set $\mathcal{R}$. Then we can wirte a concentration balance equation aroound each member of the species set.

$$\frac{dX_{i}}{dt} = \sum_{r\in\mathcal{R}}\sigma_{i,r}\cdot\theta_{r}\prod_{m\in\mathcal{M}}X_{m}^{\gamma_{r,m}}-\mu{X}_{i}\qquad\forall{i}\in\mathcal{M}$$

$\sigma_{i,r}$ denotes the stoichiometric coefficient speices $i$ in reaction $r$.  
$X_{m}$ denotes the concentration of species $m$.  
$\gamma_{r,m}$ denotes the reaction order of species $m$ in reaction $r$.   
$\mu$ denotes the specific growth rate.


## Case study

### Setup environment

```
import BSTModelKit.jl
```

### Build the model object from the model file 
The BST model file hold information to build the model equation. But it does not contain any information about parameter values. We build the model file using the build method: 

```julia
model_dictionary = build(joinpath(_PATH_TO_MODELS, "Feedback.bst"));
model_dictionary
model_dictionary["list_of_dynamic_species"]

# Get the gain matrix
G = model_dictionary["G"]

# Setting initial condition
icv = [10.0, 0.1, 0.1, 1.1, 0.0];
model_dictionary["initial_condition_array"] = icv;
```

"Setting values of parameters"
```
model_dictionary["G"]
```
```
model_dictionary["total_species_list"]
```
```
model_dictionary["S"]
```
```
model_dictionary["α"] = [0.0, 10.0, 10.0, 10.0, 0.1, 0.1];
```
```
model_dictionary["static_factors_array"] = [0.1, 0.1, 0.1];
```
### Set test values for the model parameters in the $G$-matrix and $\alpha$-vector
```
(T, X, Z) = evaluate(model_dictionary; tspan=(0.0,100.0), Δt = 0.1);
```
```
X
```
```
plot(T,X)
```
