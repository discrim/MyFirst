# Julia Cheetsheat  
Mostly needed for homeworks of F19 EECS 551 and W20 EECS 598-006.
### Iterate over a list/array/etc.
#### 1D
```julia
for element in list
```
#### 2D
Source: [Stackoverflow](https://stackoverflow.com/questions/37902670/what-is-the-simplest-way-to-iterate-over-an-array-of-arrays)
```julia
for n in eachindex(x), m in eachindex(x[n])
    x[n][m]
end
```
is fast. (cf. `eachindex()` is a function in `base/abstractarray.jl`. Source: [Official > Arrays](https://docs.julialang.org/en/v1/base/arrays/#Base.eachindex))
```julia
for n in eachindex(x)
    y = x[n]
    for m in eachindex(y)
        y[m]
    end
end
```
is the fastest (because it avoids dereferencing twice).
```julia
for y in x, for z in y
    z
end
```
is also fast if you don't need indices.

### Plots
#### Layout
Source: [Julia Plots > Layouts](https://docs.juliaplots.org/latest/layouts/)  
```julia
plot(plt_hat, plt_err, layout=(2, 1))
```
- Will plot two plots (`plt_hat` and `plt_err`) in '2 rows 1 column' layout.  
- Used in W20 EECS 598-006 HW07 P2(j)
#### Marker
```julia
scatter!(k, ccv, markershape=:+, label="Psi(xk) of ncg_inv")
```
- Choose `markershape` from `Symbol[:none, :auto, :circle, :rect, :star5, :diamond, :hexagon, :cross, :xcross, :utriangle, :dtriangle, :rtriangle, :ltriangle, :pentagon, :heptagon, :octagon, :star4, :star6, :star7, :star8, :vline, :hline, :+, :x]`
#### `savefig`
- `savefig(plot_variable, "filename.png")`
- Saving location is 'Current Project's Folder' i.e. `@__DIR__` which actually means a location that current `.jl` file exists.  
It is different from 'Current File's Folder', i.e. `@__FILE__`.
- Thus, the following is a robust way to save figure to where the current `.jl` file is located (using string concatenation):
```julia
savefig(plot_variable, string(@__DIR__, "/filename.png")
```

### Punctuations
Source: [Official > Base > Punctuation](https://docs.julialang.org/en/v1/base/punctuation/)
It contains:
- `#=` ~ `=#`: Multi-line Comments
- `<:` subtype operator

### Precision or Round
```julia
> round(1.33333, digits=3)
1.333
```
- Used in W20 EECS 598-006 HW07 P2(j)
### Random Number Generation
```julia
using Random: seed! # rand(), randn() do not require this package
seed!(0)
a = rand(3)     # 3-element array with 3 random floats.
a = rand(2, 4)  # 2 by 4 matrix with 8 random floats.
a = randn(3)    # 3-element array with 3 noramlly distributed floats.
a = randn(2, 4) # 2 by 4 matrix with 8 normally distributed floats.
```
### String Concatenation
Source: [Official](https://docs.julialang.org/en/v1/manual/strings/#man-concatenation-1)
```julia
greet = "Hello"
whom = "world"
# Robust
str1 = string(greet, ", ", whom, ".\n")
# Another way
str2 = greet * ", " * whom * ".\n"
```
