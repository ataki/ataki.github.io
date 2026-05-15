---
layout: post
title: artisans and software
---

reading code crafted by our agents today, i was struck by a thought: this code feels "mass-produced'. like suit-supply quality when you're used to zegna-level or tailor-made.

> to be clear, our setup is:
>
> - a new repo seeded with llm docs
> - multiple agents work on separate areas of the docs
> - each team member guides their own agents and is responsible for behavioral quality in their areas, and commuicating conflicts to product
> - this is not the early-days of cursor where auto-complete speeds up a human, but humans shape the code. rather, the human doesn't write a single line of code, and only does prompt-engineering.

some interesting outcomes of this way of producing software:

1. strange considerations are raised
   Because humans are not working on the doc, you get asked questions that are either obvious to humans. you also get asked to make decisions that don't **feel** necessary to make, but logically are. similar to how mass-production works for suits - you do not have to decide half-canvas vs full-canvas when tailoring. in a factory setting, a half-canvas is a cost saving. in hand tailoring, half-canvas is an aesthetic choice, and most tailors should assume the customer wants full-canvas.
   the result? as the human, I find myself sometimes lazily makig decisions, my eyes glaze across details of the decision because they don't often feel lik they matter.
2. the docs are almost unreadable to humans
   trying to review llm docs is a slog. the docs are not written for humans. enough said if you've had to actually sit down and give meaningful, detailed feedback to a doc.
3. humans are not good reviewers of this type of work in detail
   i review these docs with an llm. the llm acts as a fact-checking translator. i ask the llm to interpret my responses and update the doc.
   this behavior is the only way for me to get through my work.
4. the code reads impersonally
   this is a gut feel. you see the details, and they are..._strange_. the way modules complect. the way names are given. the way standards like function names, syntax, and files are organized. when a human writes code, the standards feel well-crafted - enforced in some ways, not enforced in areas where it's not necessary. when the llm writes code, the standard is enforced everywhere. the word "brutal" comes to mind.

Extrapolating a bit, this feels like "mass-produced" software. "Suit-supply" quality. It feels strange for us because we're used to Zegna-level or tailor-made suits. But past this era, "Suit-supply" is the norm. [Hand-crafted code](https://github.com/antirez/ds4) and [simple code](https://github.com/karpathy/llm.c) will be relics of a time long forgotten. When humans ruled the world.
