# Implementation and Testing

<!--
In addition to illustrating "coding traps", this should highlight particular
novel aspects to algorithms. Testing should be according to the scheme presented
in the Analysis chapter and should follow some suitable model---e.g. category
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
are backed by containers---running the app using containers sets a good
precedent to running it on a platform like Kubernetes with the right expertise.

Continuous integration tests code at each commit. I was able to configure
CircleCI to build the Docker image used locally, and lint and test the
code---this combined well with my use of the [GitHub
Flow](https://guides.github.com/introduction/flow/), in which I would aim to get
both tests and linting passing before merging a development branch into the
`master` branch. Towards the end of my development cycle, when I had deployed to
Heroku, I would also run through a set of checkout testing steps I devised as a
manual end-to-end regression test.

## Automated Testing

I aimed to use test-driven development to the best of my ability. Primarily,
this meant securing controller routes and making sure that novel routes outside
the standard Rails scaffold functioned as expected. This included:

- additional routes created beyond a standard Rails scaffold, such as those that
  make the current user a maintainer/enthusiast or those that remove image
  associations from a `Clear` or `EscapeGame` object
- secured routes---tests were created that challenged whether some attacking
  user could change a user ID in a form to steal ownership of a record
- some validations, such as those relating to limits on the number of image
  uploads for `EscapeGame`s and `Clear`s.
- some queries, particularly those relating to user privacy and escape room
  hiding.

SimpleCov was the standard on my year in industry with regards to coverage
testing. I would have employed this and aimed for at least 80% test coverage
across controllers, models and helpers, had time allowed for it.

The RSpec test suite ran at each commit on CircleCI's platform, halting in the
instance of a failed Docker build, linting failure, or failed test. Though the
environment in which I ran tests locally reflected its configuration, continuous
integration served to ensure that the `master` branch continued to pass and was
stable.

There were instances in which merging was delayed. CircleCI limits usage and
fails all builds that fall outside a given quota. In these instances, I would
either wait until my credits with CircleCI had reset and rerun the build, or
trust that running the tests locally qualified instead and merge. In the event
of a CI failure in an industry scenario, this would be discussed in the
development department---generally, CI serves as a strict gatekeep to `master`,
so in the majority of cases, development departments would resolve not to merge
to `master` until their CI server functioned again. Due to time constraints, I
was not quite so strict around it. This came at a cost.

As I fully expected, this created a difficulty. With `master` having been
changed without being monitored by regular CI runs, new issues had reached the
branch---particularly, absence of the Rails master key meant that encrypted
credentials couldn't be accessed during the application's initialisation cycle.
I was able to fix this and proceed, but in an industry environment with several
developers merging to `master`, this could have caused a significant slowdown in
development due to potentially overlapping changes.

Below, an example from `spec/controllers/clears_controller_spec.rb` is featured.
This is one of the automated tests in the application's RSpec suite, which is
run by CircleCI at each commit. These tests ensure that none other than the
creator of a clear can edit it---the helper method `random_user`, when given an
`owner`, selects or creates a user other than the `owner`. This user becomes
what the tests call the `attacking_user`---they are signed in and try to act
against the `Clear` record. Both instances should raise a `404` error. `404` is
generally returned across Blacklight when the user does not have access to the
record in question, and is given back in the instance of an
`ActiveRecord::RecordNotFound` error.

```ruby
RSpec.describe ClearsController, type: :controller do
  before(:each) do
    @clear = create(:clear)
  end

  it 'does not allow users to edit others\' clears' do
    clear = @clear
    attacking_user = random_user(owner: @clear.user)
    sign_in attacking_user
    expect do
      put :update, params: {
        id: clear.to_param,
        clear: attributes_for(:clear).merge(user: attacking_user)
      }
    end.to raise_error(ActiveRecord::RecordNotFound)
  end

  it 'does not allow users to delete others\' clears' do
    clear = @clear
    attacking_user = random_user(owner: @clear.user)
    sign_in attacking_user
    expect do
      delete :destroy, params: {
        id: clear.to_param
      }
    end.to raise_error(ActiveRecord::RecordNotFound)
  end
end
```

### Focused Frontend Testing

I omitted frontend testing that strayed too far beyond scaffolded tests due to
time constraints. However, image attachment forms required testing to make sure
that they behaved as users intended. One such case is detailed here.

Rails 6.0.0 introduced a change whereby newly-uploaded attachments replaced
existing attachments, as opposed to being appended to the existing group of
attachments. [Pull request #36716](https://github.com/rails/rails/pull/36716)
against the `rails` codebase describes the difference between `rails`' behaviour
before and after 6.0.0 in this situation. Blacklight was generated as a `rails`
6.0.2 application, and so needed a workaround for the new behavior. This was to
include the signed IDs as hidden fields.

The test below checks that if an image is attached to a record, a hidden field
appears for it in the form when it is rendered.

```ruby
it 'doesn\'t overwrite files on update' do
  # Attach an image so one already exists.
  image_to_attach = File.open(
    Rails.root.join(
      'spec',
      'fixtures',
      'files',
      'escape_game',
      'SSBU-Big_Blue.png'
    )
  )
  @clear.images.attach(
    io: image_to_attach,
    filename: 'original_image.png',
    content_type: 'image/png'
  )
  render
  # Make sure there's a hidden field for the image that already exists on the
  # clear
  assert_select 'form[action=?][method=?]', clear_path(@clear), 'post' do
    assert_select 'input[multiple=multiple][type=hidden]' \
                  '[name=clear\[images\]\[\]]'
  end
end
```

However, my use of React components for major features like
the Explore page means that swathes of the app are untested.

`react-rails` documents [component testing against rendered Rails
views](https://github.com/reactjs/react-rails/blob/d5da11129459cd75fd003c75319b1f7440c37322/README.md#test-component).
Stateless components such as `Avatar`s would be better tested this way---all
that would need to be asserted is that they are rendered with the correct props.
To state that more generically, the assertion is that the correct arguments are
passed to them at page render.

Some components are dependent on asynchronous functionality---the Explore view
makes a request to the app's `/explore.json` endpoint on first render, and again
afterwards. In these situations, directly employing Facebook's
[Jest](https://jestjs.io) would be preferable.

### Automated Regression and Checkout Testing Against Production

Checkout testing usually comprises a series of steps taken from an end user
perspective against a production instance. It ensures that end users can
continue to use the application as intended by checking that all features of the
experience work as intended.

During my year in industry, checkout testing after deployment was not automated.
Developers sought to automate the process so that deployment might not consume
as much time. Libraries such as
[Puppeteer](https://github.com/puppeteer/puppeteer/) can be useful for such a
purpose---previously, I have used Puppeteer to [create PDF forms of webpages
repeatably](https://github.com/boardfish/CV/blob/ed664d0e87e4d0ec1d6afab8214a5753e033669e/topdf.js).

I have documented checkout testing steps in Blacklight's README, with clear
indication that if the project were to continue, checkout testing would be
automated. If possible, I would also follow up deployment with automated
checkout testing at every instance using continuous integration. The checkout
testing steps are replicated below.

#### Checkout Testing Steps

Check that the...

- ...homepage renders correctly, particularly with regards to React components
  such as the navbar (visual check)
- ...CSS is applied to the elements (visual check)
- ...Bootstrap JS from asset pipeline works---i.e. it is possible to open the
  Filters dropdown on Explore and collapsed navbar on mobile
- ...Auth0 login flow works---i.e. it is possible to log in and hold a session
- ...Auth0 logout flow works---i.e. it is possible to log out and your session
  is destroyed
- ...controllers work---i.e. Explore returns escape games if they exist. Create
  one if it does not exist and make sure that the list of escape games you own
  on your `user#show` page displays it.
- ...JS views work---i.e. it is possible to remove images from a listing and
  have the corresponding table row disappear

## Security Concerns

I aimed to make as complete a software product as possible, given the time. Part
and parcel of this was ensuring security. In Rails, this tends to mean enforcing
restraints on which users can edit models, and which fields a user is able to
submit. There are two parts to this:

1. ensuring that users not associated with the object cannot edit it
2. ensuring that the object's associated user cannot be changed

In Blacklight, this is done as follows:

1. retrieving the object by way of a query that asks for it among only those the
   current user owns; returning a 404 status code otherwise
2. setting the object's associated user to the current user

On its own, the second part of my solution would be insecure---if an attacking
user accessed an object, they could make themselves its associated user and thus
"steal" it. The more standard way of doing this, in the case of a `PUT`/`PATCH`,
would be to strip out the incoming user ID from the hidden field in the form.
This methodology is used on create as well as on update, which means that users
cannot create records in other users' names.