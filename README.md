# NaturallyUnitful.jl

[![Code Style: Blue](https://img.shields.io/badge/code%20style-blue-4495d1.svg)](https://github.com/invenia/BlueStyle)
[![CI](https://github.com/MasonProtter/NaturallyUnitful.jl/actions/workflows/ci.yml/badge.svg)](https://github.com/MasonProtter/NaturallyUnitful.jl/actions/workflows/ci.yml)


This package reexports [Unitful.jl](https://github.com/ajkeller34/Unitful.jl) alongside two extra functions:

1. `natural`, a function for converting a given quantity to the Physicist's so-called
   "[natural units](https://en.wikipedia.org/wiki/Natural_units)", in which
 
   `ħ = c0 = ϵ₀ = k = 1`

   where `c0` is the speed of light in vacuum and `k` is the Boltzmann constant.

   ```julia
   julia> using NaturallyUnitful

   julia> natural(1u"m")
   5.067730759202785e6 eV^-1

   julia> natural(3e8u"m/s")
   1.000692285594456
   ```

   `natural` also accepts a keyword argument `base` (defaults to electron volts) which determines what unit
   your natural quantity is constructed from. Currently, the `base` unit must have dimensions of energy. 

   ```julia
   julia> natural(1u"m", base=u"GeV")
   5.067730759202785e15 GeV^-1
   ```

2. `unnatural`, a function for converting from natural units to a given `unnatural` unit such as meters

   ```julia
   julia> unnatural(u"m", 5.067730759202785e6u"eV^-1")
   1.0 m

   julia> unnatural(u"m/s", 1)
   2.99792458e8 m s^-1
   ```

## Installation Instructions 

To install, simply open the `pkg` prompt from the julia REPL by pressing `]`, and type:
```
pkg> add NaturallyUnitful
```
