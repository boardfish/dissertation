# Literature Survey

This chapter uses relevant literature to discuss the nature of escape rooms' use
of technology. The survey identifies factors such as reliability and
inspirations such as asynchronous gameplay. These go on to form guidance for
strong implementations of technology in escape rooms. The definition of escape
rooms was covered in the introduction; this chapter explores them in further depth.

## Process

The following keywords were identified for use when searching for material to
reference and discuss in the literature survey. 

- escape room / puzzle hunt
- maintainer / owner / host
- implementation
- software
- virtual reality
- education / classroom

This led to the following searches.

- escape room owner
- escape room host
- escape room maintainer
- escape room software
- escape room education
- escape room classroom
- virtual reality escape room
- portable escape room

The search was conducted using the Google Scholar search engine. Approximately
40 results from each search were checked. On this basis, approximately 320
papers were explored, not accounting for overlap.

Some additional searches were made based on discoveries such as escapED
[@clarke2016escaped] and Breakout EDU @breakoutedu to see where they had been
applied. The white paper by @nicholson2015peeking proved to be a key point of
reference across much of the relevant literature.

## Survey

In order to explore the priorities of escape rooms, it can be useful to first
study their history. Nicholson [-@nicholson2015peeking] documents escape rooms
as the culmination of a variety of media. He identifies puzzle hunts as
team-based problem-solving challenges. Treasure hunts and generic team-based
problem-solving challenges, such as those used in corporate team-building
exercises, appear most similar to escape rooms. Live-action roleplaying (LARP)
is another such inspiration [@nicholson2015peeking]. Both escape rooms and LARP
can provide entertainment through immersion in a story as the *"hero"*, a factor
that players enjoy [@duplessie2013go]. Nicholson presents the precursors to
escape rooms in further depth in his paper - Figure 2.1 summarises these.

