---
title: 'Staff Data Scientist: Comments on Will Larson''s Staff Engineer Book'
author: Harlan Harris
date: '2022-05-31'
slug: staff-data-scientist-comments-on-will-larson-s-staff-engineer-book
categories:
  - professional
tags:
  - data science
  - job titles
  - management
description: Comments on a few things from Larson's book, and highlights of a few things that jumped out as particularly resonant.
featured: yes
toc: no
usePageBundles: no
featureImage: https://staffeng.com/StaffEngCoverHero.png
featureImageAlt: Cover of Will Larson's Staff Engineer book.
codeMaxLines: 10
codeLineNumbers: no
figurePositionShow: yes
showRelatedInArticle: no
editor_options: 
  markdown: 
    wrap: 72
_build:
  render: true
  list: false
---

I recently read Will Larson's excellent book [Staff Engineer: Leadership
beyond the management track](https://staffeng.com/book). Larson covers
the individual contributor (IC, not management) roles that software
engineers fill after they are promoted past Senior Software Engineer,
with titles like Staff and Principal ("Staff-plus"). In the book, he
synthesizes his own experience and the experiences of a number of other
Staff-plus engineers, and provides great insights into how to get
promoted to that level, and how to succeed at it. Great book -- you
should read it.

As someone who has had both management roles and similar IC roles, I
thought I would comment on a few things from Larson's book, and
highlight a few things that jumped out as particularly resonant. These
comments are based mostly on my recent experience as Staff Data
Scientist (mostly focused on Search) at [Teachers Pay
Teachers](https://www.teacherspayteachers.com/Careers), and some initial
thoughts as Principal Data Scientist (mostly focused on Growth) at
[Algolia](https://www.algolia.com/careers/), where I've been for the
last month. (I'm going to talk primarily about *insights*-focused data
scientists, what others have called [Type A
(Analysis)](https://towardsdatascience.com/ode-to-the-type-a-data-scientist-78d11456019 "An Ode to the Type A Data Scientist").
Data Scientists who mostly build machine learning systems have a very
different role at this level.)

Quotes are of Larson, unless otherwise specified.

------------------------------------------------------------------------

# Archetypes

> (p.12) The more folks I spoke with about the role of Staff-plus
> engineers at their company, the better their experiences began to
> cluster into four distinct patterns...
>
> The **Tech Lead** guides the approach and execution of a particular
> team...
>
> The **Architect** is responsible for the direction, quality, and
> approach within a critical area...
>
> The **Solver** digs deep into arbitrarily complex problems and finds
> an appropriate path forward...
>
> The **Right Hand** extends an executive's attention, borrowing their
> scope and authority to operate particularly complex organization.

As a data scientist, and particularly one who used clustering to define
[subtypes of Data
Scientists](https://www.oreilly.com/library/view/analyzing-the-analyzers/9781449368388/ "Analyzing the Analyzers (O'Reilly)")
in the past, this warmed my heart. The types of work that I've done roll
up well to versions of these clusters. At TPT, I was a co-lead of the
Search team, working with a Product Manager and an Engineering Manager
to guide the approach of that team. I wasn't the Tech Lead -- someone
else had that formal role -- but I very much helped that team be
grounded in data and user experiences with search, and in some sense
split responsibilities with the PM.

Other projects rolled up to other patterns. I worked closely with the
Analytics team on [A/B
testing](https://www.harlan.harris.name/tags/a/b-testing/ "My posts on A/B testing"),
and helped TPT get stronger and smarter about how they ran tests. In
some sense, I was the "Architect" of A/B testing, although that sounds
more formal than it was. I also did some special projects in partnership
with other insights teams, such as a causal statistical analysis of a
major product launch, that feel like a "Solver" role.

I haven't really had a Right Hand role, but can imagine how a data
scientist could work closely with a CEO. One part of a CEO's role, I've
heard described, is to [interpret external
reality](https://hbr.org/2009/05/what-only-the-ceo-can-do "What Only the CEO Can Do (HBR)")
to get the organization aligned on why they're doing what they do.
Interpreting reality is very much what data scientists do too.

# What Staff-plus Data Scientists Do

> (p. 20) Staff engineers do \[the same tasks as Senior engineers\], but
> whereas previously they were the core of their work, now they're
> auxiliary tasks. Their daily schedule \[is primarily now\]: setting
> and editing technical direction, providing sponsorship and mentorship,
> injecting engineering context into organizational decisions,
> exploration, and what Tanya Reilly calls [being
> glue](https://noidea.dog/glue).

Yes, this. The primary thing I want to highlight is what successfully
injecting *data science* context into organizational decisions means. A
thing that data scientists are particularly good at is reasoning about
*uncertainty*. What we can do to support organizational decision-making
is to help leaders and management understand what is more certain and
less certain, to find ways to reduce uncertainty, and to make the best
decisions possible. Tools for this include A/B testing, good data
visualization, statistical modeling, stochastic simulation, and other
tools from the data science toolkit.

> (p. 57) \[As\] you look at how software changes over time, there are a
> small handful of places where extra investment preserves quality over
> time... I call those quality leverage points, and the three most
> impactful points are interfaces, stateful systems, and data models...
>
> *Data models* \[constrain\] your stateful system's capabilities down
> to what your application considers legal... A good data model is
> tolerant of evolution over time. Effective data models are not even
> slightly clever.

Ooh, data! For software engineers, data models are how the *software*
represents the world that the organization and the software's users care
about. It's critical to get right. For data scientists, we also care
about representing the world, and we can be an important voice in
ensuring that the data we use and the work that we (and analysts, and
business intelligence engineers, etc.) do actually approximates the real
world well. At the staff-plus level, we should have both the business
context and the technical skills to help the organization be better at
measuring, finding insights, and making decisions that reflect the
complexity of the world, while working around problems in the systems
that provide our data.

> (p. 192) \[From an interview with Katie Sylor-Miller at Etsy\]
>
> I've definitely found that... it's taking longer to actually find the
> dedicated focus time to write code as my calendar fills up with
> meetings... I'm much more focused on identifying areas for opportunity
> and then trying to sell that as work that my team or other teams
> should be doing.

In [classic management
texts](https://www.goodreads.com/book/show/324750.High_Output_Management "High Output Management"),
managers are urged to find the highest-leverage thing that they can do,
and delegate the rest. The same applies to Staff-plus ICs. Although I
spend a lot less time in meetings than I did when I was a manager, I
spend more time writing documentation and processes, or helping others
up-skill, or researching problems and proposing projects.

> (p. 195) \[More from Katie Sylor-Miller\]
>
> I also think that Staff Engineers should have a broad understanding of
> all of the adjacent fields of work to their own specialty. For me,
> working in the frontend, I put a lot of time and effort into
> understanding marketing, business goals, user experience, visual
> design, the view and business logic layers on the server, how we ship
> code to the browser, \[etc.\] Having expertise in all of these
> different areas makes it easier for me to see the broader impact of my
> technical decisions and understand those tradeoffs better.

Yes, and related -- I tend to think that an effective data scientist
working in the product organization at a tech company should be able to
operate as a software engineer a couple of levels lower. So if a Staff
Data Scientist is a "level 5" role (which it often is), then someone
filling that gap should be able to operate as a Senior (level 3)
Software Engineer. This doesn't mean that you should be spending your
time *writing* production code (not very high leverage), but it does
mean that you should be able to *read* production code and be able to
think about and communicate about software architecture and
implementation at that level. (Of course, if you work in another type of
organization, or outside of product, other rules of thumb probably
apply.)

# How Staff-plus Data Scientists Succeed

> (p. 36) Hunter Walk recommends that folks avoid "snacking," \[easy and
> low-impact work,\] when they prioritize... \[Y\]ou're unlikely to
> learn much from doing them, others are likely equally capable of
> completing them (*and* for some of them, it might be a good
> development opportunity), and there's a tremendous opportunity cost
> versus doing something higher impact.

For data scientist, the snacking is often "pulling data" or other
relatively routine work. I do think it's important for data scientists
to spend a limited amount of time on this, however, for a few reasons.
It's a good way to learn about organizational data and business
problems, both of which are critical to be well-versed in. It also
builds good will with colleagues in other departments. And it provides
an opportunity to say "yes, and" -- to provide the requested data, but
also to suggest new higher-impact initiatives that may be possible.

> (p. 39) You *should* swarm to existential problems, but if a problem
> isn't existential, then you should be skeptical of adding your efforts
> where everyone's already focused... Instead, the most effective places
> to work are those that matter to your company but still have enough
> room to actually do work. What are priorities that will become
> critical in the future, where you can do great work ahead of time?
> Where are areas that are doing *ok* but could be doing *great* with
> your support?

Data scientists are often in the unique position of having insight into
what's changing at an organization, because of our closeness to the
data. Being able to say "hey, I'm seeing this thing, and here's what I
think we should do about it" is a strong place to be.

> (p. 42) Whatever it is, things that simply won't happen if you don't
> do them are your biggest opportunity to work on something that
> matters, and it's a category that will get both narrower and deeper
> the further you get into your career.

Yes, and related:

> (p. 119) \[E\]arly in your career, you're given well-defined problems,
> but as you get deeper into it, you'll increasingly encounter poorly
> defined or undefined problems, and Staff projects will generally start
> with a poorly scoped but complex and *important* problem... From that
> broad, unclear (and potentially wrong) statement, you'll have to
> identify a concrete approach that works.

Yes, yes, yes. Doing data science at *any* level involves having a
conversation with stakeholders to understand and refine the problem, so
that you can tackle it in the most meaningful way. This gets harder or
more critical at more senior levels.

> (p. 178) \[In an interview with Keavy McMinn from Fastly\]
>
> \[Staff-plus engineers\] all work on different things, but we have a
> common goal of taking a holistic, long-term and system-wide view on
> things. We also try to find and help with the sort of things across
> engineering that might get overlooked or fall between the cracks. Our
> CTO supports our work, but doesn't identify the projects to work on,
> that's up to us.

As a Staff-plus data scientist, I really think that it's best to split
your time between the vague but important asks that come your way, and
initiatives that nobody else is thinking of yet. Of course, we need to
build support from management as we go, to ensure that we'll be able to
create impact from a project.

## Leadership

> (p. 75) \[Roughly,\] management is a specific profession, and
> leadership is an approach one can demonstrate within any profession...
>
> \[L\]eaders have a sufficiently refined view of how things *ought to
> work* such that they can rely on their distinction between how things
> *are* and how they *ought to be* to identify proactive, congruent
> actions to narrow the gap. \[Also,\] they care enough about the gap to
> actually attempt those narrowing actions.

At the Staff-plus level, data scientists should have a broad enough
context to identify and prioritize what needs to change, and a broad
enought set of skills (soft and technical) to actually push things
forward. This could mean writing a memo to senior management, or it
could mean writing a technical spec to an audience of software
engineers.

> (p. 168) \[In an interview with Ras Kasa Wililams, Staff Engineer at
> Mailchimp.\]
>
> \[O\]nce you become a Staff Engineer, you're a member of "Engineering
> Leadership"... In my view, it's about thinking globally. That means
> partnering with other\[s\]... to understand the company-wide
> business/product strategy and distill that into an Engineering-wide
> technical strategy... It's about taking that global thinking and
> applying it locally.

Especially in the "Tech Lead" version of the role, the Staff-plus data
scientist is working to keep a team aligned with the company's goals as
a whole. This can sometimes cause some disagreements. On the TPT Search
team for instance, the three co-leads (myself, the Product Manager, and
the Engineering Manager) each represented different goals, and we had to
work together to align them. I represented specific pain-points in the
user experience and associated metrics; the PM represented current
high-level product priorities; and the EM represented software quality
and robustness, and the developer experience. We were generally
effective at this because we all understood how our work rolled up to
long-term success, and because we all communicated effectively and
frequently with each other and colleagues on other teams across product
development, marketing, and other divisions.

## Defining the Role

A thing I've appreciated about becoming more senior is that you get more
of an opportunity to define your role, and define what success should
look like. Part of that is working with management to write job
descriptions, and part of it is helping to define what successful data
science at your organization means.

> (p. 171) \[Still from Ras Kasa Williams\]
>
> \[At Mailchimp, there's\] a recurring call for all Staff, Senior
> Staff, and Principal Engineers meant as a space to surface and discuss
> problems, assign owners and action items when needed, and generally
> build community with each other.

I really like this, and I think there's enough commonality in roles
between Staff-plus Software Engineers and Staff-plus Data Scientists
that we should join this sort of peer group whenever it exists. Many of
the "soft skills" challenges of having leadership expectations without
formal management authority are the same. Plus we can talk about the
irritating parts of Python.

------------------------------------------------------------------------

There's much more in the book worth discussing from the point of view of
a Staff-plus Data Scientists. If you have thoughts or experiences, I'd
love to hear them!

ps -- shout-out to Aaron Schumacher, who [excerpted some other great
snippets from the book in his
blog](https://planspace.org/20210919-staff_engineer_by_larson/ "plan ➔ space")
last year!
