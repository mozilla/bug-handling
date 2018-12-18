# New Feature Triage

## Flows

### Sources

* Bugs marked severity = `enhancement`
* Bugs with `feature` or similar in whiteboard or short description
* `[RFE]` in whiteboard, short description, or description
* Bugs not explicitly marked as a feature request, but appear to be feature requests
* Bugs marked with `feature` keyword

### Sinks

These requests are handled as:

* `RESOLVED WONTFIX`
* `RESOLVED DUPLICATE`
* priority = `P5`

## Process

### Product Manager Triage

* PM reviews bug
* Reassigns to another Product::Component if necessary **or**
* Determines next steps
  * Close bug as `RESOLVED WONTFIX` with comment as to why and thanking submitter
  * If bug is similar enough to work in roadmap, close bug as `RESOLVED DUPLICATE` of the feature bug it is similar to
    * If there's not a feature bug created already, then consider making this bug the feature bug
       * Add `[meta]` to summary
       * Add `feature` keyword
       * Set severity to `enhancement`
  * Set bug to `P5` priority with comment thanking submitter, and explaining that the request will be considered for future roadmaps

## Goals

* 80% of new feature requests triaged within one week of filing
* 100% of new feature requests triaged and or closed within one month of filing
