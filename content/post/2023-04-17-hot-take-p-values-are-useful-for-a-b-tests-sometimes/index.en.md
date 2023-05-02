---
title: 'p Values Are Useful for A/B Tests, Sometimes'
author: Harlan Harris
date: '2023-05-02'
slug: p-values-are-useful-for-a-b-tests-sometimes
categories:
  - professional
tags:
  - a/b testing
  - statistics
  - data science
description: Argues that for Superiority Decisions, classical NHST turns out to be a reasonable approach, despite the ASA statement criticizing p values.
featured: yes
toc: no
usePageBundles: no
codeMaxLines: 10
codeLineNumbers: no
figurePositionShow: yes
showRelatedInArticle: no
---

The "best practice", when evaluating the results of an online controlled experiment
(A/B test), is to use classical statistical tests, proceeding with a change
if (and only if) the result of the test includes a _p_ value of less than 0.05.
But, the American Statistical Association (ASA) said in 
[a prominent 2016 statement](https://www.tandfonline.com/doi/full/10.1080/00031305.2016.1154108) that 
"...business... decisions should not be based 
only on whether a p-value passes a specific threshold." Wait, what? Are we making
bad decisions from A/B tests? Should we stop using _p_ values and do something 
else? 

My answers are _yes_ -- we are too often making bad decisions, and _sometimes_ -- 
_p_ values are only useful for certain types of A/B test decisions. In this 
post, I'll talk about the specific decision pattern where _p_ values remain
a reasonable approach, taking the somewhat contrarian position of
defending them against the ASA's guidance (while still almost entirely agreeing
with everything else their statement says). 

# Why _p_ Values Are Bad

Let's back up. If you took one of those Introduction to Statistics classes,
you probably were taught a few things about "statistical significance", "p values",
and "null hypotheses." You probably know that before you run an experiment,
you do a "power analysis" to figure out how long you need to collect data for.
Then, after you run the experiment, you 
can plug the results into a formula to compute a value called _p_, and if that
number is less than 0.05, then the experiment was "statistically significant",
otherwise you cannot exclude the null hypothesis.
You might also know that this process was developed
in the first half of the 20th century to support academic science, especially
agricultural and medical research. The framework is called Null Hypothesis
Statistical Testing (NHST), and it is ubiquitous.

