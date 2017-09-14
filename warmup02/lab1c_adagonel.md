Lab 1
================
Angelo Dagonel
8/31/2017

------------------------------------------------------------------------

R as a calculator
=================

**Calculate Leia's total expenses**

cell phone $80 transportation $20 groceries $527 gym $10 rent $1500 other $83

*Insert chunk:* `Ctrl+Alt+I / Cmd+Option+I`

*Run current chunk:* `Ctrl+Shift+Enter / Cmd+Shift+Enter?`

Basic addition

``` r
#Total expenses
80 + 20 + 527 + 10 + 1500 + 83
```

    ## [1] 2220

Creating objects and adding with operators `<-`

``` r
#Creating objects with values using <-
phone <- 80
transportation <- 20
groceries <- 527
gym <- 10
rent <- 1500
other <- 83

#Example: Inspect value of cell phone expenses
phone
```

    ## [1] 80

``` r
#Total expenses via Sum of objects
total <- phone + transportation + groceries + gym + rent + other
total
```

    ## [1] 2220

``` r
#Total semester expenses (5 months)
semtot <- total*3
semtot
```

    ## [1] 6660

``` r
#Total school year (10 months, or 2 semesters)
yeartot <- semtot*2
yeartot
```

    ## [1] 13320

Functions
=========

Absolute values

``` r
abs(10)
```

    ## [1] 10

``` r
abs(-4)
```

    ## [1] 4

Square roots

``` r
sqrt(9)
```

    ## [1] 3

``` r
sqrt(16)
```

    ## [1] 4

Natural logarithms

``` r
log(2)
```

    ## [1] 0.6931472

Vectors
=======

Create vector of Leia's expenses using combine function `c()`

``` r
#Vector expenses
expenses <- c(phone, transportation, groceries, gym, rent, other)
names(expenses) <- c('Cell phone', 'Transportation', 'Groceries', 'Gym', 'Rent', 'Other')
expenses
```

    ##     Cell phone Transportation      Groceries            Gym           Rent 
    ##             80             20            527             10           1500 
    ##          Other 
    ##             83

``` r
#Barplot of expenses
barplot(expenses)
```

![](lab1c_adagonel_files/figure-markdown_github/unnamed-chunk-7-1.png)

``` r
#Add names to values to make data frame
expenses_names <- c('Cell phone', 'Transportation', 'Groceries', 'Gym', 'Rent', 'Other')
expenses_table <- data.frame(expenses)
expenses_table
```

|                |  expenses|
|----------------|---------:|
| Cell phone     |        80|
| Transportation |        20|
| Groceries      |       527|
| Gym            |        10|
| Rent           |      1500|
| Other          |        83|

Sort vector in decreasing order, and add values to top of bar graph

``` r
expenses_sort <- sort(expenses, decreasing=TRUE)

expenseplot <- barplot(sort(expenses, decreasing=TRUE))
expenseplot
```

|     |
|----:|
|  0.7|
|  1.9|
|  3.1|
|  4.3|
|  5.5|
|  6.7|

``` r
text(x=expenseplot,
     y=expenses_sort,
     label=expenses_sort,
     pos=3,
     cex=0.8)
```

![](lab1c_adagonel_files/figure-markdown_github/unnamed-chunk-8-1.png)

Pythagoras formula
==================

``` r
#Create 'a' and 'b' for Pythagoras
a = 3
b = 4

c = sqrt(a^2 + b^2)
c
```

    ## [1] 5

Binomial formula
================

``` r
#Compute number of combinations
choose(n=5, k=2)
```

    ## [1] 10

``` r
#Factorial
factorial(4)
```

    ## [1] 24

**Fair coin toss**

Fair coin is tossed *n=5 times*--What's the *probability* of getting *exactly 2 heads*?

``` r
#Assign objects for use in calculation
n = 5
p = 0.5
k = 2

#Combination calculation with `factorial`
comb_factorial = factorial(n)/(factorial(k)*factorial(n-k))
comb_factorial
```

    ## [1] 10

``` r
#Combination calculation with Choose
comb_choose = choose(n, k)
comb_choose
```

    ## [1] 10

``` r
#Calculate probability including Factorial
(factorial(n)/(factorial(k)*factorial(n-k)))*(p^k)*((1-p)^(n-k))
```

    ## [1] 0.3125

``` r
#or
prob1 = comb_factorial*(p^k)*((1-p)^(n-k))
prob1
```

    ## [1] 0.3125

``` r
#Calculate probability including Choose
choose(n, k)*(p^k)*((1-p)^(n-k))
```

    ## [1] 0.3125

``` r
#or
prob2 = comb_factorial*(p^k)*((1-p)^(n-k))
prob2
```

    ## [1] 0.3125

**Fair die roll**

Fair die is rolled *n=10 times*--What's the probability of rolling *exactly k=3 6s*?

``` r
#Assignment of objects
n = 10
p = 1/6
k = 3

#Combination via `choose`
comb_die1 = choose(n,k)
comb_die1
```

    ## [1] 120

``` r
#Probability including Choose
prob_die1 = comb_die1*(p^k)*((1-p)^(n-k))
prob_die1
```

    ## [1] 0.1550454

**`dbinom()` function**

`dbinom(x, size, prob, log = FALSE)` or `dbinom(k, n, prob)`

    x, q    vector of quantiles.
    p         vector of probabilities.
    n         number of observations (If length(n)>1, length = # required)
    size    number of trials (zero or more).
    prob      probability of success on each trial.
    log/.p  logical; if TRUE, probabilities p are given as log(p).

2 heads in 5 coin tosses

``` r
dbinom(2, 5, 0.5)
```

    ## [1] 0.3125

3 sixes in 3 rolls of a die

``` r
dbinom(3, 3, 1/6)
```

    ## [1] 0.00462963

2 heads in 5 coin tosses, biased coin (35%)

``` r
dbinom(2, 5, .35)
```

    ## [1] 0.3364156
