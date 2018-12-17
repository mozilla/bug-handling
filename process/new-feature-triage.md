# New Feature Triage

## Flows

### Sources

* Bugs marked severity = `enhancement`
* Bugs with `feature` or similar in whiteboard or short description
* `[RFE]` in whiteboard, short description, or description
* Bugs not explicitly marked as a feature request, but appear to be feature requests
* Bugs marked with `feature` keyword

### Sinks

The majority of requests will be handled as:

* `RESOLVED WONTFIX`
* `RESOLVED DUPLICATE`
* priority = `P5`

Some will become backlogged feature requests.

## Process

### Initial Triage

* Bugs from saved queries matching the Sources § (above) reviewed
* Priority reset to `--`
* Duplicate and incomplete requests are resolved
  * Close bug as `RESOLVED DUPLICATE` with comment thanking submitter and linking to duplicate bug
  * Close bug as `RESOLVED INCOMPLETE` with comment as to what was missing from request and thanking submitter
* Bugs which are defects have feature-related metadata removed
* Product::Component reset if needed
* Metadata on bugs is cleaned and bug tagged with `feature` keyword
* Product managers from subject areas are needinfo'ed on remaining bugs

### Product Manager Triage

* PM reviews bug
* Reassigns to another Product::Component if necessary
* Determines next steps
  * Close bug as `RESOLVED WONTFIX` with comment as to why and thanking submitter
  * Set bug to `P5` priority with comment thanking submitter, and suggesting community submit an implementation
  * Set bug to `P3` priority with comment thanking submitter, and explaining next steps in product process (without promising implementation)

### Periodic Reviews

#### Duplicated Requests

Review duplicate requests and decide if the original should be re-prioritized.

#### Inactive Requests

Requests assigned which are still open, not prioritized as `P5`, but inactive should be reviewed then re-prioritized, or closed

## KPI

* 80% of new feature requests resolved within one week of filing
* 100% of new feature requests triaged and or closed within one month of filing
