# Implementation and Testing

<!--
In addition to illustrating "coding traps", this should highlight particular
novel aspects to algorithms. Testing should be according to the scheme presented
in the Analysis chapter and should follow some suitable model - e.g. category
partition, state machine-based. Both functional testing and user-acceptance
testing are appropriate. For experimental/investigative projects, techniques
developed should be evaluated against a standard result set for calibration, as
well as the "live" data set. For theoretical projects, the relative
power/expressiveness of the theory should be evaluated with respect to competing
approaches.
-->

My commitment to emulating industry best practices carried through to
implementation. I felt it vital to use and work with such things as continuous
integration servers, containerisation, and linting tools to maintain code
quality and readability. Of course, none of these decisions were taken lightly. 

While there is still some discourse over whether containerisation in development
environments is entirely appropriate, I chose to use it to maintain some degree
of parity between running locally and running in CI. Another reason why I made
this choice was that popular production platforms such as Amazon Web Services
are backed by containers - running the app using containers sets a good
precedent to running it on a platform like Kubernetes with the right expertise.

Continuous integration tests code at each commit. I was able to configure
CircleCI to build the Docker image used locally, and lint and test the code -
this combined well with my use of the [GitHub
Flow](https://guides.github.com/introduction/flow/), in which I would aim to get
both tests and linting passing before merging. Towards the end of my development
cycle, when I had deployed to Heroku, I would also run through a set of checkout
testing steps I devised as a manual end-to-end regression test.

## Automated Testing

I aimed to use test-driven development to the best of my ability. Primarily,
this meant securing controller routes and making sure that novel routes outside
the standard Rails scaffold functioned as expected. This included:

- additional routes created beyond a standard Rails scaffold, such as those that
  make the current user a maintainer/enthusiast or those that remove image
  associations from a `Clear` or `EscapeGame` object
- secured routes - tests were created that challenged whether some attacking
  user could change a user ID in a form to steal ownership of a record
- some validations, such as those relating to limits on the number of image
  uploads for `EscapeGame`s and `Clear`s.
- some queries, particularly those relating to user privacy and escape room
  hiding.

SimpleCov was the standard at UKCloud with regards to coverage testing. I would
have employed this and aimed for at least 80% test coverage, had time allowed
for it.

The RSpec test suite ran at each commit on CircleCI's platform, halting in the
instance of a failed Docker build, linting failure, or failed test. Though the
environment in which I ran tests locally reflected its configuration, continuous
integration served to ensure that the `master` branch continued to pass and was
stable.

There were instances in which merging was delayed. CircleCI limits usage and
fails all builds that fall outside a given quota. In these instances, I
would either wait until my credits with CircleCI had reset and rerun the build,
or trust that running the tests locally qualified instead and merge. In the
event of a CI failure in an industry scenario, this would be discussed in the
department - generally, CI serves as a strict gatekeep to `master`, so in the
majority of cases, development departments would resolve not to merge to
`master` until their CI server functioned again. Due to time constraints, I was
not quite so strict around it.

### Frontend testing

I omitted frontend testing that strayed too far beyond scaffolded tests due to
time constraints. However, my use of React components for major features like
the Explore page means that swathes of the app are untested.

`react-rails` documents [component testing against rendered Rails
views](https://github.com/reactjs/react-rails/blob/d5da11129459cd75fd003c75319b1f7440c37322/README.md#test-component).
Stateless components such as `Avatar`s would be better tested this way - all
that would need to be asserted is that they are rendered with the correct props.
Or, to state that more generically, the correct arguments are passed to them at
page render.

Some components are dependent on asynchronous functionality - the Explore view
makes a request to the app's `/explore.json` endpoint on first render, and again
afterwards. In these situations, directly employing Facebook's
[Jest](https://jestjs.io) would be preferable.

### Automated regression and checkout testing against production

CHeckout testing usually comprises a series of steps taken from an end user
perspective against a production instance. It ensures that end users can
continue to use the application as intended by checking that all features of the
experience work as intended.

During my year in industry, checkout testing after deployment was not automated.
Developers sought to automate the process so that deployment might not consume
as much time. Libraries such as
[Puppeteer](https://github.com/puppeteer/puppeteer/) can be useful for such a
purpose - previously, I have used Puppeteer to [create PDF forms of webpages
repeatably](https://github.com/boardfish/CV/blob/ed664d0e87e4d0ec1d6afab8214a5753e033669e/topdf.js).

I have documented checkout testing steps in Blacklight's README, with clear
indication that if the project were to continue, checkout testing would be
automated. If possible, I would also follow up deployment with automated
checkout testing at every instance.

## On user acceptance testing

User acceptance testing became difficult to conduct due to the COVID-19
pandemic. This event endangered the very purpose of Blacklight itself, and made
it difficult to justify revealing Blacklight. The industry is already
experiencing great turbulence worldwide due to government orders to stay at
home, and would not have a use for Blacklight in its current form.

In order to make Blacklight suitable for this situation, the `EscapeGame` model
would need to make some allowances for "in-home" escape games - sets of locks,
puzzles, and props, which are distributed by escape game maintainers. These
allow enthusiasts to run their own escape game experience in the home. I would
likely do this by creating additional fields on `EscapeGame` and create another
model through Rails' [single-table
inheritance](https://api.rubyonrails.org/classes/ActiveRecord/Inheritance.html)
mechanism. The idea behind this would be that both kinds of escape game could be
shown side-by-side in views such as the Explore view. 

## Security concerns

I aimed to make as complete a software product as possible, given the time. Part
and parcel of this was ensuring security. In Rails, this tends to mean enforcing
restraints on which users can edit models, and which fields a user is able to
submit. There are two parts to this:

1. ensuring that users not associated with the object cannot edit it
2. ensuring that the object's associated user cannot be changed

In Blacklight, this is done as follows:

1. retrieving the object by way of a query that asks for it among only the
   current user's escape games; returning a 404 status code otherwise
2. setting the object's associated user to the current user

On its own, the second part of my solution would be insecure. The more standard
way of doing this on update would be to strip out the incoming user ID from the
hidden field in the form. However, there is good reasoning behind it.
This methodology is used on create as well as on update, which means that users
cannot create records in other users' names.