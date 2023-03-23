# Application Programming Interface

`AbstractBSTModel` - Type

`BSTModel` - Type
    need to describe

---

## Methods

`BSTModelKit.build`

```julia 
build(path::String)::BSTModel
```

The `build()` function takes the path to the model file as a `String` argument and returns a model dictionary of type `BSTModel`. Compatibile filetypes include .bst, .txt, .jld2, .dat, .net, and .toml files. 

**Model File Format**

~insert~

**Return**

returns a `BSTModel` object with the following components:
* **number of dynamic states:** number of dynamic species listed in the model file
* **number of static states:** number of static species listed in the model file
* **list of dynamic species:** names of dynamic species listed in the model file
* **list of static factors:** names of static species listed in the model file
* **total species list:** a combined list of the names of dynamic and static species
* **static factors array:** conditions of static factors
* **initial condition array:** initial value of each dynamic species
* **list of reactions:** list of reactions in the model
* **S:** stoichiometric matrix in the form `MxR` where `M` is the dynamic species and `R` is the reactions they partake in
* **G:** matrix containing information about the exponents of each (dynamic and static) species
* **α:** rate constants of each reaction in the model

----------------------
  
`BSTModelKit.save`    
 
```julia
save(path::String, model::T)::Bool where T <: AbstractBSTModel
```
path must end in .jld2
returns true (good) or error

----------------------
`BSTModelKit.evaluate`
```julia
evaluate(model::BSTModel; tspan::Tuple{Float64,Float64} = (0.0,20.0),
    Δt::Float64 = 0.01, input::Union{Nothing,Function} = nothing)::Tuple{Array{Float64,1}, Array{Float64,2}}
```
The `evaluate()` function uses an ODE solver to solve the system of differential equations described by the model `BSTModel`.

**Fields**
* **model:** built using the `build()` function as a `BSTModel`
* **tspan:** time-span in which the solver is required to run as a `Tuple{Float64,Float64}` (default values for tspan are (0.0,20.0))
* **Δt:** time-steps at which the solver is required to save solutions as a `Float64` object (default is 0.01)
* **input**: `Union{Nothing,Function}` object

**Return**
*  (T,X) as `Tuple{Array{Float64,1}, Array{Float64,2}}` object. T contains the various times at which the solver recorded the solution, and X is a matrix which contains the solution to the ODE system.

----------------------

`BSTModelKit.steadystate`
```julia
steadystate(model::BSTModel; tspan::Tuple{Float64,Float64} = (0.0,20.0),
    Δt::Float64 = 0.01, input::Union{Nothing,Function} = nothing)
```
The `steadystate()` function treats the system of ODEs described by the model `BSTModel` as a steady-state problem.

**Fields**
* **model:** built using the `build()` function as a `BSTModel`
* **tspan:** time-span in which the solver is required to run as a `Tuple{Float64,Float64}` (default values for tspan are (0.0,20.0))
* **Δt:** time-steps at which the solver is required to save solutions as a `Float64` object (default is 0.01)
* **input**: `Union{Nothing,Function}` object

**Return**
* Steady state solution as `Array{Float64,1}`. 
* The steady state solution does not have temporal information.

----------------------

`BSTModelKit.morris` - Method
```julia
morris(performance::Function, L::Array{Float64,1}, U::Array{Float64,1};
    number_of_samples::Int64 = 1000)::Array{Float64,2}
```
returns array [means, variances]

----------------------

`BSTModelKit.sobol` - Method
```julia
sobol(performance::Function, L::Array{Float64,1}, U::Array{Float64,1};
    number_of_samples::Int64 = 1000, orders::Array{Int64,1} = [0, 1, 2])
```
returns???

