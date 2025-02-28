---
output:
  pdf_document: default
  html_document: default
---
Lab 1: Getting started with R and RStudio
================

> ### Learning Objectives:
>
> -   Get started with R as a scientific calculator
> -   Understand pane layout of RStudio
> -   Understand the help documentation in R
> -   How to install packages
> -   Difference between .R and .Rmd files
> -   Get to know markdown syntax

### General Instructions

-   Write your descriptions, explanations, and code in an `Rmd` (R
    markdown) file.
-   Name this file as `lab01-first-last.Rmd`, where `first` and `last`
    are your first and last names (e.g. `lab01-gaston-sanchez.Rmd`).
-   Knit your `Rmd` file as an html document (default option).
-   Submit your `Rmd` and `html` files to bCourses, in the corresponding
    lab assignment.
-   Due date displayed in the syllabus (see github repo).

------------------------------------------------------------------------

## R and RStudio

-   Make sure everybody has installed **R**
    -   R for Mac: <https://cran.r-project.org/bin/macosx/>
    -   R for windows: <https://cran.r-project.org/bin/windows/base/>
-   Make sure everybody has installed **RStudio**
    -   RStudio download:
        <https://www.rstudio.com/products/rstudio/download/>
-   Difference between R-GUI and RStudio
    -   R-GUI is a simply graphical user interface
    -   RStudio is an *Integrated Development Environment* (IDE)
        -   It is much more than a simple GUI
        -   It provides a nice working environment and development
            framework
-   We are going to use mainly RStudio

------------------------------------------------------------------------

## R as a scientific calculator

Launch RStudio and notice the default position of the panes (or panels):

-   Console (entire left)
-   Environment/History (tabbed in upper right)
-   Files/Plots/Packages/Help (tabbed in lower right)

