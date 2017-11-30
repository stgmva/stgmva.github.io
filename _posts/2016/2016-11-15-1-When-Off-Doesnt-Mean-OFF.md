---
layout: page
title: "Off Doesn't Mean OFF"
subheadline: "Shazam is always listening"
teaser: "Patrick Wardle's reversal of Shazam's code."
author: Morgan
categories:
  - linked
breadcrumb: true
---

[Patrick Wardle's](https://objective-see.com/blog/blog_0x13.html) reversal of [Shazam's](https://itunes.apple.com/us/app/shazam/id897118787?mt=12) code:

> TL;DR When Shazam (macOS) is toggled 'OFF' it to simply stops processing recorded data...however recording continues
<br>
<br>
Once installed, Shazam automatically begins listening for music, "ready to name that tune at a moment's notice." This song identification or "auto tagging" (in Shazam's parlance) is of course is the main functionality of the tool.
<br>
<br>
Most (security-conscious) users probably don't want Shazam listening all the time. Shazam appears to oblige, seemingly providing an option to disable this listening:
<br>
<br>
However, sliding the selector to 'OFF' did not generate the expected, "Mic was deactivated" OverSight alert. Odd :\ ...though this did match what the OverSight user reported to me.
<br>
<br>
My first thought was perhaps OverSight had 'missed' the Mic deactivation, or contained some other bug or limitation. However testing seemed to confirm that OverSight works as expected. For example, when one quits (exits) Shazam, OverSight does receive a "Mic Deactivation" notification from the OS, and alerts this fact to the user:
<br>
<br>
So is Shazam still listening even when the user attempts to toggle it to 'OFF'?
<br>
<br>
Again, though it appears that Shazam is always recording even when the user has toggled it 'OFF' I saw no indication that this recorded data is ever processed (nor saved, exfiltrated, etc). However, I still don't like an app that appears to be constantly pulling audio off my computers internal mic. As such, I'm uninstalling Shazam as quickly as possible!

From [Digital Journal](http://www.digitaljournal.com/tech-and-science/technology/shazam-forced-to-backtrack-over-always-on-mac-mic-concerns/article/479638):

>"There is no privacy issue since the audio is not processed unless the user actively turns the app 'ON,'" James Pearson, Shazam's VP of global communications, told Motherboard in a statement. "If the mic wasn't left on, it would take the app longer to both initialize the mic and then start buffering audio, and this is more likely to result in a poor user experience where users 'miss out' on a song they were trying to identify."

A later statement from Shazam corroborates what Pearson stated, and what Whardle found in his reversal of Shazam's code.

> "Contrary to recent rumors, Shazam doesn't record anything," the company said. "Shazam accesses the microphone on devices for the exclusive purpose of obtaining a small fingerprint of a subset of the soundwaves, which are then used exclusively to find a match in Shazam's database and then deleted."

Recording or no, one would expect the off switch behavior to stay true to expectations - to be an actual OFF switch. While Shazam may not record audio while the microphone is active, it still presents another attack vector that a malicious actor might use to coopt the microphone.

[ [via Objective-See](https://objective-see.com/blog/blog_0x13.html) & [ Digital Journal](http://www.digitaljournal.com/tech-and-science/technology/shazam-forced-to-backtrack-over-always-on-mac-mic-concerns/article/479638M) ]

---
<p align="right">Typed on ErgoDox Test Board</p>
