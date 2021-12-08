# RFC: Code Review Comments Summary

## GitHub Missing Features

* Intuitive Review Comments:
  * While this feedback may be somewhat subjective and depend on personal preferences,
    it was a common issue that was mentioned by many community members.  For example,
    some comments disappear when a patch is updated, sometimes comments are auto-hidden
    and can be easy to miss.  And it can be difficult to distinguish between general
    review comments and comments on specific lines of code
* Automatic Subscription Rules (Herald Rules)
  * There is no builtin way for people to automatically subscribe to a pull request covering
    a specific part of the codebase.  This is seen as a major downside of GitHub pull requests.
* Configurable Notifications.
  * Configuration for notifications is not very flexible and it can be difficult to manage especially
     for contributors that subscribe to multiple projects.
* Good support for "Stack Reviews".
  * "Stack Reviews" are reviews of multiple dependant patches.  This is something that is easy to do
     with Phabricator, but difficult to do with GitHub.

## GitHub Positive Featues

* Familiar for new contributors.
  * Phabricator is seen by some as a barrier of entry for new contributors.
* Can enforce developer policy / restrict pushes.
  * With GitHub pull requests we can enforce parts of the developer policy with automated checks.
* Third-party hosting and support
  * Phabricator is no longer maintained upstream.
* Easier to integrate with CI and other kinds of automation.
  * GitHub actions makes it very easy to automate parts of our review process.
  * One point that was made in the comments is that it is hard to have reliable pre-commit testing with Phabricator,
    because Phabricator deals only with patches, so if the patch doesn't apply on the current main branch or some
    other known commit then you can't run CI on the patch.  With GitHub pull requests everything is a branch, so
    you can always run CI against them even if the patch is a little bit out-of-date with main.
* Merge from UI
  * You can merge pull requests directly from the web UI, which is much more simple than the Phabricator
    process of manually (or with arc) downloading the patch, applying it and pushing.  This is both a time
    saver and more intuitive for new contributors.
* IDE Integration
  * Some IDEs have GitHub PR integration which can simplify the process of creating a pull request.
* Rich diffs of .rst files.
  * GitHub will render .rst files which makes them much easier to reivew.
* Alternative interfaces  (https://pullrequest.com, reviewable.io)
  * There are alternative interfaces that layer on top of GitHub Pull Requests that provide additional
    functionality.

### GitHub Pull Request Recommended Action Items

* Write a guide for how to create "Stacked Reviews".
* Decide if we allow Pull Request branches in the main repo.
* Define a policy for merging pull requests with multiple commits.
* Determine how can we emulate Herald Rules.
* Write a guide for filtering notifications.
* Investigate alternative interfaces (https://pullrequest.com, reviewable.io)
