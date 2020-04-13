---
title: Building Digital Tools Assisting Escape Room Maintainers \break
  \large Survey and Analysis Stage, COM3610
subtitle: 
author: |
  Simon Fish | Supervisor: Andrew Stratton \
  This report is submitted in partial fulfilment of the requirement for \
  the degree of Computer Science with a Year in Industry by Simon Fish.
geometry: margin=1in
papersize: a4
links-as-notes: true
bibliography: [bibliography.bib]
link-citations: true
table-of-contents: true
documentclass: book
---
\frontmatter
<!-- First page -->
\hspace{0pt}
\vfill
### Signed Declaration

\begin{center}
All sentences or passages quoted in this report from other people's work have been specifically acknowledged by clear cross-referencing to author, work and page(s). Any illustrations that are not the work of the author 
of this report have been used with the explicit permission of the originator and
are specifically acknowledged. I understand that failure to do this amounts to
plagiarism and will be considered grounds for failure in this project and the
degree examination as a whole.

Simon Fish
\end{center}
\vfill
\hspace{0pt}
\pagebreak
<!-- Abstract -->
<!-- This should be two or three short paragraphs (100-150 words total), summarising the report. A suggested flow is background, project aims, and achievements to date. It should not simply be a restatement of the original project outline. -->
### Abstract

<!-- - explain topic -->
Escape rooms are physical, interactive experiences in which a group of participants must solve puzzles to escape a locked room, solve a mystery, or otherwise meet some goal in a particular timespan.
<!-- - explain content -->
This report uses various studies into applications of escape rooms to discuss the priorities of well-made escape games, particularly with regards to the inclusion of technology. It also marks my current progress in research into my dissertation topic as expressed in the title.
<!-- - explain highlights -->
It focuses on the difficulties in applying technology in escape rooms and 
priorities that should be held in order to mitigate these.
<!-- - explain purpose of paper -->
On this basis, it serves to document universal requirements to bear in mind when
developing hardware or software for escape rooms.

<!-- Contents -->
\tableofcontents
\mainmatter
# Introduction

<!--
- set the scene for the project by giving a little relevant background information - try to grab the reader's interest early
- clearly elucidate the aims and objectives of the project and the constraints that might affect the way in which the project is carried out. If the project involves the solution of a specific problem or the production of a specific system this should be clearly specified in an informal way
- summarise the remaining chapters of the report, in effect giving the reader an overview of what is to come
-->

The aim of this project is to build tested tools to meet the needs of escape 
room maintainers. Research will be focused towards exploring the needs of escape
room maintainers, such that a product can be designed and built to target some
subset of these needs. These needs may be related to various issues - such as 
making sure a timer is visible to the group, or to processes that currently take
more time than necessary, such as posting photos of teams to social media 
[@liam2019].
<!-- TODO: Need to rejig now I know what I'm doing -->

In order to guide the focus of my project, I will use this paper to identify and
discuss the features of escape rooms and their implementation across existing
publications. I intend to do so guided by my chosen research questions. This is 
expected to reveal requirements for developing tools for escape room maintainers
across industries.

## Research Questions

I have identified two research questions, which this stage of the project will be focused towards answering:

**RQ1**: What has been reported about concepts used in escape rooms applied in different environments?   
**RQ2**: Based on this, what can we establish as the requirements for escape games, independent of their environment?

# Background and Motivation

<!--
- explain escape rooms, inc origin (nicholson)
- why are you doing your lit review on escape rooms?
-->

