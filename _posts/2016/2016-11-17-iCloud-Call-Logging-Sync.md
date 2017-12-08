---
layout: page
title: "iCloud Call Log Sync"
subheadline: ""
teaser: "Turns out iCloud syncs your call logs. Elcomsoft reports."
author: Morgan
categories:
  - apple
breadcrumb: true
---

> Earlier today, reports surfaced on The Intercept and Forbes claiming Apple "secretly" syncs Phone and FaceTime call history logs on iCloud, complete with phone numbers, dates and times, and duration. The info comes from Russian software firm Elcomsoft, which said the call history logs are stored for up to four months.
<br><br>
Likewise, on iOS 10, Elcomsoft said incoming missed calls that are made through third-party VoIP apps using Apple's CallKit framework, such as Skype, WhatsApp, and Viber, also get synced to iCloud. The call logs have been collected since at least iOS 8.2, released in March 2015, so long as a user has iCloud enabled.
<br><br>
Elcomsoft said the call logs are automatically synced, even if backups are turned off, with no way to opt out beyond disabling iCloud entirely.
“You can only disable uploading/syncing notes, contacts, calendars and web history, but the calls are always there,” said Vladimir Katalov, CEO of Elcomsoft. "One way call logs will disappear from the cloud, is if a user deletes a particular call record from the log on their device; then it will also get deleted from their iCloud account during the next automatic synchronization.
Given that Apple possesses the encryption keys to unlock an iCloud account for now, U.S. law enforcement agencies can obtain direct access to the logs with a court order. Worse, The Intercept claims the information could be exposed to hackers and anyone else who might be able to obtain a user's iCloud credentials.
<br>...<br>
Further, in a statement today, Apple said the call history syncing is intentional.
“We offer call history syncing as a convenience to our customers so that they can return calls from any of their devices,” an Apple spokesperson said in an email. "Device data is encrypted with a user’s passcode, and access to iCloud data including backups requires the user’s Apple ID and password. Apple recommends all customers select strong passwords and use two-factor authentication.”

A lot of people are noting that Apple's [whitepaper on iOS security](https://www.apple.com/business/docs/iOS_Security_Guide.pdf) has a mention of call history in iCloud backups, I can't find anywhere in said whitepaper acknowledging that call history/logs are synced using iCloud. Not sure if this is just an oversight in documentation, or a lack of transparency.

What's curious to me is that Apple uses iCloud for this type of sync at all. The narrative is that it's necessary to sync calls across all devices - [my understanding of iMessage](http://missourivalleyambulance.com/2016-04-25-iMessage-New-Device-Sec) is that Apple keys each device and keys each message to be accessible by all devices. Why not employ a similar muli-keying for these type of sensitive records and use iMessage or something similar to enable the sync? Alternatively, if Apple _is_ doing multi-keying for syncing these types of records, why doesn't the whitepaper make mention of this?

[[via Macrumors](http://www.macrumors.com/2016/11/17/apple-says-icloud-call-syncing-intentional/)]

---
<p align="right">Typed on ErgoDox Test Board</p>