But you might not know how much pushback has happened in recent years. In 
2016, the American Statistical Association, the professional society for
statisticians in the US, published 
[a statement on _p_ values](https://www.tandfonline.com/doi/full/10.1080/00031305.2016.1154108). Here is the 
summary (bold added for the most important two points for our purposes):

1. P-values can indicate how incompatible the data are with a specified statistical model.
2. P-values do not measure the probability that the studied hypothesis is true, or the probability that the data were produced by random chance alone.
3. **Scientific conclusions and business or policy decisions should not be based only on whether a p-value passes a specific threshold.**
4. Proper inference requires full reporting and transparency.
5. A p-value, or statistical significance, does not measure the size of an effect or the importance of a result.
6. **By itself, a p-value does not provide a good measure of evidence regarding a model or hypothesis.**

If you're like most people I've worked with, marketers or product managers
or analysts, the above comes as a shock. Here we are, trying to make important
decisions about our business, and the experts are specifically saying that our
approach is bad! 

Why did the ASA say this? It's not because the _p_ value is being incorrectly
calculated, it's because in many cases it's doesn't _mean_ anything relevant
to the decision that's being made. What it does mean is the following somewhat
convoluted statement: it's the probability, if the experiment were re-run
again exactly the same way, and if in fact there was zero impact of the 
experimental manipulation, that the results would be as large or larger than
what was observed.

It's not clear at all how this confusing probability crossing an arbitrary threshold
is anywhere near the right way to decide whether to make a change to your
web site or app, or not.

# Decision Making in Science and Industry

There seems an interesting tension between the needs of practitioners in
modern organizations, and the problem that _p_ values were originally intended to
solve. Put simply, a low _p_ value, if you ran the experiment properly, means that
_probably something interesting is going on_. In science, that’s a great start -- it begins a
conversation that will take years to resolve, using replication, formal models
of mechanisms, and other methods of converging evidence. It's also worth noting
that in science, the goal is often to _estimate the impact_ of a change, or
of some parameter of the model. _p_ values only let you, best case, make an
argument that an effect size is non-zero. So yes, for science, treating 
_p_ < 0.05, on its own, as anything like conclusive or even particularly useful,
is inappropriate.

But in industry, we need to have
conversations about what data will mean for us _first_, 
then decide _as quickly as we can_ what to do once we have data. 
Taking years, or even weeks, to decide what to do with the results of an experiment
is not acceptable in almost any business. We need to take the results, then
use agreed-upon decision rules and communication patterns to move forward.

So, can we
find appropriate ways to use statistical tools to fit into the decisions and the
communication patterns that we need to have? I think we can. And in 
one particular type of A/B test, the NHST approach of a
_p_ value crossing a threshold may even be the right tool for the job.

# Superiority Decisions

Sometimes, when you're running an A/B test, you only want to roll out a new
experience if it is _almost certainly_ better than the existing experience.
This is a conservative decision, appropriate when the thing you're testing
is more expensive to maintain (or to fully build) than the control experience.
Perhaps you're adding a fancy and expensive recommendation module to a page, or you built
a quick-and-dirty version of a feature that won't scale, just for the test. 
This may not be the
most common type of A/B test that people run, but it certainly happens.
I like to call this a "Superiority Decision" test.

Before the experiment runs, you need to figure out, and as a team agree upon, 
two things -- how long to
run the experiment for, and how you'll make a decision based on the results
you see. Before jumping into statistics, let's frame these qualitatively: 

> We want to make a Superiority Decision. We want to run the experiment
until we're _quite likely_ to detect the _smallest positive impact_ that
would cause a rollout decision. Then, after we've collected the data, we
will roll out the change if statistics say that the treatment experience is 
_almost certainly_ better than the control experience.

I've found it extremely valuable to start with statements like this, getting
agreement among stakeholders, before the experiment begins. In particular, 
the _smallest positive impact_ value requires review of past experiments, 
discussion of cost-benefit tradeoffs, and a key decision to be made.

# Translating Business Decisions to Statistics

The statement above is essentially the classical NHST approach. For instance
you could set _quite likely_ to 80%, _smallest positive impact_ to 1% or whatever
seems appropriate for the experiment, and _almost certainly_ to 95%. By
agreeing on this, you can then use standard power analysis techniques
to determine how long to run the experiment, then use _p_ < 0.05 as the
decision criteria. 

(As I [discussed previously](https://www.harlan.harris.name/2022/08/communicating-a-b-test-results-for-conversion-rates-with-ratios-and-uncertainty-intervals/), although 
in _general_ _p_ < 0.05 does not mean "95% likely to be better", in the very 
simple case of a _t_ test for a properly-executed A/B test with adequate
power, it's very close,
and certainly adequate to mean "almost certainly better".)

When I've used this approach, I've paired this setup with standardized 
language around the decision, such as:

> It is almost certain that the New
Experience is better than the Control. The New Experience
is quite likely between 0.3% and 0.7% better.

The first sentence is based on the _p_ value being lower than the 0.05 threshold, 
but notably, I don't actually report the _p_ value itself in this summary.
Instead, I report uncertainty intervals around the expected change, 
as [discussed previously](https://www.harlan.harris.name/2022/08/communicating-a-b-test-results-for-conversion-rates-with-ratios-and-uncertainty-intervals/). This avoids all
of the confusion around what _p_ means, and avoids anchoring on point estimates or
other numbers, but behind the scenes, relies on the NHST pattern.

# On the ASA Statement

Returning to the ASA statement, here are my comments on each of their 
assertions:

1. P-values can indicate how incompatible the data are with a specified statistical model.

Agreed.

2. P-values do not measure the probability that the studied hypothesis is true, or the probability that the data were produced by random chance alone.

For very simple cases, which is what A/B tests are, _p_ values below a threshold
can be interpreted as an indication that we have knowledge that should allow us
to make a specific decision. Is this "true"? Maybe not, but it's still useful.

3. Scientific conclusions and business or policy decisions should not be based only on whether a p-value passes a specific threshold.

In some cases, such as the Superiority Decision described here, business decisions
should be made expediently based on pre-determined rules, which can be _p_
values below a threshold value. But in many other cases, other decision criteria
should be used.

4. Proper inference requires full reporting and transparency.

Yes, but proper reporting to non-statistically-fluent stakeholders also requires
not misleading them or burying them in jargon. As data scientists in industry,
we are hired for our ability to guide the business using the tools of statistics.
We should be intellectually honest without being offputting. Starting with
qualitative statements that everyone can agree on goes a long way in the right
direction.

5. A p-value, or statistical significance, does not measure the size of an effect or the importance of a result.

Completely true. If you have to mention _p_ values in a report, it's much
better to say _p_ < 0.05 than _p_ = 0.0034 or whatever, which will cause
stakeholders to say wince-worthy things like "very statistically significant."
Statistical significance (or, better, "reliability") just means that you've 
crossed a threshold that leads to a particular decision. You've pre-determined
the importance of the result, and you explicitly do not care, for a Superiority
Decision, how big the effect size is.

6. By itself, a p-value does not provide a good measure of evidence regarding a model or hypothesis.

Right, but it can be adequate for making a decision, specifically a Superiority
Decision. It's not a measure of evidence, just a criterion that lets us take
our win (or our loss) and move on.

