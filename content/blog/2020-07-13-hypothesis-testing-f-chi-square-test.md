---
title: "Hypothesis Testing - F Test and Chi Square Test"
date: 2020-04-30T15:49:13+05:30

# post thumb - set only one image
#image: "images/featured-post/post-1.jpg"
image: "https://res.cloudinary.com/datasciencia/image/upload/v1594638058/Greenshot/joshua-ness-unsplash-f-chi-square-test_znf9h6.jpg"
image_credit: "Photo by Joshua Ness on Unsplash"
thumbnail: "https://res.cloudinary.com/datasciencia/image/upload/v1594638057/Greenshot/joshua-ness-unsplash-f-chi-square-test-thumbnai_odz1i8.jpg"
alt: "test image"

# meta description
description: "hypothesis testing - finding the test statistic using F test and chi square test"

# taxonomies
# use only one category; tags can be multiple
categories: 
  - statistics
  - beginner
tags:
  - statistics
  - hypothesis-testing
  - fundamentals
  - inferential statistics

# post type - 'featured' or 'post' or 'hidden'
type: "post"

# set the slug for the post
slug: "hypothesis testing f test and chi square test"

# keywords
keywords:
  - statistics
  - hypothesis testing
  - A/B testing
  - inferential statistics
  - statistical inference testing

# comments - set to 'true' or 'false'
comments: true 

showMeta: false
showActions: false

# draft post or not - set 'true' or 'false'
draft: false 

#funfact
funfact: false 
funfact_description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quam nihil enim maxime corporis
cumque" 

# sidebar display
show_sidebar: true

---

This post is the final part of the four-part series in hypothesis testing. What are the tests used to find the test
statistic when we need to find the variance in the population.

In the [previous article](../hypothesis-testing-z-test-t-test), we saw what a Z test and t-test are! 
Z test and t-test are used when the hypothesis test is about the **mean** of the population.

{{< alert info "Tutorial Series">}}
This post is the part 4 of the four part series on hypothesis testing.

- [Part 1 - Introduction to hypothesis testing](../introduction-to-hypothesis-testing/)
- [Part 2 - How to do hypothesis testing](../how-to-do-hypothesis-testing/)
- [Part 3 - Finding the test statistic - Z test and T test](../hypothesis-testing-z-test-t-test/)
- **[Part 4 - Finding the test statistic - F test and Chi Square
  test](../hypothesis-testing-f-test-and-chi-square-test/)**
{{< /alert >}}

In this article, let us see two tests - the chi-squared ($\chi^2$) and F test, which tests the hypothesis about the **variance** of the population.

{{< alert info Recall >}}
The sample estimate of the population variance is given by

$$
s^2 = \frac{\sum(x_i-\bar{x})^2}{n-1}
$$
where $s$ is the sample variance, $\bar{x}$ is the sample mean, and $n$ is the number of samples.
{{< /alert >}}

<hr/>

## Chi-squared statistic

$\chi^2$ test is used to test the hypothesis about a single population variance.

### Formula

The formula for computing $\chi ^2$ is

$$
\chi ^2 = \frac{(n-1)s ^2}{\sigma ^2}
$$

Where $n - 1$ is the $df$ (degree of freedom),  $s$ is the sample standard deviation, and $\sigma$ is the population standard deviation, and $n$ is the number of samples.

#### Interpretation of $\chi ^2$

 If the chi-square value is more than the critical value, then there is a significant difference in the variance between the sample and the population.

{{< alert info Tip>}}

The Chi-square statistic is **used on numbers**. We can’t use it for percentages, proportions, means, or similar statistical value. For example, if you have 20 percent of 100 people, you need to convert it to a number (20) before running a test statistic.

{{< /alert >}}

### Application of Chi-square

A manufacturing company produces bearings of `2.65` cm in diameter. A major customer requires that the variance in diameter be no more than `0.001` $cm ^2$. The manufacturer tests `20` bearings using a precise instrument and gets the below values. Assuming the diameters are normally distributed, can the population of these bearings be rejected due to high variance at a `1%` significance level?

