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
