# Results and Discussion

<!--
The main results of your work should be presented, together with critical
discussion. The chapter should cover three things (although these would not be
used as section headings): 

Findings - present all the results (products, experimental findings, theories,
etc.) generated during the project. This may also include some off-topic
findings that were not expected, or which were side-effects of other
explorations.

Goals achieved - describes the degree to which the findings support the original
objectives laid out for the project. The goals may be partially or fully
achieved, or exceeded. An experimental project may prove, or disprove the
original thesis. A theoretical project may cover some or all of the example
cases. Note that reporting of failures to achieve goals is important since a
fundamental feature of the assessment procedures is that the processes (how you
went about your project) are often as important as the products of the project.

Further work - describes two things: firstly, new areas of investigation
prompted by developments in this project, and secondly parts of the current work
which were not completed due to time constraints and/or problems encountered.
-->

The product of my development process is a web application written in Ruby on
Rails, with React.js used to generate and drive some areas of the frontend. This
is titled Blacklight - its namesake is the kind of UV light which is employed in
puzzles in escape rooms all too regularly. Blacklight serves to emulate its
namesake, being:

- ...present in the majority of escape rooms
- ...used by maintainers as an escape room tool
- ...used by enthusiasts to discover something new

At the time of writing, Blacklight can be accessed at
https://blacklight-dev.herokuapp.com.

## Functionality Overview

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

Users have profiles on which they can write a bio, set their location, and link
to their own website. Here, those interested can see all escape games by a
single maintainer, and all escape games cleared by a user. Which of these is
shown depends on whether they have self-assigned as a maintainer, enthusiast, or
both.

Forgoing the later milestones, and many ideas that might even give Blacklight
commercial viability with them, was a difficult decision to make. However, I am
happy with the base functionality and usability that came to be.

## Discussion

To give a summary answer as regards the project's success, the goals of the
project have been met. A tool has been developed that allows escape room
maintainers to advertise their rooms and upload photos, and allows enthusiasts
to do the same in relation to escape rooms that they have cleared. Measures have
been taken to ensure that it is secure, functionally consistent, well-designed
and feature-complete. Despite this, I cannot shake the notion that with more
time available, Blacklight would feel whole, and potentially viable for public
rollout. Of course, in the current climate, Blacklight may serve little purpose
unless it were repurposed - in any other world, my personal feelings towards it
would be justified.

My implementation of continuous integration and containerisation surpasses
previous attempts I have made in personal projects. I feel as though I have
refined skills related to testing, and have particularly made strides in
building more interactive frontends with React. Room for improvement still
remains - late in development of Blacklight, I encountered limits around my use
of CircleCI, and I might have been able to capitalise on the premium feature of
Docker layer caching. I was alerted to a potentially more suitable option in
GitHub Actions, which would have alleviated both woes - with 3,000 free minutes
of running available under my current GitHub plan, I would have been able to run
somewhere over 400 builds at the average rate per month, which I expect would
have been more than enough. For comparison, I have run 201 builds against
CircleCI at the time of writing.

I recognise that my focus towards industry as opposed to academia complicated
the process and used much of my available time. Some might also say that my
focus on the practical, as opposed to the theoretical, limited the potential for
my project to be particularly novel in its approach. One survey respondent even
suggested that the intention was to introduce technology to *"trivial
features"*.

As regards further work on the project, the initial scope included the below as
ambitions. The existing framework should serve to make these straightforward to
implement, but I lament that they could not be part of the final product.

- improvements to factors relating to authentication, such as:
  - introducing two-factor authentication
  - permitting the use of social network accounts such as Facebook and Twitter
    for login.
- a 'friends' feature, that would allow users to track other users' activity on
  their timeline
- a timeline for logged-in users that would show the aforementioned, alongside
  introducing new escape games that had opened in the vicinity of the user
- the ability to reorder photos on escape games and clear records
- toggling of privacy on a user's profile per-field, e.g. visible to friends
  only or private
- metrics for maintainers - feedback on how many times their escape games and
  profile had been viewed recently
- time recording and milestones for escape games - design and functionality
  would take strong inspiration from
  [LiveSplit](https://github.com/LiveSplit/LiveSplit), and escape game
  maintainers would have a method of completing these for enthusiasts who attend
  their rooms
- leaderboards for each escape game driven by the above
- pagination of outputs

Ideas further beyond this included:

- an extensive tagging system and increased depth of filtering in the Explore
  view, with a view to allowing those with accessibility issues to quickly find
  rooms suitable for them
  - It is of note that maintainers can outline this kind of information in the
    description of their escape rooms. However, this cannot be searched or
    filtered.
- refinement of the API to be more standard
  - This would include [OpenAPI
    documentation](https://swagger.io/specification/), which could then be
    verified against the app using a tool such as
    [Apivore](https://github.com/westfieldlabs/apivore).
- Integration with social media, allowing Blacklight to consume more data from
  Google Maps and display Facebook embeds for escape room pages
- A review system specific to Blacklight (i.e. not backed by existing Google
  Maps data), with some way of weighing more experienced users' feedback against
  newer users
- maintainer groups, particularly in the instance of large franchises where
  multiple people may be responsible for the franchise's online image - this
  would allow multiple people to have ownership of an escape game
- as previously mentioned, measures to include "in-home" escape games, which
  would entail:
  - an additional filter
  - further fields available to the `EscapeGame` model, such as a definitive
    `price` - this was omitted as a field in its own right in Blacklight, as 39%
    of escape rooms charge per team and 55% charge per person, with a further 5%
    charging in other ways [@nicholson2015peeking]. Such a difference calls for
    at least two unique approaches to both collecting the data from, and
    representing the data to, the user.