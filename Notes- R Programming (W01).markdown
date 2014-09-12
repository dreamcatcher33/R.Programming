# Notes: R Programming (W01)

标签（空格分隔）：MOOC R

---

#1. Data types
##1.1 Basic types of objects:(对象）
- vector;
- matrix;
- data.frame;
- list.
- factor.( integer vector with each integer having a *lebel* )

Remarks: 
>a) Check the attributes of objects: **attributes()**;
>b) If factors are ordered, use *level* argument to specify the order. NOte the first level is used as the baseline level in linear modeling;
>c) Matrices are constructed column-wise; (按列填充)
>d) For **data.frame**, **names()** return the name of each column while **row.names()** return the name of each row. **data.matrix()** could change a data frame to a matrix.

----

##1.2 Basic types of atomic classes:(类)
- character;
- integer;
- numeric;
- logical;
- complex;( seldom used )

Remarks:
> You can create an interger like 1L.(notice the suffix **L**);
> These atomic classes could build up other complex classes.

---
# 2. Subsetting(子集提取)
> 1. **[** 的返回值总是原来的类(class),可以提取多个元素；（except when subsetting elements of matrix).
> 2. **[[** 用于提取data.frame 或者list的元素，返回对象不一定是原来的类，会尽量drop掉（变成更简单的类）。但是只能提取1个元素；
> 3. **$** 的用法同**[[**.

---
##2.1 Removing NA values
```R
good = complete.cases(airquality) 
#the object airquality has NA values.
#or:
x = c(1:5,NA);
bad.ind = is.na(x);
good = x[!bad.ind]
```
---
#3. Reading and writing data

> 1. For very big dataset, we need some technique to make it faster when reading in data. 
>>  a) calculate the memory before read in; a number = 8byte; 1MB = $2^{20}$ byte. 
>>  b) set **colClasses**, this will make 'read.table' run at least 2 times faster!

```R
initial = read.table('dataset.txt',nrows =100);
#get the colClasses information
classes = sapply(initial,class);
tabAll = read.table('dataset.txt',colClasses =classes)
```
>>  c) set **nrow**, this help with memory usage. (Linux commands \`wc` is ok) 

----------
#4. The *collection* interface
- file, opens a file;
- gzfile, bzfile,url.
- About the *open* parameter: -r (read); -w (writing); -a (appending)

```R
con = file('foo.txt','r');
x = read.csv(con);
close(con);
#or
con = url('http://www.baidu.com','r')
x = readLines(con)
```
---







        
        