![Nicholson (2019) presents the precursors to, and inspirations for, the escape
room phenomenon in this diagram. Adapted with permission from Nicholson, Scott.
2015. “Peeking Behind the Locked Door: A Survey of Escape Room Facilities.”
*White paper available online at
http://scottnicholson.com/pubs/erfacwhite.pdf*.](nicholson-figure.svg){ width=50% }

Escape rooms have grown popular in many locations across the world as a
recreational activity [@nicholson2015peeking; @stasiak2016escape], even serving
as a tourist attraction [@dilek2018real]. Nicholson reports that the *Real
Escape Game* by SCRAP was the earliest well-documented activity branded as such.
SCRAP has gone on to develop escape rooms at a much larger scale than the
typical escape room. Its *Real Escape Game Event* serves *"hundreds or thousands
of players in a large space"* - a far cry from the average team size of 4.58
people [@nicholson2015peeking]. SCRAP remains one of the longest-serving
purveyors of escape game experiences. Technology plays an active part in rooms
they have offered, such as *Pacific Rim: Shatterdome Defenders*
[@scrap2018pacific].

<!-- General introduction to argument -->

Escape room maintainers apply technology in varying ways, both inside and
outside the experience. On the outside of the escape room experience,
maintainers implement leaderboards, share team photos to social media, and
interact with the team via a screen or handheld transceiver in the room. Inside
the room, entire puzzles are driven by technology in rooms that integrate it
comfortably, and it can drive visual effects such as lasers and smoke. These
implementations can be inventive and support rooms in novel ways; *[The
Gallery](https://escapist.nl/en/)* (visited in July 2019), for example, uses a
hidden camera to take a photo of attendees, applies filters, and displays the
photo among works of art. However, there is a general aversion to the use of
technology in escape rooms, for a variety of reasons.

In discussion with @lockup2019, it was suggested that the time investment,
reliability, and necessary expertise are some of the greatest contributing
factors against the use of technology in escape rooms. Reliability particularly
guides this; a break in the flow of the escape room experience can shatter
participants' immersion and lead to negative reviews [@lockup2019]. Application
of technology in escape rooms thus brings with it some uncertainty.

Escape rooms seek to develop immersion. Technology can bolster or break this,
depending on the implementation. Immersion can be defined as captivating the
participant and making them feel invested in a situation or story. It can be
achieved through the use of theatrics such as special effects, acting, props,
and room design. In his example, @duplessie2013go creates immersion through
sound and steam to cover for his room's rotating mechanic - distracting the
participants from this gives a sense of reality to the situation they are in,
immersing them in the environment and story fully. DuPlessie is critial of
digital, rather than physical, interaction in escape rooms, citing the
importance of immersion, and recommends movement away from what he calls the
*"glowing rectangles"* as our medium of choice.

<!-- Why physical interaction gets scrapped -->

Physical interaction can be considered a foundation point of many escape rooms.
Inclusion of props, costumes, and mechanics can greatly improve immersion. 70%
of escape rooms employ a search for physical objects as part of the experience
[@nicholson2015peeking], which supports this. However, escape rooms in the
classroom tend to forgo this. Rooms of this nature may prioritise having
multiple participating groups in the room at one time. They may also use less
props in order to cut down on the time it takes to reset the room.

Prioritising multiple attendees over immersion, a study by @lopez2019examining
took place in a computer lab with groups at computers. This helped to *"decrease
the time investment for the course staff"* who were running the exercise. This
study also reveals a (context-specific) benefit to using smaller groups. The
context of programming allowed the pairs of participants to reap the benefits of
pair programming [@williams2001support; @mcdowell2002effects]. In cases such as
these, forgoing immersion for additional educational benefit seems worthwhile
and can make a marked impact. The experience likely contributed to the
*"statistically significant ($p<0.001$)"* 23% increase in passes.

A study by @lopezuse organised its puzzles in a manner whereby puzzles could be
completed in any order, allowing multiple groups to attend the room at once. One
example puzzle given in the study was an exercise likely done on paper. This
would allow all groups in the class to attempt the puzzle without it needing to
be reset, but the absence of physical interaction or props would likely reduce
participants' immersion in the scenario.

@nicholson2018creating suggests that an *"ongoing narrative"* between activities
can remedy this - this would *"empower them to be more engaged than if the games
are over in an hour"*. @dietrich2018escape trialled a similar escape game in a
classroom environment, to which 62% of participants with prior escape game
experience *"felt a similar sensation in the game presented here"*. This
suggests that strong and imaginative implementations of escape rooms in the
classroom can preserve the level of immersion traditional escape rooms often
display with adequate results.

Technology can enhance these implementations of escape rooms, preserving some
level of immersion by providing something interactive and physical.
@ross2019turning applied a decoder box developed for use in educational escape
rooms [@ross2019design]. @ross2019design reports that "the cost of a single
complete system is $30.00 AUD" (around £16 at the time of writing) and that it
is reprogrammable to handle several solutions. This arguably makes it an
inexpensive and reusable solution for classroom escape rooms. Participants in
studies that have used the decoder box prefer *"the user interface of something
physical rather than a computer based abstraction"* [@ross2019design] or *"paper
and pen or an app on their phone"* [@ross2019turning].

<!-- Visibility -->

Technology, particularly monitors, may be avoided in the escape room due to the
issue of visibility. Discussion with @lockup2019 highlighted that visibility of
the puzzle to the entire team should be a priority. @nicholson2015peeking warns
of the danger of removing just one player from the *"mental space"* of the team
- this is particularly an issue if a puzzle requires one person to work at a
computer alone. Even if a screen-based puzzle calls for multiple people, the
available space and the visibility of the screen dictates how many members of
the group can interact with it. Unless monitors are suitably placed and large
enough to be viewed by a full party, the whole team may not be able to interface
with a puzzle that applies technology. 

A greater number of monitors, or larger monitors that allow for multiple users
to interact with the puzzle (e.g. a multi-touch screen), could both counteract
this. Having said that, these come with both a literal and figurative price -
the cost of the resources themselves, and the space within the escape room in
which they can be implemented. As such, these factors make them difficult to
implement with repeat effectiveness across different escape rooms.

@rouse2017lessons applied the idea of using a computer in the classroom using a
game loaded from a memory stick. This application seems understandable; assuming
a younger audience, students would be likely to have some basic level of
expertise in, and enthusiasm for, handling computers. However, in practice, this
application of technology brings to mind the image of a small group of people
crowding around a screen, embodying a negative example in following this law of
visibility. @nicholson2018creating supports this idea, suggesting that
games using a screen do not emphasise the *"face-to-face contact"* players share
in live-action games.

Other forms of technology can still enable this *"face-to-face contact"* that
escape rooms prioritise. The Nintendo Switch video game
[*1-2-Switch*](https://www.nintendo.co.uk/Games/Nintendo-Switch/1-2-Switch-1173186.html)
often makes a point of pulling away from the screen. The majority of its
minigames rely on what is done physically with the Joy-Con controller. Players
are often instructed to face their opponent directly, and may rely on audio cues
and/or precise vibration in the Joy-Con during gameplay. It is an effective
example of how to apply technology in a way that does not lock singular players
into staring at a screen.

<!-- Resets -->

Poor implementation does not necessarily mean technology should not be excluded
from escape room environments outright. Instead, technology has the potential to
inspire change in escape rooms by targeting the time it takes to reset a room
back into a playable state. Escape rooms and technology are inherently linked -
digital escape-the-room games such as *Myst* precede and inspire physical escape
rooms [@nicholson2015peeking]. In these games, partipicants solve similar
puzzles within the limits of the player-character's capabilities, applying and
sometimes combining an inventory of objects to create new tools for use in their
escape.

These forms of escape room can be reset instantly by simply resetting the game.
Whether this is done by restarting an attempt or restarting the program itself,
it is often trivial compared to how long it takes to reset escape rooms. In
discussion with @lockup2019, he established that resetting physical escape rooms
can often take as long as 15 minutes, and that it is something escape room
maintainers generally seek to optimise; the shorter a reset takes, the more time
is available to welcome customers.

Quick resets are a priority in many different situations. A Turkish company,
Tuzak, develops portable escape games that are run in shopping centres
[@gunduz2018preventing]. Their choice to move to shopping centres was likely
made in an effort to capture new customers, making it all the more important
that the room could be reset quickly. Several studies cover the use of escape
rooms as a means for education [@lopezuse; @rouse2017lessons; @peleg2019lab;
@beguin2019computer], which would also prioritise this to fit within timetabled
school hours. The aforementioned application by @lopezuse allowed multiple
groups to tackle the escape rooms at the same time by removing the need to reset
puzzles entirely - students needed to combine the solutions to puzzles on
different worksheets to complete the room.

<!-- VR -->

The field of virtual reality is capable of creating escape rooms that bridge the
boundary between the digital (e.g. *Myst*) and the physical. The maintainer of
@lockup2019 theorises that virtual reality (VR) escape rooms such as *[EXIT
VR](https://exit-vr.de/en/)* may be the next stage for the industry, which allow
immersive rooms to be created while effectively eliminating the issue of
resetting the room as above. This would bring the escape room cycle full circle,
reincarnating the modern wave of physical escape rooms in the digital form that
inspired them.

@pendit2017virtual exercised this in the creation of their
virtual escape room *The Last Breakout*. This application revealed some
potential caveats that may be visible in the creation of VR escape rooms. Unreal
Engine 4 assisted in making the project feasible, but limited knowledge of how
to use it resulted in difficulties. These included motion sickness from
excessive movement, user experience as regards knowing when they might have
picked up an object, and display of reading materials [@pendit2017virtual].

These could be remedied with more effective VR development experience, but user
interface issues remain something that cannot be tackled without the correct
principles. In a study by @smith2009using, it was found that the context of
virtual reality clouded the line between a video game and a simulation of
reality - one child reportedly asked *"How do I kneel?"* when inside the
simulation. This misunderstanding could be attributed to how crouching in video
games works - it is most often toggled by, or activated by holding, a button
input. While @smith2009using acknowledge the *"built-in capability for higher
levels of actual human–computer interaction than traditional video games"*, this
boundary should not be ignored as the escape room industry explores VR.

<!-- Async gameplay -->

While the escape room industry investigates the *"glowing rectangles"*
@duplessie2013go warns against, the video games industry that lent it
inspiration sometimes takes small strides to recede from them. One strategy that
both industries are applying is asynchronous gameplay. In asynchronous gameplay,
two parties have different experiences that interlink to achieve the same goal.
Each industry can learn from the other's examples in applying this concept.

The video game [*Keep Talking and Nobody
Explodes*](https://keeptalkinggame.com/) is a popular example, in which one
player must defuse a bomb while the others guide them using the [bomb's
manual](https://bombmanual.com). Conceptually, the game shares fundamentals with
escape rooms - players work together to solve puzzles through logic and
communication. The communication aspect is of most importance to this point: the
game's asynchronous gameplay depends on communication for success.

Escape rooms also exemplify asynchronous gameplay. The escape room *Meltdown*
[@lockup2019] begins with most of the party in individual chambers, with the
designated 'leader' communicating from outside to coordinate the group. An
escape room study by @clarke2016escaped demonstrated a similar mechanic, using
laptops with Skype to facilitate communication between two groups in separate
rooms. One of the puzzles in *The Gallery* sees groups pulling ropes to lower a
metal ball through a hole in a cabinet. This requires two parties - one to pull
the ropes, and another to monitor the ball as it is lowered - as the cabinet
cannot be seen from where the ropes are.

Escape rooms already apply asynchronous gameplay, but *Keep Talking and Nobody
Explodes* demonstrates that with technology, it is possible in almost any
location through the use of portable gaming platforms like the Oculus Quest or
Nintendo Switch. This is all the more important during the COVID-19 pandemic, in
which companies are turning to other measures to continue the escape room
experience. SCRAP, for example, is even resorting to [livestreamed escape room
experiences](https://www.facebook.com/events/359013048391029/). This area seems
to be ripe with potential in such difficult times.

In summary, technology brings a variety of benefits, from quick resets when used
as part of a puzzle to novel ideas that may not otherwise be possible. Many
ideas and inspirations have been discussed here. The strength of escape rooms as
an educational tool has also been demonstrated here, which is worth
consideration when building for the escape room industry. However, there is a
debate as to whether the use of technology in escape rooms is always a viable
option. Escape room maintainers value reliability, with negative reviews being
the consequence for ill implementation [@lockup2019]. One of the greatest points
of contention is immersion. Care must be taken to ensure that if the
implementation separates one player from the group, it is applied in an engaging
manner. Excessive reliance upon screens is something that should be avoided in
the name of immersion.

It is clear that a balance should be maintained between these factors, and as
such, it is difficult to approach a one-size-fits-all solution for use inside an
escape room. However, it is clear that technology can advance escape rooms with
careful implementation. In particular, it can be used outside of the experience
itself in matters such as booking rooms, keeping a leaderboard, or advertising
through social media or otherwise. Software developed by @buzzshot, @xola and
@resova (eponymous in each case) capitalise on the potential for this - Buzzshot
is a general package covering all three listed areas, whereas the others focus
primarily towards bookings.

This project goes on to define advertising over social media as a feature of
interest to maintainers. It was identified during research that the escape room
community may not have a unifying platform. The project sought to meet both of
these needs by creating a platform shared by escape room maintainers and
enthusiasts.