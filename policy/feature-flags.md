## Marking-up bugs for features behind a pref

Product and release need to track bugs whose visibility is controlled through a pref. Once a feature has been QAed and approved for a release, the preference should be enabled. 

### Policy

_For any feature or fix controlled by a preference flag in Firefox, there should be a single bug (e.g. a meta bug) to track its release. If the feature requires multiple bugs/patches then this should be a `meta` bug._

_The bug which tracks a feature or fix that is controlled by a flag in Firefox preferences must do the following:_

_It **must** use the `behind-pref` flag. The leads for the feature would need to update the flags appropriately until the bug is closed._

_It **should** be added to the Firefox Feature Trello board._

_It **must** state in a comment or the summary which preference will be used to manage visibility._

_It **must** request the `qe-verify` flag (setting it to `?`) and the bug **must** be verfified (Status: RESOLVED, Resolution: VERIFIED) by QA once they have accepted the `qe-verify` request (setting the flag to `+`) before the feature can be promoted to Beta._

_The severity of the bug tracking the feature **must** be set to `enhancement`._

_The Release Managers for each train must consent to the feature being enabled on that train._

_QA **must** sign off on the feature before it is enabled in Beta._

_Any released feature **must** have a value of the parent bug's `behind-pref` flag set to the version where the feature was released, and have a state of VERIFIED and resolution FIXED._

### The `behind-pref` flag

The `behind-pref` flag is a multi-valued release-status flag with the values

- `---`
- `in-progress`
- `off`
- `releaseNN`
- `betaNN+1`
- `nightlyNN+2`

Where NN is the current relase version of Firefox. 

#### Values and Meanings

<dl>
  <dt>---</dt>
  <dd>This is not a feature that is preffed-off</dd>
  <dt>in-progress</dt>
  <dd>One or more bugs implementing the feature are still in progress and the feature is not available in any release</dd>
  <dt>off</dt>
  <dd>The code for this feature has landed in m-c but the feature is preffed-off in all releases</dd>
  <dt>releaseNN</dt>
  <dd>The feature is enabled by default in Firefox NN (Release), Beta and Nightly</dd>
  <dt>betaNN+1</dt>
  <dd>The feature is enabled by default in FirefoxNN+1 (Beta), and Nightly, but not Release</dd>
  <dt>nightlyNN+2</dt>
  <dd>The feature is enabled by default in FirefoxNN+2 (Nightly), but neither Beta or Release</dd>
</dl>

#### Maintenance 

If the current values of the flag were:

- `release60`
- `beta61`
- `beta62`

on merge day we would add

- `release61`
- `beta62`
- `nightly63`

and disable (but not delete) `release60`, `beta61`, and `nightly62`.

#### ESR

For tracking the feature in ESR, we create a `behind-pref-esr` status flag. It will be kept up with the values of the current and previous ESR releases. 

_Example_

- `---`
- `off`
- `esr59`
- `esr60`

### Example

A bug is filed, "Make Tabby Cats the default new tab experience." And the team developing this (engineering and product) decide that this should be controlled behind a preference, `browser.newtabpage.default.tabbycat`. The developers break the work for this feature down into three bugs.

- The bug's summary is updated to `[meta] Make Tabby Cats the default new tab experience`
- A comment is filed listing the name of the preference
- The `behind-pref` flag is set to `in-progress`
- The bug's severity is set to `enhancement`
- The three implementation bugs should be marked as blocking the `[meta]` bug for the new feature

As the feature is developed and the individual patches implement it land, it's kept off by compiler directives, the pref, or both. As these land, and are not backed out, these bugs can be marked RESOLVED FIXED.

The lead for the feature–which may be an engineer, a program manager, or a product manager–must notify the Nightly Release Manager before enabling it.

- The `[meta]` bug's status is moved to RESOLVED and resolution to FIXED.
- The bug's `behind-pref` flag is set to `nightlyNN+2` to indicate it's now available in nightly
- The `qe-verify` flag is set to ?, requesting QA's attention

Before the feature can graduate to Beta, it must be verified by QA. 

- QA agrees to take on verfication, setting `qe-verify` to `+`
- The feature is tested on nightly and confirmed to work as specified (implicit here is the feature team's involvement in creating a test plan)
- QA moves the bug's status to VERIFIED

If the feature does not pass testing then QA should file bugs blocking the `[meta]` bug for the feature. QA and the development team must confer and decide if the feature will be disabled in Nightly, or allowed to be kept on while bugs are fixed. This will depend on risk and severity of the bugs found. 

If it's decided to disable the feature, then it should be turned off in the nightly build and the `behind-pref` flag set to `off`. The bug's comments should explain why that decision was released. Once the defects have been resolved, then `behind-pref` can be reset to `nightlyNN+2`.

Once the feature has been verfied by QA then:

- The bug for the feature should be updated to VERIFIED FIXED
- The bug should be enabled in Beta once Release Management approves
- the `behind-pref` flag is updated to `betaNN+1` 

The feature now *rides the trains* to release, and on merge day, `behind-pref` is set to `nightlyNN`. The bug is then considered completed. 

When the next ESR is released, the `behind-pref-esr` field should be set to the version where it was relased. 

### Questions 

#### What if we turn off the feature in the main release?

The main bug's `behind-pref` value should be reset to the releases it's still on, `betaNN+1` or `nightlyNN+2`; or to `off`, and the bug's status set to REOPENED.

The bug to turn off the feature must be a dependency of the main bug.

#### What if we want to hold a feature over a release cycle and not promote it?

On merge day, the `behind-pref` flag would retain it's earlier value, and remain preffed off in other versions.

#### What if I want to enable parts of my feature in Nightly?

If your feature is incomplete, but some functionality is avalable, then mark `behind-pref` as `nightlyNN+2`. Do not request `qe-verify` until the feature is complete.

If you plan to incrementally add functionality to Nightly over a number of release cycles, then you can use a single `meta` bug to keep track of functionality, but don't promote the feature to `Beta`.

If you intend to implement functionality over a number of Beta and Release cycles, then each set of functionality should be treated as a separate `[meta]` bug subject to the process described in this document.

### Tracking queries

- Open bugs for features behind preferences
- Open bugs for features behind preferences landed but not QAed
- Bugs for features which have been disabled 