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

RSpec was employed for testing.

## Time constraints

If time were not an issue, I would have employed the following:

### Test coverage

SimpleCov was the standard at UKCloud with regards to coverage testing. I would
have employed this and aimed for at least 80% test coverage. In the end, my
testing strategy was to cover only novel backend functionality that sat
somewhere outside the standard Rails CRUD mold. This included:

- additional routes created beyond a standard Rails scaffold, such as those that
  make the current user a maintainer/enthusiast or those that remove image
  associations from a `Clear` or `EscapeGame` object
- secured routes - tests were created that challenged whether some attacking
  user could change a user ID in a form to steal ownership of a record
- some validations, such as those relating to limits on the number of image
  uploads for `EscapeGame`s and `Clear`s.
- some queries, particularly those relating to user privacy and escape room
  hiding.


- frontend testing with Jest
