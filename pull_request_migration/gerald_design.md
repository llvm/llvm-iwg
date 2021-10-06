# Design proposal for Gerald

Gerald is a user-customizable notification tool for GitHub, similar to what
[Herald](https://secure.phabricator.com/book/phabricator/article/herald/) does
for [Phabricator](https://www.phacility.com/phabricator/).

## Vision

Elaine is working on the MLIR sub-project in the LLVM monorepo. She is
interested in all changes that affect her work. To automatically assign labels
to Pull Requests she configures a couple of rules in the `.gerald` file in the monorepo:

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
- path: /llvm/doc/**
  label: documentation
  branches:
  - main
  - release*  
```

Whenever a new PullRequest (PR) is opened Gerald first checks the PR
against this config file. If an `Auto-Label` rule matches, Gerald assigns this
label to the PR.

In a second step Elaine logs into the Gerald Web UI using her Github account. In
this UI she configures her notification settings:

| repository | label notifications |
|------------|---------------------|
| llvm/llvm-project | llvm, mlir |
| ... | ...|

Whenever the labels of a PR or an Issue change, Gerald uses these settings and
adds a comment for all matches:

> *GeraldBot commented on Aug 27th:*
>
> notifying @Elaine1234, (list of other users)

GitHub then "subscribes" these users to this Issue/Pull Request and sends them
emails for this and all future changes. They also receive an initial email with
the description of the PR/Issue.

Gerald also performs these checks on commits. As GitHub does not support
labeling commits, Gerald does so internally and sends out email notifications on
such commits. For the commit notifications Elaine also needs to configure her
email address in Gerald.

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

We should not store personal information in the git repository. So we need some
database for that. For the overall system, we probably need to implement 3 parts
that communicate via a common database:

1. A web UI where users can configure their rules. We can use "Login with
   GitHub" so we don't have to manage credentials ourselves.
1. A webhook that accepts change notifications from GitHub and stores them in a
   queue.
1. A worker that processes the queue entries and sets the labels, comments on
   PRS/issues and sends commit notification emails. The worker uses the config
   information from the `.gerald` file and from the database.
