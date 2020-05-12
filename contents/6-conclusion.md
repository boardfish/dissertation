# Conclusion

<!--
The conclusions can be summarised in a fairly short chapter (2 or 3 pages). This chapter brings together many of the points that you will have made in other chapters, especially in the previous results and discussion chapter. Do not be afraid of repeating some of your earlier statements here, albeit using different wording.
-->

The needs of escape room maintainers, both internally to the escape room
experience and externally of the community, were investigated. This concluded in
a decision to build a social network, which allowed maintainers to both 
advertise among other escape rooms and share photos. The product of this was
Blacklight, a responsive web application that meets needs expressed by
maintainers and suggested by enthusiasts.

The changes caused by the COVID-19 pandemic dramatically altered the landscape
for escape room businesses, as they were forced to close. It was thus not
possible to draw firm conclusions without pivoting requirements. The end product
would not be impossible to evaluate. However, as justified in the impact
statement, doing so became infeasible due to the timing with which the pandemic
struck businesses. The original brief, which aimed to develop a product for use
directly inside escape rooms, would have resulted in a more difficult project
that would have been outright impossible to evaluate at this time.

Research concluded that the escape room industry is wary in its use of
technology inside escape rooms. On these grounds, avoidance of technology inside
the escape room could justifiably be considered the correct course of
action---this action led to a more useful premise, and product, for escape room
maintainers. 

Surveying the escape room maintainer community resulted in a decision to build a
social network between maintainers and enthusiasts, allowing maintainers to
advertise to enthusiasts on a mutually beneficial platform. The design of this
social network took several major design considerations into account.

Auth0 was chosen as the application's authentication service to reduce
the impact of an additional dependency. This proved itself to be a wise
choice---authentication was not a concern after its initial implementation in
the application. Effectively, the impact of this dependency was almost zero
during development.

The implementation of Markdown was a difficult choice due to uncertainty over
whether it is intuitive for users---suitability of this feature, and thus the
correctness of this choice, would have to be determined through user testing. I
predict that this may cause some difficulty, as some users may prefer more
typical rich text formatting fields. The approach could have been improved by
providing button controls to quickly apply formatting to selected text.
Prioritising this change would have been justifiable, as it would have made the
description field more intuitive for more of the project's potential user base.
Comfort in using this field may have prompted an increase in quality of escape
game listings on the site.

Atomic Design [@atomicdesign] helped to guide the structure of the frontend
code---it had particular strength in maintaining the sanctity of the single
responsibility principle, but the distinction between types of component gave
rise to more confusion than convenience.

As regards security, it has been partly addressed in development of Blacklight,
but it cannot be claimed that this was built as a fully secure system yet. To do
so would require strong knowledge of penetration testing and the assistance of
tools such as [OWASP ZAP](https://github.com/zaproxy/zaproxy).

The result of the project is a web application using Ruby on Rails and React
that provides an intuitive user experience. This is similar to a standard
content management system (CMS) in nature, but it requires little technical
expertise. This makes it appropriate for escape room maintainers of all levels
of technical ability. Designing Blacklight as a custom application would likely
make it a better fit for maintainers. However, it is less flexible for its
target domain than a typical CMS, as additional fields on models would require
additional development.

Blacklight enables escape room maintainers to easily
create and edit content-rich listings for their escape rooms, and allows
enthusiasts to document their experiences in clearing escape rooms as part of a
public profile. Both kinds of users' experiences are enhanced with images,
whether showcasing an escape room or commemorating a successful escape.

Blacklight was engineered through thorough application of industry practices
such as use of Kanban and automated testing. Such practices are designed to
raise developer confidence and code quality---arguably, they have done so.
However, continuous integration and testing did not give rise to any
regressions. Use of CircleCI as the platform for this may have slowed
development significantly due to long build times and limited builds, which were
equivalent to an outage. Kanban allowed for a controlled and careful development
cycle with good pace. Use of Kanban may have, in retrospect, allowed for a safe
pivot in development requirements to make Blacklight more useful during the
pandemic.

Blacklight was able to meet the basic requirements defined before development.
However, it can be considered more than a minimum viable product. The inclusion
of features such as adequate test coverage, pagination of outputs, enabling
two-factor authentication, and addressing missing accessibility features, would
allow Blacklight to be considered a minimum marketable product. However, its
current degree of stability, capability, and polish, backed by features such as
Google Maps integration and Markdown support, already make it stronger than the
specification for the minimum viable product.

Should Blacklight receive the features that make it a minimum marketable
product, it would be ready for distribution to the escape room community. The
project could go on to foster a resurgence of business in the escape room
community after the outbreak, regardless of the forms escape games take after
the pandemic. Blacklight could be adapted to any future that awaits it.