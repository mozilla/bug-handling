<!----- Conversion time: 2.356 seconds.


Using this Markdown file:

1. Cut and paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* GD2md-html version 1.0β11
* Wed Jun 13 2018 15:33:34 GMT-0700 (PDT)
* Source doc: https://docs.google.com/a/mozilla.com/open?id=1L6zpmCfQP81HRPRv4Ma5Cj7fDG4qD9mtLFDgH8FHmJ4
----->



## Performance Initiative (aka Quantum Flow v2)


## Initiative Template

Your copy of this page should live at the wiki link /bugmasters/metadata/[project].

[How do I get it there? Do you mean the wiki https://wiki.mozilla.org/Bugmasters?]


## BMO Metadata

Use this section to list the metadata your project/initiative maintains for bugs. 

The metadata you use should be linked to the big list of metadata wiki pages (link.)


### Whiteboard Tags

List the tags your project/initiative uses. For each tag please list:



*   The meaning of the tag
*   What is expected to happen to the bug when this tag is set
*   When should this tag be removed from the bug?
*   When should this tag be retired?
*   Should this become a keyword?
*   Is this shared with other projects/initiatives?


### Priority

[perf] - Performance interesting - untriaged


### Priority

[perf:p1] - Fix now - May have a very large impact on perf and "cause people to leave"

[perf:p3] - Put in backlog - May have a large impact on perf_ (will not work for Fx57)_

[perf:p5] - Patches accepted - May have an impact on perf


### States and other annotations

[perf:investigate] - root cause analysis required far enough to get to P1 P3 P5 priority

[perf:investigate:p1] - root cause analysis required - we feel this is likely a very important issue even before investigation

[perf:meta] - quantum flow related but sub bugs are the work. Will not show up in lists.

[perf-] - not a quantum performance flow bug (necessary for bugs that are parented by Quantum Flow bugs


### Mapping from Quantum Flow

Please update all bugs marked with whiteboard tag [qf to [perf. This change is designed to make the whiteboard tags more obvious and self document.


<table>
  <tr>
   <td>
   </td>
   <td><strong>From</strong>
   </td>
   <td><strong>To</strong>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>[qf]
   </td>
   <td>[perf]
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>[qf:p1]
   </td>
   <td>[perf:p1]
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>[qf:p3]
   </td>
   <td>[perf:p3]
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>[qf:p5]
   </td>
   <td>[qf:p5]
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>[qf:investigate]
   </td>
   <td>[perf:investigate]
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>[qf:investigate:p1]
   </td>
   <td>[perf:investigate:p1]
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>[qf:meta]
   </td>
   <td>[perf:meta]
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>[qf-]
   </td>
   <td>[perf-]
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>
   </td>
   <td>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>
   </td>
   <td>
   </td>
   <td>
   </td>
  </tr>
</table>



### Keywords

List the keywords your project/initiative uses. For each keyword please list:



*   The meaning of the keyword
*   What is expected to happen to the bug when this keyword has been added
*   When should the keyword be removed from the bug?
*   When should this keyword be retired?
*   Is this shared with other projects/initiatives?

Applicable Bugzilla keywords defined elsewhere

[testcase]

[testcase-wanted]

[reproducible]

We are currently not using the `perf `keyword. It is binary and we need more nuance for tracking through our Performance bugzilla workflow


### Flags

List the flags your project/initiative uses. For each flag please list:



*   The meaning of the flag
*   Which group can set the flag?
*   For each value of the flag (?, +, -, unset), what is expect to happen to the bug
*   When should the flag be reset on the bug?
*   When should this flag be retired?
*   Is this shared with other projects/initiatives


## Triages


### Schedule

Every two weeks, Tuesdays at 2PM Pacific in Bugmaster Vidyo Room/#QuantumFlow and backchannel #flow IRC


### Attendees



*   Engineering Manager
*   Program Manager
*   QA Lead
*   Others
    *   Naveed Ihsanullah
    *   Jean Gong
        *   Graphics
            *   Bas Schouten
        *   Layout
            *   Daniel Herbert
        *   PM Release Criteria Metrics
            *   Harald Kirschner
        *   JavaScript
            *   Kannan Vijayan
        *   Front End
            *   Mike Conley


### Priorities

Decisions should be made on all bugs with the tags/keywords **_xxx_**.

Please link to your project/initiatives page which covers your criteria for triage. How can an interested party learn about the results of these triages? 

https://docs.google.com/document/d/1Ka8eNAISQodT1mS_OXapFG-_kk94GoXyo4eKH1j7EV4/edit#


### Dashboards and Tracking Documents

Please link any dashboards or tracking documents your project/initiative maintains. 

Original Quantum Flow bug tagging document

https://docs.google.com/document/d/1Ka8eNAISQodT1mS_OXapFG-_kk94GoXyo4eKH1j7EV4/edit#


<!-- GD2md-html version 1.0β11 -->
