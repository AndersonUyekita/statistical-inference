`Quiz 1` Statistical Inference
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
-   📆 Week 1
    -   🚦 Start: Wednesday, 29 June 2022
    -   🏁 Finish: Thursday, 30 June 2022
-   🌎 Rpubs: [Interactive
    Document](https://rpubs.com/AndersonUyekita/quiz-1_statistical-inference)

------------------------------------------------------------------------

## Question 1

Consider influenza epidemics for two parent heterosexual families.
Suppose that the probability is 17% that at least one of the parents has
contracted the disease. The probability that the father has contracted
influenza is 12% while the probability that both the mother and father
have contracted the disease is 6%. What is the probability that the
mother has contracted influenza?

*(Hints look at lecture 2 around 5:30 and chapter 4 problem 4).*

-   [x] 11%
-   [ ] 17%
-   [ ] 6%
-   [ ] 5%

**Answer**

The events can simultaneously occur and so are **not mutually
exclusive**.

Consider:

-   ![P(A)](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;P%28A%29 "P(A)"):
    Only father probability to be infected;
-   ![P(B)](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;P%28B%29 "P(B)"):
    Only mother probability to be infected;
-   ![P(A \\cap B)](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;P%28A%20%5Ccap%20B%29 "P(A \cap B)"):
    (intersection) father and mother probability infected, and;
-   ![P(A \\cup B)](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;P%28A%20%5Ccup%20B%29 "P(A \cup B)"):
    (union) All cases of infection.

According to the formula:

![\\underbrace{P(A \\cup B)}\_{17\\%} = \\underbrace{P(A)}\_{12\\%} + P(B) - \\underbrace{P(A \\cap B)}\_{6\\%}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cunderbrace%7BP%28A%20%5Ccup%20B%29%7D_%7B17%5C%25%7D%20%3D%20%5Cunderbrace%7BP%28A%29%7D_%7B12%5C%25%7D%20%2B%20P%28B%29%20-%20%5Cunderbrace%7BP%28A%20%5Ccap%20B%29%7D_%7B6%5C%25%7D "\underbrace{P(A \cup B)}_{17\%} = \underbrace{P(A)}_{12\%} + P(B) - \underbrace{P(A \cap B)}_{6\%}")

Thus:

![P(B) = 17\\% - 12\\% + 6\\% = 11\\%](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;P%28B%29%20%3D%2017%5C%25%20-%2012%5C%25%20%2B%206%5C%25%20%3D%2011%5C%25 "P(B) = 17\% - 12\% + 6\% = 11\%")

## Question 2

A random variable,
![X](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;X "X")
is uniform, a box from 0 to 1 of height 1. (So that its density is
![f(x) = 1](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;f%28x%29%20%3D%201 "f(x) = 1")
for
![0 \\leq x \\leq 1](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;0%20%5Cleq%20x%20%5Cleq%201 "0 \leq x \leq 1").)
What is its 75th percentile? (Hints, look at lecture 2 around 21:30 and
Chapter 5 Problem 5. Also, look up the help function for the qunif
command in R.)

*(Hints, look at lecture 2 around 21:30 and Chapter 5 Problem 5. Also,
look up the help function for the qunif command in R.)*

-   [ ] 0.25
-   [ ] 0.50
-   [ ] 0.10
-   [x] 0.75

**Answer**

![](quiz-1_statistical-inference_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

The 75th percentile represents the blue area.

``` r
# Calculating using R.
stats::qunif(p = 0.75, min = 0, max = 1)
```

    ## [1] 0.75

## Question 3

You are playing a game with a friend where you flip a coin and if it
comes up heads you give her
![X](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;X "X")
dollars and if it comes up tails she gives you
![Y](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;Y "Y")
dollars. The probability that the coin is heads is p (some number
between
![0](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;0 "0")
and
![1](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;1 "1")).
What has to be true about
![X](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;X "X")
and
![Y](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;Y "Y")
to make so that both of your expected total earnings is
![0](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;0 "0").
The game would then be called “fair”.

*(Hints, look at Lecture 4 from 0 to 6:50 and Chapter 5 Problem 6. Also,
for further reading on fair games and gambling, start with the Dutch
Book problem).*

-   [ ]
    ![p = \\frac{X}{Y}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;p%20%3D%20%5Cfrac%7BX%7D%7BY%7D "p = \frac{X}{Y}")
-   [x]
    ![\\frac{p}{1-p} = \\frac{Y}{X}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cfrac%7Bp%7D%7B1-p%7D%20%3D%20%5Cfrac%7BY%7D%7BX%7D "\frac{p}{1-p} = \frac{Y}{X}")
-   [ ]
    ![\\frac{p}{1-p} = \\frac{X}{Y}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cfrac%7Bp%7D%7B1-p%7D%20%3D%20%5Cfrac%7BX%7D%7BY%7D "\frac{p}{1-p} = \frac{X}{Y}")
-   [ ]
    ![X = Y](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;X%20%3D%20Y "X = Y")

**Answer**

![ Earnings = \\underbrace{Profit}\_{Y} \\cdot \\underbrace{P(Tail)}\_{1-p} - \\underbrace{Loss}\_{X} \\cdot \\underbrace{P(Head)}\_{p}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%20Earnings%20%3D%20%5Cunderbrace%7BProfit%7D_%7BY%7D%20%5Ccdot%20%5Cunderbrace%7BP%28Tail%29%7D_%7B1-p%7D%20-%20%5Cunderbrace%7BLoss%7D_%7BX%7D%20%5Ccdot%20%5Cunderbrace%7BP%28Head%29%7D_%7Bp%7D " Earnings = \underbrace{Profit}_{Y} \cdot \underbrace{P(Tail)}_{1-p} - \underbrace{Loss}_{X} \cdot \underbrace{P(Head)}_{p}")

![ \\underbrace{Profit}\_{Y} \\cdot \\underbrace{P(Tail)}\_{1-p} - \\underbrace{Loss}\_{X} \\cdot \\underbrace{P(Head)}\_{p} = 0](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%20%5Cunderbrace%7BProfit%7D_%7BY%7D%20%5Ccdot%20%5Cunderbrace%7BP%28Tail%29%7D_%7B1-p%7D%20-%20%5Cunderbrace%7BLoss%7D_%7BX%7D%20%5Ccdot%20%5Cunderbrace%7BP%28Head%29%7D_%7Bp%7D%20%3D%200 " \underbrace{Profit}_{Y} \cdot \underbrace{P(Tail)}_{1-p} - \underbrace{Loss}_{X} \cdot \underbrace{P(Head)}_{p} = 0")

![ Y \\cdot 1-p = X \\cdot p](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%20Y%20%5Ccdot%201-p%20%3D%20X%20%5Ccdot%20p " Y \cdot 1-p = X \cdot p")

![ \\frac{p}{1-p} = \\frac{Y}{X}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%20%5Cfrac%7Bp%7D%7B1-p%7D%20%3D%20%5Cfrac%7BY%7D%7BX%7D " \frac{p}{1-p} = \frac{Y}{X}")

## Question 4

A density that looks like a normal density (but may or may not be
exactly normal) is exactly symmetric about zero. (Symmetric means if you
flip it around zero it looks the same.) What is its median?

*(Hints, look at quantiles from Lecture 2 around 21:30 and Chapter 2
Problem 7.*

-   [ ] The median must be different from the mean.
-   [x] The median must be 0.
-   [ ] We can’t conclude anything about the median.
-   [ ] The median must be 1.

**Answer**

``` r
# Symmetric mean 50% in both sides.
qnorm(p = 0.50, mean = 0)
```

    ## [1] 0

## Question 5

Consider the following PMF shown below in R

``` r
x <- 1:4
p <- x/sum(x)
temp <- rbind(x, p)
rownames(temp) <- c("X", "Prob")
temp
```

    ##      [,1] [,2] [,3] [,4]
    ## X     1.0  2.0  3.0  4.0
    ## Prob  0.1  0.2  0.3  0.4

What is the mean?

*(Hint, watch Lecture 4 on expectations of PMFs.)*

-   [ ] 4
-   [ ] 1
-   [x] 3
-   [ ] 2

**Answer**

``` r
sum(temp["X",] * temp["Prob",])/sum(temp["Prob",])
```

    ## [1] 3

## Question 6

A web site (www.medicine.ox.ac.uk/bandolier/band64/b64-7.html) for home
pregnancy tests cites the following: “When the subjects using the test
were women who collected and tested their own samples, the overall
sensitivity was 75%. Specificity was also low, in the range 52% to 75%.”
Assume the lower value for the specificity. Suppose a subject has a
positive test and that 30% of women taking pregnancy tests are actually
pregnant. What number is closest to the probability of pregnancy given
the positive test?

*(Hints, watch Lecture 3 at around 7 minutes for a similar example.
Also, there’s a lot of Bayes’ rule problems and descriptions out there,
for example here’s one for HIV testing. Note, discussions of Bayes’ rule
can get pretty heady. So if it’s new to you, stick to basic treatments
of the problem. Also see Chapter 3 Question 5.)*

-   [x] 40%
-   [ ] 30%
-   [ ] 20%
-   [ ] 10%

**Answer**

-   sensitivity
    (![P(+\|D)](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;P%28%2B%7CD%29 "P(+|D)")):
    75%
-   specificity
    (![P(-\|D^C)](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;P%28-%7CD%5EC%29 "P(-|D^C)")):
    52%
-   prevalence
    (![P(D)](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;P%28D%29 "P(D)")):
    30%

![ P(D\|+) = \\frac{\\overbrace{P(+\|D)}^{sensitivity} \\cdot \\overbrace{P(D)}^{prevalence}}{P(+\|D) \\cdot P(D)+\[1-\\underbrace{P(-\|D^C)}\_{specificity}\] \\cdot \[1-P(D)\]}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%20P%28D%7C%2B%29%20%3D%20%5Cfrac%7B%5Coverbrace%7BP%28%2B%7CD%29%7D%5E%7Bsensitivity%7D%20%5Ccdot%20%5Coverbrace%7BP%28D%29%7D%5E%7Bprevalence%7D%7D%7BP%28%2B%7CD%29%20%5Ccdot%20P%28D%29%2B%5B1-%5Cunderbrace%7BP%28-%7CD%5EC%29%7D_%7Bspecificity%7D%5D%20%5Ccdot%20%5B1-P%28D%29%5D%7D " P(D|+) = \frac{\overbrace{P(+|D)}^{sensitivity} \cdot \overbrace{P(D)}^{prevalence}}{P(+|D) \cdot P(D)+[1-\underbrace{P(-|D^C)}_{specificity}] \cdot [1-P(D)]}")

![ P(D\|+) = \\frac{\\overbrace{0.75}^{sensitivity} \\cdot \\overbrace{0.30}^{prevalence}}{0.75 \\cdot 0.30+\[1-\\underbrace{0.52}\_{specificity}\] \\cdot \[1-0.30\]} = 0.4011](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%20P%28D%7C%2B%29%20%3D%20%5Cfrac%7B%5Coverbrace%7B0.75%7D%5E%7Bsensitivity%7D%20%5Ccdot%20%5Coverbrace%7B0.30%7D%5E%7Bprevalence%7D%7D%7B0.75%20%5Ccdot%200.30%2B%5B1-%5Cunderbrace%7B0.52%7D_%7Bspecificity%7D%5D%20%5Ccdot%20%5B1-0.30%5D%7D%20%3D%200.4011 " P(D|+) = \frac{\overbrace{0.75}^{sensitivity} \cdot \overbrace{0.30}^{prevalence}}{0.75 \cdot 0.30+[1-\underbrace{0.52}_{specificity}] \cdot [1-0.30]} = 0.4011")

``` r
#Calculating using R.
(0.75*0.30)/(0.75*0.30+0.48*0.70)
```

    ## [1] 0.4010695
