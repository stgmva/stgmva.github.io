---
layout: page
title: "iMessage New Device Sec"
subheadline: ""
teaser: "You know when you add a new Apple device to your lineup, you inevitably get a message about a new device added to iMessage? Seems ridiculous doesn't it? I know I added the device, I was there. I always thought it was a bug, a remnant in iOS and OS X from the early days when iMessage was being developed. As they say, it's not a bug, it's a feature."
author: Morgan
categories:
  - apple
breadcrumb: true
---

<img align="right" src="http://i.imgur.com/tEhmHFR.jpg">

You know when you add a new Apple device to your lineup, you inevitably get a message like this one? Seems ridiculous doesn't it? I know I added the device, I was _there_. I always thought it was a bug, a remnant in iOS and OS X from the early days when iMessage was being developed. As they say, it's not a bug, it's a feature. Rich Mogull explains on [Securosis](https://securosis.com/mobile/how-imessage-distributes-security-to-block-phantom-devices/full):

> It turns out you can’t add devices to an iCloud account without triggering an alert because that analysis happens on your device, and doesn’t rely (totally) on a push notification from the server. Apple put the security logic in each device, even though the system still needs a central authority. Basically, they designed the system to not trust them.     

So you get that alert on _every_ device, because _every_ device sees the new device on it's own, independent from all the other Apple devices you own. Here's why:

> iMessage is a centralized system with a central directory server. If someone could compromise that server, they could add “phantom devices” to tap conversations (or completely reroute them to a new destination). To limit this Apple sends you a notification every time a device is added to your iCloud account.    

Because of how the devices are set up (each notifying you when a new iMessage device is added), the group of them act as your own personal iMessage canary.

> ...if they were deeply compromised (okay, forced by a government) to alter their system, the notification could be faked, but that isn’t how it works. Your device checks its own registry of keys, and pops up an alert if it sees a new one tied to your account.

If you added a new device and _didn't_ observe this popup, you could naturally assume that iMessage, or at the very least **your** iMessage account had been compromised.

For reference, every iMessage you send is encrypted end-to-end using public key crypto. You don't share a single key among your devices, each device has its own keys. Every message you send is encrypted with public keys for _each_ iMessage device you own. This means that a given message may have 4 or 5 keys attached to it. When you add a new device, it send its public key to Apple, and when Apple pushes that key to your other devices - thus you get this popup.

---
<p align="right">Typed on AEKII</p>
