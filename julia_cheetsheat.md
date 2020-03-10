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

### Plot layout
Source: [Julia Plots > Layouts](https://docs.juliaplots.org/latest/layouts/)  
```julia
plot(plt_hat, plt_err, layout=(2, 1))
```
- Will plot two plots (`plt_hat` and `plt_err`) in '2 rows 1 column' layout.  
- Used in W20 EECS 598-006 HW07 P2(j)

### Punctuations
Source: [Official > Base > Punctuation](https://docs.julialang.org/en/v1/base/punctuation/)
It contains:
- Multi-line Comments
- `<:` subtype operator

### Precision or Round
```julia
> round(1.33333, digits=3)
1.333
```
- Used in W20 EECS 598-006 HW07 P2(j)
