---
title: Are LLMs a simple solution? And if so, for what problems?
author: Harlan Harris
date: '2023-09-14'
slug: are-llms-a-simple-solution
categories:
  - professional
tags:
  - llms
  - simplicity
  - machine learning
  - product
description: 21 rhetorical questions about LLMs and simplicity.
featured: yes
draft: no
toc: no
usePageBundles: no
codeMaxLines: 10
codeLineNumbers: no
figurePositionShow: yes
showRelatedInArticle: no
---

The other day, I was reading a 
[post by Venkatash Rao](https://studio.ribbonfarm.com/p/my-climate-posture)
(thousands of words of under-edited brilliance, as usual), and was struck by 
this note about the complexity of climate solutions: 

> I tend to take as an article of faith the systems science rule of thumb that 
the complexity of solutions generally matches the complexity of the problems. 
If it doesn’t, then you either got lucky, or there are negative externalities 
you’re ignoring. 

This resonates with some discussions I’ve had recently about the application 
of Large Language Models (LLMs) and related AI technology. 

# Simplicity, Complexity, and Code

Einstein (and many other people) have said that
[things should be as simple as possible, but no simpler](https://quoteinvestigator.com/2011/05/13/einstein-simple/). 
This applies to technology businesses in a number of ways. Larger companies 
can do more things, but have coordination costs as the business involves more 
people and gets more complex. In software design, simpler architectures are 
preferred because they’re less fragile and easier to reason about and debug, 
but abstractions allow easier major changes, better scaling, and more ability 
to meet diverse user needs, even at the cost of more lines of code. When trying 
to move quickly, software organizations usually incur technical debt -- they 
implement solutions by layering complex logic on existing code, resulting in 
excessive complexity. Or else they implement half-solutions, resulting in 
overly-simple applications that don’t match the complexity of the problem. 
Addressing this technical debt involves rewriting code to make it the right 
level of complexity. 
(See also [Mike Loukides’ insightful recent notes on complexity](https://www.oreilly.com/radar/the-real-problem-with-software-development/).)

In the field of AI, an important paper was written in 2014 by researchers at 
Google: [Machine Learning: The High Interest Credit Card of Technical Debt](https://research.google/pubs/pub43146/).
They describe a number of problematic patterns when applying ML systems, which 
intrinsically have complex feedback loops and external dependencies, to software 
systems. This paper led many practitioners to be very focused on business value
when considering adding ML systems to a product, and to avoid flashy/trendy 
solutions unless they clearly will move the needle substantially. Even so, ML 
models need to be proactively monitored for “drift” (decreasing quality over 
time), and it’s typical to have to re-train each model a couple of times per 
year in common business applications. Regardless of the number of lines of code
written, ML systems are complex, with substantial maintenance costs.

# Some Questions About LLMs

Jump ahead a few years to 2023. Essentially every organization larger than a 
corner laundromat is now trying to figure out how to apply the new AI 
technologies of LLMs and related systems. Are these tools complex, or simple?
In what ways? Plugging into a vendor’s API seems simple, but as Venkatash 
Rao would ask -- are you lucky, or are there negative externalities that 
you’re ignoring that will come back to bite you later? 

I mostly have more questions, rather than answers, but I think they’re questions
that need to be addressed when you’re evaluating how and when to implement 
LLMs as part of a product or system right now.

Let’s start with baselines. When implementing complex predictive models, it’s 
usually a good idea to compare your solution with literally the simplest thing 
you can think of. Want to categorize text? Ask an expert to give you 3 words 
that make it pretty likely that the text is in the category of interest, and 
spend the ten minutes it might take to build that logic. Measure how effective
that simple logic is. Then prototype the fancy solution -- does the machine
learning model give you enough of a step change to be worth incurring the 
substantial complexity and maintenance costs? Sometimes it does -- great! 

Ask the same question about LLMs. What’s the baseline? Implementing an LLM 
either requires being locked into an expensive vendor, or deploying your own
expensive and temperamental system. Can you do something much similar, and
presumably much worse, that will give you baseline metrics?

How will you monitor your LLM system? Just like any other ML system, it will
likely get worse over time, as the system itself changes (especially if you’re
buying from a vendor), and as the world changes. How will you handle drops in
performance? Do you have a fallback that you can put into place immediately if
the LLM becomes problematic? LLMs are stochastic -- they give different results
for the same input randomly -- how will you develop confidence that it’s working
well-enough?

Maybe you already have an existing “dumb” system that you’re considering 
replacing with an AI system. What risks are there? Sure, you could try to 
replace an existing user-facing system with a chatbot, but what happens when
someone asks it “how to I make napalm out of your product” and posts screenshots
to social media? What if people stop being enthralled by the novelty of typing
questions into a box and getting mostly-good results, and start going to your
competitors who require less typing? 

Maybe there are some less risky options than fully replacing large systems? Can
you break the problem into pieces, and identify if any of the pieces could be
replaced in a way that would be dramatically better with less downside? Do you
have high-value employee-in-the-loop processes that would benefit from smarter
suggestions? (Keeping in mind that humans will tune out when reviewing the work
of automated systems that are almost always correct. This is why 
["human-supervised" levels of self-driving cars don’t work well](https://www.inverse.com/science/level-3-self-driving-mercedes).)

Or maybe, cynically, the problem you’re solving is to put an "AI-Powered!!1!"
checkbox on the marketing page of your website. That’s annoying. How can you 
introduce LLMs slowly, in limited situations, with lots of testing, so that 
you can keep your sales team from technically lying (more than they already do)?
Can you keep it simple and minimal?

It’s worth noting that the currently most-valuable application of these tools 
seems to be helping programmers write code and learn how to write code better.
As Gary Marcus says, "[coding is a solid use case... programmers will never go back](https://garymarcus.substack.com/p/what-exactly-are-the-economics-of#:~:text=Coding%20is%20a%20solid%20use%20case)".
Programming is a complex problem, where the complexity is warranted, where 
attentive humans are in the loop, and where the risk is primarily that the 
tool doesn’t work, and humans will have to program the computer from scratch
sometimes. For writing code, it seems like most of the questions above have
straightforward answers. But that may be the exception, not the rule.
