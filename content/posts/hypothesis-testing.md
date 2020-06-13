---
title: "Hypothesis Testing"
date: 2020-04-11T00:12:52+05:30
tags: [ab-testing, statistics]
image: "images/featured-post/post-1.jpg"
---

## What is Hypothesis Testing?

First let us understand what does the word _hypothesis_ mean. Let us break the word into two parts _hypo_ + _thesis_. 

What does _thesis_ mean?
_thesis_ means something that has already been proven to be true. 
e.g Atleast 60% of the adult human body is made up of water.

Sounds fine!

So what does _hypothesis_ mean?

Hypothesis is something that is **not yet** been proven to be true.

Let's come back to the original question! What is hypothesis testing?

Can we say that it is the testing of hypothesis or more precisely _the process of determining whether a given hypothesis is true or not_

To sum up, we take the hypothesis, we perform some statistical computations and prove if the hypothesis holds true or not.

## Null Hypothesis & Alternate Hypothesis

Null hypothesis is the _assertion or belief that we hold as true_ unless we have sufficient evidence to prove otherwise.

In statistical terms, we say it as _the belief we hold about the value of a population parameter_ 

!!! Remember
	Parameter is for the population and Statistic is for the sample

Let's take an example and see what is the null hypothesis and how it is written.

We believe that the mean of the population is `500`. Unless we obtain sufficient evidence that it is not `500`, our belief holds true i.e we accept that the mean is `500`

So we can write it as `null hypothesis: mean = 500`

To write it more compactly, we can represent the same thing as $ \mathbf{H}_\mathbf{0} : \mu = 500 $

where the symbol $\space\mathbf{H}_\mathbf{0}$ denotes Null hypothesis.

The _opposite_ of Null hypothesis is called as _Alternate Hypothesis_. That is, the _negation_ of the null hypothesis. 

If there is a way to represent the null hypothesis, then there should be a way to represent the alternate hypothesis. Agreed? Ah, I see I have quoted a null hypothesis there!

$\mathbf{H}_\mathbf{1}: \mu \ne 500$

where the symbol $\space\mathbf{H}_\mathbf{1}$ denotes alternate hypothesis

!!! Note
	Since the null hypothesis and the alternate hypothesis are exactly opposite statements, only one can be true. Rejecting one is accepting the other.

#### Let's check our understanding with a few examples

**Example 1**

My broadband company claims that the minimum internet speed they are providing is 150 Mbps. However, I suspect that they are not providing the promised internet speed.

Let's write the null and alternate hypothesis for this!

$$
\mathbf{H}_\mathbf{0}: speed \ge 150 Mbps
$$

$$
\mathbf{H}_\mathbf{1}: speed < 150 Mbps
$$

**Example 2**

The project manager claims that the software defects raised are resolved within 5 business days. I being the quality department manager think it is taking longer to fix the bugs. 

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

To verify the claims of the project manager, I take all of the 5 projects managed by him. He is relatively new to the project manager role and has only managed 5 projects so far.  I get the bug details from the bug tracking system - bugzilla / jira for example.

I compute the mean of all the bug resolution time by doing some computations ( calculate the difference between the bug start date and bug end date and so on). I find that the resolution time is indeed less than 5 days.

So we accept the null hypothesis here i.e. resolution time is less than or equal to 5 business days.

Wow, Hypothesis testing is very easy! 

### Level of significance

Life is not easy always, Isn't it?

In the above two cases, taking the samples was easy and our agreement / rejection of the null hypothesis was indeed accurate.

In real life scenarios, we need to estimate a population parameter based on the sample and things might go wrong. That is to say, we might reject the null hypothesis when it is actually true or we might accept the null hypothesis when it is otherwise. This depends on the sample we take and if we don't have enough samples (or worse picked up wrong samples), things might go wrong.

Say for example, the null hypothesis states that the mean of the population is greater than or equal to 500 i.e. 

$$
 \mathbf{H}_\mathbf{0}: \mu \ge 500
$$

and the alternate hypothesis is mean less than 500

$$
 \mathbf{H}_\mathbf{1}: \mu < 500
$$

Let's say, we took a sample size of 30 i.e `n=30` and found the mean is `499`. 

Ah! now comes the dilemma - whether we need to accept or reject the null hypothesis? The sample mean is just falling short by 1 from the population mean.

We go into self-doubt if we have taken the correct sample size or what happens if the sample size is increased or worst case, should I have to repeat the experiment once again and my manager fires me for wasting the time and effort?

So, what we are contemplating here is the probability of the evidence (samples picked) being unfavorable to the null hypothesis. 

This probablility is called as the _p-value_

If we say the _p-value_ or probability is `2%`, it means that our sample has `2%` chances of going wrong in rejecting the null hypothesis.

If we say the _p-value_ or probability is `30%`, it means that our sample has `30%` chances of going wrong in rejecting the null hypothesis and our chances of getting a promotion will be adversely impacted.

But, we are humans and we need to have a leeway (a threshold) for making some mistakes / error with the samples. 

This threshold is called as the **level of significance**

In other words, **level of significance** is the maximum level of risk (maximum acceptable probability - in statistical terms) that we may take in rejecting the null hypothesis while the null hypothesis is actually true. 

Level of significance is denoted by the letter $\alpha$ (alpha)

`alpha` is normally represented as `1%` or `5%` or `10%` etc. 

#### Let's consolidate our understanding!

1. if the _p-value_ is less than the _level of significance_, we reject the null hypothesis.
2. if the _p-value_ is greater than the _level of significance_, we accept the null hypothesis.

Confused? Yeah, it happened with me. If not, I salute you.

#### Proof for the 1st statement

Let's say the _p-value_ is `2%` and the _level of significance_ is `5%`. What does this mean?

It means the probability of getting our samples wrong is `2%`  but the maximum risk that we can take is `5%`. Correct?

_Remember our quest is always to prove the null hypothesis is wrong_. In this case, our samples are within the permissible limits of going wrong and hence we reject the null hypothesis.

#### Proof for the 2nd statement

Let's say the _p-value_ is `10%` and the _level of significance_ is `5%`. What does this mean?

It means the probability of getting our samples wrong is `10%`  but the maximum risk that we can take is `5%`. Correct?

In this case, our samples are above the permissible limits of going wrong and hence we cannot reject the null hypothesis and have to accept the null hypothesis.

### Confidence level 

When the null hypothesis is rejected with a level of significance of `5%` , we may be questioned of how confident we are in rejecting the null hypothesis

In other words, it is to say that what is our confidence level in rejecting the null hypothesis. 

The relationship between confidence level and the level of significance is given by the relation

$$
confidence \space level = (1 - \alpha)
$$

which in this case is

$$
confidence \space level = (1 - 0.05) \space = 0.95
$$

which means, we need to have atleast 95% confidence level to reject the null hypothesis.

### Summary

To summarize, we have seen what is hypothesis, what is a null hypothesis, what is an alternate hypothesis and when hypothesis testing can go wrong.

In the class, we have not seen the level of significance in detail and what important role it has in hypothesis testing. The last part of the article was included to make this grey area more clearer.



