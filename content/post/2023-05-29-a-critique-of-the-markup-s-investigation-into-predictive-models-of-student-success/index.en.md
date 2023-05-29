---
title: A Critique of The Markup’s Investigation into Predictive Models of Student
  Success
author: Harlan Harris
date: '2023-05-29'
slug: a-critique-of-the-markup-s-investigation-into-predictive-models-of-student-success
categories:
  - professional
tags:
  - machine learning
  - journalism
  - predictive
description: |
  The Markup's investigation into student success models in Wisconsin
  missed some important context around the value of these models, how
  to incorporate race and ethnicity appropriately, and how to communicate
  around risk scores.
featured: no
draft: no
toc: no
usePageBundles: no
featureImage: images/classroom.jpg
featureImageAlt: empty classroom
figurePositionShow: yes
showRelatedInArticle: no
---

Recently, tech-journalism site The Markup ran a 
[long, detailed, critical investigation](https://themarkup.org/machine-learning/2023/04/27/false-alarm-how-wisconsin-uses-race-and-income-to-label-students-high-risk)
of a predictive machine learning model used by the State of Wisconsin to identify 
public school students at risk of not graduating.
I mostly agree with the conclusions of the piece -- the system appears not to 
be fit for purpose and needs to be substantially improved -- but I want to 
comment on several aspects of the model and the Markup’s reporting. Although I 
know nothing about the Wisconsin model beyond what is reported, I know a lot 
about predictive student success risk models, having led a team of data 
scientists who built related models used by colleges and universities when 
I worked at [EAB](https://eab.com/products/navigate/) from 2014 through 2016. 

The Markup describes the Dropout Early Warning Systems (DEWS), a system that, 
for each Wisconsin 6th through 9th grader, predicts whether the student is 
likely to graduate from high school on time. Through deep reporting and access 
to internal data, they were able to learn a great deal about how the system 
works, and importantly, how well it works -- or doesn’t -- as a whole, and for 
racial and ethnic minorities. 

Their [conclusions](https://themarkup.org/the-breakdown/2023/04/27/takeaways-from-our-investigation-into-wisconsins-racially-inequitable-dropout-algorithm) include 
"DEWS is wrong nearly three quarters of the time when it predicts a student 
won’t graduate on time" and "it’s wrong at significantly greater rates for 
Black and Hispanic students than it is for White students."

The three points I want to make are:

1. It’s worthwhile to build predictive models of student success as part of 
advising and support systems.
2. Getting these models to work well for racial and ethnic minorities is i
mportant but difficult work, and it seems like the DEWS model got it wrong.
3. Language and design matter, and both DEWS and The Markup seem to have 
confused notions of "accuracy" and "risk", and how to communicate about model 
predictions.

-----

1.

Why build these models in the first place? Because of limited resources. 
In a perfect world, every student would have enough attention from expert 
advisors to support them at every step in their educational journey, getting 
them the help and resources that they need, so that they are engaged, learn 
successfully, and graduate on time. Both in K-12 and higher education, though, 
budgets do not allow this sort of bespoke advising team, and stretched-thin 
advising staff must do their best to support students who voluntarily seek 
help, while also doing limited outreach to other students who could most 
benefit from their support. But who will most benefit? This is where models 
can help, by triaging students, identifying those who should get a deeper look, 
and perhaps identifying useful avenues for outreach.

The Markup describes how the origin of the DEWS model was to support efforts to 
improve graduation rates by racial and ethnic minorities in Wisconsin, an 
important goal, and potentially a cost-effective way to do so. As they report, 
"94 percent of White students graduated on time last year, [but] only 82 
percent of Hispanic and 71 percent of Black students completed high school in 
four years." Something needed to change. However, it’s clear that the resulting 
model, and the system it is part of, is not helping the state build an 
equitable education system. Hopefully the attention the DEWS system is getting 
now, as a result of this reporting, will lead to improvements, and soon.

2.

Much of the article describes how the system is less accurate for racial and 
ethnic minorities. They include a quote from a state employee involved in the
system: "the model... over-identifies Black, Hispanic and other students of 
color among the non-on-time graduates." That is, the model is _mis-calibrated_. 
Ideally, if this model were to say that 100 students are each 75% likely to 
graduate on time, then around 75 of those students should do so. In this case, 
it seems like the actual graduation rate for minority students with this risk 
score is _higher_ than 75%, so those students are getting inappropriately flagged. 

With models of this sort, it’s tempting to say "don’t use race or ethnicity as 
a predictor in the model". The Markup quotes a professor who says "...[t]hey 
had demographic factors as predictors and that’s going to overemphasize the 
meaning of those variables and cause this kind of effect." But ignoring race, 
ethnicity, or other correlated factors doesn’t make those factors, or the 
history of white supremacy, go away. In fact, it’s sometimes better to _use_ 
those factors, but carefully. 

The problem arises when the model is too simple, if it treats factors as 
information that gets _added_ together, along the lines of those "you might be 
at risk for a heart attack: 3 points if you’re over 60, 2 points if you have 
high blood pressure, etc." simple models you sometimes see in magazines. 
Learning from historical data, it’s easy for the model to improperly conclude 
that being non-white reduces your likelihood of graduation, yielding scores 
that are too low. A better approach is to identify _other_ factors that may 
be _differentially_ important based on a student's race or ethnicity, and let 
the model estimate those "interaction" effects. In higher ed, for instance, 
it’s important to look at SAT or ACT scores in conjunction with race, because 
of [known issues](https://psycnet.apa.org/doiLanding?doi=10.1037%2Fedu0000104) 
with those tests. Equally skilled minority students 
[often get lower scores](https://www.brookings.edu/blog/up-front/2020/12/01/sat-math-scores-mirror-and-maintain-racial-inequity/) because of factors such as limited access to 
expensive prep classes. Everything else being equal, in some cases, a minority 
student with the same SAT score as a white student might be more likely to graduate!

Including race and ethnicity actually makes the models better, if you do so the 
right way, leveraging knowledge of how the world works and what the data means. 
A race-aware algorithm might treat SAT or ACT scores as less informative and
predictive for non-white students, or might apply a correction to counteract the
known bias. It’s pretty clear, from The Markup’s reporting, that DEWS and the 
State of Wisconsin did not try to do this.

3. 

The Markup repeatedly makes statements such as "[DEWS] was wrong nearly three 
quarters of the time it predicted a student wouldn’t graduate on time," 
implying that the model is fundamentally flawed. But this issue is not about 
the model at all, it’s about the _language_ used to describe the predictions. 

The predictive model is only part of a larger system that also includes the 
human administrators who use the model’s scores to take action, or not. And 
humans aren’t great at interpreting numerical scores. So, a reasonable decision 
was made to discretize the 0-100 probability score (which, as described above, 
is well-calibrated if, when you take all of the students with a score of 80, 
80% of them later graduate) into red/yellow/green risk categories, where in 
this case the red/yellow boundary is at 78.5. Given that most students in
Wisconsin graduate, it's probably reasonable to put a category boundary there, 
but only if the categories are described appropriately.

If you take a student with a score of 75 (indicating that you estimate that of 
100 very similar students, 75 will graduate), and give them a "red" score, 
it’s _critical_ that you _not_ call this "high risk", even if the student is 
in the riskiest group. Anybody unfamiliar with the technical details will 
assume that "high risk" means "very likely will not graduate," which is 
incorrect in this case. Instead, all of the messaging around the model should 
be carefully designed to match peoples’ 
[intuitive understanding of qualitative terms](https://en.wikipedia.org/wiki/Words_of_estimative_probability). 
A score of 75 means that the student _will likely graduate_!

Additionally, it’s important to avoid self-fulfilling prophecies, where the 
language used suggests that nothing can be done to improve a student’s odds or 
outcome. It’s too easy to interpret phrases like "high risk" as being an 
essential and unchanging part of a student’s being, not something that can and 
will change over time, or that could be changed with effort. Ideally, the model 
should be identifying students _who would benefit_ from additional support, 
and describing them as such. I would recommend, in this case, using terms such 
as "needs support" or "investigate" instead of "high risk". These terms should 
be used consistently in the system’s user interface, in training, and elsewhere. 

And, if the threshold is indeed at 78.5, maybe red isn’t the right color? Red 
implies "something is on fire", but a student who is currently 75% likely to 
graduate maybe just be yellow? Or maybe use an emoji like 👀 instead of a color,
to indicate that it’s worth watching and supporting this student closely? 
Design decisions like this can drastically affect how the system is used, and 
thought and user research should go into ensuring that the users of a machine 
learning system work properly with it. 

It’s clear from screenshots in the article that the authors of the DEWS tool 
missed an opportunity for good design, and so administrators and educators 
were mis-interpreting the results. The Markup reports a number of insightful 
comments that confirm this. It’s a shame that the system’s language is
misleading, but the good news is that this sort of thing is relatively easy to 
fix, even without changes to the predictive model itself. 

It’s also regrettable that the journalists at The Markup mis-understood this 
point, as it takes away from their strong critique of the model itself. The 
big issues with the predictive model are that it’s not very predictive -- it 
seems to mostly provide scores in the relatively narrow range of 75 to 95 -- and 
that for critical subgroups such as racial and ethnic minorities, its 
predictions are often biased high or low. Treating the design issue as a 
modeling issue confuses the matter, and misses an opportunity to discuss the 
importance of design to the system’s success. (The Markup does appropriately 
discuss how inadequate the training was, which is another common problem with 
this sort of system.) 

-----

Again, I applaud The Markup’s deep investigation into an important issue, and 
for that matter, I applaud Wisconsin’s efforts to attempt to address 
educational inequalities. Hopefully, student success models and systems in 
Wisconsin and elsewhere will continue to improve, allowing more students, 
especially those from disadvantaged backgrounds, to benefit from a strong education.
