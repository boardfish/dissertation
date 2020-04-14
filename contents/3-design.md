# Design

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

## React: Atomic Design

I selectively applied [Atomic
Design](https://atomicdesign.bradfrost.com/chapter-2/) in creation of React
components for Blacklight. I was introduced to this by an internal development
team during my time at UKCloud. Personal projects I have taken on in React thus
far were all in motion before I was introduced to this, so I saw Blacklight as
an excellent opportunity to apply it.

In summary, Atomic Design serves as *"not a linear
process, but rather a mental model to help us think of our user interfaces as
both a cohesive whole and a collection of parts *at the same time*"*<!-- FIXME:
https://atomicdesign.bradfrost.com/chapter-2/ -->. While Atomic Design in full
uses five different levels of hierarchy - atoms, molecules, organisms,
templates, and pages - I employed only three of these and expressed only two in
React.

Atoms were designed with the intent of taking in one or several Rails objects as
props, and representing those. They would not use asynchronous calls to APIs.
Molecules would comprise atoms, and in some specific cases use API calls to
retrieve the objects to display. Both of these would be used for rendering as
part of a page by the Rails templating engine.

My justification for use of Atomic Design is that it helped me to define a
purpose and a set of rules for components that I created. I could limit the
scope of a component with quicker self-justification if I could express that its
capabilities should sit within certain bounds I had defined on principle.
However, while it served useful in that regard, it was at times difficult to
ascertain what should be an atom and what should be a molecule. <!-- FIXME:
review --> In the final codebase, some components are considered atoms where
they should be molecules.

## Authentication: OmniAuth

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

Again, my time at UKCloud drew me in the direction of Keycloak and its Red
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