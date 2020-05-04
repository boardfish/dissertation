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
same time*"* [@atomicdesign]. Atomic Design guides its users to classify
components by their scale and function, promoting reuse of smaller components to
form greater wholes.

This is best expressed with an example. A component classed as an atom would be
a `div` with its inner text mapped to its state and passed in through props - it
does not control or communicate with any other components. A molecule may
contain this element and a `button` that, when clicked, changes the state of the
controllable `div` to something predefined. While Atomic Design in full uses a
five-level hierarchy - atoms, molecules, organisms, templates, and pages - I
did not employ organisms or templates in my use of the methodology.

The rules of Atomic Design make it easier to enforce the Single Responsibility
Principle [@martin2006agile] and segment code in a way that makes it more
maintainable. This was the strongest factor in my decision to employ it.
However, while it served useful in that regard, it was at times difficult to
ascertain what should be an atom and what should be a molecule. In the final
codebase, some components are considered atoms where they should be molecules.

Atoms were designed with the intent of taking in one or several Rails objects as
props, and representing those. Molecules would comprise atoms, and in some
specific cases use API calls to retrieve the objects to display. Both of these
would be used for rendering as part of a page by the Rails templating engine.

I was introduced to the concept by an internal development team during my year
in industry. Personal projects I have taken on in React thus far were all in
motion before I was introduced to this, so I saw Blacklight as an excellent
opportunity to apply it.

## Choosing an Authentication Service

It was essential to choose the best authentication service for my use case.
Doing so would set a good precedent for the whole project and strongly affect
development time. Personal familiarity lies with Keycloak in this instance - on
my year in industry, I gained a thorough knowledge of it. Other options explored
included Dex, ORY Hydra, and Auth0. Auth0 differs in that it is authentication
as a service - it hosts its own authentication instance for one to use and
manage through their platform. The rest are self-hosted. Self-hosting was a
trade-off I almost immediately acknowledged - control and convenience were in the
balance. Though I would usually elect to favour the first option, convenience
and stability drove my decision.

| Option            | SaaS?      | Documentation | Provides frontend?   | Devise compatibility        |
|-------------------|------------|---------------|------------|-----------------------------|
| ORY Hydra         | No         | Good          | No         | `omniauth_openid_connect`   |
| Keycloak          | No         | Familiar      | Yes        | `omniauth_openid_connect`   |
| Dex               | No         | Very good     | No         | `omniauth_openid_connect`   |
| Auth0             | Yes        | Very good     | Yes        | `omniauth-auth0`            |
| Devise (database) | No         | Very good     | Yes        | `:database_authenticatable` |

Table: Comparison of potential options. Regarding Devise compatibility,
`:database_authenticatable` is an argument to `ActiveRecord::Model#devise`. The
rest are Ruby gems (packages) that extend the OmniAuth protocol to provide
support for those authentication methods.

Keycloak dictates the database structure and must be talked to through its API.
This leaves control out of the developer's hands, which is a problem from a
software architecture perspective. If the developer is responsible for
self-hosting the solution, they should be able to diagnose problems with the
database. They should also be able to optimise its performance not just through
additional resource, but through manual changes such as indexing. Conversely,
Devise's user model is dictated by what the user generates, and the
corresponding database table can be changed in line with other Rails models,
making it preferable.

Hydra presents itself as being a thinner and faster alternative which does not
serve its own frontend. This is positive, but demands that the developer create
their own frontend - combined with my unfamiliarity towards Hydra, this would
use more time than necessary. Were time not an issue, Hydra would have taken my
interest and had far stronger consideration. 

In the instance that Devise vulnerabilities were revealed and patched in Ruby, I
would need to upgrade all of Blacklight in line with this. Using OmniAuth with
Devise serves as a thinner layer over Devise and allow me to easily migrate
authentication providers, should I wish to. Still, if breaking changes are
introduced in Devise, an OmniAuth provider would potentially delay upgrading
Devise.

Auth0 was chosen as my authentication provider, albeit as a compromise in the
name of stability and convenience. One benefit is that it is externally hosted
with a served login page, saving further frontend development and creating one
less self-hosting dependency. Deployment also became much easier as a result of
this choice - I was able to deploy Blacklight through Heroku buildpacks without
needing to run a separate authentication service on another dyno.

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

A minimal, yet intuitive, approach was built (Figure \ref{markdown-preview}).
This used a live preview, which showed users how their input would be rendered
on `escape_game#show` for their escape room. A link to [CommonMark's guide to
Markdown](https://commonmark.org/help/) is shown beside the input field, which
gives a quick overview of Markdown syntax.

![The Markdown preview field as at commit
`fd1d6fd`.\label{markdown-preview}](markdown-preview.png)