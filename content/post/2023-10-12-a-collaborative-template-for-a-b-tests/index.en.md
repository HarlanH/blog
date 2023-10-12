---
title: A Collaborative Template for A/B Tests
author: Harlan Harris
date: '2023-10-12'
slug: a-collaborative-template-for-a-b-tests
categories:
  - professional
tags:
  - a/b testing
  - product
  - data science
description: |
  Why a standard text document for collaborating on A/B tests is important,
  and an example template that I've used successfully.
featured: yes
draft: no
toc: no
usePageBundles: no
codeMaxLines: 10
codeLineNumbers: no
figurePositionShow: yes
showRelatedInArticle: no
---

As I've [written about before](https://www.harlan.harris.name/2022/08/communicating-a-b-test-results-for-conversion-rates-with-ratios-and-uncertainty-intervals/), as a data scientist supporting a product or marketing team with A/B testing, the job is *communication* -- helping to translate between business requirements and what we can learn from statistics. I ([and many, many others](https://www.google.com/search?q=a%2Fb+testing+document+template)) have found that there is a lot of value in having a document, shared among the team that is running the test. Some A/B testing tools include some limited workflow for collaboration on testing (e.g., [Amplitude Experiments](https://amplitude.com/amplitude-experiment) has pre-test, monitoring, and results tabs with useful graphs and summary statistics), but I think the most important thing is to have a tool that helps the team *get aligned* by forcing them to *write things down*.

I'm including below a template that I've used in the past. It's a simple collaborative document that you could put into Google Docs or Confluence or Notion, and just make copies for each A/B test. It is intentionally not part of the A/B testing tool, as it needs to be accessible to everyone, including external business stakeholders, in a familiar way. I'm going to annotate each section with some motivation -- why I think that it's important for the team (say the Data Scientist or Analyst, Product Manager, and Engineers on a team) to all work together on this document.

------------------------------------------------------------------------

# Design 🧪

## Problem statement 🔎

*What pain are we solving for our users? What are we trying to learn? Motivations and assumptions behind this change?*

> In terms of the structure of this document, first of all, emojis are important. They add an element of how you're supposed to *feel* in each section, which is motivating. Plus they're fun. Second, having these italicized prompts I've found to be super-helpful. Otherwise it's too easy to just type in a few words without thinking through *why* we're doing what we're doing.
>
> For this specific introductory section, it's important for everyone to understand not just what we're doing, but *why* -- why we think a specific change may help users, or tell us something about their desires and behavior. Also, asking for assumptions is important, as the process of identifying them may raise issues about the design of the experiment even before it starts, which will save time!

## Data 📊

*Add supporting insights here. What do we already know about user behavior?*

> Most A/B tests don't happen in a vacuum. Maybe we've run previous tests, or interviewed users, or analyzed funnels. What numbers do we have already that will ground the results? Do we have data that makes us optimistic about a change?

## Hypothesis 💡

*We expect that by changing X, we will cause user behavior to change to Y, yielding metrics impact Z.*

> This is critical -- we need to have a guess about a mechanism that we're changing, and we need everyone to understand it. It also helps the team understand what's *plausible,* in terms of outcome metrics.

## Primary Metric 📈

