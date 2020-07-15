---
title: "How To Do Hypothesis Testing?"
date: 2020-04-14T16:26:32+05:30

# post thumb - set only one image
#image: "images/featured-post/post-1.jpg"
image: "https://res.cloudinary.com/datasciencia/image/upload/v1594561225/Greenshot/glenn-carstens-peters-unsplash-hypothesis-testing_ysblsp.jpg"
image_credit: "Photo by Glenn Carstens-Peters on Unsplash"
thumbnail: "https://res.cloudinary.com/datasciencia/image/upload/v1594561225/Greenshot/glenn-carstens-hypothesis-testing-thumbnail_pjtvex.jpg"
alt: "how to do hypothesis testing"

# meta description
description: "How to do hypothesis testing?"

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
slug: "how-to-do-hypothesis-testing"

# keywords
keywords:
  - statistics
  - hypothesis
  - A/B testing
  - inferential statistics

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

Hypothesis testing is simple to understand - a matter of following a sequence of five steps.

In the [previous article](../introduction-to-hypothesis-testing), we got introduced to the concept of hypothesis - null hypothesis and the alternate hypothesis. 

We concluded with how the _p-value_  compared with the level of significance to either accept or reject the null hypothesis.

We will keep _p-value_ aside at the moment and focus on how to do hypothesis testing - the steps involved.

{{< alert info "Tutorial Series">}}
This post is the part 2 of the four part series on hypothesis testing.

- [Part 1 - Introduction to hypothesis testing](../introduction-to-hypothesis-testing/)
- **[Part 2 - How to do hypothesis testing](../how-to-do-hypothesis-testing/)**
- [Part 3 - Finding the test statistic - Z test and T test](../hypothesis-testing-z-test-t-test/)
- [Part 4 - Finding the test statistic - F test and Chi Square test](../hypothesis-testing-f-test-and-chi-square-test/)
{{< /alert >}}

## Hypothesis test steps

Just to recap, hypothesis testing is _the process of determining whether a given hypothesis is true or not_

The highlight is on the word **process**. If it is a process, then there have to be some steps associated with it.

