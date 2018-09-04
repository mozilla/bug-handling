# Triage Process for Firefox Components in Mozilla-central and Bugzilla

## Why Triage
Staying on top of the bugs in your component means:

* You get ahead of critical regressions and crashes which could trigger a point release if uncaught
	* And you don't want to spend your holiday with the Release Management team (not that they don't like you)
* Your bug queue is not overwhelming
	* Members of your team do not see the bug queue and get the ‘wiggins’

## Who Triages

Engineering managers and directors are responsible for naming the individuals responsible for triaging bugs in a component.

We use Bugzilla to track this. See the [list of triage owners](https://bugzilla.mozilla.org/page.cgi?id=triage_owners.html).

If you need to change who is responsible for triaging a bug in a component, please [file a bug against bugzilla.mozilla.org in the Administration component](https://bugzilla.mozilla.org/enter_bug.cgi?product=bugzilla.mozilla.org&component=Administration).  When a new component is created, a triage owner **must** be named.

## What Do You Triage

As a triage owner the queries you should be following for your component are:

* All open bugs in your component without a pending needinfo flag since start of current release cycle
* All open bugs with pending needinfo flags in your component which have not been modified in two weeks
* All bugs with active review requests in your component which have not been modified in five days

The above queries are already in the triage tool.

These bugs are reviewed in the weekly Regression Triage meeting
* Regressions without -status-firefoxNN decisions
* Regressions without a regression range

## How Do You Triage

Weekly or More Frequently (depending on the component) find un-triaged bugs in your component.

There's a tool to help you find bugs https://mozilla.github.io/triage-center/ and the source is at https://github.com/mozilla/triage-center/.

For each bug decide priority (you can override what's already been set, as a triage lead, you are the decider.)

<dl>
    <dt>P1</dt>
    <dd>Fix in the current release or iteration</dd>
    <dt>P2</dt>
    <dd>Fix in the next release or iteration<dd>
    <dt>P3</dt>
    <dd>Backlog<dd>
    <dt>P4</dt>
    <dd>Maintained by bots<dd>
    <dt>P5</dt>
    <dd>Will not fix, but will accept a patch<dd>
</dl>

### What About Release Status (status_firefoxNN) Flags

Release status (and tracking) flags are set independent of triage decisions, but should be consistent with triage decisions.

Also, as a release approaches, the release status of open, high priority (P1) bugs can change. Triagers and engineering leads must review open bugs with a release status of affected and fix_optional, and decide which of these to keep, and move the others to wontfix for the current cycle.

An explanation of the release status field.

### Regressions

_A regression is a code change that degrades existing functionality or performance._

#### Is a regression

* Facebook homepage does not render
* Image elements do not appear in the DOM tree
* CSS Grid rules are not recognized
* A new crash
* Memory usage increased while typing in awesomebar

#### Is not a regression

* A website dependent on an unimplented part of the CSS specification does not render as intended
* Firefox implements a feature differently than the user expects it to
* The reporter is requesting a new feature
* Refactoring code
* A bug that is not dependent on a code change in Firefox [but from external factors](https://bugzilla.mozilla.org/describecomponents.cgi?product=External%20Software%20Affecting%20Firefox) (e.g. a new crash caused by a Windows update, or a change in anti-virus software)

#### Handling regressions

If a bug has been reported with the `regression` keyword added, or the bug has the `regression` keyword, then:

* The commit which casued the regression should be found and noted in the bug
* The bug will be reviewed at the [weekly regression triage meeting](https://wiki.mozilla.org/Platform#Weekly_Regression_Triage_Meeting)

Unless a bug is resolved as invalid, wontfix, or a duplicate; or if the bug is marked as P5, it is expected that the bug will refer to the commit that caused the regression. 

If the commit which caused the regression has not been found, add the `regressionrange-wanted` keyword.  

Once the regression range has been found, the `regressionrange-wanted` keyword should be removed, and the status flags for each affected release in the range of commits set to `affected`. The triage owner for the component may decide to set the status of a bug as `wontfix` for current and future versions.

If a bug is no longer considered a regression, the `regressionrange-wanted` keyword should be removed.

### Questions and Edge Cases

#### This bug is a feature request

Set the bug's severity to `enhancement` and state to `NEW`. This bug will be excluded from future triage queries.

#### This bug's state is `UNCONFIRMED`

Are there steps to reproduce? If not, needinfo the person who filed the bug, requesting steps to reproduce. You are not obligated to wait forever for a response, and bugs for which open requests for information go unanswered can be `RESOLVED` as `INCOMPLETE`.

#### I don't have enough information to make a decision

If you don't have a reproduction or confirmation, or have questions about how to proceed, `needinfo` the person who filed the bug, or someone who can answer.

#### The `stalled` keyword

The extreme case of not-enough-information is one which cannot be answered with a `needinfo` request. The reporter has shared all they know about the bug, we are out of strategies to take to resolve it, but the bug should be kept open.

Mark the bug as stalled by adding the `stalled` keyword to it. The keyword will remove it from the list of bugs to be triaged.

The priority of `stalled` bugs should be '--' but other keywords may apply to them.

Bugs which remain `stalled` for long periods of time should be reviewed, and closed if necessary.

#### This doesn't fit into a P1, P2, P3, P4, or P5 framework

Mark it as a P3. 

If it's a tracking bug, make sure has “[meta]” in the title and has the `meta` keyword added. This will remove it from the list of untriaged bugs.

#### Bug is in the wrong Component

Remove any priority set, then either move to what you think is the correct component, or needinfo the person responsible for the component to ask them.

#### I don't think we should work on it at any time

If you'll accept a patch, mark it as P5, otherwise, close it as WONTFIX

#### My project is on GitHub

We have a guide for GitHub projects to follow when triaging.

### Watch open needinfo flags

Don't let open needinfo flags linger for more than two weeks.

Close minor bugs with unresponded needinfo flags. 

Follow up on needinfo flag requests. 

The tool will help you find these (the query is imperfect.)

### End of Iteration/Release Cycle

#### Review P1s

Are there unresolved P1s? 

Revisit their priority, and move to backlog (P3.) 

#### Review P2s

Are there P2s that should move to P1s for the next cycle?

Are there P2s you now know are lower priority, move to P3.

#### Review P3s

Are their P3 bugs you now know you won’t get to? Either demote to P5 (will accept patch) or resolve as WONTFIX.

## Tools

### Triage with me

> <q>One tool we use in addons is triage-with-me. Its a Firefox Add-on that sends all the pages you click on in bugzilla into a server which then sends the URL to everyone else in the triage.</q> – Andy McKay

The upshot is, one person clicks on links in Bugzilla, the bugs open up on everyone else's computer.

* https://addons.mozilla.org/en-US/firefox/addon/triage-with-me/
* http://www.agmweb.ca/2013-09-06-triage/
* http://www.agmweb.ca/2015-03-10-triage-with-me-update/

## Questions

* Ask in #bugmasters on irc.mozilla.org
* Email emceeaich@mozilla.com
