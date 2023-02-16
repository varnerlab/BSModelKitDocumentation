# Biochemical Systems Theory

## Background
One of the tenets of systems biology is the development of biochemical networks that can describe intricate mechanisms. Ordinary Differential Equations are widley used in this regard. However, [linear models](https://doi.org/10.1109/MCS.2009.932926) run the disadvantage of generalism, and a lack of accuracy \& efficiency.

[S-System Theory \& Power Law Formalism](https://doi.org/10.1016/0895-7177(88)90553-5) was pioneered in the 1950s by `Michael Savageau` in an effort to represent organizationally complex (biological) systems \& retain mathematical amenability. Moreover, the `S-System theory` is capable of aggregating a network of reactions, representating equations in matrix form, and transforming networks using a well-defined algorithm.

The core principle lies in the ability of `non-linear rational functions` to be appropriately represented \& approximated by a straight-line in a `log-log` plot. This allows for the deduction of the rate of a process using the `Taylor series` in a logarithmic space. Logarithmic transformation has been shown to facilitate steady-state solutions \& improve the efficiency of dynamic solutions.

## BSTModelKit.jl
The `BSTModelKit.jl` package is an implementation of the [S-System \& Power Law Formalism](https://doi.org/10.1016/0895-7177(88)90553-5) in the [Julia](https://julialang.org) programming language. Instructions for installation can be found [here](installation.md).

## Additional Resources
* A detailed account on the recasting of nonlinear differential equations to S-System form can be found [here](https://doi.org/10.1016/0025-5564(87)90035-6)