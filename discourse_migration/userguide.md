# [draft] User guide for the migration of the mailing lists

This document is intended to help LLVM users to migrate from the mailing lists to
Discourse. Discourse two basic ways for interaction: Via the [web
UI](https://llvm.discourse.group/) and via emails.

## Setting up your account

The easiest way is to create an account using your GitHub account:

1. Navigate to https://llvm.discourse.group/
1. Click on "Sign Up" in the top right corner.
1. Choose "With GitHub" on the right side and log in with your GitHub account.

## Structure of Discourse

Discourse's structure is similar to a set of mailing lists, however different
terms are used there. To help with the transition, here's a translation table
for the terms:

| Mailing list | Discourse |
|--------------|-----------|
| *Mailing list*, consists of threads | *category*, consists of topics |
| *thread*, consists of emails | *topic*, consists of posts |
| *email* | *post* |

## Setting up email interactions

Some folks want to interact with Discourse purely via their email program. Here
are the typical use cases:

* You can [subscribe to a category or topic](https://discourse.mozilla.org/t/how-do-i-subscribe-to-categories-and-topics/16024)
* You can reply to a post, including quoting other peoples texts
  ([tested](https://llvm.discourse.group/t/email-interaction-with-discourse/3306/4) on GMail).
* [Quoting previous topics in an reply](https://meta.discourse.org/t/single-quote-block-dropped-in-email-reply/144802)
* **TODO:** Creating new topics via email is
  [supported](https://meta.discourse.org/t/start-a-new-topic-via-email/62977)
  but not configured at the moment. We would need to set up an email address
  per category and give Discourse POP3 access to that email account. This sounds
  like a solvable issue.
* You can filter incoming emails in your email client by category using the
  `List-ID` email header field.

## Mapping of mailing lists to categories

This table explains the mapping from mailing lists to categories in Discourse.
The email addresses of these categories will remain the same, after the
migration.

| Mailing lists         | category in Discourse |
|-----------------------|--------------------|
| All-commits           | no migration at the moment |
| Bugs-admin            | no migration at the moment |
| cfe-commits           | no migration at the moment |
| cfe-dev               | llvm-project/clang |
| cfe-users             | **TODO** llvm-project/clang or create new category? |
| clangd-dev            | llvm-project/clangd |
| devmtg-organizers     | **TODO** create new category |
| Docs                  | infrastructure/documentation |
| eurollvm-organizers   | **TODO** create new category |
| flang-commits         | no migration at the moment |
| flang-dev             | llvm-project/flang |
| gsoc                  | community/gsoc |
| libc-commits          | no migration at the moment |
| libc-dev              | llvm-project/libc |
| Libclc-dev            | **TODO** create new category |
| libcxx-bugs           | no migration at the moment |
| libcxx-commits        | no migration at the moment |
| libcxx-dev            | llvm-project/libcxx |
| lldb-commits          | no migration at the moment |
| lldb-dev              | llvm-project/lldb |
| llvm-admin            | **TODO** create new category |
| llvm-announce         | **TODO** create new category |
| llvm-branch-commits   | no migration at the moment |
| llvm-bugs             | no migration at the moment |
| llvm-commits          | no migration at the moment |
| llvm-dev              | llvm-project/llvm |
| llvm-devmeeting       | community/devmtg |
| llvm-foundation       | **TODO**  create new category|
| Mlir-commits          | no migration at the moment |
| Openmp-commits        | no migration at the moment |
| Openmp-dev            | llvm-project/openmp |
| Parallel_libs-commits | no migration at the moment |
| Parallel_libs-dev     | **TODO** use llvm-project/pstl or create new category ? |
| Release-testers       | **TODO** create new category |
| Test-list             | **TODO** create new category |
| vmkit-commits         | no migration at the moment |
| WiCT                  | community/women-in-compilers-and-tools/ |
| www-scripts           | **TODO** |

**TODO:** add discourse links once the list is finalized

## FAQ

### I don't want to use a web UI

You can do most of the communication with your email client (see section on
Setting up email interactions above). You only need to set up your account once
and then configure which categories you want to subscribe to.

### How do I send a private message?

On the mailing list you have the opportunity to reply only to the sender of
the email, not to the entire list. That is not supported when replying via
email on Discourse. However you can send someone a private message via the
Web UI: Click on the user's name above a post and then on `Message`.

Also Discourse does not expose users' email addresses , so your private
replies have to go through their platform (unless you happen to know the
email address of the user.)

### How can my script/tool send automatic messages?**

In case you want to [create a new
post/topic](https://docs.discourse.org/#tag/Posts/paths/~1posts.json/post)
automatically from a script or tool, you can use the
[Discourse API](https://docs.discourse.org/).

### Who are the admins for Discourse?

See https://llvm.discourse.group/about

### What is the reason for the migration?

**TODO:** add more explanation here

See also
[this email](https://lists.llvm.org/pipermail/llvm-dev/2021-June/150823.html)

### How do I set up a private mailing list?

If needed categories can have individual [security
settings](https://meta.discourse.org/t/how-to-use-category-security-settings-to-create-private-categories/87678)
to limit visibility and write permissions. Contact the
[admins](https://llvm.discourse.group/about) if you need such a category.

### What will happen to our email archives?

**TODO:** Explain the migration.

**TODO:** Can we preserve the links to the email archive?
see [#46](https://github.com/llvm/llvm-iwg/issues/46)

### How Do I cross-post (send in multiple categories) a message?

Topics are assigned to exactly one category, assigning to multiple categories
[is not supported](https://meta.discourse.org/t/selecting-multiple-category/116827).

**TODO:** The documentation says tags can be used to achieve a similar outcome.
However they don't say how to do that.

### I have another question not covered here. What should I do?

Please contact iwg@llvm.org or raise a
[ticket on GitHub](https://github.com/llvm/llvm-iwg/issues).
