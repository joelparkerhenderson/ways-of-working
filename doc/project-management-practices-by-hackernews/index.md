# Project management practices by Hacker News participants

https://news.ycombinator.com/item?id=16377523

Comment summaries:

* I have been through waterfall, agile, scrum, "agile", "scrum", kanban, to-do lists. Yet, I cannot point to a single style of project management as a silver bullet. However, I have come to realize the following conditions improve the probability of success: small teams made up of scary-smart accountable people, given a well-articulated objective (not solution) and are left alone without distraction. Short of this, you almost always fall in the trap of micro-management.

* Agile is still the way to go and while many organizations have started becoming more agile they are still far from being agile. In my opinion, Scrum is part of the problem and the worst of all agile methods. Its strength is certainly that it is very well defined what you have to implement to 'do' Scrum, but as the agile manifesto states, being agile means to value "Individuals and interactions over processes and tools".

* Don’t do “projects” at all. Instead, Everything is either an “enhancement” or a “defect” broken down into the smallest deployable chunk. These can have themes (epics), labels, and dependencies. Prioritize in consultation with the business, but don’t plan more than a few months ahead.

* SAFe both directly incorporated process evaluation and improvement *and* recognizes that the process starting point appropriate to different orgs in different tasks is different, and even in its framework doesn't dictate low-level team process though it describes what process combinations are common, so it seems to, as much as a canned starting-point process can be, be a fairly robust concrete implementation of Agile Manifesto values.

* I like the WhatsApp approach. Hire smart people. If a bug is found, investigate and fix it right there and then. Have a 0 bugs backlog. Minimal software footprint: don't put software you don't need in you stackr. No QA team, no waterfall, no kanbans, no scrums. Lots of small, simple deploys.

* I go for a Kanban-like approach augmented by a tool that is more than Trello. Clubhouse is my personal favorite. Also, a trend/mindset that should have taken over (but hasn't yet) is http://asyncmanifesto.org/ . Generally it is a must if any % of your dev team is remote-based.

* For an enterprise customer like a bank, or for a mixed hardware/software environment, you may see Kanban/Agile for little sub-teams, but the actual project will be running under Prince2. Prince2 is pretty flexible about letting you run individual tasks the way you want, just don't expect to be able to reshape requirements on the fly without having to justify how that affects the 'business case'.

* I have started practising Getting Things Done (GTD) and have found it great so far. I recommend you pick up David Allen's two books. Takes a weekend to cover them properly and another few days to shift approaches.

* Kanban. Done correctly, it allows the product owner or manager, to rearrange priorities dynamically as long as they aren't in progress, it surfaces where resource or process issues are causing a bottleneck and there isn't as much ceremony. ...  Kanban is definitely much better than Scrum. ... One of the steps in the Kanban process, before software goes to Production is UAT. If the UAT WIP Limit gets above a defined threshold it's time to do a demo and bug the people who have to do the final approval.

* Agile and Scrum (big A/S) have faded into agile and scrum (little a/s). The 'One True and Holy Process' has faded into a set of processes that organization iterates on. The process should be fit to the team/organization. The team/organization should not be fit to the process. Personally, I have had good luck with a mix of kanban, with multipart estimation and Monte-Carlo simulations for projecting completion dates. So far its worked well and managing change while being able to predict completion times.

*  Check out OKRs for tying back longer-term planning into shorter-term deliverables: https://blog.realkinetic.com/okr-process-489891e6b6a8

* For large efforts, I've always subscribed to "define waterfall, build agile". If you don't really hammer away up-front on all the possible avenues stakeholders want to explore in an end product and get those fully listed out and vetted before even the first line of code is written, then the "agile" portion should be simply changing directions on which of those things are considered most critical to delivering a minimum viable product based on where you currently are in the overall effort.

* For projects as service (like consulting) use kanban, but incorporate epics and sprints where epics are communicated to the client as just "phases" and sprints are internal to the developer team. Your Project Manager (PM) should also be able to do at least some solutioning. The best projects i've worked on where ones where the PM was also the Solution Architect (SA). Every projects gets a tech lead (TL). This is the PM/SAs right hand goto person. The TL handles the design and implementation of the SAs vision. They also manage task delegation to the dev team, and acts as their escalation point. The TL must be able to get up in front of the client and explain technical jargon in a way the client understands it. I've seen the above work very well in consulting for projects in the $2-3M budget range.

* Important questions are, Do you have distributed teams vs collocated teams? The maturity of the team members, years of experiences in IT, working together? current collaboration and communication challenges between team members, intra teams and teams and management? If you spend time in analyzing these questions, you have good chance of success.
