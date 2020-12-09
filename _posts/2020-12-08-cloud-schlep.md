---
layout: post
title: cloud-schlep
---

Relevant Reading
* [Schlep blindness](http://www.paulgraham.com/schlep.html)

Consulting for cloud software is quite bad. Documentation is opaque, insights are scattered across Github, StackOverflow. Multiple AWS services offer the same functionality. Companies that start on the cloud have to move fast. They don't have time to sift through the mud.

The alternative is to look towards open source or other SaaS providers. Github, Sumologic, which provide much better experiences.

There's nothing that prevents Google or Amazon from innovating in this space,
though. They can, and do, tackle the problem in different ways:
* support calls ($)
* solution consulting ($$)
* partner with a tech consulting firm (deloitte, accenture, $$)
* hire a dev team to do the work for you ($$$)
* hire off shore team
* provide better documentation

Why do we live with this mess? In the back of our minds, AWS will eventually
"get around to it". They're a tech company, and writing documentation and
simplifying API's is WAY EASIER than creating a scalable cloud computing
platform.

Except they don't. The reason, I suspect, is two-fold. One, it's not a
priority. It *feels* more important to have teams iterate on the platform and
get the tech right. Two, cloud platform features are an *average* of all the
use cases customers might see or experience. So they don't serve most use cases
*well*.

The current strategy of *averaging* use cases seems to make the most money, at the cost of adding many more bells and whistles. But this leaves mismatched incentives. Cloud providers care about serving lots of customer use cases at the cost of feature complexity. Customers care about ease of implementation, and don't want to pay more than they need to.

<blockquote>
The most dangerous thing about our dislike of schleps is that much of it is unconscious.
Your unconscious won't even let you see ideas that involve painful schleps.
That's schlep blindness.
</blockquote>

Somewhere in the middle, friction builds. We take it for granted that this is
just the state of the world. It's just *schlep* that dev teams deal with.

