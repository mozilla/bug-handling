---
layout: default
title: Triage Priorities
---

# How to prioritize defects and enhancements

Our work *must* be focused on Mozilla's objectives, and as you triage bugs you should prioritize accordingly.

Defects which affect:

* Performance
* Privacy
* User Security

should be the highest priorities.

## Performance

* Use the perf keyword
* Add [qf:?] if you think the Performance team should look at this bug

## Privacy

* Use the privacy keyword

## User Security

* Will this bug adversely affect Firefox users if left public?
  * Add to security group
* Otherwise move bug to one of:
  * Core:: Security
  * Firefox:: Security
  * Toolkit:: Security
  * Webkit:: Security
