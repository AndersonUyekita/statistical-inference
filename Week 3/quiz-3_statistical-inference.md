`Quiz 3` Statistical Inference
================

-   👨🏻‍💻 Author: Anderson H Uyekita
-   📚 Specialization: <a
    href="https://www.coursera.org/specializations/data-science-statistics-machine-learning"
    target="_blank" rel="noopener">Data Science: Statistics and Machine
    Learning Specialization</a>
-   📖 Course:
    <a href="https://www.coursera.org/learn/statistical-inference"
    target="_blank" rel="noopener">Statistical Inference</a>
    -   🧑‍🏫 Instructor: Brian Caffo
-   📆 Week 3
    -   🚦 Start: Friday, 01 July 2022
    -   🏁 Finish: Friday, 01 July 2022
-   🌎 Rpubs: [Interactive
    Document](https://rpubs.com/AndersonUyekita/quiz-3_statistical-inference)

------------------------------------------------------------------------

## Question 1

In a population of interest, a sample of 9 men yielded a sample average
brain volume of 1,100cc and a standard deviation of 30cc. What is a 95%
Student’s T confidence interval for the mean brain volume in this new
population?

-   [ ] \[1092, 1108\]
-   [ ] \[1080, 1120\]
-   [ ] \[1031, 1169\]
-   [x] \[1077,1123\]

**Answer**

A simple application of “Gosset’s t distribution”.

![CI = \\bar {brain} \\pm t\_{n-1} \\cdot \\frac{S}{\\sqrt{n}} = 1100 \\pm t\_{n-1} \\cdot \\frac{30}{\\sqrt{9}}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;CI%20%3D%20%5Cbar%20%7Bbrain%7D%20%5Cpm%20t_%7Bn-1%7D%20%5Ccdot%20%5Cfrac%7BS%7D%7B%5Csqrt%7Bn%7D%7D%20%3D%201100%20%5Cpm%20t_%7Bn-1%7D%20%5Ccdot%20%5Cfrac%7B30%7D%7B%5Csqrt%7B9%7D%7D "CI = \bar {brain} \pm t_{n-1} \cdot \frac{S}{\sqrt{n}} = 1100 \pm t_{n-1} \cdot \frac{30}{\sqrt{9}}")

The
![t\_{n-1}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;t_%7Bn-1%7D "t_{n-1}")
will be calculated based on
![\\alpha](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Calpha "\alpha")
equal to 5%.

![t\_{(n-1,1-\\frac{\\alpha}{2})} \\implies t\_{(8,0.975)}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;t_%7B%28n-1%2C1-%5Cfrac%7B%5Calpha%7D%7B2%7D%29%7D%20%5Cimplies%20t_%7B%288%2C0.975%29%7D "t_{(n-1,1-\frac{\alpha}{2})} \implies t_{(8,0.975)}")

Calculating the “t-value”:

``` r
qt(p = 1 - 0.05/2, df = 9 - 1)
```

    ## [1] 2.306004

![CI = 1100 \\pm 2.306004 \\cdot \\frac{30}{\\sqrt{9}} = \[1077,1123\]](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;CI%20%3D%201100%20%5Cpm%202.306004%20%5Ccdot%20%5Cfrac%7B30%7D%7B%5Csqrt%7B9%7D%7D%20%3D%20%5B1077%2C1123%5D "CI = 1100 \pm 2.306004 \cdot \frac{30}{\sqrt{9}} = [1077,1123]")

``` r
# Calculating the bottom bound.
b1 <- 1100 - qt(p = 1 - 0.05/2, df = 9 - 1) * 30 / sqrt(9)

# Calculating the upper bound.
b2 <- 1100 + qt(p = 1 - 0.05/2, df = 9 - 1) * 30 / sqrt(9)

# Printing the boundaries
c(b1, b2)
```

    ## [1] 1076.94 1123.06

## Question 2

A diet pill is given to 9 subjects over six weeks. The average
difference in weight (follow up - baseline) is -2 pounds. What would the
standard deviation of the difference in weight have to be for the upper
endpoint of the 95% T confidence interval to touch 0?

-   [x] 2.60
-   [ ] 1.50
-   [ ] 2.10
-   [ ] 0.30

**Answer**

According to the [Statistical inference for data
science](https://github.com/AndersonUyekita/statistical-inference/blob/main/book/statistical-inference-for-data-dcience.pdf)
book, on page 76, this question is similar to the “Gosset’s sleep data”.

The sample is small, so it is mandatory to use t-student.

![Boundaries = mn \\pm 1 \\cdot t\_{(n-1, 1-\\frac{\\alpha}{2})} \\cdot \\frac{s}{\\sqrt{n}} ](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;Boundaries%20%3D%20mn%20%5Cpm%201%20%5Ccdot%20t_%7B%28n-1%2C%201-%5Cfrac%7B%5Calpha%7D%7B2%7D%29%7D%20%5Ccdot%20%5Cfrac%7Bs%7D%7B%5Csqrt%7Bn%7D%7D%20 "Boundaries = mn \pm 1 \cdot t_{(n-1, 1-\frac{\alpha}{2})} \cdot \frac{s}{\sqrt{n}} ")

![t\_{(n-1,1-\\frac{\\alpha}{2})} \\implies t\_{(8,0.975)}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;t_%7B%28n-1%2C1-%5Cfrac%7B%5Calpha%7D%7B2%7D%29%7D%20%5Cimplies%20t_%7B%288%2C0.975%29%7D "t_{(n-1,1-\frac{\alpha}{2})} \implies t_{(8,0.975)}")

Thus:

``` r
# Calculating the t_8,0.975
qt(p = 0.975, df = 9 - 1)
```

    ## [1] 2.306004

According to the question statement, the upper endpoint is **zero**.

![0 = -2 + \\underbrace{t\_{(8,0.975)}}\_{2.306004} \\cdot \\frac{S}{\\sqrt{9}} ](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;0%20%3D%20-2%20%2B%20%5Cunderbrace%7Bt_%7B%288%2C0.975%29%7D%7D_%7B2.306004%7D%20%5Ccdot%20%5Cfrac%7BS%7D%7B%5Csqrt%7B9%7D%7D%20 "0 = -2 + \underbrace{t_{(8,0.975)}}_{2.306004} \cdot \frac{S}{\sqrt{9}} ")

``` r
# Calculating the S
2 * sqrt(9) / qt(p = 0.975, df = 9 - 1)
```

    ## [1] 2.601903

## Question 3

In an effort to improve running performance, 5 runners were either given
a protein supplement or placebo. Then, after a suitable washout period,
they were given the opposite treatment. Their mile times were recorded
under both the treatment and placebo, yielding 10 measurements with 2
per subject. The researchers intend to use a T test and interval to
investigate the treatment. Should they use a paired or independent group
T test and interval?

-   [x] A paired interval
-   [ ] It’s necessary to use both
-   [ ] You could use either
-   [ ] Independent groups, since all subjects were seen under both
    systems

**Answer**

Following the example “Example of the t interval, Gosset’s sleep data”,
on page 76, it is a paired interval.

## Question 4

In a study of emergency room waiting times, investigators consider a new
and the standard triage systems. To test the systems, administrators
selected 20 nights and randomly assigned the new triage system to be
used on 10 nights and the standard system on the remaining 10 nights.
They calculated the nightly median waiting time (MWT) to see a
physician. The average MWT for the new system was 3 hours with a
variance of 0.60 while the average MWT for the old system was 5 hours
with a variance of 0.68. Consider the 95% confidence interval estimate
for the differences of the mean MWT associated with the new system.
Assume a constant variance. What is the interval? Subtract in this order
(New System - Old System).

-   [ ] \[-2,70, -1.29\]
-   [ ] \[1.29, 2.70\]
-   [x] \[-2.75, -1.25\]
-   [ ] \[1.25, 2.75\]

**Answer**

According to the [Statistical inference for data
science](https://github.com/AndersonUyekita/statistical-inference/blob/main/book/statistical-inference-for-data-dcience.pdf)
book, on page 79, this question is similar to the explanation about
“Confidence Interval”.

![\\mu\_{new} - \\mu\_{old} = \\bar m\_{new} - \\bar m\_{old} \\pm t\_{(nx + ny-2,1-\\frac{\\alpha}{2})} \\cdot S\_{p} \\cdot (\\frac{1}{nx} + \\frac{1}{ny})^{1/2}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cmu_%7Bnew%7D%20-%20%5Cmu_%7Bold%7D%20%3D%20%5Cbar%20m_%7Bnew%7D%20-%20%5Cbar%20m_%7Bold%7D%20%5Cpm%20t_%7B%28nx%20%2B%20ny-2%2C1-%5Cfrac%7B%5Calpha%7D%7B2%7D%29%7D%20%5Ccdot%20S_%7Bp%7D%20%5Ccdot%20%28%5Cfrac%7B1%7D%7Bnx%7D%20%2B%20%5Cfrac%7B1%7D%7Bny%7D%29%5E%7B1%2F2%7D "\mu_{new} - \mu_{old} = \bar m_{new} - \bar m_{old} \pm t_{(nx + ny-2,1-\frac{\alpha}{2})} \cdot S_{p} \cdot (\frac{1}{nx} + \frac{1}{ny})^{1/2}")

![\\mu\_{new} - \\mu\_{old} = 3 - 5 \\pm 2.100922 \\cdot S\_{p} \\cdot 0.4472136](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cmu_%7Bnew%7D%20-%20%5Cmu_%7Bold%7D%20%3D%203%20-%205%20%5Cpm%202.100922%20%5Ccdot%20S_%7Bp%7D%20%5Ccdot%200.4472136 "\mu_{new} - \mu_{old} = 3 - 5 \pm 2.100922 \cdot S_{p} \cdot 0.4472136")

![\\mu\_{new} - \\mu\_{old} = 3 - 5 \\pm 2.100922 \\cdot 0.6412488 \\cdot 0.4472136](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cmu_%7Bnew%7D%20-%20%5Cmu_%7Bold%7D%20%3D%203%20-%205%20%5Cpm%202.100922%20%5Ccdot%200.6412488%20%5Ccdot%200.4472136 "\mu_{new} - \mu_{old} = 3 - 5 \pm 2.100922 \cdot 0.6412488 \cdot 0.4472136")

![CI = \\mu\_{new} - \\mu\_{old} = \[-2.751649,-1.248351\]](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;CI%20%3D%20%5Cmu_%7Bnew%7D%20-%20%5Cmu_%7Bold%7D%20%3D%20%5B-2.751649%2C-1.248351%5D "CI = \mu_{new} - \mu_{old} = [-2.751649,-1.248351]")

``` r
# NEW -> y
my = 3
vy = 0.60
ny <- 10

# OLD -> x
mx = 5
vx = 0.68
nx <- 10

a <- qt(p = 0.975, df = ny + nx - 2)

b <- sqrt(1/nx + 1/ny)

c <- sqrt(((nx - 1)*vy + (ny - 1)*vx)/(nx + ny - 2))

my - mx + a*b*c
```

    ## [1] -1.248351

``` r
my - mx - a*b*c
```

    ## [1] -2.751649

## Question 5

Suppose that you create a 95% T confidence interval. You then create a
90% interval using the same data. What can be said about the 90%
interval with respect to the 95% interval?

-   [ ] The interval will be the same width, but shifted.
-   [ ] It is impossible to tell.
-   [x] The interval will be narrower.
-   [ ] The interval will be wider

## Question 6

To further test the hospital triage system, administrators selected 200
nights and randomly assigned a new triage system to be used on 100
nights and a standard system on the remaining 100 nights. They
calculated the nightly median waiting time (MWT) to see a physician. The
average MWT for the new system was 4 hours with a standard deviation of
0.5 hours while the average MWT for the old system was 6 hours with a
standard deviation of 2 hours. Consider the hypothesis of a decrease in
the mean MWT associated with the new treatment.

What does the 95% independent group confidence interval with unequal
variances suggest vis a vis this hypothesis? (Because there’s so many
observations per group, just use the Z quantile instead of the T.)

-   [x] When subtracting (old - new) the interval is entirely above
    zero. The new system appears to be effective.
-   ~~\[ \] When subtracting (old - new) the interval contains 0. The
    new system appears to be effective.~~
-   ~~\[ \] When subtracting (old - new) the interval is entirely above
    zero. The new system does not appear to be effective.~~
-   ~~\[ \] When subtracting (old - new) the interval contains 0. There
    is not evidence suggesting that the new system is effective.~~

**Answer**

> Because there’s so many observations per group, just use the Z
> quantile instead of the T.

``` r
# NEW
sd_new <- 0.5
var_new <- sd_new^2
n_new <- 100

# OLD
sd_old <- 2
var_old <- sd_old^2
n_old <- 100

# Calculating the boundaries.
6 - 4 - qnorm(0.975) * sqrt(var_new/n_new + var_old/n_old)
```

    ## [1] 1.595943

``` r
6 - 4 + qnorm(0.975) * sqrt(var_new/n_new + var_old/n_old)
```

    ## [1] 2.404057

The entire CI is above zero, which indicates the new standard works.

## Question 7

Suppose that 18 obese subjects were randomized, 9 each, to a new diet
pill and a placebo. Subjects’ body mass indices (BMIs) were measured at
a baseline and again after having received the treatment or placebo for
four weeks. The average difference from follow-up to the baseline
(followup - baseline) was −3 kg/m2 for the treated group and 1 kg/m2 for
the placebo group. The corresponding standard deviations of the
differences was 1.5 kg/m2 for the treatment group and 1.8 kg/m2 for the
placebo group. Does the change in BMI over the four week period appear
to differ between the treated and placebo groups? Assuming normality of
the underlying data and a common population variance, calculate the
relevant *90%* t confidence interval. Subtract in the order of
(Treated - Placebo) with the smaller (more negative) number first.

-   [ ] \[-5.531, -2.469\]
-   [ ] \[2.469, 5.531\]
-   [x] \[-5.364, -2.636\]
-   [ ] \[2.636, 5.364\]

**Answer**

Following the page 79 (Confidence interval).

``` r
# treat - placebo
sd_p <- 1.8
var_p <- sd_p*sd_p

sd_t <- 1.5
var_t <- sd_t*sd_t

s_p <- sqrt(((9 - 1)*var_p + (9 - 1)*var_t)/(9 + 9 - 2))

-3 - 1 + qt(p = 0.95, df = 9 + 9 - 2) * s_p * (1/9 + 1/9)^0.5
```

    ## [1] -2.636421

``` r
-3 - 1 - qt(p = 0.95, df = 9 + 9 - 2) * s_p * (1/9 + 1/9)^0.5
```

    ## [1] -5.363579
