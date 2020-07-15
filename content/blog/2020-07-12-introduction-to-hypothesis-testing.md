---
title: "Introduction to Hypothesis Testing"
date: 2020-04-12T06:12:40+05:30

# post thumb - set only one image
#image: "images/featured-post/post-1.jpg"
image: "https://res.cloudinary.com/datasciencia/image/upload/v1594525227/Greenshot/randy-jacob-unsplash-hypothesis-testing_os6zju.jpg"
image_credit: "Photo by Randy Jacob on Unsplash"
thumbnail: "https://res.cloudinary.com/datasciencia/image/upload/v1594525226/Greenshot/randy-jacob-unsplash-hypothesis-testing-thumbnail_yppxr2.jpg"
alt: "hypothesis testing - which is true?"

# meta description
description: "Introduction to hypotheses testing - Part 1"

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
slug: "introduction-to-hypothesis-testing"

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

Hypothesis testing is a fundamental concept in statistics on which we do data analysis. A good understanding of hypothesis testing will help us in the long run.

{{< alert info "Tutorial Series">}}
This post is the part 1 of the four part series on hypothesis testing.

- **[Part 1 - Introduction to hypothesis testing](../introduction-to-hypothesis-testing/)**
- [Part 2 - How to do hypothesis testing](../how-to-do-hypothesis-testing/)
- [Part 3 - Finding the test statistic - Z test and T test](../hypothesis-testing-z-test-t-test/)
- [Part 4 - Finding the test statistic - F test and Chi Square test](../hypothesis-testing-f-test-and-chi-square-test/)

{{< /alert >}}


First, let us understand what does the word _hypothesis_ means. Let us break the word into two parts _hypo_ + _thesis_. 

What does _thesis_ mean?
_thesis_ implies something that is already proven to be true. 
e.g., At least 60% of the adult human body contains water.

Sounds fine!

So what does _hypothesis_ mean?

A hypothesis is something that is **not yet** proven to be true.

Let's come back to the original question! What is hypothesis testing?

It is the _the process of determining whether a given hypothesis is correct or not_

To sum up, we take the hypothesis, we perform some statistical computations and prove if the theory holds true or not.

## Null Hypothesis & Alternate Hypothesis

The null hypothesis is the _assertion or belief that we hold as true_ unless we have sufficient evidence to prove otherwise.

In statistical terms, we say it as _the belief we hold about the value of a population parameter_ 

!!! Remember
	The parameter is for the population, and Statistic is for the sample.

Let's take an example and see what the null hypothesis is and how to write one.

We believe that the mean of the population is `500`. Unless we obtain sufficient evidence that it is not `500`, our belief holds, i.e., we accept that the mean is `500`.

So we can write it as `null hypothesis: mean = 500`

To write it more compactly, we can represent the same thing as $ \mathbf{H}_\mathbf{0} : \mu = 500 $

Here, the symbol $\space\mathbf{H}_\mathbf{0}$ denotes the Null hypothesis.

The _opposite_ of the Null hypothesis is _Alternate Hypothesis_. That is, the _negation_ of the null hypothesis. 

If there is a way to represent the null hypothesis, then there should be a way to describe the alternate hypothesis. Agreed? Ah, I see I have quoted a null hypothesis there!

$\mathbf{H}_\mathbf{1}: \mu \ne 500$

Here, the symbol $\space\mathbf{H}_\mathbf{1}$ denotes the alternate hypothesis.

!!! Note
	Since the null hypothesis and the alternate hypothesis are precisely contradictory statements, only one can be true. Rejecting one is accepting the other.

#### Let's check our understanding with a few examples

**Example 1**

My broadband company claims that the minimum internet speed they are providing is 150 Mbps. However, I suspect that they are not providing the promised internet speed.

Let's write the null and alternate hypotheses for this!

$$
\mathbf{H}_\mathbf{0}: speed \ge 150 Mbps
$$

$$
\mathbf{H}_\mathbf{1}: speed < 150 Mbps
$$

**Example 2**

The project manager claims that his team resolves the software defects raised within five business days. I being the quality department manager, think it is taking longer to fix the bugs. 

Can we write the null and alternate hypothesis for this?

$$
\mathbf{H}_\mathbf{0}: Resolution\space  period \le 5 days
$$

$$
\mathbf{H}_\mathbf{1}: Resolution\space period > 5 days
$$

#### Let's see how we can prove the alternate hypothesis

**Example 1**

