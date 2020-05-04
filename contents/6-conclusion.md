# Conclusion

<!--
The conclusions can be summarised in a fairly short chapter (2 or 3 pages). This chapter brings together many of the points that you will have made in other chapters, especially in the previous results and discussion chapter. Do not be afraid of repeating some of your earlier statements here, albeit using different wording.
-->

The needs of escape room maintainers, both internally to the escape room
experience and externally of the community, were investigated. This concluded in
a decision to build a social network, which both allowed maintainers to
advertise among other escape rooms and share photos. The product of this was
Blacklight, a responsive web application that meets needs expressed by
maintainers and suggested by enthusiasts.

Research concluded that the escape room industry is wary in its use of
technology. The experience delivered by escape rooms regularly relies on the
physical, as opposed to the digital, in order to build excitement and immersion.
While technology can be, and has been, employed in engaging and novel ways,
maintainers are still cautious in their uses of it. Stability and reliability
have been cited as some of the highest-priority reasons for this.

For those reasons, it is difficult to develop technology for use inside the
escape room itself. Instead, a solution was considered that focuses more on
improving the day-to-day operation of escape rooms as businesses. Surveying the
escape room maintainer community resulted in a decision to build a social
network between maintainers and enthusiasts, allowing maintainers to advertise
to enthusiasts on a mutually beneficial platform.

The design of this social network took several major design considerations into
account. Auth0 was chosen as the application's authentication service to reduce
the impact of an additional dependency. The implementation of Markdown was a
difficult choice due to uncertainty over whether it is intuitive for users.
Atomic Design [@atomicdesign] helped to guide the structure of the frontend code.

Over roughly 4½ weeks of development time, Blacklight was engineered through
thorough application of industry practices such as use of Kanban and automated
testing. The result is a web application using Ruby on Rails and React that
makes strides towards being secure and providing a strong user experience. It
enables escape room maintainers to list their escape rooms, and enables
enthusiasts to mark which rooms they have cleared and commemorate their
experiences with photos.

This was able to meet the basic requirements I defined at the start of the
project. With more time available, additional features could be added to make it
a fully compelling product in its own right. At present, the industry would
struggle to use it to its full capacity due to its reliance on permanent escape
rooms at physical locations. There is further room for growth beyond the minimum
viable product in terms of features, but more basic priorities should be
addressed before then. These include reaching adequate test coverage, pagination
of outputs, enabling two-factor authentication, and addressing missing
accessibility features.