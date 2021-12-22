# RFC: Code Review Comments Summary

## GitHub Missing Features

* UI Deficiencies:
  * On a subjective level, some community members mentioned they are less
      productive reviewing on GitHub. Using the two tabs between reviewing files
      and discussion comments instead of a unified view lead to some people
      reporting that they are using separate browser tabs to review on GitHub.
   * GitHub does not allow to comment on arbitrary line outside of the
      immediate context of the changed lines.
   * Comments become hidden and discussion marked as "obsolete"
      automatically, even when the comment isn't actually addressed or
      the discussion isn't marked "resolved" by the author. In Phabricator
      hiding is an explicit action from each individual.
      This leads to a recurring complain of an impression of "disappearing
      comments": they disappear from the diff view, but remain in the
      history of the "Conversation" tab, disconnected from the patch.
   * In case of force-push (either amend or rebase):
     * the UI does not provide a direct access to view the changes since a
        previous state.
     * Comments can't be viewed in their original context, you only see the
        4 lines above the comment.
* Automatic Subscription Rules (Herald Rules)
  * There is no builtin way for people to automatically subscribe to a pull request covering
    a specific part of the codebase.  This is seen as a major downside of GitHub pull requests.
* Good support for "Stack Reviews".
  * "Stack Reviews" are reviews of multiple dependant patches.  This is something that is easy to do
     with Phabricator, but does not have an equivalent with GitHub.
* GitHub isn't open-source and does not offer us any way to implement missing features of customize it for the needs of the project.
* E-mails don't include patch content; 

## GitHub Positive Features

* Familiar for new contributors.
  * Phabricator is seen by some as a barrier of entry for new contributors.
* Third-party hosting and support
  * Phabricator is no longer maintained upstream.
* Easier to integrate with CI and other kinds of automation.
  * GitHub actions makes it very easy to automate parts of our review process.
* Merge from UI
  * You can merge pull requests directly from the web UI, which avoid leaving the review tool
     to push to main, avoid having to manipulate command line tools (`arc` or `patch`, `git`).
     Phabricator does not have an equivalent.
* IDE Integration
  * Some IDEs have GitHub PR integration which can simplify the process of creating a pull request.
* Rich diffs of .rst files.
  * GitHub will render .rst files which makes them much easier to reivew.
* Alternative interfaces  (https://pullrequest.com, reviewable.io)
  * There are alternative interfaces that layer on top of GitHub Pull Requests that provide additional
    functionality.

### Workflow Improvement Opportunities with GitHub

* Can enforce developer policy / restrict pushes.
   * With GitHub pull requests we can enforce parts of the developer policy with automated checks.
* One point that was made in the comments is that it is hard to have reliable pre-commit
  testing with Phabricator, because Phabricator deals only with patches, so if the patch
  doesn't apply on the current main branch or some other known commit then you can't run
  CI on the patch.  With GitHub pull requests everything is a branch, so you can always run
  CI against them even if the patch is a little bit out-of-date with main.

### GitHub Pull Request Recommended Action Items

* Write a guide for how to create "Stacked Reviews".
* Decide if we allow Pull Request branches in the main repo.
* Define a policy for merging pull requests with multiple commits.
* Determine how can we emulate Herald Rules.
* Write a guide for filtering notifications.
* Investigate alternative interfaces (https://pullrequest.com, reviewable.io)
