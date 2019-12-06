---
title: Building Digital Tools Assisting Escape Room Owners \break
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
All sentences or passages quoted in this report from other people's work have been specifically acknowledged by clear cross-referencing to author, work and page(s). Any illustrations that are not the work of the author of this report have been used with the explicit permission of the originator and are specifically acknowledged. I understand that failure to do this amounts to plagiarism and will be considered grounds for failure in this project and the degree examination as a whole.

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
This paper uses various studies into applications of escape rooms to discuss the priorities of well-made escape games, particularly with regards to the inclusion of technology. It also marks my current progress in research into my dissertation topic as expressed in the title.
<!-- - explain highlights -->
It focuses on the difficulties in applying technology in escape rooms and priorities that should be held in order to mitigate these.
<!-- - explain purpose of paper -->
On this basis, it serves to document universal requirements to bear in mind when developing hardware or software for escape rooms.

<!-- Contents -->
\tableofcontents
\mainmatter
# Introduction

<!--
- set the scene for the project by giving a little relevant background information - try to grab the reader's interest early
- clearly elucidate the aims and objectives of the project and the constraints that might affect the way in which the project is carried out. If the project involves the solution of a specific problem or the production of a specific system this should be clearly specified in an informal way
- summarise the remaining chapters of the report, in effect giving the reader an overview of what is to come
-->

The aim of this project is to build tested tools to meet the needs of escape room owners. Research will be focused towards exploring the needs of escape room owners, such that a product can be designed and built to target one or several of these. These needs may be related to issues such as making sure a timer is visible to the group, or to processes that currently take more time than necessary, such as posting photos of teams to social media (@liam2019).

In order to guide the focus of my project, I will use this paper to discuss the features of escape rooms and analyse their implementation across existing research. I intend to do so guided by my chosen research questions. This will reveal some universal requirements that should be kept in mind when developing tools for escape room owners across industries.

## Research Questions

I have identified two research questions, which this stage of the project will be focused towards answering:

**RQ1**: How are concepts used in escape rooms applied in different environments?   
**RQ2**: Based on this, what can we establish as the requirements for escape games, independent of their environment?

# Background and Motivation

<!--
- explain escape rooms, inc origin (nicholson)
- why are you doing your lit review on escape rooms?
-->

Escape rooms are physical, interactive experiences in which a group of participants must solve puzzles to escape a locked room, solve a mystery, or otherwise meet some goal in a particular timespan. They are a phenomenon that has existed since around 2007 (@nicholson2015peeking), and are a growing industry. Escape rooms are run both by enthusiasts as solo ventures, and as franchises across the country. @nicholson2015peeking documents escape rooms as the culmination of a variety of media. Of those he has listed, I feel the puzzle or treasure hunt genre shares the most fundamentals with escape rooms - both puzzle hunts and escape rooms can be defined as a team-based problem-solving challenge done in person. Various others have lent features to escape rooms, such as immersion in a story as the "hero", which @duplessie2013go reports as being something participants enjoy. This is embodied by live-action roleplaying, another inspiration for the genre (@nicholson2015peeking). Nicholson presents the precursors to escape rooms in further depth in his paper - Figure 2.1 summarises these.

Escape rooms have grown popular in many locations across the world as a recreational activity (@nicholson2015peeking, @stasiak2016escape), even serving as a tourist attraction (@dilek2018real). Nicholson reports that the *Real Escape Game* by SCRAP was the earliest well-documented activity branded as such. SCRAP has gone on to develop escape rooms at a much larger scale than the typical escape room, which serves teams of an average size of 4.58 people (@nicholson2015peeking).

