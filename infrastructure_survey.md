# Survey of existing project infrastructure

The set of tools used by the LLVM project are it's *infrastructure*. This page
contains an overview of the existing tools, what they are used for and a contact
for each of these.  The purpose of this document is to establish an initial survey of what we're working with, not to be exhastive.  We hope to document individual pieces and workflows in detail at a later time.  

The [Getting Involved](http://llvm.org/docs/GettingInvolved.html) page
explains the intended workflows for using these tools.

<!-- 
Template for new infrastructure components 

### (Name of component)

- Description: 
- Most important workflows:
- Admin contact: 
- Hosted at:
- Integrations:
- 
-->

## Communication

There are several tools used for communication.

### IRC

- see [IRC](https://llvm.org/docs/GettingInvolved.html#irc) on accessing
- no LLVM specific infrastructure required
- no central admin
- use case: interactive chats between community members
  - somewhat redundant to Slack and Discord
- integrations:
  - see [IRC](https://llvm.org/docs/GettingInvolved.html#irc)
- Ideas:
  - Do we have an integration with Discord?  
    [discord-irc](https://github.com/reactiflux/discord-irc) seems to be useful.
- Current challenges:
  - N/A

### Mailing lists

- see [Mailing Lists](https://llvm.org/docs/GettingInvolved.html#mailing-lists>)
- Dedicated [Mailman](http://www.gnu.org/software/mailman/index.html) instance
- hosted at TODO
- administrated by TODO
- use cases: asynchronous communication of the community and code reviews
  - somewhat redundant to Discourse
- ideas:
  - Maybe integrate with Discourse?
- Current challenges:
  - Difficult to realize GDPR deletion requests

### Discourse

- [llvm.discourse.group/](https://llvm.discourse.group/)
- hosted service
- `Admins <https://llvm.discourse.group/about>`_
- use case: asynchronous communication of the community
  - somewhat redundant to the mailing lists.
- Integrations:
  - Github for single sign on

### Discord

- Join the group with this [invitation](https://discord.gg/xS7Z362)
- use case: interactive chats between community members
  - somewhat redundant to Slack and IRC
- Admins: See discord -> Server settings -> Members -> filter for admins
- TODO: do we have an integration with IRC?  
  here also [discord-irc](https://github.com/reactiflux/discord-irc) seems to be
  useful.
- Integrations:
  - [BuildBot status](https://discord.com/channels/636084430946959380/646265759823167498/666582633706291200)
  - Github commits
  - YouTube
  - Twitter

### Slack

- [llvm.slack.com](https://llvm.slack.com)
- hosted service, not clear if this is public vs foundation board resource
- administrated by TODO
- use case: interactive chats between board and ops team
  - somewhat redundant to IRC and Discord

### Twitter

- [@llvm.org](https://twitter.com/llvmorg)

## Source Code Repository

### Git and Github

- Multiple repositories hosted on [GitHub](http://github.com/llvm/)
  - most prominent: the [LLVM Monorepo](https://github.com/llvm/llvm-project)
- Hosted service by GitHub
- administrated by TODO
- use case: storing/versioning of the project source code
- Integrations:
  - display BuildBot status
  - Email notifications
  
### Legacy SVN

- Does the legacy SVN repo still exist?  If so, what is it being used for?
- Do we want a historical archive, either active or offline?

## Code reviews

We probably need a master list of which sub-projects are using each mechanism.

### On the mailing lists

- Per the [documentation][https://llvm.org/docs/CodeReview.html], we allow code review by email on llvm-commits and cfe-commits.

### Phabricator

- Code reviews for `llvm-project` and some other projects are performed in
  [Phabricator](https://reviews.llvm.org/) and on the mailing lists.
- Phabricator is hosted on Google Cloud
- Administrated by TODO
- Integrations:
  - Single sign on with Google and Github
  - Reading data from Github
  - Triggering builds on pre-merge testing
  - sending Emails on mailing list
  - processing email responses (major enhancement)

### GitHub Pull Requests

- Some projects are using Pull Requests for code reviews.
- Native feature of GitHub, does not need hosting or administration.

## Build infrastructure

The project is using multiple build systems with different scopes and
technologies.

### Build bots

- use case: post-merge testing on various operating systems and platforms
- workers hosted and maintained by the community
- server hosted and maintained by Access Softtek
- [Production server](http://lab.llvm.org:8011/), sending emails
- [Staging server](http://lab.llvm.org:8014/), no email notifications, for
  testing purposes.
- We really need an index of active bots, and points of contact for each.

### Green dragon

- [green.lab.llvm.org/green/](http://green.lab.llvm.org/green/)
- use case: post merge testing on Apple's MacOS
- Hosted at Apple
- administrated by TODO

### Pre-merge testing

- use case: pre-merge testing of patches on Phabricator
- Integrations
  - Phabricator to get patches and show results
  - Github repository to get sources
  - Buildkite to run the builds
- Links:
  - Github project [google/llvm-premerge-checks](https://github.com/google/llvm-premerge-checks/)
  - [Buildkite project](https://buildkite.com/llvm-project)

### LLVM GN buildbot

- [45.33.8.238](http://45.33.8.238/)
- use case: post-merge testing using GN build system
- Hosted at TODO
- Administrated by TODO

### LNT

- [lnt.llvm.org](http://lnt.llvm.org)
- Nightly tests, measuring performance and code size
- Hosted on Google Cloud
- Current challenges:
  - is looking for new maintainer

## Bug Tracker

- [bugs.llvm.org](https://bugs.llvm.org/)
- self-hosted Bugzilla on TODO
- Administrated by TODO
- Migration to Github Issues in progress

## Build Systems

- The official build system is *CMake*.
- other, unsupported build systems:
  - [gn](https://github.com/llvm/llvm-project/tree/master/llvm/utils/gn)
  - Support for Bazel currently in discussion.

## Test tooling

### Unit testing

- using [googletest](https://github.com/google/googletest)

### LIT

- home-grown testing framework [LIT](https://llvm.org/docs/CommandGuide/lit.html)
- included in the
  [LLVM monorepo](https://github.com/llvm-mirror/llvm/tree/master/utils/lit)

## Web sites

- llvm.org
- foundation.llvm.org
- community-dot-o.llvm.org
- blog.llvm.org
- mlir.llvm.org
- clang.llvm.org
- lldb.llvm.org
- clangd.llvm.org
- reviews.llvm.org
- bugs.llvm.org
- circt.llvm.org
- releases.llvm.org

## Content Delivery Network (CDN)

Binaries/releases are distributed by [Fastly](https://www.fastly.com/).

## test case reduction

- bugpoint
- llvm-reduce
- c-reduce (external tool, but heavily used)
- delta (external tool, but heavily used)

## practical formal reasoning

[Alive2](https://github.com/AliveToolkit/alive2) is an external effort to build
tooling around formal semenatics for LLVM IR.  It is being used extensively
validate InstCombine transforms before submission, and (less extensively) to
isolate which transform is miscompiling.  It's also being used to drive efforts
to improve the specification of poison and undef in the LangRef.

## external testing and revert to green

As a project, we rely heavily on external testing of ToT to ensure quality via
bisection and revert-to-greeen. A few of particular note:

- Google's weekly build with new ToT compiler finds a lot.  The hashes of
  previously builds are available (where?) and are consumed by others as a
  defacto "recent stable" series.
- See Green Dragon above.
- https://llvm-compile-time-tracker.com - ongoing effort to track and actively
  revert changes which impact compile time negatively.  Contact: Nikita Popov?
- Nuno Lopes and his team maintains a [dashboard][https://web.ist.utl.pt/nuno.lopes/alive2/]
  of currently failing LLVM tests related to the ongoing efforts to formalize poison/undef.
- Fuzzing efforts

  - Google's OSS Fuzz
  - Azul runs a [java fuzzer][https://github.com/AzulSystems/JavaFuzzer] which
    finds a lot of miscompiles.
  - [clang-triage][https://github.com/sliedes/clang-triage] - externally
    developed, doesn't appear to still be active
  - to be continued...
  
Running these efforts are probably mostly out of scope for the working group,
but supporting them w/ e.g. bisection and reduction tooling is not.  We should
probably also establish point of contacts for each if they're going to be
reverting lots of changes upstream.

## code analysis reports

- https://llvm.org/reports/scan-build/
- https://llvm.org/reports/coverage/ (out of date)
- https://scan.coverity.com/projects/llvm (*very* out of date)

It's unclear who owns these, or how they're generated.

## packages and distribution

Various distributions package LLVM, we may want to document tooling and
assumptions around that.

https://apt.llvm.org/ provides "nightly" LLVM packages.  Unclear how widely this
is used.  It does appear to be actively maintained.  See section on technical
details towards end of page.

- Contact: Sylvestre Ledru
- Last time @ChristianKuehnel talked to the Sylvestre, there were no usage metrics available.

## Google Workspace

[Google Workspace](https://workspace.google.com/) is in the LLVM foundation to
manage mailing lists (e.g. iwg@llvm.org) and to collaborate on documents.
This is not used in the LLVM community.
