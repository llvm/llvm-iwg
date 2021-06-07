# User guide for the migration of the mailing lists

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
| cfe-dev               | **TODO** |
| cfe-users             | **TODO** |
| clangd-dev            | lvm-project/clang |
| devmtg-organizers     | community/devmtg |
| Docs                  | infrastructure/documentation |
| eurollvm-organizers   | community/eurollvm |
| flang-commits         | no migration at the moment |
| flang-dev             | lvm-project/flang |
| gsoc                  | community/gsoc |
| libc-commits          | no migration at the moment |
| libc-dev              | lvm-project/libc |
| Libclc-dev            | **TODO** |
| libcxx-bugs           | no migration at the moment |
| libcxx-commits        | no migration at the moment |
| libcxx-dev            | lvm-project/libcxx |
| lldb-commits          | no migration at the moment |
| lldb-dev              | lvm-project/lldb |
| llvm-admin            | **TODO** |
| llvm-announce         | **TODO** |
| llvm-branch-commits   | no migration at the moment |
| llvm-bugs             | no migration at the moment |
| llvm-commits          | no migration at the moment |
| llvm-dev              | lvm-project/llvm |
| llvm-devmeeting       | community/devmtg |
| llvm-foundation       | **TODO** |
| Mlir-commits          | no migration at the moment |
| Openmp-commits        | no migration at the moment |
| Openmp-dev            | lvm-project/openmp |
| Parallel_libs-commits | no migration at the moment |
| Parallel_libs-dev     | **TODO** |
| Release-testers       | **TODO** |
| Test-list             | **TODO** |
| vmkit-commits         | **TODO** |
| WiCT                  | **TODO** |
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

see https://lists.llvm.org/pipermail/llvm-dev/2021-June/150823.html

### How do I set up a private mailing list?

If needed categories can have individual [security
settings](https://meta.discourse.org/t/how-to-use-category-security-settings-to-create-private-categories/87678)
to limit visibility and write permissions. Contact the
[admins(https://llvm.discourse.group/about) if you need such a category.

### What will happen to our email archives?

**TODO:** Explain the migration.

### I have another question not covered here. What should I do?

Please contact iwg@llvm.org or raise a
[ticket](https://github.com/llvm/llvm-iwg/issues).
