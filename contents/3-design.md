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

I selectively applied [Atomic
Design](https://atomicdesign.bradfrost.com/chapter-2/) in creation of React
components for Blacklight. In summary, Atomic Design serves as "not a linear
process, but rather a mental model to help us think of our user interfaces as
both a cohesive whole and a collection of parts *at the same time*"<!-- FIXME:
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