# Notes: R programming (W02)

标签（空格分隔）： R MOOC

---

#1. Control structure
```R
if(<condition>){
}else if(<condition>){
}else{
}
x = ifelse(,,)
```
Remarks:
>a) **seq_along(vec)**  返回向量vec的所有下标；
>b) **seq_len(n)** 返回从1到n长度为n的一个序列。
>c) **break()**: break the execution of a loop
>d) **next()**: skip an interation of a loop
>e) **return()**: exit a function

---
#2. Dates (日期) and times (时刻)

##2.1 Class types.
class **Date** for dates;
class **POSIXct** and **POSIXlt** for times.
**POSIXct**: inherit: a very long integer.
**POSIXlt**: stores the day of the week,the month,the year,etc..

```R
as.Date("2012-03-01");
x = Sys.time(); #in POSIXct format.
x = as.POSIXlt(x)
names(unclass(x));
## [1] "sec"   "min"   "hour"  "mday"  "mon"
## [6] "year"  "wday"  "yday"  "isdst"
```
---

##2.2 Operation on dates and times.

calculation like: **+,-**; comparison like **>,<,==**.
Note that the class type on the two side of the operators should be the same or compatible.

---

