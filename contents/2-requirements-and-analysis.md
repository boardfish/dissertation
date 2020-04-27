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

To find some insight into the challenges escape room maintainers face, I met
with Liam Woff on the 20th November. Liam and I discussed some areas that could
be targeted, which inspired a survey I sent to the Facebook group created by
@nicholson2015peeking. This group is for escape room enthusiasts, of which a
subset are maintainers. I sought and gained access to the group as part of my
work. The majority of posts during research were from enthusiasts who would
report back from rooms they have attended, though I have seen posts about types
of puzzles that can be implemented. I chose to survey this group as it appeared
to be a central hub for what seemed, to an outsider, to be a sparse online
community. 

From the seven responses received, the following conclusions were drawn:

- The majority of the group already shares photos online, but those that do not
  are all interested by the prospect of it
- Memberships, in-character communications, advertisement among other escape
  rooms, and participant metrics are all of interest
- Memberships are agreed upon by those interested as something that should not
  be done without the involvement of technology

Comments of note included that use of technology in escape rooms is
*"limit[ed]/eliminate[d]"* due to loss of revenue in the event of failure without
failover - *"dependability and available work around (sic)"* were agreed to be of importance. Additionally, investment in technology as a showpiece is avoided as
*"each room only lasts 1-[1.5] years"* in that particular offering.

I was able to elicit a direction from these conclusions - the idea of a social
network shared by escape room maintainers and enthusiasts allowed me to
potentially target several of these factors at once. In particular, the purpose
of this social network would be to allow escape rooms to advertise among others
of their ilk and share photos. I concluded my analysis of the results by setting
a goal statement.

---

**Goal Statement**

To design and build a system that:

- allows escape room maintainers to share photos with their community
- allows escape room maintainers to advertise among other escape rooms
- allows escape room enthusiasts to discover new escape rooms to tackle
- allows escape room enthusiasts to track which escape rooms they have cleared

---

With these as an initial guide, I began to set requirements using the MSCW
system (see Appendix I), aiming to complete all defined as **Must**- and
**Should**-Have by the end of the project. Though these were not formally
defined and did not dictate the order in which I completed tasks, I thought on
what I had learned during my year in industry - while haste was of the essence,
I made strides to emulate the software development process as I had seen it
firsthand.

Stories were written with parts of the goal statement ('epics') in mind and
estimated according to their complexity using a modified Fibonacci scale. In
agile software development, complexity estimates are preferred to time estimates
as the former are easier to settle upon [@karlesky2008agile]. Stories with
estimates any greater than 13 would need to be broken down into smaller stories.
This was a principle I kept in mind from my year in industry. Atlassian suggests
a differing scale and limit, but the basic principle of keeping stories small
and manageable is there. Velocity is of the essence, and smaller tickets assist
with that. <!-- https://www.atlassian.com/agile/project-management/estimation -->

Another factor that was kept in mind when creating stories was keeping them
open. Stories, as often as possible, would need to describe what the user would
wish to achieve, as opposed to what the developer working on them should aim to
do. Framing stories from this perspective allowed their implementation to remain
open to change and interpretation.

As mentioned in the previous chapter, I have had more hands-on experience with
Scrum than with Kanban. Kanban is employed when more flexibility is desired. It
prioritises throughput and encourages a "culture of 'done'" by enforcing
work-in-progress limits [@rehkopf2018kanban]. With this in mind, it would be
difficult to set more than two development milestones. Treating each MSCW
category as an epic and taking the amount of time necessary for work on this
report and my other modules into account, I aimed to work on the project for a
month, devoting two to three weeks to each milestone.

I figured that each milestone would take a similar amount of time - while Rails'
built-in generators would likely ease the burden of scaffolding the initial
functionality, setting that groundwork in the right way would take slow and
careful decisions. Scaffolds would dictate the flow of the rest of the project
to a degree. In the end, the following deadlines were decided:

- **Development commences** March 12th
- **Must milestone completed** March 26th *(actual completion date: March 24th)*
- **Should milestone completed** April 16th *(actual completion date: April
  13th)*

![A Gantt chart representing my set goals versus the final completion
dates.](gantt-chart.svg)

<!-- FIXME: Text not visible and the damn thing is an eyesore. -->

After setting my focus, I decided my solution would take the form of a web
application. Ruby on Rails was chosen as the development platform. The QOC
analysis below was the source of this decision, in which I weighed up other
potential candidates such as Iron (Rust), ASP.NET MVC 5 (C#), and Next.js.

\pagebreak

|  | **Priority** | 4 | 5 | 4 | 2 | 4 | 3 | 3 | 5 |
|:-----:|:----------------:|:-----------:|:-------------:|:---------:|:-------------:|:--------------------------:|:----------------------------:|:---------:|:-----------------:|
| **Total** | **\hfill Tool \hfill \rotatebox{90}{Criteria}** | \rotatebox{90}{Familiarity} | \rotatebox{90}{Documentation} | \rotatebox{90}{Stability} | \rotatebox{90}{Linux support} | \rotatebox{90}{Docker resources} | \rotatebox{90}{Developer tools (generators)} | \rotatebox{90}{Community} | \rotatebox{90}{Development cycle} |
| 145 | Rails (ERB) | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 4 |
| 108 | Next.js | 3 | 4 | 3 | 5 | 5 | 1 | 2 | 5 |
| 109 | ASP.NET MVC 5 | 2 | 5 | 5 | 1 | 5 | 5 | 3 | 2 |
| 66 | Iron | 1 | 2 | 1 | 5 | 3 | 1 | 1 | 4 |
| 130 | Rails (React) | 4 | 4 | 5 | 5 | 5 | 3 | 5 | 4 |

Table: QOC chart [@maclean1991questions] for choice of stack, with priority
values and totals revealed.

Originally, I weighed ERB and React against one another as view engines. This
estimation was taken on the assumption that I would use React even where
interactivity and state management were not required. In hindsight, this
approach would have slowed development. Instead, my final decision to apply
React only where functional improved the quality of the application without
hampering development time.

However, doing so came at the cost of accessibility. With wider prior knowledge,
perhaps this not have been the case - the web design strategy of progressive
enhancement [@champeon2020web], in combination with use of the WAI-ARIA standard
[@aria], could have been used to mitigate this from the outset. I was not aware
of progressive enhancement as a priority during development. I realise that it
is not practical to dismiss the absence of progressive enhancement - after all,
1.1% of users are not getting JS enhancements [@herlihy2013how].
