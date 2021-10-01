# Design proposal for Gerald

Gerald is a user-customizable notification tool for GitHub, similar to what
[Herald](https://secure.phabricator.com/book/phabricator/article/herald/) does
for [Phabricator](https://www.phacility.com/phabricator/).

## Vision

Elaine is working on the MLIR sub-project in the LLVM monorepo. She is
interested in all changes that affect her work. TO get notified on relevant
changes, she configures a couple of rules in the `.gerald` file in the monorepo:

```yaml
Auto-Label:
# Rules that automatically label Pull Requests based on the files they modify
- path: /llvm/** # path expression 
  label: llvm # label to assign
  branches: # notify on commits to these branches 
  - main
  - release*
- path: /mlir/**
  label: mlir
  branches:
  - main
  - release*

Notifications:
# Notify users on new labels: When one of these labels is assigned to an issue
# or Pull Request, notify the list of users
- labels: 
  - mlir
  - llvm  
  users: 
  - Elaine1234 # Elaine's github user account
  - Gao1234 # Elaine's colleague who also wants the same notifications

Email-Mapping:
# For sending email notifications, we actually need to know the users email 
# addresses. Github does not give out this.
- Elaine1234: elainesemail@provider.xyz
```

Whenever a new PullRequest (PR) is opened Gerald first checks the PR
against this config file. If an `Auto-Label` rule matches, Gerald assigns this
label to the PR. In the second phase Gerald checks the `Notifications` rules
against new labels that were assigned to Issues or PRs. For all matches, Gerald
adds a comment:

> *GeraldBot commented on Aug 27th:*
>
> notifying @Elaine1234, @Gao1234

GitHub then "subscribes" these users to this Issue/Pull Request and sends them
emails for this and all future changes.

Gerald also performs these checks on commits. As GitHub does not support
labeling commits, Gerald does so internally and sends out email notifications on
such commits. Gerald uses the `Email-Mapping` to get the user's email addresses
as GitHub does not provide these.

## Thoughts on the Design

Some of these features are available in other bots already, however I'm not
aware of a Bot that does all of this.

GitHub offers the
[Webhook
API](https://docs.github.com/en/developers/webhooks-and-events/webhooks)
and the [REST API](https://docs.github.com/en/rest) to interact with it. So we
could run our own services that is notified by GitHub via the Webhook API of any
changes in a repo and then uses the REST API to comment or modify Issues or PRs.
For sending commit emails, we would sill need an email account that supports
sending a large quantity of emails.

Keeping user email addresses in a public place is probably not the best solution
however the git commits already contain these addresses, so the information is
public already.

However this would mean we need to implement and maintain such a service.
