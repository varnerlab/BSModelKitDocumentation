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

For example, we need to model a linear pathway consisting of successive reactions. 
It contains three static species (E1,E2,E3) and five dynamic species (X1,X2,X3,X4,X5).

```julia
# Setting the path to BST file
path_to_model_file = joinpath(pwd(),"data","Feedback.bst");

# Build the model
model_object = build(path_to_model_file);

# Get the gain matrix
G = model_object.G

#Get the stoichoimetric array
S = model_object.S

# Setting initial condition
icv = [10.0, 0.1, 0.1, 1.1, 0.0];
model_object.initial_condition_array = icv; 

#Setting values of α parameters"
model_object.α = [0.0, 10.0, 10.0, 10.0, 0.1, 0.1];

#Setting values of static factors array
model_object.static_factors_array = [0.1, 0.1, 0.1];

#Solving and Plotting
(T, X) = evaluate(model_object; tspan=(0.0,100.0), Δt = 0.1);
plot(T,X)
```
