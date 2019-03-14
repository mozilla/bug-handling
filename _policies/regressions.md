---
title: How to Mark Regressions in Mozilla Central
layout: policy
published: true
description: Marking-up regressions in Mozilla Central
---

## Regressions in Mozilla Central

_A regression is a bug (in our scheme a `defect`) introduced by a [changeset](https://en.wikipedia.org/wiki/Changeset) that degrades existing functionality or performance._

- Bug 101 *fixes* Bug 100 with Change Set A
- Bug 102 *reported which describes previously correct behavior now not happening*
- Bug 102 *investigated and found to be introduced by Change Set A*

### Is a regression

* Facebook homepage does not render
* Image elements do not appear in the DOM tree
* CSS Grid rules are not recognized
* A new crash
* Memory usage increased while typing in awesomebar

### Is not a regression

* A website dependent on an unimplented part of the CSS specification does not render as intended
* Firefox implements a feature differently than the user expects it to
* The reporter is requesting a new feature
* Refactoring code
* A bug that is not dependent on a code change in Firefox [but from external factors](https://bugzilla.mozilla.org/describecomponents.cgi?product=External%20Software%20Affecting%20Firefox) (e.g. a new crash caused by a Windows update, or a change in anti-virus software)

### Policy

For regression bugs in Mozilla-Central, our policy is to tag the bug as a regression, identify the commits which caused the regression, then mark the bugs associated with those commits as causing the regression. 

* The commit which casued the regression should be found and noted in the bug
* The bug will be reviewed at the [weekly regression triage meeting](https://wiki.mozilla.org/Platform#Weekly_Regression_Triage_Meeting)

Unless a bug is resolved as invalid, wontfix, or a duplicate; or marked as P5, it is expected that the bug will link to the commit that caused the regression. 

## Marking a Regression Bug

- **Bug Type** is `defect`
- **Keywords** _must_ include `regression`
- **Status_FirefoxNN** is initially set to `affected` for each version (in current nightly, beta, and release) of Firefox in which the bug was found
- The bug's description covers previously working behavior which is no longer working [ed. I need a better phrase for this]

Until the change set which caused the regression has been found through [mozregression](https://mozilla.github.io/mozregression/) or another tool, the bug should also have the `regressionwindow-wanted` keyword. 

Once the regression range has been found, the `regressionrange-wanted` keyword should be removed. 

Set the **Regressed By** field to the id of the bug associated with the changeset that introduced the regressions.

The triage owner for the component may decide to set the status of a bug as `wontfix` for current and future versions.

Setting the **Regressed By** field will update the **Regresses** field in the other bug. 

Set a needinfo for the author of the regressing changeset asking them to fix or revert the regression.

## Previous Method 

Previously we over-loaded the **Blocks** and **Blocked By** fields to track the regression, setting **Blocks** to the id of the bug associated with the change set causing the regression, and using the `regression`, `regressionwindow-wanted` keywords and the status flags as described above.

This made it difficult to understand what was a dependency and what was a regression when looking at dependency trees in Bugzilla.

## FAQs

*To be written* 