![](https://res.cloudinary.com/datasciencia/image/upload/v1594561625/Greenshot/hypothesis-testing-steps_jy8cur.jpg)

The steps for testing the hypothesis are

1. State the null hypothesis and the alternate hypothesis 
2. Choose the level of significance
3. Find critical values
4. Find test statistic
5. Draw your conclusion

Ok. Sounds good! Let us take stock of what knowledge we already have on the steps mentioned above. 

We know what the null and the alternate hypothesis are, level of significance, and probably presume what draw your conclusion means.

{{< alert info "Reference" >}}

If you have missed reading the [previous article](../introduction-to-hypothesis-testing) in this series, I recommend reading it first before proceeding to read further.

{{< /alert >}}

What we don't know about at this point is

- Step 4 - Find critical values and 
- Step 5 - Find the test statistic.

Good! Let's see what a critical value is and then proceed to understand how to find the critical value.

To understand the critical value and critical region, we need first to understand what _one-tailed_ and _two-tailed_ tests are.

## One-Tailed and Two-Tailed Tests

In statistics, when there is a long tail to the right of a frequency distribution, the data is positively skewed and where is a long tail to the left, the data is negatively skewed.

So it has to do something with the distribution curve? Yes, you are right! 

Let's dive into detail!

### What are tails?

In the day-to-day context, we know a tail is that extra portion attached to the body of an animal. 

Similarly, in the context of statistics, tails are that portion attached to the side of distribution - see figure below - _the grey area_

![](https://i.imgur.com/o35gMNp.png)

{{< alert info "Note" >}}
Distribution need not have two tails always. There can be only one tail as well. 
{{</alert >}}

Now that we have seen the tails visually, we understand things better.
But, there are two tails here - do we have names that distinguish between these tails? 

Yes! It's "upper" tail and "lower" tail.

The following image shows the lower tail and upper tail respectively.

![](https://i.imgur.com/yvJK9if.png)

#### Upper tail

The upper tail is towards the upper side i.e., the positive side of the graph (see image above). Remember, positive values lie on the chart's right side (1, 2, 3, etc.). It is also called as "right-tail".

#### Lower tail

The lower tail is towards the lower side, i.e., the negative side of the graph. Hence it is referred to as "left-tail" as well. 

>So if the distribution has just one tail, it can be either an _upper-tail **or** lower-tail_, and if the distribution has two-tails, it will have both _upper-tail **and** lower-tail_.

#### Critical Region / Rejection Region

The region shaded in grey, i.e., the tail area is called the **Critical Region** or **Rejection Region**

The following image shows the _rejection region for the lower-tailed graph_

![](https://i.imgur.com/sKoJ8i9.png)

Similarly, the image below depicts the _rejection region for the upper tailed graph_

![](https://i.imgur.com/iH0jI91.png)

The _rejection region for the two-tailed graph_ is shown below.

![](https://i.imgur.com/NuHvOL8.png)

So far, so good!?

Now in real-life problems, we will not be given the graph to understand if the tail is towards the left or right or it is two-tailed.

Based on the problem statement, we need to figure out the hypothesis and then decide if its right-tailed or left-tailed or both!

### One-Tailed tests

One-tailed tests can be either an upper tailed test or a lower tailed test.

How can we spot or understand which tailed-tests the problem we have at hand belongs? Upper tail or lower tail?

Remember, in the [previous article](../introduction-to-hypothesis-testing), we had stated the hypothesis for two examples. Let's revisit those examples.

**Example 1**

My broadband company claims that the minimum internet speed they provide me is 150 Mbps. However, I suspect that they are not providing the promised internet speed.

Let's write the null and alternate hypotheses for this!

$$
\mathbf{H}_\mathbf{0}: speed \ge \space 150 Mbps 
$$

$$
\mathbf{H}_\mathbf{1}: speed < \space 150 Mbps
$$

We are trying to prove our alternate hypothesis with evidence is that the speed is less than 150 Mbps.

To determine which tailed test we need to use here, we see the symbol of alternate hypothesis, i.e - if it is less than `<` 150 Mbps, it is called a _lower tail_ test.

![](https://i.imgur.com/z4RRP87.png)


**Example 2**

The project manager claims that his team resolves the software defects raised within five business days. I being the quality department manager, think it is taking longer to fix the bugs. 

The null and alternate hypothesis is below

$$
 \mathbf{H}_\mathbf{0}: \text { Resolution period } \le 5 \space \text {days}
$$

$$
\mathbf{H}_\mathbf{1}: \text { Resolution period } > 5 \space \text {days}
$$

We see that the alternate hypothesis symbol (greater than) `>` 5 days. Hence, it is an _upper-tail_ test.

![](https://i.imgur.com/026muUN.png)

{{<alert info Note >}} 
- The upper-tailed test or lower-tailed test is determined based on the **alternative hypothesis** only and **NOT** the null hypothesis.
- One-tailed tests can be either an _upper-tail_ test or a _lower-tail_ test and the test is determined by the **symbol** of the alternate hypothesis $\mathbf{H}_\mathbf{1}$
{{< /alert >}}

### Two-Tailed tests

#### So how does the hypothesis of a two-tailed test look like?

A residential school claims that the average time the students of the school get to do extra-curricular activities is 200 hours per year, but the parents doubt that they spend so much time.

The null and the alternate hypothesis looks like the below.

$$
 \mathbf{H}_\mathbf{0}: \mu = 200 \space \text {hours}
$$

$$
  \mathbf{H}_\mathbf{1}: \mu \ne 200 \space \text {hours}
$$

Here we see the symbol of the alternate hypothesis is $\ne$ which means the test is a _two-tailed_ test. We don't check for increase or decrease i.e. $\ge$ or $\le$ but, we check for a change in the parameter.

So the critical region/tails are split over both the ends.

Both the ends contain $\alpha/2$, making a total of $\alpha$ - which is the level of significance. Refer to the [previous article](../introduction-to-hypothesis-testing) for level of significance.

![](https://i.imgur.com/5tayxLc.png)

{{< alert info "Milestone reached" >}}
From the hypothesis statement, we understand if the test is either a one-tailed (upper or lower tail) or two-tailed.
We are still in step 3 - Finding the critical value
{{< /alert >}}

Let's understand what a critical value is, and then we will see how to compute the critical value.

### Critical value

We know what a critical region or a rejection region is! So critical value should be near or in that critical region.

To take an analogy, the critical values of water - i.e., the boiling point is 100 deg Celcius and the freezing point is 0 deg Celcius. It is an important measure that helps us make critical decisions.

Similarly, the critical value in statistics helps us to make important decisions.

#### Definition of critical value

A critical value is a line on a graph that splits the graph into sections. If our test value falls into that region, then we reject the null hypothesis - which means the samples and the evidence we had taken supports the alternate hypothesis.

Critical value depicted in the graph below - for lower-tailed graph

![](https://i.imgur.com/aTaG3bX.png)

Similarly, the critical value for the upper-tailed graph is below.

![](https://i.imgur.com/mIsCOBT.png)

Critical values for a two-tailed graph are below.

In the case of a two-tailed graph, the value we compute should be either below or above the critical value for rejecting the null hypothesis.

![](https://i.imgur.com/kHb4sZ1.png)

Ok - now we have visualized what a critical value is. This critical value is nothing but the **'Z' score**.

#### Example of a 'Z' score

Let's say we have a sample normal distribution. As per the empirical split (or rule), 68% lie within the `1` standard deviation from the mean, 95% lie within `2` standard deviation from the mean and 99.7% of the values lie within `3` standard deviations from the mean.

We know that the 'Z' score for `+2.0` standard deviation is `1.96`, and `-2.0` standard deviation is `-1.96`. Use
Z-table to find the Z-score.

Let us see how we use the level of significance ($\alpha$) to find the critical value (Z score).

### Critical value and level of significance

We use the level of significance ($\alpha$) to determine the critical value. How?

**Example:** 

Determine the critical value at `5%` level of significance. Presume its a **right-tailed / upper-tailed test**.

We know $\alpha$ = `5%` (see image below to find where level of significance $\alpha$ of 5% falls)
and 1 - $\alpha$ is `95%`

![](https://i.imgur.com/AgZGTmb.png)

We know that `95 %` of the values fall within the `2` standard deviation mark in a normal distribution, and the corresponding the 'Z' score is `1.96`.

So the critical value (_Z_) is `1.96`.

#### So how will we determine if we have to accept or reject the null hypothesis?

> I am quoting a new word _test statistic_ here. We will see what it is and how to compute it in the next post. At the moment, just think of _test statistic_ as a number calculated from our samples by a formula.

If the test statistic (_test Z_) is less than the critical value (_Z_), we will accept the null hypothesis. In other words, we have not stepped into the rejection region and hence will accept.

$$
\text {test} \space Z \le Z : \space accept \space  \mathbf{H}_\mathbf{0}
$$

$$
\text {test} \space Z > Z : \space reject \space  \mathbf{H}_\mathbf{0}
$$

Let's visualize the above scenario with an example graph!

Below are the numbers.

Critical value _Z_ = `1.96`
Test statistic (_test Z_) = `0.5`

Since the test statistic is less than the critical value, we will accept the null hypothesis $\mathbf{H}_\mathbf{0}$

![](https://i.imgur.com/4AbSXzL.png)

### Summary

In this article, we focussed on the 3rd step of the hypothesis testing process - _Find the critical value_

We started with what are tails, upper tail and lower tail, one-tailed tests and two-tailed tests, critical region/rejection region, critical values, and when to accept or reject the null hypothesis.

In the next post, we will explore more on finding the _test statistic, which is the 4th step of the hypothesis testing process.

{{< alert info "Next part in the series">}}
- [Part 3 - Finding the test statistic - Z test and T test](../hypothesis-testing-z-test-t-test/)
{{< /alert >}}
