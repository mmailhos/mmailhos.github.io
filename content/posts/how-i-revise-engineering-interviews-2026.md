+++
title = "How I’d Revise Engineering Interviews for 2026"
date = "2026-04-06T09:00:00+02:00"
draft = false
tags = ["hiring", "leadership", "engineering culture", "ai"]
categories = ["Leadership"]
description = "The signals have changed: how to interview software engineers with AI and avoid costly hiring mistakes"
+++

A bad hire is incredibly expensive: salary, recruiting fees, technical debt, and toll on team morale. Yet, interviewers still rely on the wrong signals. After running over a hundred interviews in the past couple of years, I want to share the common traits I've been looking for as an interviewer to help de-risk the hiring decision.

Software engineering was never about writing code; it's always been about solving business problems. Despite this, most companies I've talked to in the past 12 months are still interviewing with LeetCode and Kubernetes trivia. If an AI agent can pass your technical test, not only is your process broken but you’re also sending a bad signal about your engineering culture.

Instead of testing if a candidate can outperform an agent, we should be testing if they can direct one. The best hires are pragmatic owners who identify the right problems to solve and leverage every tool at their disposal to ship them.

### 2015-style interviews fail in the AI era

During my career, I've been grinding LeetCode challenges, and spending evenings on _Cracking the Coding Interview_. I got tested on so many different types of questions, from Fizz Buzz to LeetCode hard questions, rapid-fire trivia to open-ended organizational discussions. Finally, I've seen how they rarely transpose to our day-to-day job.

I've also been on the other side of the table as I ran over a hundred interviews at Canva, and led final decision meetings. By 2025, I transitioned to AI-assisted interviews: very broad and deeply technical challenges to solve in just under an hour. This has completely changed my view on which signals to probe and look for.

Now, the AI coding workflows are becoming more mature and well adopted (more than [36% of Stack Overflow 2025](https://survey.stackoverflow.co/2025) survey respondents use AI-enabled tools). Shipping fast is the norm, and coding language fluency is harder to probe and no longer a key differentiator. We expect engineers to be broader across domains and exercise critical thinking. 

With this change of modus operandi, engineers spend more time reading code, whether that is text-completion or code reviews - than writing it. Being able to audit the code is a large part of the job now. One of my favorite types of interview is to ask the candidate to extend an existing system or do a code review exercise.

{{< protip >}}
use one of your company's open-source projects, and phrase a problem as seen by your users that relates to this project. Sharing a problem rather than asking for a specific solution is one of the best ways to probe for curiosity and adaptation to your business and to the existing code base. For some positions or if your process allows, you may even not ask for code, and keep the problem architectural only.
{{< /protip >}}

Value interviews are now immensely more important than before. They give extra time to probe on soft skills such as leadership, communication and strategy and are absolutely worth extra investment. Try to go deep into past experiences and key decisions, as any discussion too shallow is easily "fakable".

## De-scoping

The most expensive mistake is solving the wrong problem. At this stage, I am not looking for technical details, but for the ability to scope a problem to meet business needs. Can they find the right MVP to solve based on the known constraints?

The more senior the engineer, the more I keep the problem vague and high-level. I expect the candidate to probe and ask clarifying questions. Great engineers make the problem smaller and less ambiguous before diving in. They clearly question and state their assumptions out loud so we can validate them collaboratively.

I particularly appreciate candidates who explicitly call out "out of scope", and overly expensive or complicated edge cases not worth optimising for.

While tighter scopes are expected for junior roles, we must stay mindful of the new floor: anything already well-defined can now be largely delegated to an agent.

## First-Principles Design

Once the scope is clear, we move to high-level design. This isn’t about choosing a specific technology, but about articulating trade-offs and laying down the fundamentals.

I do not care whether a candidate wants to introduce a new MySQL or Postgres database, as long as they can state why a relational database is required. I am looking for the ability to explicitly tie system properties - like consistency or durability - back to the business requirements we just defined.

Many interviewers fall into the trap of asking technology-specific trivia, expecting candidates to recite framework features like magic incantations. For example, I was once asked how I would scale Kubernetes pods based on non-native metrics. A question like this tests my ability to do a Google search. It also sends a negative signal about the company: what kind of micro-management or "check-box" engineering culture is actually happening there?

Frameworks and libraries are transient; architectural patterns and the trade-offs they imply are what stay constant.

{{< protip >}}
a quick diagram can go a long way here. I recommend the [Container view](https://c4model.com/diagrams/container) from the C4 model. An LLM can easily generate mermaid diagrams for anything below this. If the candidate gets lost in details, this is your opportunity to elevate the discussion to an appropriate level of details.
{{< /protip >}}

## AI leverage with ownership

It's now time to implement a working solution. In a 60-minute exercise, we want to see the deliverable: running code. We deal with all sorts of constraints in the real world, and time is a very clear one here.

I like to spend a few minutes analyzing the candidate’s development environment itself. It’s a great learning piece: How tight is their feedback loop? Is their AI setup leveraging local tooling (MCP, Skills) to be more efficient? What is their reasoning for picking a specific model for this task?

I value engineers who can leverage the best tools, but I am specifically looking for how they _direct_ those tools. Thoughtworks warns that *[complacency with AI-generated code](https://www.thoughtworks.com/radar/techniques/complacency-with-ai-generated-code)* is a leading cause of technical debt and declining quality, and [CISQ](https://www.it-cisq.org/wp-content/uploads/sites/6/2022/11/CPSQ-Report-Nov-22-2.pdf) has shown that the average developer spends roughly 1/3 of their week addressing tech debt. In short, if the candidate isn’t deeply owning the code during an interview, they aren't going to day-to-day, and the velocity will suffer. 

The best candidates I’ve seen apply Test-Driven Development (TDD) principles to the AI workflow. They focus on reviewing test cases before looking at implementation details. They care about how the interface is exposed and consumed first, ensuring the contract is right before fixing lower-level logic.

Eventually, I start probing harder on the craft skills like attention to edge-cases and other domains such as concurrency, encoding, failure modes, space/time complexity, accessibility, security...

{{< protip >}}
if your interview process is asynchronous, ask for the candidate’s AI transcripts. It reveals how they iterate, the quality of the prompts they write, and the level of details they dive into. You can also ask for a Loom to see how comfortable they are walking through the code.
{{< /protip >}}

## Final take

This isn't 2015 anymore. Asking an experienced candidate to answer framework trivia questions or white-board a sorting algorithm is a complete disconnect from the real world.

On the other hand, hiring someone who relies on AI without deep ownership or architectural understanding is shooting yourself in the foot in the long run as you're trading short-term speed for long-term debt such as bottlenecks in performance, reliability and maintainability issues.

Tools and frameworks are changing faster than ever. Embrace AI, but make sure to probe for the ability to understand the business problem, articulate the trade-offs they are making, and ship fast with ownership.