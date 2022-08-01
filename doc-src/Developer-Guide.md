# nRonn Developer's Guide

## Release checklist

* Update the version in files
  * nronn.gemspec (update the release date, too)
  * `lib/ronn.rb`
* Update `CHANGES` with the release date
* Regenerate the man pages with `bundle exec rake man`
* Run the tests one last time! `bundle exec rake test`
* Commit the updated files
* Tag the release: `git tag vX.Y.Z`
* `git push --tags`
* Create the Release on GitHub Releases
* Build and deploy the gem to RubyGems
  * `gem build nronn.gemspec`
  * `gem push nronn-<version>.gem`
* TODO: Announce the release somewhere

After the release, start development on the next release:

* Update the version in files
  * nronn.gemspec
  * `lib/ronn.rb`
* Update `CHANGES` with a new section for the next release
* Regenerate the man pages again: `rake man`
* Commit and push

## Running tests

`bundle exec rake test` will run all the tests.

Do `RONN_QUIET_TEST=1 bundle exec rake test` for shorter output that omits the possibly-long
diff outputs.