#### Data
2.69, 2.66, 2.64, 2.59, 2.62, 2.63, 2.69, 2.66, 2.63, 2.65, 2.57, 2.63, 2.70, 2.71, 2.64, 2.65, 2.59, 2.66, 2.62, 2.57

### Solution approach

The problem talks about a single population variance. Therefore, we can use the $\chi ^2$ test.

#### Known parameters

$\text {sample size} \space n = 20$

level of significance $ \space \alpha = 1\% \space  or \space  0.01$

Degree of freedom $= n - 1 \text { which is } \space  20 - 1 \space = 19$

Population variance $\sigma ^2 = 0.001$

Let's follow the hypothesis testing process.

**1. State the null and the alternate hypothesis.**

The variance in diameter to be **no more than** 0.001 $cm ^2$.

So the null hypothesis is 

$$
 \mathbf{H}_\mathbf{0}: diameter \le 0.001
$$

and the alternate hypothesis is

$$
 \mathbf{H}_\mathbf{1} : diameter > 0.001
$$

Since the alternate hypothesis has the greater than symbol $>$, it is a chi-square **right-tailed** test.

**2. Find the level of significance**

The level of significance provided is $\alpha = 0.01$

**Note:** If the level of significance is not given, take the default $\alpha = 0.05$

**3. Find the critical value**

The critical value is found out in the chi-squared table for $df = 19$ and $\alpha = 0.01$. 

The critical value is **36.191** i.e $\chi ^2_c = 36.191$