*What metric will we use to make a decision, once the experiment is complete? (link to a graph of the metric's recent historical trends) (link to prior experiments that attempted to move this metric)*

> Everyone involved in an A/B test needs to have good intuitions about the primary metric that you're trying to move. How much does it vary over time? What causes it to vary? How much has the team been able to move the metric in the past? Dropping in these links, and reviewing them frequently, help develop this intuition.

## Secondary and Guardrail Metrics 📈

*What other metrics will we be tracking? What metrics might block a release, if they decrease substantially, even if the primary metric is as we hoped?*

> I highly recommend [Kohavi et al.'s treatment of Guardrail metrics](https://www.google.com/books/edition/Trustworthy_Online_Controlled_Experiment/Gu-CEAAAQBAJ?bshm=rimc/1), based on decades of collective experience running A/B tests. It is likely that changes will introduce unintended side-effects, so you need to track many things in almost any A/B test.

## Variants 🆎

*Add visuals and description of the control experience and all variants, and/or link to the PRD.*

> Some A/B tests will be supporting a change that has been described previously in a Product Requirements Document. Others will be simple cosmetic changes, where just screen shots of what's changing are adequate.

## Targeting 🎯

*Which users will be part of this experiment? Who should be excluded? (platforms, segments, etc) Will the analysis be segmented? (That is, will any user sub-groups be looked at separately?)*

> You need to agree on this in advance. Although you *should* do post-hoc analyses, to learn as much as possible, you really want to make *decisions* based on criteria you've determined in advance. Who is part of the experiment, and what differential impact on different sub-groups might mean, needs to be part of that discussion. For instance, what if your change increases a metric overall, and for new users, but hurts it for returning users? Do returning users matter more? This ties into the next section:

## Decision Plan ⚖️

*What outcomes will lead to what decisions? Who is involved in the decision, and who is the final decision-maker? Is this a Superiority, Bias-to-Ship, Agnostic, or other type of decision?*

> See [The Five Types of A/B Test Decision](https://www.harlan.harris.name/2023/07/the-five-types-of-a-b-test-decisions/) for more on these types.
>
> It's important to know who will be making the call, and to plan ahead for various scenarios. What if your results are ambiguous? What if a key guardrail metrics is trending down? The more you can plan ahead, the faster you can move once data is in. And [fast decisions is the whole game](https://benn.substack.com/p/method-for-measuring-analytical-work).

# Rollout 🚀

## Allocation 💯

*How will we split users and/or ramp up?*

Off group (not in the experiment)

-   Variant name: off
-   Percent:

Off_Control group (in the experiment, control condition)

-   Variant name: off_control
-   Percent:

On group (in the experiment, test condition; add more groups if testing more than one thing)

-   Variant name: on
-   Percent:

> This is an important technical detail. If you're planning to ramp up the experiment, perhaps first exposing a small proportion of users to ensure that the code is working properly, then you *must* have a three-condition experiment. Users who were in the Off group initially should get re-bucketed to Off_Control or On randomly, once you've ramped up, but the users who were in those groups initially should not get re-bucketed.
>
> If you don't, and you start with (say) a 5/95 split, then move to 50/50, you lose several things. You can no longer easily determine if your A/B split is working correctly. To the extend that the effect of your change varies over time (perhaps weekends vs weekdays), you may well end up with biased and hard to understand results. And some users may switch from Off to On, which can also confuse your results. I believe that all standard A/B testing tools handle this correctly, but be careful if you're using a home-grown feature-flagging system.

## Power Analysis ±

*(may be customized by data science, depending on the experiment design and decision plan)*

Estimated weekly traffic exposed to the experiment (all variants):

Decision requirements for this metric:

Number of weeks required:

Link to analysis:

> Before the experiment, a data scientist (or well-trained analyst) should analyze the key metric and how it's expected to be affected, and perform a power analysis. This could be as simple as using an on-line calculator, or it may require a custom analysis and simulation. The "decision requirements" are based on the type of A/B decision (see the Five Types post), but are generally a threshold for a change in the metric. It's important that everyone agrees on how long the experiment is to be run for.

## Monitors 🚨

*How will we ensure that data is flowing, the A/B split is correct, etc? link/embed tracking charts*

> This could be to the A/B testing tool you're using, or to a dashboard based on your data warehouse. But regardless, it's important to peek in those first few days, to make sure that everything is working as expected. But don't expect to learn much if anything about your metrics -- those will bounce around a lot before settling down!
>
> I generally recommend only peeking to determine if you need to stop an experiment that's actively *hurting* metrics. A good time to do that is often after 1 week, when you've had a full weekday/weekend cycle. Otherwise, waiting until the planned duration has completed will maximize the likelihood that you make the correct decision.

# Learn 🎓

## Experiment Results 📈

*Impact to primary metrics for test. Describe and show results, then fill out the list.*

> This is where you'll describe what happened. I've found it useful to put charts and graphs and statistics here, but it's also important to have a standard, consistent format for the results:

-   **Dates**: January 1, 1970 - January 15, 1970

-   **OEC**: Furlongs per Fortnite

-   **Outcome Consistent Interval**: -10.0% - +5.0%

-   **Decision**: Roll back

> When did we run this test, what was the Overall Evaluation Criteria, what was the uncertainty/confidence/plausible interval on the change to the OEC, and what did you decide to do. Every test must have something like this. It's often a good idea to export this table into a spreadsheet or something, so you can easily see the results of all of your tests. (In Confluence, you can do this sort of automatically with Table Excerpt macros!)

## Insights 🕵️

*Secondary metrics and emergent behavior. Other learnings such as usability, segment trends, traffic shifts, etc.*

> You didn't just make a decision, you probably learned something about your users. That's valuable information for your company. Write it down.

## Next Steps ⏭️

*Action items, such as roll out winner, additional user testing, iterations on winning (or losing) variant, retest, etc.*

> Almost every test I've been a part of has led to, at a minimum, ideas for other things that could be changed.

# Appendix 📖

## Resources and notes 📝

*Any links to Figma, Jira, Docs etc?*

## Development details 💻

*Worrisome edge cases, dependencies, tradeoffs made, teams impacted -- link to technical design doc(s)*

> Some A/B tests are easy to implement. Others aren't, or have downstream impact. You probably want to document this.

------------------------------------------------------------------------

That's the document! You are more than welcome to use it within your organization. Please let me know about your experience, whether having a consistent, non-jargon-y template helped your team get aligned, and whether you ended up making useful changes!
