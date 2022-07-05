`Quiz 4` Statistical Inference
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
-   📆 Week 4
    -   🚦 Start: Friday, 01 July 2022
    -   🏁 Finish: Tuesday, 05 July 2022
-   🌎 Rpubs: [Interactive
    Document](https://rpubs.com/AndersonUyekita/quiz-4_statistical-inference)

------------------------------------------------------------------------

## Question 1

A pharmaceutical company is interested in testing a potential blood
pressure lowering medication. Their first examination considers only
subjects that received the medication at baseline then two weeks later.
The data are as follows (SBP in mmHg)

| Subject | Baseline | Week 2 |
|:-------:|:--------:|:------:|
|    1    |   140    |  132   |
|    2    |   138    |  135   |
|    3    |   150    |  151   |
|    4    |   148    |  146   |
|    5    |   135    |  130   |

Consider testing the hypothesis that there was a mean reduction in blood
pressure? Give the P-value for the associated two sided T test.

*(Hint, consider that the observations are paired.)*

-   [ ] 0.10
-   [x] 0.087
-   [ ] 0.05
-   [ ] 0.043

**Answer**

-   Two weeks later = few observations = T-distribution
-   We have the same subject measured in baseline and the experiment =
    paired

``` r
# Calculating the Hypothesis using a T-distribution with a paired.
q1 <- stats::t.test(x = c(140,138,150,148,135),
                    c(132,135,151,146,130),
                    paired = TRUE,
                    alternative = "two.sided")

# P value.
q1$p.value
```

    ## [1] 0.08652278

## Question 2

A sample of 9 men yielded a sample average brain volume of 1,100cc and a
standard deviation of 30cc. What is the complete set of values of
![\\mu_0](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cmu_0 "\mu_0")
that a test of
![H_0: \\mu = \\mu_0](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;H_0%3A%20%5Cmu%20%3D%20%5Cmu_0 "H_0: \mu = \mu_0")
would fail to reject the null hypothesis in a two sided 5% Students
t-test?

-   [ ] 1081 to 1119
-   [ ] 1031 to 1169
-   [ ] 1080 to 1120
-   [x] 1077 to 1123

**Answer**

-   sample
    (![n](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;n "n"))
    = 9
    -   Due to the n value being small, it must be used as a
        t-distribution.
-   ![\\mu](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cmu "\mu")
    = 1100 cc
-   ![\\sigma](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Csigma "\sigma")
    = 30 cc
-   ![\\alpha](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Calpha "\alpha")
    = 5%

![\\mu \\pm t\_{(n-1,1-\\frac{\\alpha}{2}) \\cdot \\frac{sd}{\\sqrt(n)}}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cmu%20%5Cpm%20t_%7B%28n-1%2C1-%5Cfrac%7B%5Calpha%7D%7B2%7D%29%20%5Ccdot%20%5Cfrac%7Bsd%7D%7B%5Csqrt%28n%29%7D%7D "\mu \pm t_{(n-1,1-\frac{\alpha}{2}) \cdot \frac{sd}{\sqrt(n)}}")

``` r
n <- 9
mu <- 1100
sd <- 30
alpha <- 5/100

# Calculating the quantile to df = 8 and p = 0.975
t_8_975 <- qt(p = (1 - alpha/2), df = 9 - 1)

# Calculating the CI.
mu + c(-1,1) * t_8_975 * sd / sqrt(n)
```

    ## [1] 1076.94 1123.06

## Question 3

Researchers conducted a blind taste test of Coke versus Pepsi. Each of
four people was asked which of two blinded drinks given in random order
that they preferred. The data was such that 3 of the 4 people chose
Coke. Assuming that this sample is representative, report a P-value for
a test of the hypothesis that Coke is preferred to Pepsi using a one
sided exact test.

-   [ ] 0.62
-   [ ] 0.005
-   [ ] 0.10
-   [x] 0.31

**Answer**

-   p_coke = 3/4
-   p_pepsi = 1/4
-   Coke is preferred to Pepsi, and; Probability to 3 or 4 person prefer
    Coke.
-   Using a one sided exact test.

My Hypothesis:

![H\_{0}: p = 0.5](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;H_%7B0%7D%3A%20p%20%3D%200.5 "H_{0}: p = 0.5")

![H\_{a}: p \> 0.5](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;H_%7Ba%7D%3A%20p%20%3E%200.5 "H_{a}: p > 0.5")

General formula:

![P(n) = {4 \\choose n} \\cdot (1-p)^{(4-n)} \\cdot (p)^{n}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;P%28n%29%20%3D%20%7B4%20%5Cchoose%20n%7D%20%5Ccdot%20%281-p%29%5E%7B%284-n%29%7D%20%5Ccdot%20%28p%29%5E%7Bn%7D "P(n) = {4 \choose n} \cdot (1-p)^{(4-n)} \cdot (p)^{n}")

![ P(Prefer \\ Coke) = P(p \\ge 3)$ = $P(3) + P(4)](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%20P%28Prefer%20%5C%20Coke%29%20%3D%20P%28p%20%5Cge%203%29%24%20%3D%20%24P%283%29%20%2B%20P%284%29 " P(Prefer \ Coke) = P(p \ge 3)$ = $P(3) + P(4)")

![P(p \\ge 3) = {4 \\choose 3} \\cdot (1-p)^{(4-3)} \\cdot (p)^{3} + {4 \\choose 4} \\cdot (1-p)^{(4-4)} \\cdot (p)^{4}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;P%28p%20%5Cge%203%29%20%3D%20%7B4%20%5Cchoose%203%7D%20%5Ccdot%20%281-p%29%5E%7B%284-3%29%7D%20%5Ccdot%20%28p%29%5E%7B3%7D%20%2B%20%7B4%20%5Cchoose%204%7D%20%5Ccdot%20%281-p%29%5E%7B%284-4%29%7D%20%5Ccdot%20%28p%29%5E%7B4%7D "P(p \ge 3) = {4 \choose 3} \cdot (1-p)^{(4-3)} \cdot (p)^{3} + {4 \choose 4} \cdot (1-p)^{(4-4)} \cdot (p)^{4}")

![P(p \\ge 3) = 0.3125](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;P%28p%20%5Cge%203%29%20%3D%200.3125 "P(p \ge 3) = 0.3125")

``` r
# Calculating the probability.
P_3_4 <- choose(4,3) * (1-1/2)^1 * (1/2)^3 + choose(4,4) * (1-1/2)^0 * (1/2)^4

P_3_4
```

    ## [1] 0.3125

## Question 4

Infection rates at a hospital above 1 infection per 100 person days at
risk are believed to be too high and are used as a benchmark. A hospital
that had previously been above the benchmark recently had 10 infections
over the last 1,787 person days at risk. About what is the one sided
P-value for the relevant test of whether the hospital is *below* the
standard?

-   [ ] 0.22
-   [x] 0.03
-   [ ] 0.52
-   [ ] 0.11

**Answer**

``` r
ppois(q = 10, lambda = 1/100 * 1787)
```

    ## [1] 0.03237153

## Question 5

Suppose that 18 obese subjects were randomized, 9 each, to a new diet
pill and a placebo. Subjects’ body mass indices (BMIs) were measured at
a baseline and again after having received the treatment or placebo for
four weeks. The average difference from follow-up to the baseline
(followup - baseline) was −3 kg/m2 for the treated group and 1 kg/m2 for
the placebo group. The corresponding standard deviations of the
differences was 1.5 kg/m2 for the treatment group and 1.8 kg/m2 for the
placebo group. Does the change in BMI appear to differ between the
treated and placebo groups? Assuming normality of the underlying data
and a common population variance, give a p-value for a two sided t test.

-   [ ] Less than 0.05, but larger than 0.01
-   [x] Less than 0.01
-   [ ] Less than 0.10 but larger than 0.05
-   [ ] Larger than 0.10

**Answer**

![H\_{0}: \\mu\_{diff,treated} - \\mu\_{diff,placebo} = 0](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;H_%7B0%7D%3A%20%5Cmu_%7Bdiff%2Ctreated%7D%20-%20%5Cmu_%7Bdiff%2Cplacebo%7D%20%3D%200 "H_{0}: \mu_{diff,treated} - \mu_{diff,placebo} = 0")

![H\_{a}: \\mu\_{diff,treated} - \\mu\_{diff,placebo} \\ne 0](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;H_%7Ba%7D%3A%20%5Cmu_%7Bdiff%2Ctreated%7D%20-%20%5Cmu_%7Bdiff%2Cplacebo%7D%20%5Cne%200 "H_{a}: \mu_{diff,treated} - \mu_{diff,placebo} \ne 0")

![\\underbrace{\\mu\_{diff,treated} - \\mu\_{diff,placebo}}\_{0} = \\bar{treated} - \\bar{placebo} \\pm t\_{(n + n -2, 1-\\frac{\\alpha}{2})} \\cdot S\_{p} \\cdot (\\frac{1}{n} + \\frac{1}{n})^{1/2} ](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cunderbrace%7B%5Cmu_%7Bdiff%2Ctreated%7D%20-%20%5Cmu_%7Bdiff%2Cplacebo%7D%7D_%7B0%7D%20%3D%20%5Cbar%7Btreated%7D%20-%20%5Cbar%7Bplacebo%7D%20%5Cpm%20t_%7B%28n%20%2B%20n%20-2%2C%201-%5Cfrac%7B%5Calpha%7D%7B2%7D%29%7D%20%5Ccdot%20S_%7Bp%7D%20%5Ccdot%20%28%5Cfrac%7B1%7D%7Bn%7D%20%2B%20%5Cfrac%7B1%7D%7Bn%7D%29%5E%7B1%2F2%7D%20 "\underbrace{\mu_{diff,treated} - \mu_{diff,placebo}}_{0} = \bar{treated} - \bar{placebo} \pm t_{(n + n -2, 1-\frac{\alpha}{2})} \cdot S_{p} \cdot (\frac{1}{n} + \frac{1}{n})^{1/2} ")

![t\_{(n + n -2, 1-\\frac{\\alpha}{2})} \\cdot S\_{p} \\cdot (\\frac{1}{n} + \\frac{1}{n})^{1/2} = \\bar{treated} - \\bar{placebo}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;t_%7B%28n%20%2B%20n%20-2%2C%201-%5Cfrac%7B%5Calpha%7D%7B2%7D%29%7D%20%5Ccdot%20S_%7Bp%7D%20%5Ccdot%20%28%5Cfrac%7B1%7D%7Bn%7D%20%2B%20%5Cfrac%7B1%7D%7Bn%7D%29%5E%7B1%2F2%7D%20%3D%20%5Cbar%7Btreated%7D%20-%20%5Cbar%7Bplacebo%7D "t_{(n + n -2, 1-\frac{\alpha}{2})} \cdot S_{p} \cdot (\frac{1}{n} + \frac{1}{n})^{1/2} = \bar{treated} - \bar{placebo}")

![t\_{(n + n -2, 1-\\frac{\\alpha}{2})} = \\frac{\\bar{treated} - \\bar{placebo}}{S\_{p} \\cdot (\\frac{1}{n} + \\frac{1}{n})^{1/2}}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;t_%7B%28n%20%2B%20n%20-2%2C%201-%5Cfrac%7B%5Calpha%7D%7B2%7D%29%7D%20%3D%20%5Cfrac%7B%5Cbar%7Btreated%7D%20-%20%5Cbar%7Bplacebo%7D%7D%7BS_%7Bp%7D%20%5Ccdot%20%28%5Cfrac%7B1%7D%7Bn%7D%20%2B%20%5Cfrac%7B1%7D%7Bn%7D%29%5E%7B1%2F2%7D%7D "t_{(n + n -2, 1-\frac{\alpha}{2})} = \frac{\bar{treated} - \bar{placebo}}{S_{p} \cdot (\frac{1}{n} + \frac{1}{n})^{1/2}}")

``` r
# Sample
n <- 9

# Treated
x_treat <- -3 
s_treat <- 1.5

# Placebo
x_placebo <- 1 
s_placebo <- 1.8

# The pooled variance estimator is:
sp <- sqrt(((n - 1) * s_treat^2 + (n - 1) * s_placebo^2)/(n + n - 2))

# Calculating the quantile given: mu_treat - mu_placebo = 0
t <- (x_treat - x_placebo)/(sp * sqrt(1/n + 1/n))

# Given t, its possible to calculate the probability.
q5_pvalue <- pt(t, n + n - 2)

# Formatting
format(q5_pvalue, digits = 2,scientific = FALSE)
```

    ## [1] "0.000051"

## Question 6

Brain volumes for 9 men yielded a 90% confidence interval of 1,077 cc to
1,123 cc. Would you reject in a two sided 5% hypothesis test of
![H_0 : \\mu = 1,078](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;H_0%20%3A%20%5Cmu%20%3D%201%2C078 "H_0 : \mu = 1,078")?

-   [ ] Where does Brian come up with these questions?
-   [x] No you wouldn’t reject.
-   [ ] Yes you would reject.
-   [ ] It’s impossible to tell.

**Answer**

The 90% CI already includes the
![\\mu=1078](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cmu%3D1078 "\mu=1078"),
so if I increase the CI to 95%, it will still contain the
![\\mu=1078](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cmu%3D1078 "\mu=1078").
For this reason, I will not reject the
![H_0](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;H_0 "H_0")
statement.

## Question 7

Researchers would like to conduct a study of
![100](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;100 "100")
healthy adults to detect a four year mean brain volume loss of
![.01\~mm^3](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;.01~mm%5E3 ".01~mm^3").
Assume that the standard deviation of four year volume loss in this
population is
![.04\~mm^3](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;.04~mm%5E3 ".04~mm^3").
About what would be the power of the study for a
![5\\%](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;5%5C%25 "5\%")
one sided test versus a null hypothesis of no volume loss?

-   [ ] 0.70
-   [ ] 0.60
-   [x] 0.80
-   [ ] 0.50

**Answer**

-   n = 100 (normal)
-   one sided test = `lower.tail = FALSE`
-   sd = 0.04
-   delta = 0.01
-   ![\\alpha = 5\\%](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Calpha%20%3D%205%5C%25 "\alpha = 5\%")

``` r
# Inputs
n <- 100
alpha <- 5/100
sd <- 0.04
mu <- 0.01

# Calculating the z value from alpha equal to 5%
z <- qnorm(p = (1 - alpha))

# Calculating the probability.
pnorm(z * sd/sqrt(n), mean = mu, sd = sd/sqrt(n), lower.tail = FALSE)
```

    ## [1] 0.8037649

## Question 8

Researchers would like to conduct a study of
![n](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;n "n")
healthy adults to detect a four year mean brain volume loss of
![.01\~mm^3](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;.01~mm%5E3 ".01~mm^3").
Assume that the standard deviation of four year volume loss in this
population is
![.04\~mm^3](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;.04~mm%5E3 ".04~mm^3").
About what would be the value of
![n](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;n "n")
needed for
![90\\%](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;90%5C%25 "90\%")
power of type one error rate of
![5\\%](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;5%5C%25 "5\%")
one sided test versus a null hypothesis of no volume loss?

-   [ ] 120
-   [ ] 180
-   [ ] 160
-   [x] 140

**Answer**

-   ![\\Delta](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5CDelta "\Delta")
    = 0.01
-   sd = 0.04
-   power = 90%
-   type one error = 5% = `sig.level`
-   type = one sided test

``` r
# Calculating the n value.
q8 <- power.t.test(power = 0.9,
                   delta = 0.01,
                   sd = 0.04,
                   sig.level = 0.05,
                   type = "one.sample",
                   alternative = "one.sided")

# Printing the n
round(q8$n)
```

    ## [1] 138

## Question 9

As you increase the type one error rate,
![\\alpha](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Calpha "\alpha"),
what happens to power?

-   [ ] No, for real, where does Brian come up with these problems?
-   [ ] It’s impossible to tell given the information in the problem.
-   [ ] You will get smaller power.
-   [x] You will get larger power.
