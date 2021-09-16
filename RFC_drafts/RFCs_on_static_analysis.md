# LLVM RFCs on static analysis

author: (@ChristianKuehnel)
created: 2021-09-16

## Overview

This document contains a series of RFCs for LLVM around the usage of static
analysis tools. All of these RFCs can be implemented separately, however they
deliver the most impact if implemented together.

## RFC 1: Clang-format the entire code base

### tl;dr

I propose to enforce
[clang-format](https://clang.llvm.org/docs/ClangFormat.html) on all new changes
to the monorepo to achieve a consistent style of code formatting.

### Problem statement

The LLVM code base has grown over time and not all code follows the
[LLVM Coding Standards](https://llvm.org/docs/CodingStandards.html). However it
does not make sense to convert all existing code as this would mess up the git
history, this would results in 1.5 million lines of code changed.

### Proposed solution

I propose to implement the following changes:

1. Set up a post-merge check on Buildbot to verify new patches stick to the
   clang-format requirements. This check shall use the latest released version
   of clang-format.
1. Enable clang-format checks in pre-merge testing.
1. Agree on parts of the code base that shall be excluded from auto-formatting
   (e.g. 3rd party code, generated code, test data).
1. Update the clang-format configuration in the repo as needed.

### Benefits

* Having common coding standards makes the code base easier to read and
  navigate. It also makes it easier to contribute to various parts of the code
  base.
* Having a tool to automatically format the code reduces the effort for the
  developers to do so.
* Automatic checks prevent backslides.
* "Eat your own dog food": We (LLVM) should be using the tools we’re creating.

### Risks

* Automatic code formatting will not always provide the perfect results.
* Enforcing clang-format only on patches only will not ensure that we ever get
  all of the code base formatted.

## RFC 2: Enforce clang-tidy checks on all modified code

### tl;dr

I propose to require all modified code to got through clang-tidy checks. However
the author and reviewers are free to ignore the findings as they find
appropriate.

### Problem statement

C++ is a tricky language and it’s easy to shoot yourself in the foot. Thus smart
people created clang-tidy as part of LLVM to help developers work around typical
pitfalls. However today we’re not forcing people to run clang-tidy on their
changes. Also the findings do not always make sense and they do have false
positives, so it does not make sense to enforce zero new findings.

Currently the code base contains around 70’000 clang-tidy findings. We have
clang-tidy already checks enabled in pre-merge testing.

### Proposed solution

I propose to implement the following changes:

1. Agree with the community on a clang-tidy configuration for the LLVM monorepo
   and put the config files into the repository. We probably also need to
   disable some of the checks in some parts of the code base (e.g. naming
   conventions) for historic reasons. Then update the [Coding
   Standards](https://llvm.org/docs/CodingStandards.html) where needed.
2. Agree on parts of the code base that shall be excluded from clang-tidy checks
   (e.g. 3rd party code, generated code, test data).
3. Setup `arc lint` to enable users to automatically check their changes before
   uploading. Offer a script to do the same thing for users not using `arc`.
4. Set up a post-merge check on Buildbot to notify authors if they submitted a
   new finding in their patch.

### Benefits

* Having static analysis enabled by default should prevent typical programming
  errors.
* Having automatic checks is cheap.
* The checks are automatic, so this does not cause additional effort for human
  reviewers.
* Authors may ignore the findings if they do not make sense.  
* Eat your own dogfood: We (LLVM) should be using the tools we’re creating.

### Risks

* Allowing authors to ignore the findings might not prevent all errors.
* It will take some time for developers to get used to the clang-tidy
  requirements. In the beginning this will require additional effort.
* The LLVM code base has grown over a long period of time. It might not make
  sense to clean up all findings. So we should agree on some checks to be
  disabled in some parts of the code base.

## RFC 3: Reduce clang-tidy findings towards zero

### tl;dr

I propose to agree to the long-term goal to reduce the number of clang-tidy
findings in the LLVM monorepo towards zero.

### Problem statement

The code base has grown over time and we have accumulated technical debt. While
a finding might not be causing a problem today, when the code is used in a
different way tomorrow. We currently have around 70’000 clang-tidy findings on
the main branch.

### Proposed solution

We should set ourselves the long-term goal to as many clang-tidy findings
from our codebase as is reasonable. This goal does *not* need a timeline, we
just commit to
getting better over time and to be willing to work on this topic as a community
(via patches or reviews).

We can reach that goal in several ways:

* Fix the actual findings in existing code.
* Enable only the checks we care about in the directories we care about.
* Prioritize the checks with the highest expected value and disable the rest for
  now.
* Incrementally improve the checks themselves to reduce false-positives.

### Benefits

* We’re reducing the technical debt in the code base over time.
* This should reduce the number of (unknown) bugs.
* Making such a goal explicit sends the clear message that contributions to
  reduce findings are welcome. It might attract contributors willing to put
  their time into this effort.
* Improving the accuracy of the clang-tidy checks would improve the tool for all
  users.  

## Risks

* Refactorings to reduce findings might introduce new bugs.
* There is a huge pile of findings in the code base today and it is a lot of
  effort to reduce these.
* We will most likely never actually get to zero.
* We might find false-positives that are really hard to fix properly.
* Refactorings to (internal) APIs might break downstream users.

## RFC 4: Set up a static analysis dashboard

### tl;dr

I propose to set up a dashboard to show the current status and recent changes to
the overall static analysis results of the LLVM monorepo.

### Problem statement

LLVM’s code base has grown over the years and accumulated technical debt. This
cannot be resolved in an instant but is a long-term process (see RFC 3 above).
We need some tools to better understand the current situation and to track
progress.

### Proposed solution

I propose to set up a tool/dashboard that shows the following data:

* All current clang-tidy findings with the option to drill down into certain
  categories/severities of findings and into the directory structure.
* Show findings inline per source code file.
* Show graph of the development of findings over time.
* Show new/removed findings per commit.
* Find and show code clones.
* Nice-to-have: Show test coverage overall and per commit.

Thoughts on choosing the right tool:

* Hosted solutions are preferred over something we need to run ourselves.
* The tool must be able to handle the findings from the latest clang-tidy
  release.
* All data shall be publicly visible. For changing the settings, admins need to
  authenticate.
* Nice-to-have: We can customize the dashboards for certain aspects (e.g.
  sub-projects).
* Nice-to-have: We can integrate this with Buildbot to collect test coverage
  information.

### Benefits

* We can see the current situation and the tools understand the results.
* We can track progress in reducing the findings.

### Risks

* Yet another tool to be configured and maintained.
* The tool might show us that we’re not making any progress.
* Having transparency might create (unwanted) pressure on contributors or
  sub-projects to decrease the number of findings.
