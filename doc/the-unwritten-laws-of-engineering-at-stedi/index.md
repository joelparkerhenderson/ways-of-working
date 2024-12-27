# The unwritten laws of engineering at Stedi

This document captures the cornerstones of Stedi’s engineering culture. As a
result of following the framework, product development may sometimes come to a
screeching halt. The work itself may be tedious and frustrating. Progress may
take many multiples of the time it would take using other methods.

This impact is short term, immaterial, and ultimately irrelevant. The framework
aligns with our long-term ambitions; nothing is more important than keeping a
high bar across these dimensions.

That's the difference between principles and preferences: principles are what
you do regardless of the cost – everything else is just a preference.

### Key tenets

* Minimize long-term operational toil.

* Eliminate waste.

### Practices

The following practices represent the bare minimum expectation of all teams:

* Security is job zero.

  * There is nothing more important than securing our systems.

* Prioritize on-call.

  * Implement thorough, pragmatic alerting and alarming.

  * The baseline for alerts and alarms is expected to be zero.

  * Prioritize work to mitigate the causes of pages above all else except for
    security.

* Define all infrastructure as code.

  * Define all production infrastructure as code, from build and deployment
    pipelines to operational dashboards.

  * Automate dependency updates and deployments to production.

  * Keep all dependencies up to date across all non-archived repositories.

  * Dependencies can be updated individually or in batches, in real-time or
    subject to some delay (for security or convenience), but the process must be
    automated.

* Investigate service metrics, build times, and infrastructure costs.

  * Review service metrics, build times, and infrastructure costs (both
    per-request and total spend).

  * The goal is not to strictly minimize these metrics via unbounded investment
    that has diminishing returns, but rather to surface flaws in configuration
    or implementation that are causing unnecessary waste.

* Pull pain forward.

  * When a service’s future is assured (that is, when it reaches or will soon
    reach GA), pull forward technical problems that get harder over time (e.g.,
    backwards-incompatible changes; major architectural shortcomings).

### Practices for practices

‘Best effort’ is ineffective – if ‘best effort’ were all it took, everything
would be in place already!

Instead, implement mechanisms for continuous improvement – generally:
preventative controls and/or detective controls wherever possible, with a root
cause analysis process for any exceptions.

## Component selection

In the fight against entropy, we use the following prioritization framework for
component types:

* Managed, ‘serverless’ primitives.

  * Use managed, serverless (defined as ‘usage-based pricing with little to no
    capacity planning required’) primitives wherever possible, even at the cost
    of functionality.

  * Within those managed service options, use the highest-order primitive that
    fits a given use case.

* Open source libraries and open standards.

  * Where a suitable managed service cannot be found, use open source libraries
    and adopt open standards wherever possible.

* Our own code and formats.

  * When all other options have been exhausted, build it ourselves.

### Selection framework for component sources

* Optimize for a cohesive set of components rather than selecting best-in-breed
  options, even when more compelling or popular alternatives exist.

* When choosing a set of components, invest in continuously-compounding
  ecosystems built by high-velocity organizations who are philosophically
  aligned with Stedi. Current ecosystems include AWS (infrastructure) and GitHub
  (source control, build, and deployment).

* Introduce new ecosystems at a clear boundary (e.g., GitHub for source control,
  build, and deployment of code; AWS for running the code), rather than in the
  middle of a system. For example, we would not use a database hosted at
  PlanetScale in an otherwise all-AWS backend.

## Refactors

We often identify more suitable ways of building something (that is, more
suitable according to the framework listed above) after we’ve begun, or after
we’ve finished. For example, we might start with writing our own code, only to
later realize that what we’ve written is similar to some open source library
instead.

When the refactor:

* will get easier over time, we’ll wait until it gets easier.

* will get harder over time, we'll do it without delay.

Generally, the framework when considering a refactor is to ask: if we were
starting again today knowing everything we know now, would we build it this new
way that we’re considering? If yes, will it get easier or harder over time? If
you’d build it the new way and it will get harder over time, do it now.

That said, large-scale lateral migrations (lifting-and-shifting that results in
a functionally-equivalent customer experience) are extremely costly. We try to
avoid these when possible.


## Communication


### Discussing tradeoffs

Like all approaches to building software, Stedi’s approach comes with many
tradeoffs – including, but certainly not limited to:

* Managed services, open source libraries, and open standards often have steep
  learning curves and poor documentation; they are often inflexible and lacking
  functionality.

* Managed services are harder to test, slower to iterate against, and harder to
  diagnose; they are expensive and have unpredictable roadmaps.

* Maintaining infrastructure as code is tedious and painful.

* Automated dependencies updates are distracting and error-prone.

These same tradeoffs will show up again and again; enumerating them at each
juncture is distracting and demoralizing. Instead, focus discussions on
mitigation. For example:

* “Given that this managed service will be hard to unit test. Let’s come up with
  a plan for how we can ship with confidence.”

* “Since the cloud deployment feedback loop is slower than local development, we
  should invest in tooling to speed this up.”

