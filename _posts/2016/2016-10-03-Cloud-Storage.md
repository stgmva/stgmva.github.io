---
layout: page
title: "Unlimited, Encrypted, Zero Knowledge Cloud Storage"
subheadline: ""
teaser: "The goal, as I see it, is to find a cloud storage solution that offers competitive pricing, and control over my content - specifically the ability to encrypt it prior to transit."
author: Morgan
categories:
  - tech
image:
    title: http://imgur.com/bzfyRP5.jpg
    homepage: http://imgur.com/bzfyRP5.jpg
    thumb: http://imgur.com/bzfyRP5.jpg
    caption: Boxcryptor
    caption_url: https://www.boxcryptor.com/en/vision
breadcrumb: true
---


I've been searching for a [zero-knowledge](https://en.wikipedia.org/wiki/Zero-knowledge_proof) cloud storage service for some time. For someone who is privacy and security focused, most of the common options like [Dropbox](https://www.dropbox.com/) or [Google Drive](https://www.google.com/drive/) go out the window right way. Both companies of course encrypt your content in transit, but both have at least _some_ level of visibility into one's content once it is at rest.

There are a few popular secure options out there, notably from [SpiderOak](https://spideroak.com/). Their product offers zero knowledge storage using local encryption. I did some playing with the service, but I found the desktop software confusing and lacking the functionality I wanted. The mobile software was just terrible. No company gets mobile cloud storage right in my opinion - namely that I want most of the same file-system power that I get on a desktop.

The goal, as I see it, is to find a cloud storage solution that offers competitive pricing, and control over my content - specifically the ability to encrypt it prior to transit. If encrypt my content locally it won't matter what level of visibility the provider has into the content - without the local keys it will be useless (aside from metadata, but that's basically impossible to avoid being tracked/mined). It was also important for me to have good mobile clients, and fast sync between devices.

Clearly no single product or service is going to deliver what I wanted. The first step was [Boxcryptor](https://www.boxcryptor.com/en). Its functionality is quite simple: encrypt content _before_ it is uploaded. Boxcryptor is compatible with most company's solutions, be it Dropbox, Google Drive, iCloud, OneDrive, Amazon, etc. It can even encrypt arbitrary folders on a system if the cloud storage isn't directly compatible. Boxcryptor is free for individuals connected to only 1 service. Business and multi-cloud-provider setups require a license.

![](http://imgur.com/B4WaWAt.jpg)

In terms of managing one's private keys, Boxcryptor offers two options: one can create a Boxcryptor account, and Boxcryptor will sync your keys across all your devices, alternatively one can create a local account, and your keys remain locally on your device, and are never transmitted by Boxcryptor to any other drives. Getting Boxcryptor set up on other devices requires copying that private key to the second device, then providing the passphrase (on desktop this simply requires copying the key over a flash drive, on mobile the key can be sent via a secured medium like Airdrop).

After Boxcryptor is set up, it will create an alias in Finder, the Boxcryptor folder behaves like a mounted volume, but provides contextual options for encryption when adding new content.

![](http://imgur.com/MiMKEyE.jpg)

Encrypted content in the Boxcryptor folder is denoted by a green padlock. If Boxcryptor is not actively running, viewing encrypted files is not possible.

![](http://imgur.com/H6Wcn7k.jpg)

I initially played with Boxcryptor on [iCloud Drive](http://www.apple.com/icloud/icloud-drive/) and Dropbox - performance was fantastic on using either cloud provider. I ended up deciding that iCloud's sync was too slow, and that Dropbox's client and pricing weren't up-to-snuff.

I ended up settling on [Amazon Cloud Drive](https://www.amazon.com/clouddrive/home) _(will be referred to as ACD going forward)_. At $60/yr for unlimited storage their product is a steal. The only downside to ACD is that no desktop sync client is available. ACD very one-sided. Amazon _does_ have a desktop client, but its sole purpose is upload. Managing content and downloading it from ACD must be done from the web.

![](http://imgur.com/Brv2boc.jpg)
[[Source]](https://www.odrive.com/features/sync)

Enter the second step: [ODrive](https://www.odrive.com/). This is **really** clever software for cloud storage. It changes the entire thought process behind cloud storage in a way that really make sense to me. ODrive talks to numerous cloud providers and is itself a sync client. Most importantly: ODrive gives ACD a true desktop sync experience. Suddenly I'm not relegated to web-based uploads/downloads, I have truly unlimited storage at my fingertips.

What is so clever about Odrive is a very simple sync/unsync model. With typical sync clients all content from the cloud is synced locally as well. Normally that is what I'd prefer, but with truly unlimited ACD I'll have *terabytes* in the cloud - I have room for that on my server, but not my laptop.

![](http://imgur.com/YN0AgAi.jpg)

Obviously other providers client's offer selective sync functionality, but that's often buried in the preferences, with Odrive it's a contextual menu. When folders are synced, their content is downloaded locally, when they are unsynced, a zero byte placeholder is present on the file system. This workflow makes it very simple to have certain folders always syncing everything locally, and others syncing nothing. With Odrive I can have the right content on the right computers, but I can always go back to sync.

ODrive also offers the ability to sync arbitrary folders back to ACD. I have a main repository for files that I manage much like one would manage any cloud storage. I _also_ have setup sync for several folders on _several_ drives on my server. I have the ability to sync *all* my content from *all* my machines now. With the content I've got, I'm easily reaching into terabytes of synced content.

Technically speaking ODrive is free, but for features like unsync there is a [yearly license of $100](https://www.odrive.com/upgrade) - a fair price in my book.

My setup is likely needlessly complicated, but I really like the level of control and simple day-to-day usability. I have Odrive on all my machines and have syncing setup so that each machine has the content it will normally need. Almost all the files are also encrypted with Boxcryptor.

I've only been running with this setup for a few weeks now, but I'm really pleased with it. The pricing is reasonable, between ODrive and ACD it's roughly $13/mo. Obviously this is a lot more than the [$8/mo](https://www.dropbox.com/business/plans-comparison) Dropbox charges for 1TB, however, considering the power and amount of storage I'm getting, it's a fair trade.

It's good to be back into cloud storage. I avoided it like the plague when I became security conscious, but I feel like I've got a setup. With local encryption keys and a powerful sync client, I'm likely as secure and private as I could be while using cloud storage.

---
<p align="right">Typed on ErgoDox Test Board</p>
