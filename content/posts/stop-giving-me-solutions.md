+++
title = "Stop Giving Me Solutions"
date = "2026-03-02T09:00:00+01:00"
draft = false
tags = ["leadership", "ownership", "engineering culture"]
categories = ["Leadership"]
description = "How prescriptive leadership erodes engineering culture"
+++

## "It’s just a quick fix."

A few years ago, shortly after joining a scale-up, I was handed a task as part of my onboarding: _"Add an autoscaler to this ECS service to reduce the cost of unused compute. It shouldn’t take more than half a day."_

At first, it sounded straightforward. The service was significantly overprovisioned with very little load. A rough estimate suggested we could reduce the fleet size by 80% and immediately cut costs. It looked like an easy win, so I implemented it.

Before calling the task complete, I ran a load test approximating production traffic. The autoscaling logic triggered correctly, and new tasks started launching. But then, requests started failing, and clients began seeing 502 and 504 errors.

Digging deeper, I found a few issues:

- The concurrency model (Gunicorn/gevent) lacked proper monkey patching.
- Neither the client nor the Traefik proxy layer implemented retries.
- New ECS tasks took up to 8 minutes to become ready to serve traffic.
- Health checks and timeout configurations were misaligned.

After talking more with the core maintainer, latency wasn’t the primary constraint as this service handled long-running jobs, but availability was.

In short: the system was not designed to scale horizontally in a safe way.

Instead of delivering immediate business value, I had to spend our limited time budget proving **why** the prescribed solution was insufficient, and investigating what actual architectural changes were needed. Ultimately, the cost of refactoring the service outweighed the immediate infrastructure savings, and we made the pragmatic business decision to move on to higher-priority initiatives. These machines are still burning money today.

## **The Anti-Pattern: Prescribing the "How"**

What went wrong here? I was handed a prescriptive solution that ignored the system's historical context.

When organizations prescribe exact solutions to their engineers, they unintentionally build a culture of dependency. We train teams to wait for instructions rather than think critically, shifting the engineer's role from a _problem-solver_ to a mere _implementer_.

More importantly, when an engineer just executes a predefined task, they don't own the deliverable. If the solution fails, the accountability falls on whoever wrote the ticket. You cannot hold someone accountable for an outcome if they had no say in the methodology.

This is entirely incompatible with a culture of true engineering ownership, which a lot of companies claim to have.

## **A Better Way: Framing the "Why"**

We could have achieved a much better outcome simply by phrasing the task differently:

_"In the foo project, it appears our image-processing machines are largely underutilized and costing us money. Could we aim to reduce this bill by ~80%, or do the best we can within a 2-day timebox?"_

This approach provides context, states the business goal, and sets a measurable constraint. Most importantly, it delegates the _methodology_ to the engineer.

In this case, simply optimizing the client to handle failures gracefully and setting a fixed, smaller number of nodes would have met the goal.

## **Influencing Through Inquiry**

As a tech lead, it is tempting to push for the solution you see in your head. But the best way to ensure an implementation actually solves the root issue is to collaborate. 

Instead of dictating, ask:

- _What approaches have you considered?_  
- _How should we handle the edge case when X happens?_  
- _What do you see as the biggest roadblock here?_  
- _What is the engineering effort of solution Z compared to the business benefit?_  

Beside, guiding an engineer to the solution themselves gives them a sense of achievement and total ownership.

## **Scaling Ownership: A Canva Success Story**

While working as a Staff SRE at Canva, I led a year-long initiative to discover and remediate systemic reliability risks across a platform serving 250 million MAUs.

We built an automated system that parsed incident postmortems, Slack context, and Service SLOs using data science and LLMs. This allowed us to build a comprehensive and continuous backlog of reliability risks backed with evidence of business impact.

SREs translated these risks into well-framed problem statements for the owning teams. We ensured every ticket had:

1. **Clear user impact**, linked to previous incident metadata.
2. **Measurable outcomes**, tied directly to observability metrics.
3. **A framing of business risk.**

By the time I left, we had accumulated a backlog of over 80 well-framed reliability risks, with half successfully adopted onto product team roadmaps. We rarely saw pushback because we weren't telling them _how_ to write their code; we were showing them a critical business problem and trusting them to solve it.

Even better, the engineers who were able to solve this risks could measure their impact through real business metrics. How good!

## **Conclusion**

When people are trusted to design their own solutions, they become deeply invested in making them work. Solutions are often better and engineers grow in their craft and develop autonomy.
