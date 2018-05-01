<!----- Conversion time: 1.377 seconds.


Using this Markdown file:

1. Cut and paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* GD2md-html version 1.0β11
* Tue May 01 2018 14:28:12 GMT-0700 (PDT)
* Source doc: https://docs.google.com/a/mozilla.com/open?id=1lll5J6cE-QZEvg6eGvuqX8R5eMUHSMIOcSR-QFJ4g24
----->



## Marking-up bugs for features behind a pref

Product and release need to track bugs whose visibility is controlled through a pref. Once a feature has been QAed and approved for a release, the preference should be enabled. 


### Policy

_A bug for a feature/fix that is controlled by a flag in Firefox preferences must do the following:_

_The bug **must** have the `behind-pref` flag set to +._

_Any bug controlled by a flag **must** be added to the Firefox Feature Trello board._

_The bug **must** state in a comment or the summary which preference will be used to manage visibility._

_The bug **must** have the `qe-verify` flag set to ? until verified._

_When it is time to release the feature on a channel, a bug, dependent on the feature bug, should be filed to flip the pref._


### Example

A bug is filed, "Make Tabby Cats the default new tab experience." 

It's decided that this should be controlled behind a preference, `browser.newtabpage.default.tabbycat`:



*   A comment is filed listing the name of the preference
*   The `behind-pref` flag is set to +
*   The `qe-verify` flag is set to ?

A patch lands in mozilla-central with the code for the feature controlled by the preference, then:



*   By default, the flag enabling the feature **should not** be set
*   The feature is tested with and without the flag set and confirmed to work
*   If it passes `qe-verify` is set to + and work continues
*   Otherwise the patch is backed out to be landed again later

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

<!-- GD2md-html version 1.0β11 -->
