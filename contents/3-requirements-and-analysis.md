# Requirements and Analysis

<!--
Detail the aims and objectives of your project and analyse individual parts in
detail. The analysis may cover more than is finally implemented. As a result of
the analysis, you should state what will be covered by the project and what will
not be done and why. Due consideration should also be given to how you will
evaluate your work. Evaluation is one of the most important aspects of any piece
of work and it should be thought about in the early stages. Consider tests or
experiments that can be conducted to establish the success of the work.

This should state, in a more detailed way, the objectives of the project by
requirement and the analysis should break the problem down into manageable
steps. There may be more than one suitable approach; the analysis may cover more
of the area than is finally implemented. Testing and evaluation should be given
due consideration. It is important that you state how you will evaluate your
work. For a design project it is appropriate to consider testing at the same
time as specification.
-->

The objective of the project was to build a tool for the escape room community.
The exact form in which this would come was to be dictated by the nature of the
problem - if the scenario called for a tool that would be active inside escape
rooms themselves, it would have been more likely to be hardware. At the initial
stage, this was the intent - a set of networked microcontrollers/SoCs that would
unite to track the escape room experience - but this was abandoned. The idea of
building an escape room, even in the form of a prototype, was out of scope.
Additionally, @liam2019 warned that digital uptake in traditional escape rooms
may be middling due to the inherent risk and time involvement, as discussed in
the literature survey.

I surveyed the escape room community on Facebook to determine a firmer course of
action, taking a selection of options as discussed with an escape room owner
[@liam2019] for further feedback. The Facebook group created by
@nicholson2015peeking was chosen to be surveyed. From the seven responses
received, the following conclusions were drawn:

- The majority of the group already shares photos online, but those that do not
  are all interested by the prospect of it
- Memberships, in-character communications, advertisement among other escape
  rooms, and participant metrics are all of interest
- Memberships are agreed upon by those interested as something that should not
  be done without the involvement of technology

I was able to elicit a direction from these conclusions - the idea of a social
network shared by escape room maintainers and enthusiasts allowed me to
potentially target several of these factors at once. In particular, the purpose
of this social network would be to allow escape rooms to advertise among others
of their ilk and share photos. I concluded my analysis of the results by setting
a goal statement.

---

**Goal Statement**

To design and build a system that:

- allows escape room owners to share photos with their community
- allows escape room owners to advertise among other escape rooms
- allows escape room enthusiasts to discover new escape rooms to tackle
- allows escape room enthusiasts to track which escape rooms they have cleared

---

<!-- TODO: appendix for initial requirements -->

With these as an initial guide, I began to set requirements using the MSCW
system, aiming to complete all defined as **Must**- and **Should**-Have by the
end of the project. Though these were not formally defined and did not dictate
the order in which I completed tasks, I thought on what I had learned during my
year in industry - while haste was of the essence, I made strides to emulate the
software development process as I had seen it firsthand.

Stories were written with parts of the goal statement ('epics') in mind and
estimated according to their complexity using a modified Fibonacci scale. In
agile software development, complexity estimates are preferred to time estimates
as the former are easier to settle upon [@karlesky2008agile]. Stories with
estimates any greater than 13 would need to be broken down into smaller stories.
This was a principle I kept in mind from my year in industry. Atlassian suggests
a differing scale and limit, but the basic principle of keeping stories small
and manageable is there. Velocity is of the essence, and smaller tickets assist
with that. <!-- https://www.atlassian.com/agile/project-management/estimation -->

Another factor I kept in mind when creating stories was keeping them open.
Stories, as often as possible, would need to describe what the user would wish
to achieve, as opposed to what the developer working on them should aim to do.
Framing stories from this perspective allowed me to keep their implementation
open to change and interpretation.

<!-- TODO: explain rationale behind Rails -->

My approach was not reminiscent of the Scrum process used in my team last year.
Instead, I elected to move towards a Kanban approach. Kanban is employed when
more flexibility is desired. It prioritises throughput and encourages a "culture
of 'done'" by enforcing work-in-progress limits<!--
https://www.atlassian.com/agile/kanban/wip-limits -->. With this in mind, it
would be difficult to set more than two development milestones. Treating each
MSCW category as an epic and taking the amount of time necessary for work on
this report and my other modules into account, I aimed to work on the project
for a month, devoting about two weeks to each milestone.

I figured that each milestone would take a similar amount of time - while Rails'
built-in generators would likely ease the burden of scaffolding the initial
functionality, setting that groundwork in the right way would take slow and
careful decisions. Scaffolds would dictate the flow of the rest of the project
to a degree.

Forgoing the later milestones, and many ideas that might even give Blacklight
commercial viability with them, was a difficult decision to make. However, I am
happy with the base functionality and usability that came to be.

- **Dev commenced** Mar 12th
- **Must done** Mar 26th (actual 24th)
- **Should done** Apr 16th (actual 13th)

 <!-- cite: https://www.atlassian.com/agile/kanban/kanban-vs-scrum
-->