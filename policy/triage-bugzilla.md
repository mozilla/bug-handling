# Triage Process for Firefox Components in mozilla-central and Bugzilla (Original)

## Why Triage

Staying on top of the bugs in your component means:

* You get ahead of critical regressions and crashes which could trigger a point release if uncaught
	* And you don't want to spend your holiday with the Release Management team (not that they don't like you)
* Your bug queue is not overwhelming
	* New members of your team do not see the bug queue and get ''the wiggins''

## Who Triages

See list of [triage leads](https://wiki.mozilla.org/Bugmasters/Project/Bug_Handling/Triage_Leads).

## What Do You Triage
There are several queries you should be minding:

* All open, confirmed bugs in a component without a pending needinfo flag since 1 July 2016
* All bugs with pending needinfo's in a component which have not been modified in two weeks
* All bugs with active review requests in a component which have not been modified in five days
* Regressions without -status-firefoxNN decisions
* Regressions without a regression range

The [above queries are already in the triage tool](https://mozilla.github.io/triage-center/).

## How Do You Triage

### Weekly or More Frequently (depending on the component)
Find un-triaged bugs in your component. 

There's a tool to help you find bugs https://mozilla.github.io/triage-center/ and the source is at https://github.com/mozilla/triage-center/.

For each bug decide priority (you can override what's already been set, as a triage lead, you are the decider.)

* P1
	* Fix in the current release or iteration
* P2
	* Fix in the next release or iteration
* P3
	* Backlog
* P4
	* Maintained by bots
* P5
	* Will not fix, but will accept a patch

### What About Release Status (`status_firefoxNN`) Flags

Release status (and tracking) flags are set independent of triage decisions, but should be consistent with triage decisions.

If an unresolved bug is marked `status_firefoxNN = affected` then `priority = P1` should be true. 

This relationship is ''not'' transitive.

If a bug is triaged as P1, its status may be one of `affected`, `wontfix`, `fix-optional`, `disabled` as well. 

Also, as a release approaches, the release status of open, high priority (P1) bugs can change. Triagers and engineering leads ''must'' review open bugs with a release status of `affected` and `fix_optional`, and decide which of these to keep, and move the others to `wontfix` for the current cycle.

Use the shared query [Planned Fixes for Next Release](https://bugzilla.mozilla.org/buglist.cgi?cmdtype=runnamed&namedcmd=Planned%20Fixes%20for%20Next%20Release&list_id=13846696) to review these, and move the ones which make sense to [Planned Fixeds for Current Cycle](https://bugzilla.mozilla.org/buglist.cgi?cmdtype=runnamed&namedcmd=Planned%20Fixes%20for%20Current%20Cycle&list_id=13846701).

An explanation of the [release status field](https://wiki.mozilla.com/Bugmasters/Process/Triage/Release_Status).

### How Do I Handle Edge Cases

#### I Don't Have Enough Information

If you don't have a reproduction or confirmation, or have questions needinfo someone who can answer your question and finish triaging the bug when they reply.

#### This doesn't fit into a P1, P2, P3, P4, or P5 framework

Mark it as a P3. If it's a tracking bug, make sure it's marked as [meta].

#### Wrong Component

Remove any priority set, then either move to what you think is the correct component, or needinfo the person responsible for the component to ask them.

#### I don't think we should work on it at any time 

If you'll accept a patch, mark it as P5, otherwise, close it as WONTFIX

## Watch open needinfos

Don't let open needinfos linger for more than two weeks. Close minor bugs with unresponded needinfos. Chase down other needinfo requestees. The tool will help you find these (the query is imperfect.)

## End of Iteration

* P2s become P1s after review
* Hoist selected P3s to P2's or P1

## Tools

{{Quote|text=One tool we use in addons is triage-with-me. Its a Firefox Add-on that sends all the pages you click on in bugzilla into a server which then sends the URL to everyone else in the triage.|source=Andy McKay}}

The upshot is, one person clicks on links in Bugzilla, the bugs open
up on everyone else's computer. 

* https://addons.mozilla.org/en-US/firefox/addon/triage-with-me/
* http://www.agmweb.ca/2013-09-06-triage/
* http://www.agmweb.ca/2015-03-10-triage-with-me-update/

## ’My project is on GitHub'

[We have a guide for GitHub projects to follow when triaging](https://mozilla.github.io/bmo-harmony/labels).

## Questions 

* Ask in #bugmasters on irc.mozilla.org
* Email emceeaich@mozilla.com