* “The documentation in this AWS library is sparse and outdated, so let’s make
  sure we contribute back early and often before we lose the context.”

* “This AWS service doesn’t support this feature we’ll want down the line, so
  let’s schedule a meeting with the AWS PM to see if it’s on their roadmap
  before building it ourselves.”

### Discussing roadblocks

Technology evolves rapidly. All features and functionality we use today did not
exist at one point; features and functionality that don’t exist today might
exist tomorrow. Most importantly, features and functionality you think don’t
exist today might already exist.

When hitting a roadblock or an apparent dead end – for example, when it appears
that a certain managed service or library isn’t able to do something – draw a
distinction between when you’ve definitively determined that something is not
supported, vs. when you’ve exhausted ideas that you’ve come up with but have not
definitively proven it isn’t possible.

In other words: ‘Absence of evidence’ is not ‘evidence of absence.’ False
determinations of impossibilities are extremely costly to us, particularly
because the false determination in one corner of Stedi spreads to all of Stedi.

Something is definitive when you can provide a link to source documentation
confirming that it isn’t possible.

* Acceptable: “A Lambda can’t run for more than 15 minutes – see documentation:
  Function timeout – 900 seconds (15 minutes).”

* Unacceptable: “X-ray doesn’t support cross-account traces [no citation].”

When you have tried a number of things but haven’t been able to make it work,
that is not definitive.

* Acceptable: “I haven’t been able to lock down this AWS resource via a
  tenant-scoped role. Here’s what I’ve tried…”

* Unacceptable: “Tenant scoped IAM access won’t work for this.”

If you have tried a number of things and haven’t been able to make something
work, post somewhere: “I haven’t been able to make this work, and I’m running
out of ideas/time. Here’s what I’ve tried…” The fastest way to lose credibility
here is to falsely and authoritatively proclaim that something isn’t possible
without having done the work to back it up.

On the flip side, if you see something pronounced as impossible without the
supporting documentation, ask for the documentation. If you see this happening
and fail to ask for the work to back it up, you have lowered our bar for
technical rigor.

###     Written communication

Our standard of “Write important things down” doesn’t mean “record actions
already taken.”

The most important function of writing is as a tool for thinking. It follows
that writing should almost always precede action, particularly in software
development.

Paul Graham explained this nicely in an essay that I’ve pulled passages from
below:

“Writing about something, even something you know well, usually shows you that
you didn't know it as well as you thought. Putting ideas into words is a severe
test.

Once you publish something, the convention is that whatever you wrote was what
you thought before you wrote it. These were your ideas, and now you've expressed
them. But you know this isn't true.

It's not just having to commit your ideas to specific words that makes writing
so exacting. The real test is reading what you've written. You have to pretend
to be a neutral reader who knows nothing of what's in your head, only what you
wrote.

There may exist people whose thoughts are so perfectly formed that they just
flow straight into words. But I've never known anyone who could do this, and if
I met someone who said they could, it would seem evidence of their limitations
rather than their ability. Indeed, this is a trope in movies: the guy who claims
to have a plan for doing some difficult thing, and who when questioned further,
taps his head and says "It's all up here." Everyone watching the movie knows
what that means. At best the plan is vague and incomplete. Very likely there's
some undiscovered flaw that invalidates it completely.

In precisely defined domains it's possible to form complete ideas in your head.
People can play chess in their heads, for example. And mathematicians can do
some amount of math in their heads, though they don't seem to feel sure of a
proof over a certain length till they write it down. But this only seems
possible with ideas you can express in a formal language.

The reason I've spent so long establishing this rather obvious point is that it
leads to another that many people will find shocking. If writing down your ideas
always makes them more precise and more complete, then no one who hasn't written
about a topic has fully formed ideas about it. And someone who never writes has
no fully formed ideas about anything nontrivial.

It feels to them as if they do, especially if they're not in the habit of
critically examining their own thinking. Ideas can feel complete. It's only when
you try to put them into words that you discover they're not. So if you never
subject your ideas to that test, you'll not only never have fully formed ideas,
but also never realize it.

Putting ideas into words is certainly no guarantee that they'll be right. Far
from it. But though it's not a sufficient condition, it is a necessary one.”

Writing a doc is not a perfunctory gesture, and asking someone for a doc on
something is not a punishment or a mechanism for control. Writing a doc is a way
of:

* surfacing requirements and assumptions, and

* driving clarity of reasoning stemming from those requirements and assumptions.

Without this step, our software has little hope of delivering the results we
want over the long term.

Note that a doc doesn’t necessarily have to take the form of prose – in some
cases, the right format for a doc could be a proposed API spec with bullet point
lists of constraints, principles, or requirements. The goal of a doc is to reify
your thinking and to share it with others.

As a final thought, not everyone has to write docs here. Some people just want
to execute, and there is plenty of room for that, too – but if you just want to
execute, you’ll be executing on the plan, architecture, or implementation
described in someone else’s doc. Our domain is too complex, and our ambitions
are too large to build software willy-nilly.
