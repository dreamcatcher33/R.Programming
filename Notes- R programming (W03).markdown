# Notes: R programming (W03)
Looping functions

标签（空格分隔）： MOOC R

---

#1. Looping functions:
- **lapply**: very very important!!fastest!.usually use with **split** function.
- **sapply**: a user friendly version of **lapply**;
- **apply**; internally a R for loop,thus slow!!
- **tpply**; 
- **mapply**;

----
#2. **lapply**
*function (X,FUN, ...)*
> a) Looping is done internally in C code.
> b) X: a list;
> c) **sapply** is a user friendly version of **lapply**;

#3.**apply**
*function (X, MARGIN, FUN, ...)*
>a) internally a R for loop, speed similar with the for loop;
>b) some shortcut functions:（Much faster)
    **rowSums,colSums,rowMeans,colMeans**.

---
#4. **tapply**
apply a function over subsets of a vector;
*function (X, INDEX, FUN = NULL, ..., simplify = TRUE)*
> a) X: vector; INDEX: factor

#5. **split**
*function (x, f, drop = FALSE, ...)*
>a) x: vector/list/data.frame; f: factor or a list of factors;drop: whether empty factors levels should be dropped

#6. **mapply**
*function (FUN, ..., MoreArgs = NULL, SIMPLIFY = TRUE,USE.NAMES = TRUE)*
Applies a function in parallel over a set of arguments.
useful when generating simulation data.

---
#7. debug
> traceback()
> debug(function.name)


