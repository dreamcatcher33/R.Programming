# Notes: R programming (W04)

标签（空格分隔）： MOOC R

---


# 1. The **str()** function.
str() function in R could accept any type of object and returns the *structure* of the object.
It's very versatile and the return value was brief but valuable.

---

# 2. Generating Simulation data.

##2.1 Generating random numbers from probalibility distribution in R;
```R
setseed(50);
rnorm();
rpois();
rbinom();
rexp();
#etc.
```
---

##2.2 Generating random numbers from complex models;
eg: Generating data for Poisson model:
$Y\sim Poisson(\mu),$
$log (\mu) = \beta_0 +\beta_1 * x $
$\beta_0 =0.5$,$\beta_1 = 0.3$.

The R program could be:
```R
setseed(100);
x = rnorm(100);
beta0 = 0.5;beta1= 0.3;
log.mu = beta0 +beta1 * x ;
y = rpois(100,exp(log.mu));
plot(x,y);
```
---
##2.3 Generating random numbers from arbitrary distribution using the **sample()** function.
eg: bootstrapping:
```R
set.seed(200);
x = 2:5;
sample(x,replace = T); #x was a vector.
```
eg: permutation:
```R
sample(x);
```
---

#3. R profiler

Goals: 
- profiling code, get to know where expends most of the running time.
- For optimizing you code.

##3.1 Already knowing your core function consuming time.
function **system.time()**;

- parameter: an expression.That could be:

    a)  a function;
    b)  a block of codes with {}.

- return value: 
    
    a) user time; ( the user indicated the computer)
    b) elapsed time. (This was the time user actually fells)

---

##3.2 Do not know where takes your time.
function **Rprof()** and **summaryRprof()**
eg:
```R
library(MASS); library(boot)
storm.fm <- nls(Time ~ b*Viscosity/(Wt - c), stormer,
			 start = c(b=30.401, c=2.2183))
st <- cbind(stormer, fit=fitted(storm.fm))
storm.bf <- function(rs, i) {
 st$Time <-  st$fit + rs[i]
 tmp <- nls(Time ~ (b * Viscosity)/(Wt - c), st,
			start = coef(storm.fm))
 tmp$m$getAllPars()
}
rs <- scale(resid(storm.fm), scale = FALSE) # remove the mean

Rprof("boot.out")
storm.boot <- boot(rs, storm.bf, R = 4999) # slow enough to profile
Rprof(NULL);
tmp=summaryRprof("boot.out");
tmp$by.self
### or type "R CMD Rprof boot.out" in the command line.
```
---

A framework to estimate the time consumed for several blocks of code:
```R
Rprof()
## some code to be profiled
Rprof(NULL)
## some code NOT to be profiled
Rprof(append=TRUE)
## some code to be profiled
Rprof(NULL)
## Now post-process the output as described in Details
```
---

#4. Scoping rules
R used *lexical scoping* or *static scoping*.
That is:
The values of **free variables** are searched for in the environment in which the function was *defined* instead of *called*!
You will make better understanding of the scoping rules used in R after you understand the environment. 

- **search()** function returned all the definition of environment (or namespace);
- **library('package')** made the order of the package to be the 2nd on the search() list;
- Application: write a 'constructor' function. (e.g. maximizing the likelihood function with fixed parameters / none-fixed parameters, draw likelihood curve).

---