**FYI:** you can change the default location of the panes, among many
other things: [Customizing
RStudio](https://support.rstudio.com/hc/en-us/articles/200549016-Customizing-RStudio).
If you have no experience working with R/RStudio, you don’t have to
customize anything right now. It’s better if you wait some days until
you get a better feeling of the working environment. You will probably
be experimenting (trial and error) some time with the customizing
options until you find what works for you.

### First contact with the R console

If you have never used software in which you have to type commands and
code, our best suggestion is that you begin typing basic things in the
**console**, using R as a scientific calculator.

For instance, consider the monthly bills of Leia (a stats undergrad
student):

-   cell phone $80
-   transportation $20
-   groceries $527
-   gym $10
-   rent $1500
-   other $83

You can use R to find Leia’s total expenses by typing these commands in
the console:

``` r
# total expenses
80 + 20 + 527 + 10 + 1500 + 83
```

    ## [1] 2220

Often, it will be more convenient to create **objects** or **variables**
that store one or more values. To do this, type the name of the
variable, followed by the assignment operator `<-`, followed by the
assigned value. For example, you can create an object `phone` for the
cell phone bill, and then inspect the object by typing its name:

``` r
phone <- 80
phone
```

    ## [1] 80

All R statements where you create objects are known as “assignments”,
and they have this form:

``` r
object <- value
```

this means you assign a `value` to a given `object`; you can read the
previous assignment as “phone gets 80”.

RStudio has a keyboard shortcut for the arrow operator `<-`: `Alt` + `-`
(the minus sign).

Notice that RStudio automagically surrounds `<-` with spaces, which
demonstrates a useful code formatting practice. So do yourself (and
others) a favor by ALWAYS surrounding an assignment operator with
spaces.

You will be working with RStudio a lot, and you will have time to learn
most of the bells and whistles RStudio provides. Think about RStudio as
your “workbench”. Keep in mind that RStudio is NOT R. RStudio is an
environment that makes it easier to work with R, while taking care of
many of the little tasks than can be a hassle.

### Your Turn

-   Make more assignments to create variables `transportation`,
    `groceries`, `gym`, `rent`, and `other` with their corresponding
    amounts.

-   Now that you have all the variables, create a `total` object with
    the sum of the expenses.

-   Assuming that Leia has the same expenses every month, how much would
    she spend during a school “semester”? (assume the semester involves
    five months).

-   Maintaining the same assumption about the monthly expenses, how much
    would Leia spend during a school “year”? (assume the academic year
    is 10 months).

### Object Names

There are certain rules you have to follow when creating objects and
variables. Object names cannot start with a digit and cannot contain
certain other characters such as a comma or a space. You will be wise to
adopt a convention for demarcating words in names.

``` r
i_use_snake_case
other.people.use.periods
evenOthersUseCamelCase
```

The following are invalid names (and invalid assignments)

    # cannot start with a number
    5variable <- 5

    # cannot start with an underscore
    _invalid <- 10

    # cannot contain comma
    my,variable <- 3

    # cannot contain spaces
    my variable <- 1

This is fine but a little bit too much:

``` r
this_is_a_really_long_name <- 3.5
```

### Functions

R has many functions. To use a function type its name followed by
parenthesis. Inside the parenthesis you pass an input. Most functions
will produce some type of output:

``` r
# absolute value
abs(10)
abs(-4)

# square root
sqrt(9)

# natural logarithm
log(2)
```

### Comments in R

All programming languages use a set of characters to indicate that a
specifc part or lines of code are **comments**, that is, things that are
not to be executed. R uses the hash or pound symbol `#` to specify
comments. Any code to the right of `#` will not be executed by R.

``` r
# this is a comment
# this is another comment
2 * 9

4 + 5  # you can place comments like this
```

### Case Sensitive

R is case sensitive. This means that `phone` is not the same as `Phone`
or `PHONE`

``` r
# case sensitive
phone <- 80
Phone <- -80
PHONE <- 8000

phone + Phone
```

    ## [1] 0

``` r
PHONE - phone
```

    ## [1] 7920

### Your turn

Take your objects (i.e. variables) `phone`, `transportation`,
`groceries`, `gym`, `rent`, and `other` and pass them inside the
*combine* function `c()` to create a vector `expenses`.

Now, use the graphing function `barplot()` to produce a barchart of
`expenses`:

``` r
barplot(expenses)
```

Find out how to use `sort()` to sort the elements in `expenses`, in
order to produce a bar-chart with bars in decreasing order. Also, see if
you can figure out how to display the names of the variables below each
of the bars. Also optional, see if you can find out how to display the
values of each variable at the top of each bar.

------------------------------------------------------------------------

## Introduction to R Markdown files

Most of the times you won’t be working directly on the console. Instead,
you will be typing your commands in some **source file**. The most basic
type of source files are known as *R script files*. But there are more
flavors of source files. A very convenient type of source file that
allow you to mix R code with narrative is an **R markdown file**
commonly referred to as `Rmd` file.

### Get to know the `Rmd` files

In the menu bar of RStudio, click on **File**, then **New File**, and
choose **R Markdown**. Select the default option (Document), and click
**Ok**.

**Rmd** files are a special type of file, referred to as a *dynamic
document*, that allows to combine narrative (text) with R code. Because
you will be turning in most homework assignments as `Rmd` files, it is
important that you quickly become familiar with this resource.

Locate the button **Knit HTML** (the one with a knitting icon) and click
on it so you can see how `Rmd` files are renderer and displayed as HTML
documents.

*R markdown* files use a special syntax called **markdown**. To be more
precise, Rmd files let you type text using either: 1) R syntax for code
that needs to be executed; 2) markdown syntax to write your *narrative*,
and 3) latex syntax for math equations and symbols.

You will have time to learn the basics of this syntax in the first
warmup assignment. And we actually expect that feel comfortable with
markdown at the end of the semester.

### Your turn

Open a new `Rmd` file in the *source* pane, and include all the previous
commands in separated code chunks. Knit the file to get an html
document. These are the files that you have to submit to bCourses when
you finish the lab work.