![](https://i.imgur.com/oMCGtpp.png)

**4. Find the test statistic**

To find the test statistic, we will use the formula.

$$
\chi ^2 = \frac{(n-1)s ^2}{\sigma ^2}
$$

We don't know the sample variance $s ^2$, but it can be computed using the data provided.

Copy the data in excel and use the formula `VAR.S` and get the value, which in turn is $0.001621$.

Substituting the values, we get

$$
\chi ^2 = \frac{19 \* 0.001621}{0.001}
$$

which gives

$$
\chi ^2 = 30.8
$$

**5. Draw the conclusion - to accept/reject the null hypothesis**

![](https://i.imgur.com/0SxM4Y0.png)

Since the $\chi^2 _{test} < \chi^2 _{critical}$ i.e. `30.8` < `36.191`, we accept the null hypothesis.

The bearings produced are within the specified limits required by the customer.

To conclude, a $\chi ^2$ test (chi-squared) is used to test the hypothesis about a single population variance.

<hr/>

## F test 

$\chi ^2$ is useful when testing hypotheses about a single population. 

What if we want to test the hypothesis about the difference in variances of two populations?

**Example**: Do parts manufactured on two different machines have the same variance or not?

### Formula

Since the F-test compares two different populations' variances using samples collected from each population, we can say that F-test is a ratio of two sample variances, i.e.

$$
F = \frac{s_1 ^2}{s_2 ^2} = \frac{est.\sigma ^2_1}{est.\sigma ^2_2}
$$

What does this formula mean?

We know that $s_1$ is the standard deviation of sample 1, and $s_2$ is the standard deviation of sample 2.

Since the F test compares two **variances**, we need to square the standard deviation. (Remember: variance = standard deviation$^2$)

#### Interpretation

Ideally, this F ratio should be about 1

- if the two samples come from the same population
- or the two samples come from a different population with the same variance

So if we compute the F ratio and see if the value is near to 1, it means two samples have the same variance, thereby the population variance is also the same.

Bigger the F ratio - bigger the variance (or the two population is not related to each other)

**Important**: Since the F test/distribution deals with two samples, there will be two degrees of freedom - one for sample 1 and another for sample 2.

**Facts**:

1.  The curve is not symmetrical but skewed to the right.
2.  There is a different curve for each set of  _df_.
3.  The  _F_  statistic is greater than or equal to zero.
4.  As the degrees of freedom for the numerator and the denominator gets larger, the curve approximates the normal.

### Application of the 'F' test

A machine produces metal sheets with `22mm` thickness. There is a **variability** in thickness due to machines, operators, manufacturing environment, raw material, etc. The company wants to know the consistency of **two machines** and randomly samples `10` sheets from machine 1 and `12` sheets from machine 2. Thickness measurements are taken. Assume sheet thickness is normally distributed in the population.

The company wants to know if the variance for each sample comes from the same population variance (i.e., population variances are equal) or from different population variances (population variances are unequal).

#### Data provided

| Machine 1 | Machine 2 |
|-----------|-----------|
| 22.3      | 22.0      |
| 21.8      | 22.1      |
| 22.3      | 21.8      |
| 21.6      | 21.9      |
| 21.8      | 22.2      |
| 21.9      | 22.0      |
| 22.4      | 21.7      |
| 22.5      | 21.9      |
| 22.2      | 22.0      |
| 21.6      | 22.1      |
|           | 21.9      |
|           | 22.1      |

### Solution Approach

#### Understanding the type of test

Here the problem statement is about knowing the consistency of _two machines_ in terms of _variability_.

For variances test, we have two tests - $\chi ^2$ and F test. But since we have to compare two variances, we have to go with the F test.

#### Known parameters

Samples from machine one $n_1 = 10$

Samples from machine two $n_2 = 12$

We have the data for machine one and machine two from which we can find the variance with excel.

#### Compute the rest of the parameters

![](https://i.imgur.com/GEyw7ES.png)

We compute the variance and the count of samples.

![](https://i.imgur.com/xDhf34z.png)

The degree of freedom for machine one is `9` ($df_1 = n_1 - 1$).

The degree of freedom for machine two is `11` ($df_2 = n_2 - 1$).

#### Following the hypothesis testing process

There are five steps to the hypothesis testing process. Let's follow that one by one.

**1. State the null and the alternate hypothesis**

Since this problem talks about variance in the two machines, the null hypothesis will be that there is no variance.

$$
 \mathbf{H}_\mathbf{0}: \sigma_1 ^2 = \sigma_2 ^2
$$

The alternate hypothesis will be

$$
 \mathbf{H}_\mathbf{1}: \sigma_1 ^2 \ne \sigma_2 ^2
$$	

Based on the symbol of the alternate hypothesis, which is $\ne$, we conclude that this is a **two-tailed** test.

**Tip**: If there is any difficulty in stating the null hypothesis, start with the alternate hypothesis and then draft the null hypothesis.

**2. Find the level of significance**

The level of significance $ \alpha $ is not given, and hence, a $ \alpha $ of `5`% or `0.05` is presumed.

Since this is a two-tailed test, we have to divide $\alpha$ by `2`, which gives the value as `0.025` for each tail.

**3. Find the critical value**

Similar to tables for other tests, F tests also have a corresponding table called the F-table.

The F-table has a degree of freedom one ($df_1$) on the 'x' axis and degree of freedom two ($df_2$) on the 'y' axis.

Let's see the F table for $df_1 = 9$ and $df_2 = 11$ to find the critical value for F test. The critical value is 

$$F _{0.025,9,11} = 3.5879$$. 

![](https://i.imgur.com/iq9ZRyX.png)

This number is for the right-tail. Remember, we have a two-tails for this hypothesis testing.

We also need to compute the left-tail critical value which can be either computed like the F-table above with a level of significance $\alpha = 0.975 (1-0.025 = 0.975)$ and the $df_1 = 9$ and $df_2 = 11$.

The other method of doing this is to divide 1 by $F _{0.025,9,11}$

$$
F _{0.975,9,11} = \frac{1}{F _{0.025,9,11}}
$$

$$
F _{0.975,9,11} = \frac{1}{3.5879} = 0.2787
$$

**4. Find the test statistic**

The test statistic is computed by the F distribution formula - which is

$$
F = \frac{s_1 ^2}{s_2 ^2}
$$

So the F score is `5.62`

$$
F _{score} = \frac{0.11378}{0.02023} = 5.62
$$

**5. Draw the conclusion**

From the above steps, we know that the $F _{critical} = 3.5879 \text { and} \space \text {the } F _{score} = 5.62$

Since $F _{score} > F _{critical}$ or in other words, falls into the rejection region, we reject the null hypothesis. 

That is, the variance in machine one and machine two are not equal. Machine one has a higher variance and hence needs inspection for issues.

The graph below illustrates the F score and the F critical value and why we reject the null hypothesis.

![](https://i.imgur.com/ogYXdYk.png)

<hr/>
	
## ANOVA

ANOVA - Analysis of Variance

ANOVA is used to analyze the means of the samples.

In the $\chi^2$ test, we saw how to compare variance within a single population. In the F test, we saw how to analyze the variance between two samples of a single population / two population.

What if there are three or more samples? Can we find if they are from the same population? We use the ANOVA test for this purpose.

When performing the ANOVA test, we try to determine if the difference between the averages reflects a real difference between the groups or the random noise inside each group.

The groups here mean samples - say out of a Population p, we are taking three groups of samples - $n_1, n_2, n_3$.


### Assumptions in the ANOVA test

- The samples taken are independent; (taking samples in one group does not affect the probability of the samples taken in other groups)
- The population must be normally distributed.

### Null hypothesis and computation

Since we are comparing three groups or more, the null hypothesis of ANOVA would look like below.

$$
 \mathbf{H}_\mathbf{0}: \mu_A = \mu_B = \mu_C
$$

We compute the F value and compare it with the critical value determined by the degrees of freedom. Here, the degree of freedom is calculated for the groups and the number of items in each group.

### Example

Let's say we have three groups - A, B, and C, with the below samples picked.

| Group A | Group B | Group C |
|---------|---------|---------|
| 37      | 62      | 50      |
| 60      | 27      | 63      |
| 52      | 69      | 58      |
| 43      | 64      | 54      |
| 40      | 43      | 49      |
| 52      | 54      | 52      |
| 55      | 44      | 53      |
| 39      | 31      | 43      |
| 39      | 49      | 65      |
| 23      | 57      | 43      |

These three groups have an equal number of samples.

The degree of freedom of the groups = $df_g = 3 - 1 = 2$.

The degree of freedom for the samples within each group is $df_s = 9 + 9 + 9 = 27$ i.e. $n-1$ for each group which is $10 - 1 = 9$

Let us calculate the mean of each of the groups and the total mean (total of all the means of the three groups divided by 3)

|            | Group A | Group B | Group C |
|-----------:|:-------:|:-------:|:-------:|
|            |    37   |    62   |    50   |
|            |    60   |    27   |    63   |
|            |    52   |    69   |    58   |
|            |    43   |    64   |    54   |
|            |    40   |    43   |    49   |
|            |    52   |    54   |    52   |
|            |    55   |    44   |    53   |
|            |    39   |    31   |    43   |
|            |    39   |    49   |    65   |
|            |    23   |    57   |    43   |
|       Mean of individual groups |    **44**   |    **50**   |    **53**   |
| Mean of all the three groups |    **49**   |         |         |

{{< alert info Important >}}
ANOVA considers two types of variance

- Between groups
	- How far each group mean vary from the total mean (i.e. in this case, how $44, 50, 53$ vary from the total mean $49$
	
- Within groups
	- How far individual values vary from their respective group mean.
{{< /alert >}}


**Note**: We will compute the F score both manually as well as using excel. If you want to move on with excel computation only, you may skip the below section and can proceed with calculation with excel (using data-analysis add-in).

### Formula

We compute F value for the groups, which is the ratio between the two variances - i.e., the variance between groups and variance within groups.

$$
F = \frac{Variance\space Between\space Groups}{Variance\space Within\space Groups}
$$

{{< alert info Recall >}}
We know that the formula for variance is

$$
s ^2 = \frac{\sum(x - \bar{x}) ^2}{n -1} = \frac{SS}{df}
$$

where $\sum(x - \bar{x}) ^2$ is the _sum of squares_ $SS$ and the $n -1$ is the _degree of freedom_.
{{< /alert >}}

So the formula for the f value becomes

$$
F = \frac {\text {Variance Between Groups}} {\text {Variance Within Groups}} = \frac {\frac{SSG}{df _{groups}}}{\frac {SSE} {df _{error}}}
$$

where SSG = Sum of Squares Groups, $df _{groups} =$ degrees of freedom (groups) and
SSE = Sum of Squares Error and $df _{error}$ = degrees of freedom (error)

### Solution approach

As with any hypothesis testing, let us perform the calculation using the hypothesis testing steps.

**1. State the null and the alternate hypothesis**

For ANOVA, the hypothesis will always be - the means across different groups will be equal.	
In this case, the means of the groups will be equal is the null hypothesis.

$$
 \mathbf{H}_\mathbf{0}: \mu_A = \mu_B = \mu_C
$$

The alternate hypothesis will be $\mathbf{H}_\mathbf{1}: \mu_A \ne \mu_B \ne \mu_C$

{{< alert info Important >}}
In ANOVA, there will be **NO two-tailed test**. ANOVA will ALWAYS be one-tailed, and that will be **upper-tailed only**. Why?
We know that in the formula, we are dividing the sum of squares between groups and within groups, which would always yield a positive value, and hence it will always be _upper tailed_.
{{< /alert >}}


**2. Find the level of significance**

Here level of significance is not provided; we will take the default $\alpha = 0.05$

**3. Find the critical value**

We know that the two degrees of freedom - for the groups and within the groups are 2 and 27, respectively. So, $df_1 = 2$ and $df_2 = 27$

Looking into the F table (for ANOVA) at `0.05` significance level, we get the $F_{critical}$	value as $3.35$ (see image below)

![](https://i.imgur.com/B0ucElO.png)

**4. Find the test statistic**

To compute it manually, we will be using excel. The following screenshot shows how it is done.

We know the formula is

$$
F = \frac{\text {Variance Between Groups}}{ \text {Variance Within Groups}} = \frac{\frac{SSG}{df _{groups}}}{\frac{SSE}{df _{error}}}
$$

#### Computing the sum of squares within groups and between groups manually.
	
![](https://i.imgur.com/fZLQycd.png)

substituting in the formula, we get

$$
F _{test} = \frac{\frac{420}{2}}{\frac{3300}{27}} = 1.718
$$

#### Computing the sum of squares within groups and between groups via excel data-analysis add-in.

1. Enter the data in excel

![](https://i.imgur.com/a87UPqd.png)

2. Go to Data -> Data Analysis and select "Anova - Single-factor" and click "OK."

![](https://i.imgur.com/qhJSZ3w.png)
	
3. Give the input range and check "labels in first row" as we have the group headers in the first row and input the significance level. Click "OK"

![](https://i.imgur.com/q0stppA.png)

4. We get the analysis in a new sheet.

![](https://i.imgur.com/I1AhY5O.png)

**5. Draw your conclusion**

Here we see that the $F _{score} \text {is less than the } F _{critical}$ (`1.718` < `3.354`), and hence we will accept the null hypothesis - which means that there is no difference between the means of any group.

![](https://i.imgur.com/mOHKOzb.png)


## Summary

To summarize, we have seen two tests: the chi-square and the F test to test the population's variances.

We have also seen ANOVA to test the hypothesis when more than two groups of samples are picked from the population.

Thanks for reading! If you enjoyed reading this article, consider subscribing to our newsletter below. We will notify
you on the latest content published on datasciencia.

