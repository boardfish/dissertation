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

Forgoing the later milestones, and many ideas that might even give Blacklight
commercial viability with them, was a difficult decision to make. However, I am
happy with the base functionality and usability that came to be.
