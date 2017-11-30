---
layout: page
title: "Phillips Hue Motion Sensor"
subheadline: ""
teaser: "Phillips' Hue Motion Sensor seems like the perfect way to automate a great smart lighting platform, but is it?"
author: Morgan
categories:
  - tech
image:
    title: http://imgur.com/aaRVL55.jpg
    homepage: http://imgur.com/aaRVL55.jpg
    thumb: http://imgur.com/aaRVL55.jpg
    caption: Source
    caption_url: http://imgur.com/aaRVL55.jpg
breadcrumb: true
---

Phillips' [Hue Motion Sensor](http://www2.meethue.com/en-us/productdetail/philips-hue-motion-sensor) seems like the perfect way to automate a great smart lighting platform, but is it?

I've been using [SmartThings](https://www.smartthings.com/) (with a [1st gen hub](https://www.amazon.com/Samsung-SmartThings-STH-ETH-001-Hub-Generation/dp/B00FWYESVQ/ref=zg_bs_6478740011_18)) for some time, but lately I've been interested in moving to a platform that supports [HomeKit](http://www.apple.com/ios/home/) - enter [Phillips Hue](http://www2.meethue.com/en-us/). My biggest barrier to moving to an alternate platform has been a distinct lack of motion sensors. It's pretty hard to have 'automation' without an _automated_ way to trigger lights.

Phillips Hue is the natural choice for a HomeKit compatible setup. I'd been waiting for some time for the [motion sensor](http://www2.meethue.com/en-us/productdetail/philips-hue-motion-sensor) to come out. 2 weeks ago I picked up an entire rig:

+ [Hue Bridge](http://www2.meethue.com/en-us/productdetail/philips-hue-bridge)
+ 5x [Hue White Bulbs](http://www2.meethue.com/en-us/productdetail/philips-hue-white-extension-bulb-a19)
+ 2x [Hue motion sensors](http://www2.meethue.com/en-us/productdetail/philips-hue-motion-sensor)

I found the initial setup simple enough. Connect the bridge to my network, configure up using my phone - easy. I set about placing bulbs & sensors where I'd want them - namely the bedroom & bathroom. In those rooms I want to just walk in and walk out and let the lights take care of themselves. For other rooms in the house I'll trigger scenes manually - like in the living room.

<center> <img src="http://imgur.com/3qqmx6a.jpg" alt="adding hue motion"> </center>
[[Source]](http://www.howtogeek.com/247500/how-to-set-up-your-philips-hue-lights/)

Adding the bulbs & accessories was dead simple too. Each device was quickly added and configured. Devices were also easily added to HomeKit.

<center> <img src="http://imgur.com/OlMDiUG.jpg" alt="adding hue motion"> </center>
[[Source]](http://www.vesternet.com/compatibility/homekit)

All that was necessary was to scan a code provided on the Hue bridge's box, then all my devices were present in the Home app on my iPhone...except they weren't.

> strike 1

As it turns out, the motion sensor is _not_ HomeKit compatible. Little did I know when I made the purchase, but for whatever reason Phillips did not see fit to do the needed work to make the motion sensor compatible. In theory they could enable compatibility in a future software update, though HomeKit devices require certain encryption hardware so I'm guessing the requisite hardware simply isn't present in the sensor.

HomeKit compatibility or no, I pressed on. I figured that I wouldn't strictly speaking need HomeKit for triggering motion, I could just let the Hue app control that trigger, and worry about setting scenes for my other rooms manually via Siri.

On to the sensor itself. This sensor is quite impressive. Not only does it sense motion, it senses luminance as well - this gives it the ability to determine how bright to set the lights depending on the ambient light in the room. Great! Right way I noticed that this sensor is significantly more sensitive than the [Ecolink sensors](https://www.amazon.com/gp/product/B00FB1TBKS/ref=oh_aui_search_detailpage?ie=UTF8&psc=1) I use with SmartThings currently. Often my Ecolink sensors fail to sense motion quickly, requiring me to wave my arms about to get them to trigger, the Hue sensor on the other hand caught the motion every time. Even better!

<center> <img src="http://imgur.com/Mq2NhNd.jpg" alt="lighting depending on hours"> </center>
[[Source]](http://www.howtogeek.com/247500/how-to-set-up-your-philips-hue-lights/)

So I've got a great platform that pretty much _just works_ (unlike SmartThings), and really high quality sensors. Everything should be perfect and happy, right?

No.

> strike 2

As it turns out, Phillips' software controls for the motion sensor are really dimwitted. While you're able to set light sensitivity and define how bright you want the light to be depending on the ambient light and time frame, they missed the most important thing with a motion sensor: the ability to override it. At time of writing there's no way to have a scene take priority over the motion sensor.

If I'm in the bedroom reading the lights turn off every 5 minutes (or whatever timeframe you define), meaning I have to wave my arms around to turn the lights back on. With SmartThings (and presumably other systems) you can define a mode that overrides the typical sensor behavior. Unfortunately there's just no way to do this within the Phillips app. Presumably using the Home app on iPhone one could define a scene like this, but as said above, this sensor isn't HomeKit compatible.

There's no doubt, of the limited lighting systems I've played with, Phillips Hue is no doubt the best. The bridge & devices are fantastic. They're so easy to add, and the lighting control was basically instant (unlike the multi-second delay I get with SmartThings), but the inability to control that sensor as much as I like is a deal-breaker. Phillips might add this functionality, they might not, but I'm not going to wait around to see if it happens. The whole rig was returned the next day.

The good news is that [Elgato](https://www.elgato.com/en/eve) has announced a [HomeKit compatible motion sensor](https://www.elgato.com/en/eve/eve-motion). It's due out before the end of the year. Perhaps once that is available I'll try this again. I do have somewhat of a sour taste in my mouth, but I'm hopeful that a Philips + Elgato + HomeKit solution will be sufficient to replace my aging and slow SmartThings setup.

---
<p align="right">Typed on ErgoDox Test Board</p>
