# Special Matrices

A [Julia](http://julialang.org) package for working with special matrix types.

This package extends the `Base.LinAlg` library with support for special
matrices which are used in linear algebra.

[![Build Status](https://travis-ci.org/jiahao/SpecialMatrices.jl.svg)](https://travis-ci.org/jiahao/SpecialMatrices.jl)

## Currently supported special matrices

## [`Frobenius`](http://en.wikipedia.org/wiki/Frobenius_matrix) matrix

Example

```julia
julia> using SpecialMatrices

julia> F=Frobenius(3, [1.0:3.0]) #Specify subdiagonals of column 3
6x6 Frobenius{Float64}:
 1.0  0.0  0.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  0.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0  0.0
 0.0  0.0  2.0  0.0  1.0  0.0
 0.0  0.0  3.0  0.0  0.0  1.0

julia> inv(F) #Special form of inverse
6x6 Frobenius{Float64}:
 1.0  0.0   0.0  0.0  0.0  0.0
 0.0  1.0   0.0  0.0  0.0  0.0
 0.0  0.0   1.0  0.0  0.0  0.0
 0.0  0.0  -1.0  1.0  0.0  0.0
 0.0  0.0  -2.0  0.0  1.0  0.0
 0.0  0.0  -3.0  0.0  0.0  1.0

julia> F*F #Special form preserved if the same column has the subdiagonals
6x6 Frobenius{Float64}:
 1.0  0.0  0.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  0.0  0.0  0.0
 0.0  0.0  2.0  1.0  0.0  0.0
 0.0  0.0  4.0  0.0  1.0  0.0
 0.0  0.0  6.0  0.0  0.0  1.0

julia> F*Frobenius(2, [5.0:-1.0:2.0]) #Promotes to Matrix
6x6 Array{Float64,2}:
 1.0   0.0  0.0  0.0  0.0  0.0
 0.0   1.0  0.0  0.0  0.0  0.0
 0.0   5.0  1.0  0.0  0.0  0.0
 0.0   9.0  1.0  1.0  0.0  0.0
 0.0  13.0  2.0  0.0  1.0  0.0
 0.0  17.0  3.0  0.0  0.0  1.0

julia> F*[10.0:10.0:60.0]
6-element Array{Float64,1}:
  10.0
  20.0
  30.0
  70.0
 110.0
 150.0
```

## [`Companion`](http://en.wikipedia.org/wiki/Companion_matrix) matrix

```julia
julia> A=Companion([1,2,1])
3x3 Companion{Int64}:
 0  0  -1
 1  0  -2
 0  1  -1
```

## `Strang` matrix

A special `SymTridiagonal` matrix named after Gilbert Strang

```julia
julia> Strang(6)
6x6 Strang{Float64}:
  2.0  -1.0   0.0   0.0   0.0   0.0
 -1.0   2.0  -1.0   0.0   0.0   0.0
  0.0  -1.0   2.0  -1.0   0.0   0.0
  0.0   0.0  -1.0   2.0  -1.0   0.0
  0.0   0.0   0.0  -1.0   2.0  -1.0
  0.0   0.0   0.0   0.0  -1.0   2.0
```

