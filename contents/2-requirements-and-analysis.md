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

The initial specification for the project was a set of networked
microcontrollers/systems-on-chips that would unite to track the escape room
experience. This was abandoned as the idea of building an escape room, even in
the form of a prototype, was out of scope. To seal this decision, my literature
survey concluded that digital uptake in escape rooms may be middling due to the
inherent risk and time involved.

To find some insight into the challenges escape room maintainers face, I met
with the maintainer of the Lockup Escape Rooms in Sheffield on the 20th
November. They had around two years' experience in maintaining their escape
rooms at that time. We discussed some areas that could be targeted and some
ideas that I had previously prepared. This would go on to inspire a survey I
would distribute to the wider community of maintainers ([Appendix II][Appendix
II: Escape Room Owner Survey]).

The survey used the ideas The Lockup Escape Rooms and I had discussed. The
Facebook group created by @nicholson2015peeking would serve as the audience for
the survey. It is for escape room enthusiasts worldwide, and includes a smaller
number of maintainers. I chose to survey this group as it appeared to be a
central hub for what seemed, to an outsider, to be a sparse online community.
The survey needed to be agreed to by the group moderators before being sent out.
Hearing the opinions of an escape room maintainer helped me to anticipate the
potential results and begin planning. 

These results were drawn from the seven responses received ([Appendix
III][Appendix III: Collated Survey Results]):

- Four maintainers already share photos online, but the remaining three
  are all interested by the prospect of it
- Memberships, in-character communications, advertisement among other escape
  rooms, and participant metrics are all of interest to at least five members of
  the group
- Memberships are agreed upon by the five interested parties as something that
  should not be done without the involvement of technology
- Ease of use *always* influences each maintainer's decision when investing in
  technical solutions to problems
- Reliability *always* influences all bar one of the group's decisions in the
  above

Notable comments included that one maintainer sought to *"strictly
limit/eliminate the use of"* technology in their escape rooms. The following
reasoning was given for these decisions:

- *"Losing revenue"* in the event of failure without failover.  Switchover that
  necessitates *"an electrician or computer programer (sic)"* was specified as a
  potential cause of revenue loss. Another maintainer agreed that
  *"dependability and available work around (sic)"* were agreed to be of
  importance. This aligned with my discussion with Lockup Escape Rooms.
- *"Each room only lasts 1--1½ years"*, reducing the maintainer's budget for
  props for each room. *"[The maintainers] do not invest as much into props
  unless they can be reused in another game"*, meaning investment in technology
  as a showpiece is generally avoided in that particular offering.

I was able to elicit a direction from these results---the idea of a social
network shared by escape room maintainers and enthusiasts allowed me to
potentially target several of these factors at once. Primarily, this social
network would allow escape rooms to advertise among others of their ilk and
share photos. I concluded my analysis of the results by setting a goal
statement.

---

**Goal Statement**

To design and build a system that:

- allows escape room maintainers to share photos with their community
- allows escape room maintainers to advertise among other escape rooms
- allows escape room enthusiasts to discover new escape rooms to tackle
- allows escape room enthusiasts to track which escape rooms they have cleared

---

With these as an initial guide, I began to set requirements using the MSCW
system (see [Appendix I][Appendix I: Initial Requirements]), aiming to complete
all defined as **Must**- and **Should**-Have by the end of the project. User
stories were written with parts of the goal statement ('epics') in mind and
estimated according to their complexity using a modified Fibonacci scale.

In agile software development, complexity estimates are preferred to time
estimates as the former are easier to settle upon [@karlesky2008agile]. Stories
with estimates any greater than 13 would need to be broken down into smaller
stories. This was a principle employed by my team and I on my year in industry.
@atlassian suggests a differing scale and limit, but in either case, it is a
priority to keep stories small and manageable. Velocity is of the essence, and
smaller tickets assist with that.

Another factor that was kept in mind when creating stories was keeping them open
to interpretation. Stories, as often as possible, would need to describe what
the user would wish to achieve, as opposed to what the developer working on them
should aim to do. Framing stories from this perspective allowed their
implementation to remain open to change and interpretation. By not enforcing
how a ticket should be implemented until it is worked on, it could be ensured
that the right tool for the job would be chosen.

