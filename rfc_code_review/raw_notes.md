# Raw notes from analysis of Code Review feedback

## Raw Summary

* GitHub:
  * Easier for new contributors.
  * Stack Reviews more dificiult.
  * Comments on reviews can be displayed in unintuitave ways.
  * Cannot diff previous versions of the PR.
    * This can be resovled by enforcing a specific PR process.
  * Can prevent pushes to enforce developer policy.
  * Can move driectly to repo.
  * Potential to clutter repo with branches.
  * Can easily cross reference issues.
  * No herald rules.
  * Possible to use an alternative interfaces (https://pullrequest.com, reviewable.io)
  * Easier to enable autoatmion.
  * IDE integration.
  * Notifications are noisy.
  * Merge patches from UI.
  * Difficult to view patch history.
  * Rich diffs of .rst files.
  * Language specifix syntax highlightin in markdown.
  * Can apply changes from UI.
  * Automatically commit approved changes without commit access.
* Phabricator;
  * No long-term support
  * Hard to rgister.
  * Manual upload or arcanist.
  * Rebae and merging must be done manually or with arcanist.
  * More intuitive interface.
  * Hard to apply patches.
  * Pre-merge testing is unreliable.
  * Unclear what to do when patch is accepted.

## Raw Notes

* Comments 0 - 9
  * GitHub PRs is easier for new contributors to use. [22 Thumbs Up] [15 Thumbs Up]
  * GitHub PRs makes it difficult to review individual patches of large patchsets [9 Thumbs Up]
    * There is some disagreement on this point.
  * Github PRs makes it hard to distinguish review comments from code.
  * Github PRs cannot show what changed from prevoius versions of a patch.
  * Github PRs make it easier to enforce Develoer Policy (branch protections, review requirements, etc.)
  * Github PRs can merge directly to repo.
  * Github PRs some features may clutter the repo with banches.
  * Phabricator has no long-term support plan.
  * Phabricator is hard to register.
  * Phabricator requires uploading a diff manually or using an extra tool to submit patches.
  * Phabriactor requires rebase and merging to be done by hand or with Phabricator
* Comments 10 - 19
  * GitHub PRs can easily cross reference issues.
  * Phabricator interface is more intuitive.
  * Github PRs missing Hearald.
  * Lower prodcutivity with GitHub could reduce amount of reiviewer time for new contribuotors
  * Github PRs makes it easier to enforce passing presubmit tests.
  * Github has a CLI tool.
  * Alternative Github interfaces are available. https://www.pullrequest.com/
  * Can trigger workflows based on pull requsts
  * Easier to automate.
  * IDEs/Editors have integrations with Github
  * Github notifications are too noisy, requires using mail filters.

* Comments 20-29
  * UI options for merging patches.
  * Can have patches without branches.
  * Old GitHub comments get hidden when new patches are uploadd.
  * Github restricts where you can put comments.
  * Can't view patch history when force pushed.
  * Phabricator auto-subscribe is easier.
  * Github can automatically add reviewers.
  * Hard to apply Phabricator patches.
  * Concerns about using force push for GitHub review.
* Comments 30 -39
  * GH lets you compare edits of comments and PR descriptions.
  * GH You can reference PRs in other repositories.
  * GH Will let you view diffs of renderend .rst files.
  * GH allows language specific syntax highlighting in markdown.
  * Phabricator makes it easier to keep track of acitve comment threads and which comments have been addressed.
  * GH has better integrtion with issues.
  * GH has better integration with third-party tools.
  * GH interface is worse than Phabricator.
  * Should consider alternative GH interfaces, like reviewable.io.
  * Phabriactor is easier to revew revisions to a patch.
* Comments 40 - 49
  * GH: Makes pre-merge testing simple an convinient.
  * Phabricator pre-merge testing is unreliable, because patches need to be appliable.
* Comments 50 - 59
  * Poor notification system for reviews.
  * Stacked reviews are difficult, we could use a separate developer repo for branches.
  * Github pull requests can create cluttered history (We would need a policy for this).
* Comments 60 - 69
  * You can actually leave comments on unchanged lines for GH
  * GH allows comments on a range of lines.
  * Phabricator interface is confusing.
  * Phabiracotr don't know what to do when a review is approved.
  * Phabricator needs to create a patch manually.
* Comments 70 - 79
  * GH: Only administrators can edit pull request metadata.
  * GH: Confusing comment display for new revisions of PRs
  * GH: Beter integration with CI tools
  * GH: No "Active Revisions" view ( https://github.com/pulls provides this).
  * GH: Squash Merge Messy history
* Comments 80 - 85
  * GH: Can retreive exact state of patch for building and testing.
  * GH: Can apply canges from UI
  * PH: Full history of comments
  * PH: Full file context
  * GH: Approved PRs can be committed automatically even if contributore does nothave access.
  * GH: More automation opportunities
  * GH: Collapses comments in an unintuitive way.