To check the internet speed, I visit [Speed Test](http://speedtest.net) from my home computer and measure the speed. I do this 'n' number of times and find that the mean speed is around 100 Mbps.

So we reject the null hypothesis and accept the alternate hypothesis - which is the internet speed is less than 150 Mbps

**Example 2**

To verify the project manager's claims, I take all of the five projects managed by him. He is relatively new to the project manager role and has only managed five projects so far.  I get the bug details from the bug tracking system - Bugzilla / Jira, for example.

I compute the mean of all the bug resolution time by doing some computations ( calculate the difference between the bug start date and bug end date and so on). I find that the resolution time is indeed less than five days.

So we accept the null hypothesis here i.e., resolution time is less than or equal to 5 business days.

Wow, Hypothesis testing is straightforward and easy! 

### Level of significance

Life is not always easy; Isn't it?

In the above two cases, taking the samples was easy, and our agreement/rejection of the null hypothesis was indeed accurate.

In real-life scenarios, we need to estimate a population parameter based on the sample, and things might go wrong. That is to say, we might reject the null hypothesis when it is true, or we might accept the null hypothesis when it is otherwise. It depends on the sample we take, and if we don't have enough samples (or worse picked up wrong samples), things might go wrong.

Say, for example, the null hypothesis states that the mean of the population is greater than or equal to 500 i.e. 

$$
 \mathbf{H}_\mathbf{0}: \mu \ge 500
$$

and the alternate hypothesis is mean less than 500

$$
 \mathbf{H}_\mathbf{1}: \mu < 500
$$

Let's say we took a sample size of 30 i.e, `n=30` and found the mean is `499`. 

Ah! Now comes the dilemma - whether we need to accept or reject the null hypothesis? The sample mean is just falling short by one from the population mean.

We go into self-doubt if we have taken the correct sample size or what happens if I increase the sample size or worst case, should I have to repeat the experiment once again and my manager reprimands me for wasting time and effort?

So, we are contemplating the probability of the evidence (samples picked) being unfavorable to the null hypothesis. 

This probability is known as the _p-value_

If we say the _p-value_ or probability is `2%`, our sample has `2%` chances of going wrong in rejecting the null hypothesis.

If we say the _p-value_ or probability is '30 %`, our sample has '30 %` chances of going wrong in rejecting the null hypothesis. Our chances of getting a promotion will impact adversely.

We are humans, and we need to have a leeway (a threshold) for making some mistakes/errors with the samples. 

This threshold is called the **level of significance**

In other words, **level of significance** is the maximum level of risk (maximum acceptable probability - in statistical terms) that we may take in rejecting the null hypothesis while the null hypothesis is correct. 

Level of significance is denoted by the letter $\alpha$ (alpha)

`alpha` is normally represented as `1%` or `5%` or '10 %` etc. 

#### Let's consolidate our understanding!

1. if the _p-value_ is less than the _level of significance_, we reject the null hypothesis.
2. if the _p-value_ is higher than the _level of significance_, we accept the null hypothesis.

Confused? Yeah, it happened with me too.

#### Proof for the 1st statement

Let's say the _p-value_ is `2%`, and the _level of significance_ is `5%`. What does this mean?

It means the probability of getting our samples wrong is `2%`, but the maximum risk that we can take is `5%`. Correct?

_Remember our quest is always to prove the null hypothesis is wrong_. In this case, our samples are within the permissible limits of going wrong, and hence we reject the null hypothesis.

#### Proof for the 2nd statement

Let's say the _p-value_ is `10%` and the _level of significance_ is `5%`. What does this mean?

It means the probability of getting our samples wrong is `10%`, but the maximum risk that we can take is `5%`. Correct?

In this case, our samples are above the permissible limits of going wrong, and hence we cannot reject the null hypothesis and have to accept the null hypothesis.

### Confidence level 

When the null hypothesis is rejected with a level of significance of `5%`, we may be asked how confident we are in rejecting the null hypothesis.

In other words, it is to say that what is our confidence level in rejecting the null hypothesis. 

The formula below gives the relationship between confidence level and the level of significance.

$$
confidence \space level = (1 - \alpha)
$$

which in this case is

$$
confidence \space level = (1 - 0.05) \space = 0.95
$$

which means we need to have at least a 95% confidence level to reject the null hypothesis.

### Summary

To summarize, we have seen what hypothesis is, what is a null hypothesis, what an alternate hypothesis is, and when hypothesis testing can go wrong. I hope this introduction to hypothesis testing gave you a solid understanding of the fundamentals on which you can build upon.

Thanks for reading! If you enjoyed reading this article, consider subscribing to our newsletter below. We will notify you on the latest content published on datasciencia.

{{< alert info "Next part in the series">}}
- [Part 2 - How to do hypothesis testing](../how-to-do-hypothesis-testing/)
{{< /alert >}}

