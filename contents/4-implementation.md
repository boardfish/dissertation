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
this combined well with my use of the <!-- TODO: Cite! --> [GitHub
Flow](https://guides.github.com/introduction/flow/), in which I would aim to get
both tests and linting passing before merging. Towards the end of my development
cycle, when I had deployed to Heroku, I would also run through a set of checkout
testing steps I devised as a manual end-to-end regression test.

## Automated Testing

I aimed to use test-driven development wherever it was most critical. Primarily,
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
environment in which I ran tests locally was incredibly similar, continuous
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

`react-rails` documents component testing <!-- TODO: cite -->
[here](https://github.com/reactjs/react-rails/blob/d5da11129459cd75fd003c75319b1f7440c37322/README.md#test-component).
Stateless components such as `Avatar`s would be better tested this way - all
that would need to be asserted is that they are rendered with the correct props.
Or, to state that more generically, the correct arguments are passed to them at
page render.

Some components are dependent on asynchronous functionality - the Explore view
makes a request to the app's `/explore.json` endpoint on first render, and again
afterwards. In these situations, directly employing Facebook's
[Jest](https://jestjs.io) would be preferable.

### Automated regression and checkout testing against production

During my year in industry, this was in high demand. Deployment of the company's
primary products would take some quite time due to the number of manual steps
involved - checkout testing played no small part in this. I have documented
checkout testing steps in Blacklight's README, with clear indication that if the
project were to continue, checkout testing would be automated. If possible, I
would also follow up deployment with automated checkout testing at every
instance.