------------------------------------------------------------------------

## Getting Help

Because we work with functions all the time, it’s important to know
certain details about how to use them, what input(s) is required, and
what is the returned output.

There are several ways to get help.

If you know the name of a function you are interested in knowing more,
you can use the function `help()` and pass it the name of the function
you are looking for:

``` r
# documentation about the 'abs' function
help(abs)

# documentation about the 'mean' function
help(mean)
```

Alternatively, you can use a shortcut using the question mark `?`
followed by the name of the function:

``` r
# documentation about the 'abs' function
?abs

# documentation about the 'mean' function
?mean
```

-   How to read the manual documentation
    -   Title
    -   Description
    -   Usage of function
    -   Arguments
    -   Details
    -   See Also
    -   Examples!!!

`help()` only works if you know the name of the function your are
looking for. Sometimes, however, you don’t know the name but you may
know some keywords. To look for related functions associated to a
keyword, use double `help.search()` or simply `??`

``` r
# search for 'absolute'
help.search("absolute")

# alternatively you can also search like this:
??absolute
```

Notice the use of quotes surrounding the input name inside
`help.search()`

------------------------------------------------------------------------

### Your Turn: Pythagoras formula

The pythagoras formula is used to compute the length of the hypotenuse,
![c](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;c "c"),
of a right triangle with legs of length
![a](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;a "a")
and
![b](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;b "b").

