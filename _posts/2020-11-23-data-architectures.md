---
layout: post
title: data architectures
---

# Data Architectures

Relevant Reading  

* [Data Monolith to Data Mesh](https://martinfowler.com/articles/data-monolith-to-mesh.html)
* [Narrator.ai](https://www.narrator.ai/)
* [Emerging Data Architectures, a16z](https://a16z.com/2020/10/15/the-emerging-architectures-for-modern-data-infrastructure/)

How do you build data architectures that don't fall down? 
It's a problem in the data sector many companies have struggled to answer,
and a question I've spent the past 6 years thinking about.

To understand why, we have to get to the roots. There are two problems that
beseige data architectures: scale and complexity. Scale is when your data volumes increase by an order of 
magnitude. Teams have spent a decade tackling this problem. Complexity
is when the semantics of your data change. No team as far as I know has
deliberately tried to tackle this problem in an original way.

## Recent Innovations

The newest concept in the past year is Zhamak Dehghani's idea of a "Data Mesh".
At its essence, it's about applying domain-driven design to data architectures.
*The innovation comes from phrasing the problem as an issue with org structure
and thinking rather than a pure tech problem.* The thinking mirrors the tech industry's
recent migration to service-oriented architecture; it's about the
[domain](https://eng.uber.com/microservice-architecture/), not the technology.

We see a parallel evolution over the past decade in thinking about services and data.
Back in 2008, when the idea of microservices was introduced, people focused on
building technology first - thrift, rest frameworks, ci/cd as a service. Then, orgs
started leveraging this tech. They realized quickly that without the
right boundaries, you run into further complexities due to dependencies across
services. Some orgs <a href="https://segment.com/blog/goodbye-microservices/">
moved back to a monolith</a>, and <a href="https://monzo.com/blog/we-built-network-isolation-for-1-500-services">others doubled down</a>.

But we're hearing more and more stories of increasing complexity. This complexity
becomes tough to tackle when your eng org is in a competitive market and
needs to iterate quickly. A good analogy I've heard is "replacing the engine of a moving car".

Back in data land, the tech is now roughly here. You have companies that offer
stream processing as a service, storage and warehousing, and even analytics
tracking. You can also build your own on the cloud (on-prem is stil fairly
challenging). But how do you "apply" this technology in a way that doesn't fall
down?

So we're back to the complexity. What does the data mesh promise to solve? One,
it puts domain teams<sup>1</sup> in the driver's seat. **Domain teams now produce and
maintain data as a product**. This is not a new concept, but the 
definition of a "data product" wasn't well-known up until now. Neither was the
understanding of how to maintain one. How do you measure quality except through
ad-hoc scripts? What operational burden can you take away from domain teams?

## Why This Could Work

The verdict's out on whether data mesh is a good abstraction. But it lines up
with intuition. It makes sense to say we haven't been able to solve the
modeling problem because responsibilities are incorrectly aligned. The
natural next question to ask is: who should be responsible? 

Domain teams are a good guess, but what if your org isn't neatly divided
up into domain boundaries? Services like Narrator.ai provide an interesting
answer: outsource your data modeling to folks outside your org. This has its
limits<sup>2</sup>. At the end of the day, your domain team needs
to untangle the complexity its created by remodeling its domain.
Creating another layer of abstraction only leads to a leaky layer.

The other question to answer a data mesh is: what organizational complexity does
this incur? I suspect we'll have to train domain teams on best practices
for analytical modeling, thereby growing the responsibilities of a
software engineering team. For larger organizations, this might not be
possible due to the scale. They probably need specialized
consulting services to bridge the gap.

For younger organizations that are not entrenched in org or tech debt,
it's a perfect opportunity to try this out. If we get it right, we'll
have answered some important questions about the nature of data modeling.

---

<sup>1</sup> Domain teams are eng teams that support a business domain with
clear boundaries to other teams. they maintain services, pipelines, apps,
and most importantly, their domain models.

<sup>2</sup> The narrator.ai approach is worth mentioning; an 11-column table
to abstract all your needs. at the center is a triple of
"activity-relationship-activity". Essentially, Narrator wants you to re-model
your data as a <a href="https://en.wikipedia.org/wiki/Semantic_triple">semantic triple</a>.
This has been tried once before, notably for <a
href="https://en.wikipedia.org/wiki/Resource_Description_Framework">storing
metadata</a> about the web. While triple store are very expressive,
it isn't the most obvious way to express many use cases, and there will be
impedance mismatches