Escape rooms are physical, interactive experiences in which a group of
participants must solve puzzles to escape a locked room, solve a mystery, or
otherwise meet some goal in a particular timespan. They are a phenomenon that
has existed since around 2007 [@nicholson2015peeking], and are a growing
industry. Escape rooms are run both by enthusiasts as solo ventures, and as
franchises across the country. Nicholson [-@nicholson2015peeking] documents
escape rooms as the culmination of a variety of media. Nicholson identifies
puzzle hunts as team-based problem-solving challenges<!-- TODO: is this a quote?
-->, which, with treasure hunts, appears most similar to escape rooms. Various
others have lent features to escape rooms, such as immersion in a story as the
"hero", which @duplessie2013go reports as being something participants enjoy.
This is embodied by live-action roleplaying, another inspiration for the genre
[@nicholson2015peeking]. Nicholson presents the precursors to escape rooms in
further depth in his paper - Figure 2.1 summarises these.

![Nicholson (2019) presents the precursors to, and inspirations for, the escape room phenomenon in this diagram. Adapted with permission from Nicholson, Scott. 2015. “Peeking Behind the Locked Door: A Survey of Escape Room Facilities.” *White paper available online at http://scottnicholson.com/pubs/erfacwhite.pdf*.](nicholson-figure.svg)

Escape rooms have grown popular in many locations across the world as a
recreational activity [@nicholson2015peeking; @stasiak2016escape], even serving
as a tourist attraction [@dilek2018real]. Nicholson reports that the *Real
Escape Game* by SCRAP was the earliest well-documented activity branded as such.
SCRAP has gone on to develop escape rooms at a much larger scale than the
typical escape room, which serves teams of an average size of 4.58 people
[@nicholson2015peeking].

My goal in writing this literature survey is to understand not only the needs of
the commercial escape room industry, but also the differing requirements for the
application of escape rooms in education and corporate contexts. The major
difference between these contexts is that the commercial escape room industry is
most regularly founded on permanent fixtures, and educational escape rooms are
often applied in a classroom environment, which can imply more limited space and
the need to tear down the room after it has been completed. These different
environments dictate some differences between escape room experiences. However,
as I intend to show in the literature survey, inspiration can be taken from both
contrasting environments and applied universally.

# Literature Survey

Escape room maintainers are able to apply technology to varying degrees. On the
outside of the escape room experience, maintainers implement leaderboards, share
team photos to social media, and interact with the team via a screen or handheld
transceiver in the room. Inside the room, entire puzzles can be based on
technology, if the owner has the necessary expertise. Some more unique
applications within the room are also possible, such as using a hidden camera to
take a photo of the team, apply filters, and display the photo among works of
art as demonstrated in [The Gallery](https://escapist.nl/en/), which I visited
in July 2019. However, there is a general aversion to the use of technology in
escape rooms, for a variety of reasons. @liam2019 suggests that the time
investment, reliability, and necessary expertise are some of the greatest
contributing factors. @duplessie2013go approaches this from the perspective of
immersion - with 70% of escape room games being purely physical activities
[@nicholson2015peeking], DuPlessie recommends movement away from what he calls
the "glowing rectangles" as our medium of choice.

The increasing application of IT in education means that computers are often
part of the school environment, and can be used as a tool when building an
escape room experience for educational purposes. Several studies cover the use
of escape rooms as a means for education [@lopezuse; @rouse2017lessons;
@peleg2019lab; @beguin2019computer]. @rouse2017lessons applied technology to an
escape room in the classroom using a game loaded from a memory stick. This
application seems understandable, as Rouse's audience was likely to have some
basic level of expertise in, and enthusiasm for, handling computers as part of
the digital native generation. However, in practice, it brings to mind the image
of a small group of people crowding around a screen. @liam2019 warns against
situations like this, saying that visibility of the puzzle to the entire team
should be a priority. 

<!-- TODO: Reshuffle this paragraph? -->
However, poor implementation does not mean technology should not be excluded
from escape room environments outright. Instead, I feel technology has the
potential to inspire change in escape rooms. Escape rooms and technology are
inherently linked - digital escape-the-room games such as *Myst* precede and
inspire physical escape rooms [@nicholson2015peeking]. These forms of escape
room evade a shortfall that is one of physical escape room maintainers' greatest
anathemas - resetting these rooms is as simple as resetting the game. Whether
this is done by restarting an attempt, restarting the game, or removing save
files and starting over, it is often trivial compared to how long it takes to
reset escape rooms. @liam2019 suggests that resetting rooms can often take as
long as 15 minutes, and that it is something escape room maintainers seek to
optimise; the shorter a reset takes, the more time is available to welcome
customers.

Commercial escape rooms are often permanent fixtures. This means that more
immersive environments and more complex physical puzzles can be built. However,
puzzles of a physical nature usually need to be reset by the room owner back to
their original state, so that more than one group can attend a room in the same
day. Contrary to this, escape rooms built in a classroom environment are usually
of a temporary nature, and may even try to allow for multiple groups to attempt
the room at once, at the cost of immersion and interactivity. A study by
@lopezuse organised its puzzles in a manner whereby puzzles could be completed
in any order, allowing multiple groups to attend the room at once. One example
puzzle given in the study was an exercise likely done on paper - exercises in
this form make resets trivial, as a fresh worksheet is all that is necessary,
but they also demonstrate the lack of immersion. Commercial escape rooms
regularly employ more physical interaction - 78% of escape rooms employ a search
for physical objects as part of the experience [@nicholson2015peeking]. Some
varieties of commercial escape room visit the other end of this spectrum, such
as those developed by Tuzak, an Istanbul company developing portable escape
games [@gunduz2018preventing]. Portable or temporary escape games often trade
immersion for greater logical challenge.

Application of technology in escape rooms comes with some uncertainty, and a
break in the flow of the escape room experience can shatter participants'
immersion and lead to negative reviews [@liam2019]. This also creates some
difficulty when it comes to visibility - unless monitors are suitably placed and
large enough to be viewed by a full party, the whole team may not be able to
interface with a puzzle that applies technology. This is particularly an issue
if a single typical workstation is set up - @nicholson2015peeking warns of the
danger of removing just one player from the "mental space" of the team.

@liam2019 theorises that VR escape rooms such as [EXIT
VR](https://exit-vr.de/en/) may be the next stage for the industry, which allow
immersive rooms to be created while effectively eliminating the issue of
resetting the room as above. This would bring the escape room cycle full circle,
reincarnating the modern wave of physical escape rooms in the digital form that
inspired them.

While the escape room industry cautiously explores the "glowing rectangles"
@duplessie2013go warns against, the video games industry sometimes takes small
strides to recede from them. This has resulted in concepts that escape rooms,
and interactive experiences of all kinds, can learn from. [*Keep Talking and
Nobody Explodes*](https://keeptalkinggame.com/) focuses on asynchronous
gameplay, in which one player must defuse a bomb while the others guide them
using the [bomb's manual](https://bombmanual.com). Conceptually, the game shares
fundamentals with escape rooms, but what is of most importance here is that the
foremost task in the game is communication. Escape rooms already apply
asynchronous gameplay - The Lockup Escape Rooms' *Meltdown* [@liam2019] begins
with most of the party in individual chambers, with the designated 'leader'
communicating from outside - but *Keep Talking and Nobody Explodes* demonstrates
that with technology, it is possible in almost any location.
[*1-2-Switch*](https://www.nintendo.co.uk/Games/Nintendo-Switch/1-2-Switch-1173186.html)
similarly pulls away from the screen, with the majority of its minigames relying
on what is done physically with the Joy-Con controller and instructing players
to face their opponent directly. It is an effective example of how to apply
technology in a way that does not lock singular players into staring at a
screen.

In summary, technology brings a variety of benefits, from quick resets when used
as part of a puzzle to interesting and reactive ideas that may not otherwise be
possible. Many ideas and inspirations have been discussed here. However, care
must be taken to ensure that if the implementation separates one player from the
group, it is applied in an engaging manner. Escape room maintainers value
reliability, with negative reviews being the consequence for ill implementation
[@liam2019]. The strength of escape rooms as an educational tool has also been
demonstrated here, which is worth consideration when building for the escape
room industry.

## Keywords

I identified the following keywords for use in my search. The search was
conducted using the Google Scholar search engine.

- escape room / puzzle hunt
- owner / host
- implementation
- software
- virtual reality
- education / classroom

This led to the following searches.

- escape room owner
- escape room host
- escape room software
- escape room education
- escape room classroom
- virtual reality escape room
- portable escape room

Additional searches were made based on discoveries such as escapED
[@clarke2016escaped] and Breakout EDU @breakoutedu to see where they had been
applied.

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

# Design

<!--
This should explain the design technique chosen (and justify why it is
appropriate) from the various ones available; it should select a suitable subset
of the things described in the analysis chapter and develop a design. Where
trade-offs exist between different designs, the chosen approach should be
justified. Suitable diagram-techniques (e.g. UML, other drawings) should be used
where appropriate. If a method is applied selectively, explain which parts were
used and why. Experimental projects should pay careful attention to control
conditions, samples selected, etc. to ensure a valid result.
-->

# Implementation and Testing

<!--
In addition to illustrating "coding traps", this should highlight particular
novel aspects to algorithms. Testing should be according to the scheme presented
in the Analysis chapter and should follow some suitable model - e.g. category
partition, state machine-based. Both functional testing and user-acceptance
testing are appropriate. For experimental/investigative projects, techniques
developed should be evaluated against a standard result set for calibration, as
well as the "live" data set. For theoretical projects, the relative
power/expressiveness of the theory should be evaluated with respect to competing
approaches.
-->

RSpec was employed for testing.

## Time constraints

If time were not an issue, I would have employed the following:

### Test coverage

SimpleCov was the standard at UKCloud with regards to coverage testing. I would
have employed this and aimed for at least 80% test coverage. In the end, my
testing strategy was to cover only novel backend functionality that sat
somewhere outside the standard Rails CRUD mold. This included:

- additional routes created beyond a standard Rails scaffold, such as those that
  make the current user a maintainer/enthusiast or those that remove image
  associations from a `Clear` or `EscapeGame` object
- secured routes - tests were created that challenged whether some attacking
  user could change a user ID in a form to steal ownership of a record
- some validations, such as those relating to limits on the number of image
  uploads for `EscapeGame`s and `Clear`s.
- some queries, particularly those relating to user privacy and escape room
  hiding.


- frontend testing with Jest

# Results and Discussion

<!--
The main results of your work should be presented, together with critical discussion. The chapter should cover three things (although these would not be used as section headings): 

    Findings - present all the results (products, experimental findings, theories, etc.) generated during the project. This may also include some off-topic findings that were not expected, or which were side-effects of other explorations.
    Goals achieved - describes the degree to which the findings support the original objectives laid out for the project. The goals may be partially or fully achieved, or exceeded. An experimental project may prove, or disprove the original thesis. A theoretical project may cover some or all of the example cases. Note that reporting of failures to achieve goals is important since a fundamental feature of the assessment procedures is that the processes (how you went about your project) are often as important as the products of the project.
    Further work - describes two things: firstly, new areas of investigation prompted by developments in this project, and secondly parts of the current work which were not completed due to time constraints and/or problems encountered.
-->

The product of my development process is a web application written in Ruby on
Rails, with React.js used to generate and drive some areas of the frontend.
Blacklight allows users to log in through the Auth0 authentication service only,
though this allows for plenty of expansion in and of itself. Users are prompted
to define themselves as an escape game maintainer, enthusiast, or both. This
only affects the user's experience, not their level of access.

Escape game maintainers have options revealed to them to create and manage
escape games. These escape games have an array of associated data that can be
added, including the expected time to complete them, their location (by way of
Google Maps integration), images, and a Markdown-compatible extended
description. Listings can also be hidden from view and access via a checkbox on
the editing form.

Enthusiasts can browse these escape games and mark them as cleared by selecting
the lock icon on any listing. This is consistent across the site. Doing so adds
the escape game to the 'My Cleared Games' section of the site for that user.
There, users can upload photos to associate with each escape room, which also
appear to the left of the list in a singular photo gallery.

Users have profiles where they can write a bio, set their location, and link to
their own website. Here, those interested can see all escape games by a single
maintainer, and all escape games cleared by a user. Which of these is shown
depends on whether they have self-assigned as a maintainer, enthusiast, or both.

I have been able to make good progress in defining my scope this semester. The
most important thing I have had to do is to get in contact with the escape room
community - I have been able to reach out to all of Sheffield's escape rooms,
though only one has returned any interest in supporting the project. This was
The Lockup Escape Rooms in Sheffield.

I got in contact early in November, which was a busy time for all rooms. In
initial communications with The Lockup, Liam offered a free attempt at one of
the two rooms offered pro bono. I took up this offer on the 29th November with a
group of friends, tackling the *Meltdown* escape room and its hard mode option
in 53 minutes and 57 seconds. The experience was enjoyable for all, and I was
interested to see some science applied within the room - one of the puzzles
relied on mixing chemicals and using the colours of the resultant reactions to
solve the next puzzle. 
<!-- TODO: quote nicholson. This puzzle seemed to dabble in needing real-world knowledge, but was also heavily guided, so it seemed the focus was more on doing something interactive and captivating rather than difficult in this instance. -->

Before this, I met with Liam on the 20th November to discuss the challenges he
faces as an escape room owner, and his philosophy in developing the rooms he
offers at The Lockup. Engagement, visibility and breakability all inspire his
approach: the entire party must be able to interact with, and be engaged by,
puzzles in the room, and the puzzles should not take long to reset to their
initial state for the next party that attends the escape room [@liam2019]. Liam
and I discussed some areas that could be targeted, which inspired a survey I
sent to the Facebook group created by @nicholson2015peeking.

Nicholson runs a [Facebook
group](https://www.facebook.com/groups/608883549212939/) for escape room
enthusiasts, encompassing both maintainers and participants, to which I sought
and gained access as part of my work. The majority of posts during research were
from enthusiasts who would report back from rooms they have attended, though I
have seen posts about types of puzzles that can be implemented. I chose to
survey this group, as it appeared to be a central hub for what seemed to be a
sparse online community. 

After setting my focus, I decided my solution would take the form of a web
application. Ruby on Rails was chosen as the development platform. The QOC
analysis below was the source of this decision, in which I weighed up other
potential candidates such as Iron (Rust), ASP.NET MVC 5 (C#), and Next.js.

|  | **Priority** | 4 | 5 | 4 | 2 | 4 | 3 | 3 | 5 |
|:-----:|:----------------:|:-----------:|:-------------:|:---------:|:-------------:|:--------------------------:|:----------------------------:|:---------:|:-----------------:|
|  | **Criteria** | Famili-<br>arity | Documen-<br>tation | Sta-<br>bility | Linux support | Available Docker resources | Developer tools (generators) | Comm-<br>unity | Develop-<br>ment cycle |
| 145 | Rails (ERB) | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 4 |
| 108 | Next.js | 3 | 4 | 3 | 5 | 5 | 1 | 2 | 5 |
| 109 | ASP.NET MVC 5 | 2 | 5 | 5 | 1 | 5 | 5 | 3 | 2 |
| 66 | Iron | 1 | 2 | 1 | 5 | 3 | 1 | 1 | 4 |
| 130 | Rails (React) | 4 | 4 | 5 | 5 | 5 | 3 | 5 | 4 |

Originally, I weighed ERB and React against one another as view engines. This
estimation was taken on the assumption that I would use React even where
interactivity and state management were not required. In hindsight, this
approach would have slowed development. Instead, my final approach of applying
React only where functional improved the quality of the application without
hampering development time.

# Bibliography
