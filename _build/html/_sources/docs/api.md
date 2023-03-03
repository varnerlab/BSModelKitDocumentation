# Application Programming Interface

`AbstractBSTModel` - Type

`BSTModel` - Type
    need to describe

`BSTModelKit.build` - Method

```julia 
build(path::String)::BSTModel
```

The `build()` function takes the path to the model file as a `String` argument and returns a model dictionary of type `BSTModel`. Compatibile filetypes include .bst, .txt, .jld2, .dat, .net, and .toml files. 
need to describe how to properly format model file
returns a model dictionary (need to describe components)
    
`BSTModelKit.save` - Method    
 
```julia
save(path::String, model::T)::Bool where T <: AbstractBSTModel
```
path must end in .jld2
returns true (good) or error

`BSTModelKit.evaluate` - Method
```julia
evaluate(model::BSTModel; tspan::Tuple{Float64,Float64} = (0.0,20.0),
    Δt::Float64 = 0.01, input::Union{Nothing,Function} = nothing)::Tuple{Array{Float64,1}, Array{Float64,2}}
```
returns (T,X) as Tuple{Array{Float64,1}, Array{Float64,2}}

`BSTModelKit.steadystate` - Method
```julia
steadystate(model::BSTModel; tspan::Tuple{Float64,Float64} = (0.0,20.0),
    Δt::Float64 = 0.01, input::Union{Nothing,Function} = nothing)
```
returns steady state solution as Array{Float64,1}

`BSTModelKit.morris` - Method
```julia
morris(performance::Function, L::Array{Float64,1}, U::Array{Float64,1};
    number_of_samples::Int64 = 1000)::Array{Float64,2}
```
returns array [means, variances]

`BSTModelKit.sobol` - Method
```julia
sobol(performance::Function, L::Array{Float64,1}, U::Array{Float64,1};
    number_of_samples::Int64 = 1000, orders::Array{Int64,1} = [0, 1, 2])
```
returns???

