---
title: LLMs and Theories of Consciousness
author: Harlan Harris
date: '2023-09-03'
slug: llms-and-theories-of-consciousness
categories:
  - professional
tags:
  - cognitive science
  - consciousness
  - llms
description: |
  A speculative method for adding rudamentary consciousness to LLMs,
  leveraging the work of two prominent cognitive scientists.
featured: yes
draft: no
toc: no
usePageBundles: yes
codeMaxLines: 10
codeLineNumbers: no
figurePositionShow: yes
showRelatedInArticle: no
---

There’s been an immense amount of discussion about Large Language Models (LLMs) 
such as ChatGPT over the last year, of course. Some of that discussion has been 
whether they are intelligent, conscious, or on the path to Artificial General 
Intelligence.

I’m particularly interested in the "consciousness" question, as it was an area 
of personal interest when I was working as a cognitive scientist, in a prior 
career. I never did research on the topic, but I read plenty of philosophers of 
mind and neuroscientists as they tried to pin down what, exactly (or even 
vaguely), consciousness might be. One of my favorite treatments of the topic is 
by neuroscientist Antonio Damasio, most accessibly covered in his book 
[The Feeling of What Happens](https://www.google.com/books/edition/The_Feeling_of_what_Happens/RSOPDHP9QekC).
(I recently read a new collection of short essays by him, entitled 
[Feeling & Knowing](https://www.google.com/books/edition/Feeling_Knowing/1KrpDwAAQBAJ),
but I wouldn’t recommend it. It feels more like footnotes or stray thoughts than
a coherent presentation or a novel contribution.) 

Damasio makes a number of claims, a few of which I’ll try to briefly summarize 
here. I think that it’s worth thinking about LLMs in the context of theories of
mind and consciousness, to clarify what those systems are actually doing (or not
doing), and what it might take to tentatively bridge the gap. In some ways, 
LLMs seem conscious, in that they behave in a way that, if a human did that, 
we would say that they were conscious.

Damasio’s core ideas are as follows (Wikipedia has a 
[good summary](https://en.wikipedia.org/wiki/Damasio%27s_theory_of_consciousness)):

* Intelligence is a low bar. Any system that reacts in a self-beneficial way to
both external stimuli and what he calls "homestatic" signals is behaving
intelligently. Homestatic signals are internal body signals about the chemical
and physical health of the body, such as whether blood chemistry, temperature,
or other systems are within bounds, or if the body has been damaged. 
Single-celled animals are, under this view, intelligent. 
* Consciousness is based on a lower-level capability, which is the ability to 
_represent_ (remember) the homeostatic signals in some form, rather than just 
react to them. When humans have a _feeling_ that they are cold, or thirsty, or 
in pain, then they are representing these signals as having a relationship to
the _self_. So, it seems likely that most animals are conscious.
* Human-level intelligence and consciousness requires other systems, such as 
language, attention, and theory-of-mind. But those things aren’t required for 
basic consciousness.

David Chalmers, a philosopher and another prominent writer in the field, 
has recently been writing about 
[LLMs and consciousness](https://www.bostonreview.net/articles/could-a-large-language-model-be-conscious/).  He doesn’t believe it’s likely that current LLMs are conscious, and 
provides a half-dozen gaps that he suspects rule it out. But these gaps could,
in theory and likely practice, be addressed. 

Three of his gaps, two that he spends a few paragraphs on, and one that he 
mentions in an "and also" list, that I think get at the heart of what might be
required to build a minimally-conscious LLM model:
 
* First is a "global workspace", a "limited-capacity... central clearing-house 
in the brain for gathering information from numerous non-conscious modules and
making information accessible to them." LLMs don't really have this, although
systems such as ChatGPT have limited contextual memories that start to move in
this direction.
* Second is "unified agency" -- a conscious entity needs "stable goals and 
beliefs of their own over and above the goal of predicting text." ChatGPT has
constraints about what it's willing to generate, but its responses don't
generally appear to be from a single entity.
* Third is "stimulus-independent processing... thinking without inputs" -- 
you might call this a stream of thought or even a 
[stream of consciousness](https://en.wikipedia.org/wiki/Stream_of_consciousness_(psychology)).
When nobody is asking a LLM a question, it's basically _comatose_. No processing
is going on at all.

It might be that LLMs, because of their general-purpose nature, and their 
ability to summarize prompted text relatively well, could be used in a 
relatively simple system with these three capabilities and rudimentary 
consciousness. People have been building more-complex LLM-based systems with 
aspects of this already -- 
[Chain of Thought prompting](https://arxiv.org/abs/2201.11903) and 
[Tree of Thought](https://arxiv.org/abs/2305.08291) architectures already get 
at the idea of having processing be based on the composition of multiple 
prompt-response pairs. The goals of these systems has generally been to 
improve response accuracy, especially for reasoning tasks.

What if we focused on the consciousness-related gaps, rather than performance 
on any specific task? What would a simple LLM-based system with a global 
workspace, unified agency, and a stream of thought look like? 

Here's my completely untested proposal for such a system. 

* The system maintains 
a queue of something like 20 (50?) text statements, generated as described below. 
This is the global workspace. Old entries disappear as new ones are added.
* The system asks prompts of its _own_ global workspace, while also reacting to 
external prompts (potentially from multiple external sources/people). These 
prompts happen on a regular basis, perhaps every 10 seconds, regardless of 
whether external prompts are happening or not. 
* Those system-generated prompts might have several standard forms, perhaps 
something like:
  + What are the key things a conscious, intelligent agent motivated by 
  helpfulness, kindness, and a strong desire to avoid harm to humans or 
  humankind (abbreviated CIAHKAHH, for the purposes of this blog post, but presumably 
  spelled out in practice) would remember from the global workspace below?
  + What would a CIAHKAHH feel about the global workspace below?
  + What goals would a CIAHKAHH have, given the global workspace below?
* External prompts might get prefixed with the most recent responses to these questions: 
  + You are a CIAHKAHH with the following recent history: <global workspace>. 
  You have been asked the following question by human X. 
  Please respond accordingly. <prompt>
* The result would be summarized before being added to the list:
  + You are a CIAHKAHH with the following recent history. <global workspace> 
  Please summarize the below prompt and response into a two sentence summary 
  to be added to your recent history. X prompts: <prompt> You responded: <response>

The _unified agency_ is maintained by the mix of hard-coded goals in the 
standard prompts, and dynamic goals maintained in the global workspace. 
Different instances of this system would have different dynamic goals, based on 
experience, and thus different but unified agency. 
_Stimulus-independent processing_, the periodic self-referential queries of 
the global workspace, is key to making this all (I suspect) work reasonably coherently.

{{< figure src="consciousllmdiagram.png" title="Proposed LLM-based perhaps-conscious architecture" >}}

Are there independent reasons for having a consciousness system like this? 
That is, would consciousness be _adaptive_ for an intelligent system like a 
language model? It might! In particular, by having these hard coded goals 
(I’m reminded of [Asimov’s 3 laws of robotics](https://en.wikipedia.org/wiki/Three_Laws_of_Robotics)), a model 
like this might give more helpful answers, and might be less likely to 
provide problematic responses. 

What about risks? Unlike other approaches to extending LLMs, such as 
embedding/embodying them in the real world, or providing them access to 
external systems with real-world effects, it’s hard to imagine a system like 
this causing a great deal of harm. Certainly, with the hard-coded goals, it’s 
less likely to do so than a simple Google search, which will happily tell you 
[how to make home-made napalm](https://www.google.com/search?q=how+to+make+napalm&oq=how+to+make+napalm).
(Please don’t.) 

And what about obligations? Would it be murder to pull the plug on a system 
like this? I don’t think so. Most philosophers of mind are pretty sure that 
animals such as mice have consciousness (although almost certainly not based 
on any sort of language). Most humans set out mouse traps and eat relatively 
intelligent and conscious mammals without much guilt, and certainly without 
criminal charges. Also note that just because this system is based on language, 
doesn’t mean that it rises to human-level consciousness. It just so happens 
that we invented LLMs that are good enough to implement this sort of thing
before we invented the sort of highly complex multi-sensory systems that likely 
are required for consciousness in (say) mice.

Does this proposal make sense? I’m not deep in the cutting edge of LLM-based 
cognitive science right now, so if I’m restating ideas other people are already 
running with, or have already ruled out, please let me know!