![hypotenuse](https://wikimedia.org/api/rest_v1/media/math/render/svg/5fd521cee81d583ce94bf6710984cc2a9eb7c3da)

Calculate the hypotenuse of a right triangle with legs of length 3 and
4. Use the `sqrt()` function, and create variables `a = 3` and `b = 4`.
If you don’t know what’s the symbol to calculate exponents, search for
the help documentation of the arithmetic operators: `?Arithmetic`.

### Your Turn: Binomial Formula

The formula for the binomial probability is:

![binomial
probability](https://wikimedia.org/api/rest_v1/media/math/render/svg/38d86cba65d40f015a2b807d2b736250805abe45)

where:

-   ![n](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;n "n")
    is the number of (fixed) trials
-   ![p](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;p "p")
    is the probability of success on each trial
-   ![1 - p](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;1%20-%20p "1 - p")
    is the probability of failure on each trial
-   ![k](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;k "k")
    is a variable that represents the number of successes out of
    ![n](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;n "n")
    trials
-   the first term in parenthesis is not a fraction, it is the number of
    combinations in which
    ![k](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;k "k")
    success can occur in
    ![n](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;n "n")
    trials

R provides the `choose()` function to compute the number of
combinations:

![combinations](https://wikimedia.org/api/rest_v1/media/math/render/svg/08bdf0fff474c26293414f9eb01ab4bc73ef941f)

For instance, the number of combinations in which
![k](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;k "k")
= 2 success can occur in
![n](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;n "n")
= 5 trials is:

``` r
choose(n = 5, k = 2)
```

    ## [1] 10

Combinations are typically expressed in terms of factorials as:

![combs](https://wikimedia.org/api/rest_v1/media/math/render/svg/813f7124a61dac205542db3f8491b36cb306453a)

Conveniently, R also provides the function `factorial()` to calculate
the factorial of an integer:

``` r
factorial(4)
```

    ## [1] 24

Let’s consider a simple example. A fair coin is tossed 5 times. What is
the probability of getting exactly 2 heads?

-   Create the objects `n`, `k`, and `p` for the number of trials, the
    number of success, and the probability of success, respectively.

-   Use `factorial()` to compute the number of combinations “*n choose
    k*”

-   Apply the binomial formula, using `factorial()`, to calculate the
    probability of getting exactly 2 heads out of 5 tosses.

-   Recalculate the same probability but now using `choose()` (instead
    of `factorial()`)

-   Consider rolling a fair die 10 times. What is the probability of
    getting exactly 3 sixes?

-   Now look for help documentation (e.g. `help.search()` or `??`) using
    the keyword binomial: `binomial`.

-   You should get a list of topics related with the searched term
    `binomial`.

-   Choose the one related with the *Binomial Distribution*, which is
    part of the R package `stats` (i.e. `stats::Binomial`).

-   Read the documentation and figure out how to use the `dbinom()`
    function to obtain the above probabilities: 2 heads in 5 coin
    tosses, and 3 sixes in 3 rolls of a die.

-   How would you modify the previous binomial function to calculate the
    same probability (2 heads in 5 tosses) of a **biased** coin with a
    chance of heads of 35%?

-   Finally, obtain the probability of getting more than 3 heads in 5
    tosses with a biased coin of 35% chance of heads.

------------------------------------------------------------------------

## Installing Packages

R comes with a large set of functions and packages. A package is a
collection of functions that have been designed for a specific purpose.
One of the great advantages of R is that many analysts, scientists,
programmers, and users can create their own pacakages and make them
available for everybody to use them. R packages can be shared in
different ways. The most common way to share a package is to submit it
to what is known as **CRAN**, the *Comprehensive R Archive Network*.

You can install a package using the `install.packages()` function. To do
this, we recommend that you run this command directly on the console. Do
NOT include this command in a code chunk of an Rmd file: you will very
likely get an error message when knitting the Rmd file.

To use `install.packages()` just give it the name of a package,
surrounded by qoutes, and R will look for it in CRAN, and if it finds
it, R will download it to your computer.

``` r
# installing (run this on the console!)
install.packages("knitr")
```

You can also install a bunch of packages at once:

``` r
# run this command on the console!
install.packages(c("readr", "ggplot2"))
```

Once you installed a package, you can start using its functions by
*loading* the package with the function `library()`. By the way, when
working on an Rmd file that uses functions from a given package, you
MUST include a code chunk with the `library()` command.

``` r
# (this command can be included in an Rmd file)
library(knitr)
```

### Your turn

This part doesn’t need to be included in your Rmd file. Instead, type
commands directly on the console:

-   On the console, install packages `"stringr"`, `"RColorBrewer"`, and
    “`XML`”
-   Calculate:
    ![3x^2 + 4x + 8](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;3x%5E2%20%2B%204x%20%2B%208 "3x^2 + 4x + 8")
    when
    ![x = 2](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;x%20%3D%202 "x = 2")
-   Calculate:
    ![3x^2 + 4x + 8](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;3x%5E2%20%2B%204x%20%2B%208 "3x^2 + 4x + 8")
    but now with a numeric sequence for
    ![x](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;x "x")
    using `x <- -3:3`
-   Find out how to look for information about math binary operators
    like `+` or `^` (without using `?Arithmetic`).
-   There are several tabs in the pane
    `Files, Plots, Packages, Help, Viewer`. Find what does the tab
    **Files** is good for?
-   What about the tab **Help**?
-   In the tab **Help**, what happens when you click the button with a
    House icon?
-   Now go to the tab **History**. What is it good for? and what about
    the buttons of its associated menu bar?
-   Likewise, what can you say about the tab **Environment**?

------------------------------------------------------------------------

## Review Questions

Take a look at the following commands. Notice the difficulty of reading
code when assignment operators are not surrounded by spaces (Don’t do
this!). Without typing the code on the console, try to guess what will
be the output:

    # example 1
    var<-3
    Var*2


    # example 2
    x<-2
    2x<-2*x


    # example 3
    sqrt4 <- sqrt(4)
    sqrt4


    # example 4
    a number <- 16


    # example 5
    "one number" <- 16
    `one number`
    one number

### RStudio working environment

Understand the **pane layout** (i.e. windows) of RStudio. What is the
purpose of the following panes?

-   Source
-   Console
-   Environment, History, etc
-   Files, Plots, Packages, Help, Viewer

Play with the customizing options of RStudio (appearance of source pane,
etc)

-   font
-   size
-   background
