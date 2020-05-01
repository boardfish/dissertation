# Design and Architectural Decisions

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

This chapter discusses choices I made with regards to design methodology and
choice of approach. 

## Atomic Design

In summary, [Atomic Design](https://atomicdesign.bradfrost.com/chapter-2/)
serves as *"not a linear process, but rather a mental model to help us think of
our user interfaces as both a cohesive whole and a collection of parts *at the
same time*"* [@atomicdesign]. While Atomic Design in full uses a five-level
hierarchy - atoms, molecules, organisms, templates, and pages - I employed three
of these, of which two were expressed in React.

I was introduced to the concept by an internal development team during my year
in industry. Personal projects I have taken on in React thus far were all in
motion before I was introduced to this, so I saw Blacklight as an excellent
opportunity to apply it.

Atoms were designed with the intent of taking in one or several Rails objects as
props, and representing those. They would not use asynchronous calls to APIs.
Molecules would comprise atoms, and in some specific cases use API calls to
retrieve the objects to display. Both of these would be used for rendering as
part of a page by the Rails templating engine.

Atomic Design helped me to define a purpose and a set of rules for components
that I created. I could limit the scope of a component with quicker
self-justification if I could express that its capabilities should sit within
certain bounds I had defined on principle. However, while it served useful in
that regard, it was at times difficult to ascertain what should be an atom and
what should be a molecule. <!-- FIXME: review -->In the final codebase, some
components are considered atoms where they should be molecules.

## Choosing an Authentication Service

Authentication, as one of the first and most fundamental areas tackled on the
project, was of high importance to get right. Personal familiarity lies with
Keycloak in this instance. Other options explored included Dex, ORY Hydra,
FreeIPA and Auth0. Auth0 differs from the others in that it is authentication as
a service - it hosts its own authentication instance for one to use and manage
through their platform, with similar flexibility to the other options. The rest
are self-hosted. Self-hosting was a trade-off I almost immediately acknowleged -
control and convenience were in the balance.

In principle, I would always choose control over convenience. Personally, I am
strongly in favour of self-hosting, though during my time at the University, I
have made necessary compromises here to avoid the pitfalls of self-hosting from
interfering with my work. This would be another situation in which I would
choose to compromise, as will be explained.

Again, my year in industry drew me in the direction of Keycloak and its Red
Hat-supported twin, Red Hat SSO. Both are OAuth authentication platforms, and
have provisions for setting policies and permissions and creating groups. Red
Hat SSO was running in production at UKCloud while I was there, and I personally
built up a lot of responsibility for implementations in that area. My
familiarity with it and trust in its production-readiness made it one potential
candidate for authentication.

One of Keycloak's primary problems, from a software architecture perspective, is
that throughput is limited by the server. This is something of a guarantee with
any authentication server, but particularly in Keycloak's instance, much
overhead comes from its responsibility to serve the frontend.

Hydra presents itself as being a thinner and faster alternative which does not
serve its own frontend. This is positive, but demands that the developer create
their own frontend - combined with my unfamiliarity towards Hydra, this would
use more time than necessary. Were time not an issue, Hydra would have taken my
interest and had far stronger consideration. 

Dex seems more accessible than Keycloak to one with knowledge of the OAuth2
protocol. Keycloak has extensive documentation, but much is left to the user to
create and discover. Dex gave a strong impression as regards user-friendly
documentation. As with Hydra, if time were not a constraint, Dex would have also
been explored and considered to a far greater degree - most likely, it would
win out over Hydra for developer-friendly documentation.

Of course, Rails' own option of Devise with database authentication was
ever-present. However, I would not be as comfortable using this as a potential
SSO provider - in the instance that vulnerabilities were revealed and patched in
Ruby that affected Devise database authentication, I would need to upgrade all
of Blacklight in line with this. OmniAuth in Devise would serve as a thinner
layer over the top and allow me to easily migrate authentication providers,
should I wish to.

Auth0 was chosen as my authentication provider, albeit as a compromise in the
name of stability and convenience. One benefit is that it is externally hosted
with a served login page, saving further frontend development and creating one
less self-hosting dependency. Deployment also became much easier as a result of
this choice - I was able to deploy Blacklight through Heroku buildpacks without
needing to run an authentication service in a separate container, or additional
networking configuration. Developer documentation is additionally very strong
with Auth0 - I am glad to report that my experience in implementing Auth0 was
mostly straightforward.

In this instance, the choice to use Auth0 as an authentication provider was
valid for several reasons. Creating a dependency of large size would mean that
in the event of a situation that called for further development, an extortionate
amount of time would need to be expended. Such situations could include, for
example, a security flaw or a significant update. Centralising this on two major
dependencies - Auth0 and the `omniauth-auth0` gem, which are both managed by
Auth0 Inc. - puts it in far safer hands.

\pagebreak

## Content Input and Presentation

It was a priority to allow escape game maintainers a strong degree of control
over their profile through intuitive means. They would be able to make their
escape game more visible on the site through searches by entering details such
as its relative difficulty and location. In particular, a rich text description
was identified as an essential feature that would help maintainers to make
listings that accurately represent their escape games.

This would include both text formatting and external links. Inspiration was
taken from [Kickstarter](https://kickstarter.com), a crowdfunding site which
allows rich-text descriptions. Campaign runners use these to good effect with
inline images acting as headings. Inline images were decided to be out of scope
during development, but rich text was still essential.

![A rich-text description from Kickstarter, showcasing use of bold text and
inline images with captions. Playtonic Games, viewed on April 17, 2020
"Yooka-Laylee - A 3D Platformer Rare-vival!" (Screenshot by
author)](kickstarter.png){ width=50% }

Rails delivers rich text inputs and storage through its ActionText extension,
which was included in version 5. Restrictions on access to ActionText features
were not identified - such restrictions would be vital in ensuring a level
playing field on the site for all maintainers. ActionText was thus foregone in
favour of Markdown. 

In selection of Markdown as the engine to drive rich text for Blacklight, it was
strongly acknowledged that users may find learning Markdown "prohibitively
difficult" [@ovadia2014markdown]. However, Markdown is employed on blogging
sites such as Tumblr, Reddit and WordPress [@ovadia2014markdown], with which I
expected escape room maintainers may have some familiarity.

A minimal, yet inuitive, approach was built. A key feature of these was the live
preview, which showed users how their input would be rendered on
`escape_game#show` for their escape room. A link to [CommonMark's guide to
Markdown](https://commonmark.org/help/) is shown beside the input field, which
gives a quick overview of Markdown syntax.

<!-- TODO: live preview screenshot -->