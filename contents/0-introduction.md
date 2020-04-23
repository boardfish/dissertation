
# Introduction

<!--
The introduction has several purposes. Clearly one is to set the scene for the
project by giving a little relevant background information - try to grab the
reader's interest early. Another is to clearly elucidate the aims and objectives
of the project and the constraints that might affect the way in which the
project is carried out. If the project involves the solution of a specific
problem or the production of a specific system this should be clearly specified
in an informal way. Finally, the introduction should summarise the remaining
chapters of the dissertation, in effect giving the reader an overview of what is
to come.

The type of project will dictate the content and structure of the following
chapters and you should discuss this with your supervisor. For example, for a
theoretical project it is likely that several chapters will be devoted to
constructing the theoretical foundations for the project and will consist of
your own interpretation and synthesis of existing work with suitable examples
discussed throughout. A sequence of chapters that cover theoretical framework,
conditions and assumptions and theory application and comparisons may be
appropriate. For an experimental project, the experimental goals, design,
execution and evaluation might be covered. What now follows is a typical
structure for a 'design and build' project. 

At the end of chapter 1, you should include a brief discussion of your view of
the relationship between your project, and your degree programme. In your
discussion, you should mention any advantages or challenges created by this
relationship.
-->

Escape rooms are physical, interactive experiences in which a group of
participants must solve puzzles to escape a locked room, solve a mystery, or
otherwise meet some goal in a particular timespan. They are a phenomenon that
has existed since around 2007 [@nicholson2015peeking], and are a growing
industry.

---

Please note the following definitions:

**Maintainers** refer to those who own and run escape rooms. They are
responsible for such things as building and maintaining the escape room, and
running the experience for groups. In many cases, they are also responsible for
elements of the escape room experience outside of the room itself, such as
maintaining its image on social media.

**Enthusiasts** refer to attendees of escape rooms - particularly those who take
a firm interest in them, regardless of their degree of experience. 

---

My goal in this project was to understand the needs of the commercial escape
room industry, such that a product could be developed to remedy them. Such a
product would aim to increase efficiency or expand the industry with new
capabilities. The escape room industry has a wide variation of scale in
application, from maintainers running singular escape rooms to major companies
such as SCRAP delivering escape games to dozens, if not hundreds, of people. It
also has varied contexts - escape rooms on permanent fixtures, portable escape
games, and applications in education such as EscapED [@clarke2016escaped]. It
can also be noted that during the COVID-19 pandemic taking hold at the time of
writing, maintainers are moving towards products that enthusiasts can use in
their own homes.

With a strong understanding of this in mind, and feedback from the community
itself, a product could then be designed and built to target some subset of
these needs. These needs may be related to various issues, such as making sure
a timer is visible to the participating group and maintainer, or to processes
that currently take more time than necessary, such as posting photos of teams to
social media [@liam2019].

## Research Questions

Two research questions were identified, which the literature review stage of the
project is focused towards answering:

**RQ1**: What has been reported about concepts used in escape rooms applied in
different environments?   
**RQ2**: Based on this, what can be established as the requirements for escape
games, independent of their environment?

## Relationship between Project and Degree Programme

The project did not directly tie in with any of my modules this year. I
acknowledged during research that my solution could potentially build on skills
learned from modules such as *COM3505 Internet of Things*, should my solution
have incorporated microcontroller hardware. In such an instance, I would likely
have elected to use the ESP32 microcontroller out of familiarity.

However, my approach has been influenced by learnings from software
development-focused modules such as *COM1001 Introduction to Software
Development* and *COM3420 Software Hut*. The concept of agile processes was
introduced in the former, though my experience with *COM390 Year in Industry*
presented this in a practical manner that more directly inspired my approach.
The limited time available meant that many Rails best practices were not
transferred through Software Hut - instead, many of these came through to me
during my year in industry.

My approach was not reminiscent of the Scrum process used in my team last year.
Instead, I elected to move towards use of Kanban, which would allow me to be
more flexible with my priorities and adjust my principles in light of time
constraints. This created a challenge for me. My work at UKCloud during *COM390
Year In Industry* gave me a strong set of principles regarding software
development, particularly as regards programming. I wished to include
industry-standard processes in my work, including continuous integration,
vulnerability testing, and measurement of test coverage. While I was able to
make efforts towards tackling the first two, I lament that I could not commit to
any figure on test coverage, let alone track it. In essence, my experience
during my year in industry widened the scope of my capabilities and priorities
alike, but due to time constraints, I could not apply them to the fullest.