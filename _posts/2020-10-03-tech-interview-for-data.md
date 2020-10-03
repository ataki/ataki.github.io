---
layout: post
title: tech-interviewing-for-data
---

# Tech Interviewing for Data

***This is still in draft stage. Feel free to leave thoughts via messenger
or twitter dm's***

## Evolution of the data engineer

I'm a software engineer by trade. At my first couple of jobs, I found myself building systems to power these heavy, feature-rich dashboards and systems for our users who wanted to be data-driven. Back then, that was the phrase du-jour. 
We should use data to inform and track our every decision! This was back before
the Facebooks, Youtubes, and Palantirs of the world proved that systems and social behavior, when instrumented and structured correctly, revealed a lot of insights.

The most interesting techincal problems we kept running into was always: how do
you build elegant systems to discover these insights? We knew a fair bit about
building for web and mobile compared to today, but nothing about how to
discover these insights automatically.

Then somewhere along the way, companies started discovering this problem, and
threw software engineers at the problem. we all set off building what we
needed at individual companies, using roughly the same patterns. a few
technologies stuck - airflow, spark, redshift, kafka, presto, hbase, s3 - and others failed.

These tools wound up creating other problems. At some point, we needed
operators because we had arguably built the wrong abstractions. Enter - wait,
data engineers? I'm still not exactly sure how this happened, but the operators of the tools and builders of the tools got caught up in the same name. job postings for data engineer didn't usually specify which. This miscommunication led to an unfortunate conclusion: data and software engineering are separate disciplines and should not be confused with each other.

## Skill sets

At the essence, I argue that data and software engineers are cut from the same
cloth. The tools we use have different names, but they come down to solving
similar sets of technical problems. You think about data modeling, efficient
ways to express business logic, and design scalable architectures based on
requirements - olap vs oltp.

And yet, the technical interview has not changed. We interview data, devops, and other engineers at most companies with the same set of generalist questions. One of the best devops engineers I know got a question about scalable api design 4 years ago (this skill set wasn't mentioned in the job posting). Whether this thrash and miscommunication is actually good is up to the employer, but the fact is, the process has not fundamentally changed. If you're a data engineer, you need to study for software.

With that, I'll turn attention towards helping data engineers of data engineers who
want to transition back into software, or vice versa. For the data -> software
route, I outline an opinionated study plan.

# Opinionated Plan

## The Study Tools

Start with [EPI Python](https://www.amazon.com/Elements-Programming-Interviews-Python-Insiders/dp/1537713949/ref=pd_sbs_14_1/144-7045158-5168703?_encoding=UTF8&pd_rd_i=1537713949&pd_rd_r=d6330c76-ddb4-42fb-b9ce-9ff71b9d9035&pd_rd_w=kw6Wi&pd_rd_wg=z6FEY&pf_rd_p=b65ee94e-1282-43fc-a8b1-8bf931f6dfab&pf_rd_r=JVQ852TPXJ80KFSYMY8A&psc=1&refRID=JVQ852TPXJ80KFSYMY8A). Most data engineers have worked with Python (or Java, depending on your era) due to the tooling available to us. This is the single best study resource.

EPI has a repo you can run locally with test cases. Set up the repo locally via
[github](https://github.com/adnanaziz/EPIJudge).

### Python tooling
If you haven't heard of these modules, learn them. Most are a part of the native
Python library.

* `pdb`: python debugger
* `heapq`: min-heap implementation
* `dataclasses`: data tuples as first class citizens ("lightweight classes")
* `collections.Counter`: counter data structure

## Carve Out Time
The book contains different study plans depending on how much time you have. I
would pick either the 1 month or 4 month track. If you have a full-time job, you'll need to devote at least one entire day (8-10hrs) in your weekend to studying for this.

The book is optimistic in its time estimate. I always wind up taking longer b/c
I enjoy thinking about every nook and cranny of the problem, and developing an
intuition for the algorithm.

## What The End State Should Feel Like
Now you're ready to study. Start by visualizing the end state.

A frequent question I used to ask and get is: how do you know you've done
enough studying? It's not when you're fed up with studying.

IMO the best mentality is to be so prepared that **you literally can't wait to get to the problem in the interview.** There's a joy in having solved so many problems that you're wishing the interview gives you one you haven't heard of before and struggle with. Most interviewers will not. The reason is that problems solvable in 20-35min come down to using the same data structures and algorithmic patterns with tweaks.

If you're into metrics, another one is that you can code up a problem from
start to finish in 20min or less. This can literally be the same problem you've
seen before, and solved before. But you need to start with a blank editor page.
You may need to practice solving the same problem 3-4 times, and just getting
faster. I've written merge sort in an embarrassing number of languages and frameworks. But each time you start from scratch, you learn something new. Ichi-go, ichi-e. Every encounter is different

## Approach to studying
Tackle the problem in your study list in the following way. Skip linked lists.

1. Start with coding on pencil and paper. Don't use an editor until you have
   the solution written down in full
2. Write your solution in a text editor and fix issues. Note the gaps - misspellings, missing variables, etc.
3. Run the EPI test harness. Fix bugs. Get stuck. Repeat.
4. Once you've coded it, throw everything away and start from scratch on paper.
   This time, aim to make fewer mistakes - you know the arc of the story, which
   bugs you introduced the first time. Observe what happens the second time,
   when you can anticipate where the challenges are.
5. Look at the solution. You'll feel a bit stupid b/c the reference solution may solve it a different way. Figure out why. Then go to step 4 and start from scratch.

For each problem, if you get stuck and can't pass the test cases, stop. Take a coffee break. Come back. Debug and examine using the debugger. It might take days. Don't look at the solution.

## Preparing for design
For folks who have spent 5+ years in the tech industry, these start counting
more.

The design interviews are a different beast altogether, and there's no easy
reference guide here. Two representative problems for preparing coming from data teams is to think about these two problem:

```
Design a distributed logger

You're at a startup and need to collect metrics from a variety
of production services and aggregate.

You may or may not know the user's analytical needs
ahead of time. Design a system to do this.
```

```
Design a tool that measures blood flow on a patient's body

You're an engineer at a healthcare company and are designing a solution for
measuring a patient's blood flow without invasive procedures.

Design a system to do this.
```

As you can see, there are so many ways to answer this question. Make assumptions, design a solution, then Ask seasoned engineers in your network peers for feedback. If you know me, message me and request a
mock interview.

## Why Do All This

I'll end with the why. This is probably an extreme view. Interview performance at tech companies have
implications beyond the initial interview. They affect your salary
negotiations, your initial perception to the hiring manager and teammates
involved, and your perceived trajectory.

Over a long tenure at a company (3+), these matter less. Given the rate of
attrition at tech comapnies, this can have significant bearing on your job.
Even if you get the job, a stellar interview performance is perceived
differently from a fits well interview performance.

