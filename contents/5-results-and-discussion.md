# Results

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

### Practical Use

Were Blacklight to be released, I would encourage its use in the following ways:

- Using the Explore view when searching for new escape games to tackle alone or
  with friends
- Linking to escape games during discussion and recommendations on other
  platforms
- After completion, marking an escape game as cleared and uploading photos
  directly to the site
- Showing records of escape games cleared, and the associated photos, to others

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
features"*. Still, in spite of having had to limit the scope of the project
further and forgo many ideas that might have even given Blacklight commercial
viability, I am very satisfied with the quality of the product that I was able
to make.

## Further Work

The existing framework should serve to make the following features
straightforward to implement. Security, basic stability, and social features
take priority. Blacklight would be in a deployable state with features listed
under **Immediate Priorities** - these would provide a stable experience with
strong social links between users. Particularly, the increase in test coverage
would make Blacklight a more stable platform on which to develop.

### Initial Scope

#### Immediate Priorities

- **Pagination of outputs**
- **>80% test coverage**
- **Improvements to factors relating to authentication**, such as:
  - introducing two-factor authentication
  - permitting the use of social network accounts such as Facebook and Twitter
    for login.
- **The ability for users to add others as friends**   
  Doing so would allow users to track other users' activity on their timeline
- **Leaderboards for each escape game**
- **A timeline for logged-in users**   
  This would show the aforementioned, alongside introducing new escape games
  that had opened in the vicinity of the user
- **The ability to reorder photos on escape games and clear records**

#### Additional Features

- **Time recording and milestones for escape games**   
  Design and functionality would take strong inspiration from
  [LiveSplit](https://github.com/LiveSplit/LiveSplit), and escape game
  maintainers would have a method of completing these for enthusiasts who attend
  their rooms
- **Metrics for maintainers**   
  Feedback on how many times their escape games and
  profile had been viewed recently
- **Toggling of privacy on a user's profile per-field**   
  e.g. visible to friends only or private

### Further Ideas

Many other ideas were discussed, but were not included in the original scope.
These included the following:

#### Immediate Priorities

- **Measures to include "in-home" escape games**   
  These features would be immediately vital due to the COVID-19 outbreak. They
  would aim to ensure that Blacklight would remain a viable product for use by
  the industry. Blacklight has caveats that make it inappropriate for the
  industry at present, such as some reliance on escape rooms having a physical
  location. These features would encompass:
  - an additional filter to select only "in-home" escape-games or standard
    escape rooms
  - further fields available to the `EscapeGame` model, such as a definitive
    `price`   
    This was omitted as a field in its own right in Blacklight, as 39% of escape
    rooms charge per team and 55% charge per person, with others pricing either
    via a *"base cost...plus an additional fee per player"*, or *"banded
    models"* in which groups of different sizes are charged differently.
    [@nicholson2015peeking]. Such a difference calls for at least two unique
    approaches to both collecting the data from, and representing the data to,
    the user.
- **An extensive tagging system** 
- **Increased depth of filtering in the Explore view**   
  Included with a view to allowing those with accessibility issues to quickly
  find rooms suitable for them. This would be particularly effective in tandem
  with the above suggestion. It is of note that maintainers can outline this
  kind of information in the description of their escape rooms. However, this
  cannot be searched or filtered.
- **Refinement of the API to be more standard**   
  This would include [OpenAPI documentation](https://swagger.io/specification/),
  whose correctness could then be verified against the app using a tool such as
  [Apivore](https://github.com/westfieldlabs/apivore). OpenAPI documentation
  opens opportunities for a vast array of integrations with Blacklight's API
  using tools such as [OpenAPI
  Generator](https://github.com/OpenAPITools/openapi-generator), saving
  developers the need to stub or create their own language-specific clients for
  Blacklight.
- **The ability to bookmark escape games as an enthusiast**
- **A review system**   
  This would be specific to Blacklight (i.e. not backed by existing Google
  Maps data), with some way of weighing more experienced users' feedback against
  newer users.

#### Additional Features

- **Additional measures to improve accessibility**   
  Blacklight's dark mode and use of the
  [Solarized](https://github.com/altercation/solarized) theme, which uses CIELAB
  [@ISO11664] to maintain readable color contrasts, encourages readability and
  visibility across the site. However, additional measures could have been taken
  to improve usability of the site with assistive technologies in line with the
  WAI-ARIA specification [@aria], particularly with regards to React-heavy views
  such as the Explore view.
- **A searchable Google Maps view**
- **Integration with social media**   
  More specifically, this would be to allow Blacklight to consume more data from
  Google Maps and display other social media embeds for escape room pages. Doing
  so would allow Blacklight to support escape rooms' existing social media
  presence, and integrate location data into the experience in a more natural
  way.
- **Maintainer groups**   
  This has a use case particularly in the instance of large franchises where
  multiple people may be responsible for the franchise's online image. The
  feature would allow multiple users to have ownership of an escape game.

