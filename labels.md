# A Mozillian’s Garden of Metadata for GitHub
You have good reasons for running your piece of the Firefox project on GitHub: familiar tooling,  an easy path for contributors, change sets which are integrated with code reviews, and emoji 🦊.

To have better consistency with code and task tracking among Mozilla Central, Bugzilla, and GitHub, I request that you use a common set of labels in your projects. Some of the reasons why improved consistency in our conventions would benefit us include: 

* Consistency makes measurement of processes easier across the organization
* Consistency increases clarity for those than need to work across different repositories and bug trackers
* Consistency reduces friction around engineering mobility between projects

Several of you are doing this already. But we need you to do some tuning of your process.

## Statuses
Bugs in GitHub issues have two states: closed and open. Bugzilla has a ~~more confusing~~ richer set of states.

When you close a bug, add a label indicating [the resolution](https://wiki.mozilla.org/BMO/UserGuide/BugStatuses#Resolutions).

* `invalid`
  - The problem described is not a bug. 
* `wontfix`
  - The problem described is a bug which will never be fixed. 
* `duplicate`
  - The problem is a duplicate of an existing bug. Be sure to link the bug this is a duplicate of.
* `worksforme`
  - All attempts at reproducing this bug were futile, and reading the code produces no clues as to why the described behavior would occur. incomplete
  - The problem is vaguely described with no steps to reproduce, or is a support request.

## Priorities
Firefox projects in Bugzilla use the priority field to indicate when and if a bug will be worked on. 

Use these labels in your project to indicate priorities.

* `P1`
  - Fix in the current release or iteration 
* `P2`
  - Fix in the next release or iteration 
* `P3`
  - Backlog 
* `P5`
  - Will not fix, but will accept a patch 

You probably already have a set of tags, so do an edit to convert them or use [the GitHub settings app](https://github.com/probot/settings).

## Keywords 
In GitHub issues metadata is either a label or the bug’s open/closed state. 

Some Bugzilla metadata behaves like labels, but you need to be careful with how you use it in order not to confuse QA.

### Regressions 

In Bugzilla, the `regression` keyword indicates a regression in existing behavior introduced by a code change. 

When a bug is labeled as a regression in GitHub does it imply the regression is in the code module in GitHub, or the module that’s landed in Mozilla Central? Using the label `regression-internal` will signal QA that the regression is internal to your development cycle, and not one introduced into the Mozilla Central tree. 

If it is not clear which pull request caused the regression, add the `regressionwindow-wanted` label.

### Other Keywords

Other useful labels include `enhancement` to distinguish feature requests, and `good first issue` to signal to contributors ([along with adequate documentation](http://blog.humphd.org/why-good-first-bugs-often-arent/).)

## Status Flags
Bugzilla uses a set of status flags to communicate priorities between contributors, product managers, and the the release management team. 

A bug which contributors consider a high priority may not effect the current release, and vice versa.

In Bugzilla, status for each release number is represented by a field which takes [one of multiple values](https://wiki.mozilla.org/Bugmasters/Process/Triage/Release_Status).

It's recommended that you don't use status and tracking flag tags in GitHub issues and use another tool such a Trello or a worksheet to communicate to Release Drivers on work that needs to land in the `mozilla-centra1` repository.

## Summary
* Resolution statuses
	* `invalid`, `duplicate`, `incomplete`, `worksforme`, `wontfix`
* Regressions
	* `regression`, `regressionwindow-wanted`, `regression-internal`
* Priority
	* `P1`, `P2`, `P3`, `P5`
* Other keywords
	* `enhancement`, `good first bug`