![Nicholson (2019) presents the precursors to, and inspirations for, the escape room phenomenon in this diagram. Adapted with permission from Nicholson, Scott. 2015. “Peeking Behind the Locked Door: A Survey of Escape Room Facilities.” *White paper available online at http://scottnicholson.com/pubs/erfacwhite.pdf*.](nicholson-figure.svg)

My goal in writing this literature survey is to understand not only the needs of the commercial escape room industry, but also the differing requirements for the application of escape rooms in education and other contexts. The major difference between these contexts is that the commercial escape room industry is most regularly founded on permanent fixtures, and educational escape rooms are often applied in a classroom environment, which can imply more limited space and the need to tear down the room after it has been completed. These different environments dictate some differences between escape room experiences. However, as I intend to show in the literature survey, inspiration can be taken from both contrasting environments and applied universally.

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

<!-- Escape rooms' relative infamy means that they have not become a widespread research target, though **their use in education**  is becoming an area in which research is growing. Gamification brings a variety of benefits to the field of education (@kiesler2011gamification), which are capitalised upon by those implementing escape rooms in education. There are various tested means of implementing escape rooms in the classroom, from Breakout EDU @breakoutedu to recruiting an agency for this purpose (@zhang2018trapped), to implementing one using resources already available in the classroom.  -->

Escape room owners are able to apply technology to varying degrees. On the outside of the escape room experience, owners implement leaderboards, share team photos to social media, and interact with the team via a screen or handheld transceiver in the room. Inside the room, entire puzzles can be based on technology, if the owner has the necessary expertise. Some more unique applications within the room are also possible, such as using a hidden camera to take a photo of the team, apply filters, and display the photo among works of art as demonstrated in [The Gallery](https://escapist.nl/en/), which I visited in July 2019. However, there is a general aversion to the use of technology in escape rooms, for a variety of reasons. @liam2019 suggests that the time investment and necessary expertise are some of the greatest contributing factors. @duplessie2013go approaches this from the perspective of immersion - with 70% of escape room games being purely physical activities (@nicholson2015peeking), DuPlessie recommends movement away from what he calls the "glowing rectangles" as our medium of choice.

The increasing application of IT in education means that computers are often part of the school environment, and can be used as a tool when building an escape room experience for educational purposes. Several studies cover the use of escape rooms as a means for education (@lopezuse; @rouse2017lessons; @peleg2019lab, @beguin2019computer). @rouse2017lessons applied technology to an escape room in the classroom using a game loaded from a memory stick. This application seems understandable, as Rouse's audience was likely to have some basic level of expertise in, and enthusiasm for, handling computers as part of the digital native generation. However, in practice, it brings to mind the image of a small group of people crowding around a screen. @liam2019 warns against situations like this, saying that visibility of the puzzle to the entire team should be a priority. 

<!-- TODO: Reshuffle this paragraph? -->
However, ill implementation does not mean technology should not be excluded from escape room environments outright. Instead, I feel technology has the potential to inspire change in escape rooms. Escape rooms and technology are inherently linked - digital escape-the-room games such as *Myst* precede and inspire physical escape rooms (@nicholson2015peeking). These forms of escape room lack a shortcoming that is one of physical escape room owners' greatest anathemas - resetting these rooms is as simple as resetting the game. Whether this is done by restarting an attempt, restarting the game, or removing save files and starting over, it is often trivial compared to how long it takes to reset escape rooms. @liam2019 suggests that resetting rooms can often take as long as 15 minutes, and that it is something escape room owners seek to optimise; the shorter a reset takes, the more time is available to welcome customers.

Commercial escape rooms are often permanent fixtures. This means that more immersive environments and more complex physical puzzles can be built. However, puzzles of a physical nature usually need to be reset by the room owner back to their original state, so that more than one group can attend a room in the same day. Contrary to this, escape rooms built in a classroom environment are usually of a temporary nature, and may even try to allow for multiple groups to attempt the room at once, at the cost of immersion and interactivity. A study by @lopezuse organised its puzzles in a manner whereby puzzles could be completed in any order, allowing multiple groups to attend the room at once. One example puzzle given in the study was an exercise likely done on paper - exercises in this form make resets trivial, as a fresh worksheet is all that is necessary, but they also demonstrate the lack of immersion. Commercial escape rooms regularly employ more physical interaction - 78% of escape rooms employ a search for physical objects as part of the experience (@nicholson2015peeking). Some varieties of commercial escape room visit the other end of this spectrum, such as those developed by Tuzak, an Istanbul company developing portable escape games (@gunduz2018preventing). Portable or temporary escape games often trade immersion for greater logical challenge.

Application of technology in escape rooms comes with some uncertainty, and a break in the flow of the escape room experience can shatter participants' immersion and lead to negative reviews (@liam2019). This also creates some difficulty when it comes to visibility - unless monitors are suitably placed and large enough to be viewed by a full party, the whole team may not be able to interface with a puzzle that applies technology. This is particularly an issue if a single typical workstation is set up - @nicholson2015peeking warns of the danger of removing just one player from the "mental space" of the team.

@liam2019 theorises that VR escape rooms such as [EXIT VR](https://exit-vr.de/en/) may be the next stage for the industry, which allow immersive rooms to be created while effectively eliminating the issue of resetting the room as above. This would bring the escape room cycle full circle, reincarnating the modern wave of physical escape rooms in the digital form that inspired them.

While the escape room industry cautiously explores the "glowing rectangles" @duplessie2013go warns against, the video games industry sometimes takes small strides to recede from them. This has resulted in demonstration of some ideas escape rooms, and interactive experiences of all kinds, can learn from. [*Keep Talking and Nobody Explodes*](https://keeptalkinggame.com/) focuses on asynchronous gameplay, in which one player must defuse a bomb while the others guide them using the [bomb's manual](https://bombmanual.com). Conceptually, the game shares fundamentals with escape rooms, but what is of most importance here is that the foremost task in the game is communication. Escape rooms already apply asynchronous gameplay - The Lockup Escape Rooms' *Meltdown* (@liam2019) begins with most of the party in individual chambers, with the designated 'leader' communicating from outside - but *Keep Talking and Nobody Explodes* demonstrates that with technology, it is possible in almost any location. [*1-2-Switch*](https://www.nintendo.co.uk/Games/Nintendo-Switch/1-2-Switch-1173186.html) similarly pulls away from the screen, with the majority of its minigames relying on what is done physically with the Joy-Con controller and instructing players to face their opponent directly. It is an effective example of how to apply technology in a way that does not lock singular players into staring at a screen.

In summary, technology brings a variety of benefits, from quick resets when used as part of a puzzle to interesting and reactive ideas that may not otherwise be possible. Many ideas and inspirations have been discussed here. However, care must be taken to ensure that if the implementation separates one player from the group, it is applied in an engaging manner. Escape room owners value reliability, with negative reviews being the consequence for ill implementation (@liam2019). The strength of escape rooms as an educational tool has also been demonstrated here, which is worth consideration when building for the escape room industry.

<!-- **The participant focus in existing research** seeks to understand the sentiment of those who attend escape rooms. Often, this is with the intent of drawing conclusions about where escape room owners should focus their efforts, or the effects of an owner's design choices on their participants (@wiemker2015escape). These, however, do not target the more fundamental changes that can be made in how an escape room is run day-to-day, and do not expose the difficulties of running an escape room. -->

## Keywords

I identified the following keywords for use in my search. The search was conducted using the Google Scholar search engine.

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

Additional searches were made based on discoveries such as escapED (@clarke2016escaped) and Breakout EDU @breakoutedu to see where they had been applied.

# Requirements and Analysis

<!--
Detail the aims and objectives of your project and analyse individual parts in detail. The analysis may cover more than is finally implemented. As a result of the analysis, you should state what will be covered by the project and what will not be done and why. Due consideration should also be given to how you will evaluate your work. Evaluation is one of the most important aspects of any piece of work and it should be thought about in the early stages. Consider tests or experiments that can be conducted to establish the success of the work.
-->

The objective of my project is to build a tool for the escape room community. This may come in the form of hardware, software, or some combination of the two. I will survey the escape room community on Facebook to determine what to do here - I have a selection of ideas, which I was able to discuss with an escape room owner (@liam2019).

This has evolved from the initial proposal, which was to build an escape room exclusively using technology. After much discussion with my supervisor, we determined that this was too vast of a goal for the project. This would have been a distributed system using a variety of networked technology. The next phase of this idea was to create a framework for digital puzzles, which would use a variety of inputs and outputs - using the Quando framework developed by @stratton2019quando, I would quickly be able to construct interactions across many media. Quando has support for the Leap Motion @leap hand-tracking device, micro:bit @micro, and a variety of in-browser technology. However, the project may use a closed-source license in future (@stratton2019), which meant that I found it difficult to rely on for my work. Additionally, @liam2019 warns that digital uptake in escape rooms may be middling due to the inherent risk, as discussed in the literature survey.

My next step is to survey the industry, which is subject to the approval of an ethics review of my questionnaire. A questionnaire will be sent to the Facebook group created and maintained by @nicholson2015peeking. This will help to solidify the direction of my project.

# Progress

<!--
What have you achieved to date? Describe any results you have. It may be appropriate for your project to combine this chapter with the following chapter - discuss this with your supervisor.
-->

I have been able to make good progress in defining my scope this semester. The most important thing I have had to do is to get in contact with the escape room community - I have been able to reach out to all of Sheffield's escape rooms, though only one has returned any interest in supporting the project. This was The Lockup Escape Rooms in Sheffield.

I got in contact early in November, which was a busy time for all rooms. In initial communications with The Lockup, Liam offered a free attempt at one of the two rooms offered pro bono. I took up this offer on the 29th November with a group of friends, tackling the *Meltdown* escape room and its hard mode option in 53 minutes and 57 seconds. The experience was enjoyable for all, and I found it refreshing to see some science applied within the room - one of the puzzles relied on mixing chemicals and using the colours of the resultant reactions to solve the next puzzle.

Before this, I met with Liam on the 20th November to discuss the challenges he faces as an escape room owner, and his philosophy in developing the rooms he offers at The Lockup. Engagement, visibility and breakability all inspire his approach: the entire party must be able to interact with, and be engaged by, puzzles in the room, and the puzzles should not take long to reset to their initial state for the next party that attends the escape room (@liam2019). Liam and I discussed some areas that could be targeted, which will inspire a survey I send to the Facebook group created by @nicholson2015peeking. At the time of writing, my ethics application has not been processed, so this will be distributed as soon as possible afterwards.

Nicholson runs a [Facebook group](https://www.facebook.com/groups/608883549212939/) for escape room enthusiasts, encompassing both owners and participants, to which I sought and gained access as part of my work. The majority of posts, at the time of writing, seem to be from enthusiasts who report back from rooms they have attended, though I have seen posts about types of puzzles that can be implemented. I intend to survey this group, as it appears to be a central hub for what may be a sparse online community. 

Though I have not yet locked in my approach, I have been learning to develop for the ESP32 microcontroller and the unPhone platform (@cunningham2019unphone).  This provides a strong framework for IoT development at a low cost and may be an outlet to explore in the development of my artifact.

# Conclusions and Project Plan

<!--
Give a brief summary of the main achievements to date and a detailed plan of work (e.g. using a Gantt chart) to the end of project.
-->

It is difficult for me to provide a detailed plan at this stage, since I have not been able to calibrate the scope of my project in time for submission of the literature review. However, I should be able to define this once I understand from my survey what the industry wants. I intend to aim for completion of the project in mid-April, which will give me two months of float to work with. Independent of what I choose to build, I intend to:

- Break the task down into epics and tickets, as explained by @drumondscrum.
- Refine the tickets. The goal is to be able to pick up any given ticket and to have left myself enough information that I could comfortably progress with it.
- Estimate the tickets using story points. Of course, these would be subjective estimates, but I have no doubt that they will assist in helping me to prioritise and schedule work. They will give me confidence in being able to predict how much I should be able to complete by the end of the project.
- Begin work, focusing in particular towards research into unknown areas. Should I choose to use a tool that I don't yet have full knowledge of, I will first make sure that my knowledge and capabilities in using it are adequate.

In writing this literature survey, I have extended my awareness of both the strengths and difficulties in implementing technology in escape rooms. I will need to bear this in mind strongly when development of my solution begins. I have also been shown the value of escape room technology in other forms than the typical commercial application - a tool that is as effective in pedagogy as it is in escape rooms is of the essence.

# Bibliography
