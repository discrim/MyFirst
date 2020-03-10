# Julia Cheetsheat  
Mostly needed for homeworks of F19 EECS 551 and W20 EECS 598-006.
### Iterate over a list
```julia
for element in list
```
### Plot layout
Source: [Julia Plots - Layouts](https://docs.juliaplots.org/latest/layouts/)  
```julia
plot(plt_hat, plt_err, layout=(2, 1))
```
- Will plot two plots (`plt_hat` and `plt_err`) in '2 rows 1 column' layout.  
- Used in W20 EECS 598-006 HW07 P2(j)
