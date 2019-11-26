---
title: Building Digital Tools Assisting Escape Room Owners \
  \large Survey and Analysis Stage, COM3610
subtitle: 
author: |
  Simon Fish | Supervisor: Andrew Stratton \
  This report is submitted in partial fulfilment of the requirement for \
  the degree of Computer Science with a Year in Industry by Simon Fish.
geometry: margin=1in
papersize: a4
links-as-notes: true
bibliography: bibliography.bib
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
All sentences or passages quoted in this report from other people's work have been specifically acknowledged by clear cross-referencing to author, work and page(s). Any illustrations that are not the work of the author of this report have been used with the explicit permission of the originator and are specifically acknowledged. I understand that failure to do this amounts to plagiarism and will be considered grounds for failure in this project and the degree examination as a whole.

Simon Fish
\end{center}
\vfill
\hspace{0pt}
\pagebreak
<!-- Abstract -->
<!-- This should be two or three short paragraphs (100-150 words total), summarising the report. A suggested flow is background, project aims, and achievements to date. It should not simply be a restatement of the original project outline. -->
### Abstract

<!-- TODO: -->

<!-- Contents -->
\tableofcontents
\mainmatter
# Introduction

<!--
- set the scene for the project by giving a little relevant background information - try to grab the reader's interest early
- clearly elucidate the aims and objectives of the project and the constraints that might affect the way in which the project is carried out. If the project involves the solution of a specific problem or the production of a specific system this should be clearly specified in an informal way
- summarise the remaining chapters of the report, in effect giving the reader an overview of what is to come
-->

Escape rooms are physical, interactive experiences in which a group of participants must solve puzzles to escape a locked room, solve a mystery, or otherwise meet some goal in a particular timespan. They are a phenomenon that has existed since around 2007 @nicholson2015peeking, and are a growing industry. Escape rooms are run both by enthusiasts as solo ventures, and as franchises across the country.

The aim of this project is to build tested tools to meet the needs of escape room owners. Research will be focused towards exploring the needs of escape room owners, such that a product can be designed and built to target one or several of these. These needs may be related to issues such as making sure a timer is visible to the group, or to processes that currently take more time than necessary, such as posting photos of teams to social media @liam2019.

## Research Questions

I have identified two research questions, which this stage of the project will be focused towards answering:

1. What do escape room owners consider their biggest timesinks?
2. What would need to be built in order to rectify these problems in a way that serves escape room owners most effectively?

I intend for this stage of the report to decide the scope I intend to tackle with the artifact I will build for this project, after which I will find the answer to the third question I have:

3. Does the solution I have developed effectively counteract an identified timesink?

# Literature Survey

<!--
Depending on the type of the project, relevant literature may be hard to find, and a technology survey/review of relevant mathematics/review of similar software tools may be more appropriate - you should discuss this with your supervisor. 

- demonstrate your awareness and understanding of the background literature to your topic
- set the proposed research in a wide context
- progress to a more detailed account of the most relevant work in the area
- take care to include some up-to-date references
- Reviewing the literature can help to identify questions and issues that have not yet been answered, ideally questions that will be addressed through your project.
- can incorporate criticisms of previous work, although you need to take care here that your criticisms do not reflect a lack of understanding.

Think of the review as writing an essay on the background literature for your project. You should not just provide a list of references followed by a short summary of each of them. Instead the review should be organised and structured in a meaningful way, and the themes and relationships between the references identified. You should expect to redraft the review several times in order to arrive at a text that is clearly written, easy to understand, but that displays an in-depth understanding of the topic. 

It is usual to assume that the reader is familiar with first and second year course material. Any further material needed should be summarised either and suitable references cited.
-->

Relevant research was very difficult for me to find in this area. I suspected this was for a variety of reasons.

**The secrecy and competitiveness of the market** means that "there are not resources publicly available to help those wanting to start or improve an escape room" (@nicholson2015peeking). The latter case is particularly relevant to my aims, which seek to mitigate common timesinks for escape room owners. Nicholson runs a [Facebook group](https://www.facebook.com/groups/608883549212939/) for escape room enthusiasts, encompassing both owners and participants, to which I sought and gained access as part of my work. The majority of posts, at the time of writing, seem to be from enthusiasts who report back from rooms they have attended, though I have seen posts about types of puzzles that can be implemented. I intend to survey this group, as it appears to be a central hub for what may be a sparse online community. 

However, escape room blog The Logic Escapes Me reports that [ERIC](https://thelogicescapesme.com/news/eric-2019-a-roundup/), an industry convention, has been running for three years. This year's iteration hosted talks in which such themes as immersion, a "hierarchy of needs", and an analysis of the industry in China were discussed. Opportunities such as these can expose the potential for iteration upon existing ideas (@nicholson2015peeking).

<!-- TODO: cite TLEM properly -->

**The participant focus in existing research** seeks to understand the sentiment of those who attend escape rooms. Often, this is with the intent of drawing conclusions about where escape room owners should focus their efforts, or the effects of an owner's design choices on their participants (@wiemker2015escape). These, however, do not target the more fundamental changes that can be made in how an escape room is run day-to-day, and do not expose the difficulties of running an escape room.

<!-- , @dilek2018real, @stasiak2016escape) TODO: back this up -->

**The novelty of the market** is likely to be a large factor - escape rooms began to surge only around 2012-2013 in various parts of the world, though they have existed since as early as 2007 (@nicholson2015peeking). Their relative infamy means that they have not become a widespread research target, though **their use in education** (@clarke2016escaped) is becoming an area in which research is growing, as gamification brings a variety of benefits to the field of education (@kiesler2011gamification).
<!-- TODO: more... -->

## Keywords

I identified the following keywords for use in my search. The search was conducted using the Google Scholar search engine.

- escape room owner
- escape room host
- escape room implementation
<!-- - puzzle hunt -->
- escape room software

# Requirements and Analysis

<!--
Detail the aims and objectives of your project and analyse individual parts in detail. The analysis may cover more than is finally implemented. As a result of the analysis, you should state what will be covered by the project and what will not be done and why. Due consideration should also be given to how you will evaluate your work. Evaluation is one of the most important aspects of any piece of work and it should be thought about in the early stages. Consider tests or experiments that can be conducted to establish the success of the work.
-->

# Progress

<!--
What have you achieved to date? Describe any results you have. It may be appropriate for your project to combine this chapter with the following chapter - discuss this with your supervisor.
-->

<!--
- Got in touch with Liam from the Lockup
- Emailed the rest of the rooms bar Great Escape
- Tried to join Nicholson's facebook group - should get in touch with him!
- Learned my way around the ESP32/unPhone on the IoT module
-->

# Conclusions and Project Plan

<!--
Give a brief summary of the main achievements to date and a detailed plan of work (e.g. using a Gantt chart) to the end of project.
-->