Kanban prioritises throughput and encourages a *"culture of 'done'"* by
enforcing work-in-progress limits [@rehkopf2018kanban]. It is often employed
when more flexibility is desired---this drove my decision to use is in spite of
previous experience with Scrum. When defining personal deadlines, it was
necessary to take the amount of time needed for work on this dissertation paper
and my other modules into account. With this in mind, the scope for the project
was limited to tackling the Must- and Should-Have tickets. These were defined as
the development milestones. I aimed to work on the project for around a month
and a half.

Two to three weeks were devoted to each milestone. I figured that each milestone
would take a similar amount of time---while Rails' built-in generators would
likely ease the burden of scaffolding the initial functionality, setting that
groundwork in the right way would take slow and careful design decisions. These
decisions would dictate the flow of the rest of the project. In the end, the
following deadlines were decided:

- **Development commences** March 12th
- **Must milestone completed** March 26th *(actual completion date: March 24th)*
- **Should milestone completed** April 16th *(actual completion date: April
  13th)*

![A Gantt chart representing my set goals versus the final completion
dates.](gantt-chart.svg)

After setting my focus, I decided my solution would take the form of a web
application. Ruby on Rails was chosen as the development platform. The QOC
analysis below was the source of this decision, in which I weighed up other
potential candidates such as Iron (Rust), ASP.NET MVC 5 (C#), and Next.js (JS).

|  | **Priority** | 4 | 5 | 4 | 2 | 4 | 3 | 3 | 5 |
|:-----:|:----------------:|:-----------:|:-------------:|:---------:|:-------------:|:--------------------------:|:----------------------------:|:---------:|:-----------------:|
| **Total** | **\hfill Tool \hfill \rotatebox{90}{Criteria}** | \rotatebox{90}{Familiarity} | \rotatebox{90}{Documentation} | \rotatebox{90}{Stability} | \rotatebox{90}{Linux support} | \rotatebox{90}{Docker resources} | \rotatebox{90}{Developer tools (generators)} | \rotatebox{90}{Community} | \rotatebox{90}{Development cycle} |
| 145 | Rails (ERB) | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 4 |
| 108 | Next.js | 3 | 4 | 3 | 5 | 5 | 1 | 2 | 5 |
| 109 | ASP.NET MVC 5 | 2 | 5 | 5 | 1 | 5 | 5 | 3 | 2 |
| 66 | Iron | 1 | 2 | 1 | 5 | 3 | 1 | 1 | 4 |
| 130 | Rails (React) | 4 | 4 | 5 | 5 | 5 | 3 | 5 | 4 |

: QOC chart [@maclean1991questions] for choice of stack, with priority
values and totals revealed.

I chose to prioritise documentation and speed of development cycle over all
else. With sufficient documentation and fast compile times, I would be able to
work quickly and effectively, with sufficient fallback in case of problems.
Stability and familiarity also factored into my decision strongly---I would need
to be sure that the language interface would not radically change during the
course of development, and that I would feel comfortable with the language
chosen. Docker resources were also prioritised so that less work would be
necessary to deploy the application in a container in a production environment.

Originally, ERB and React were weighed against one another as view engines. This
estimation was taken on the assumption that React would be used even where
interactivity and state management were not required. In hindsight, this
approach would have slowed development. Instead, my final decision to apply
React only where functional improved the quality of the application without
hampering development time.

However, doing so came at the cost of accessibility. With wider prior knowledge,
perhaps this may not have been the case---the web design strategy of progressive
enhancement [@champeon2020web], in combination with use of the WAI-ARIA standard
[@aria], could have been used to mitigate this from the outset. I was not aware
of progressive enhancement as a priority during development. [@herlihy2013how]
investigated that 1.1% of `gov.uk` users were not getting JS enhancements at
that time---though this may have changed in either direction over time, it is
still a significant figure and signifies the importance of the need for
`noscript` fallbacks.
