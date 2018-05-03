## Marking-up bugs for features behind a pref

Product and release need to track bugs whose visibility is controlled through a pref. Once a feature has been QAed and approved for a release, the preference should be enabled. 

### Policy

_A bug for a feature/fix that is controlled by a flag in Firefox preferences must do the following:_

_The bug **must** have the `behind-pref` flag set to +._

_Any bug controlled by a flag **must** be added to the Firefox Feature Trello board._

_The bug **must** state in a comment or the summary which preference will be used to manage visibility._

_The bug **must** request the `qe-verify` flag (setting it to `?`) and the bug **must** be verfified (Status: RESOVED, Resolution: VERIFIED) by QA once they have accepted the `qe-verify` request (setting the flag to `+`)._

_When it is time to release the feature on a channel, a bug, dependent on the feature bug, should be filed to flip the pref._

### Questions

> _NB: this is not the current practice for feature visiblity and under discussion._
>
> In current practice, the preference enabling the feature is set on, and compiler flags are used to turn it off in non-Nightly  builds.
>
> There is also discussion of moving feature visibility out of the preference system and into a separate 'feature flags' system more consistent with how other products and projects enable features.

### Example

A bug is filed, "Make Tabby Cats the default new tab experience." 

It's decided that this should be controlled behind a preference, `browser.newtabpage.default.tabbycat`:

*   A comment is filed listing the name of the preference
*   The `behind-pref` flag is set to +
*   The `qe-verify` flag is set to ?, requesting QA's attention

![Screenshot of Bugzilla with tracking pane open for editing displaying the behind-pref and qe-verify flags](/public/images/feature-flags-editing-in-bmo.png)

By default, the preference enabling the feature **should not** be set.

A patch lands in mozilla-central with the code for the feature controlled by the preference, then:

*   The bug's status is moved to RESOLVED and resolution to FIXED.
*   QA agrees to take on verfication, setting `qe-verify` to `+`
*   The feature is tested with and without the flag set and confirmed to work
*   QA moveds the bug's resolution to VERIFIED
*   Otherwise the patch is backed out to be landed again later, and the bug REOPENED

RelMan and product management decide if the feature will be enabled in Nightly, then:

*   The patch to flip the pref on should be attached to the "Make Tabby Cats the new default tab experience" bug

If a decision is made to uplift the feature to another release, then RelMan and product must decide when to enable the feature. If they do decide to enable it then:

*   The patch to turn the pref on which has been attached to the "Make Tabby Cats the new default tab experience" bug should be requested to be uplifted to the appropriate train

Once we reach code freeze for the the new release, RelMan and product must decide if the feature goes out with the flag turned on, then:

*   A bug is filed to turn off the feature. The bug **must** be marked as blocking release.

If the release goes out with the preference for the feature turned off, another bug **must** be filed to turn the preference on.

### Tracking queries

*   Open bugs for features behind preferences
*   Open bugs for features behind preferences landed but not QAed
*   Open bugs for features behind preferences blocking release
