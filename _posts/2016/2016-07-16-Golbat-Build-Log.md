---
layout: page
title: "A Wild Golbat Appeared"
subheadline: "40% Keyboard Build Log"
teaser: "Some folks think a 60% keyboard is small, they've got nothing on 40% boards."
author: Morgan
categories:
  - keyboards
breadcrumb: true
---
![](http://imgur.com/1TnlT0Z.jpg)

<div class="video-container"><iframe title="YouTube video player" class="youtube-player" type="text/html"
width="640" height="390" src="http://www.youtube.com/embed/B--WB8W05vg"
frameborder="0" allowFullScreen></iframe></div>

Some folks think a 60% keyboard is small, they've got nothing on 40% boards.

My first 40% was [Planck]({{ site.baseurl }}/2016-03-02-Building-Planck). As beautiful as my Planck is, I never could master it. Perhaps it was just the 40% size, perhaps it was the ortholinear layout (which I now have a lot more confidence in), but that board never clicked with me. There were other 40% boards out there ([Quark](https://deskthority.net/workshop-f7/quark-keyboard-40-staggered-layout-that-fits-all-planck-cases-t10474.html), [JD40](https://geekhack.org/index.php?topic=57630.0)), but parts were hard to source. After Planck I was on the hunt for a 40% that used the standard staggered key layout.

Golbat is such a board. Sourced out of China, Golbat features a staggered layout, and a sandwich case design made of aluminum and acrylic. Perfect!

![](http://imgur.com/pz8LmWX.jpg)

I joined GL1TCH3D's [group buy](https://geekhack.org/index.php?topic=78510.0) on Geek Hack back in January, with an estimated arrival date of March. Of course, like many group buys, this one suffered a few delays, but last week I finally received my Golbat.

<img align="right" src="http://i.imgur.com/G4z054P.jpg"> I'll say outright that I'm not completely satisfied with the board. When I opened the box, my immediate reaction was disappointment. During the group buy, there were several options for plate colors. It turns out my memory is quite faulty. Here I sat for 6 months thinking that I'd ordered a blue plate for this board, only to find out it's actually teal. Looking back at the original group buy post, the plate pictured is indeed teal. In hindsight, I wish I had ordered gold. I'm still attempting to get over the initial disappointment, but as I use Golbat more and more it's growing on me.

### The Parts

+ Golbat 40% Keyboard Kit
+ PCB Mount Stabilizers
+ Gateron Green Switches
+ Gateron Red Switches

### The Build

Golbat offers two options for plates - an ANSI plate, or a HHKB plate. Naturally, I opted for to use the HHKB plate for this build.

![](http://imgur.com/69Ir7Gc.jpg)

I chose [Gateron](https://deskthority.net/wiki/Gateron_KS-3_series) greens for this board, a clicky switch with 80 gram springs. I very much disliked blue MX mount switches when I got in to the hobby, but I discovered blue's heavier brethren several months ago and was very impressed. Greens are significantly heavier than blues, the heavier spring completely changes the feel of the switch, making it far more pleasant. I also thought it comical to have a super-heavy switch in such a tiny board.

![](http://imgur.com/CwLmJWa.jpg)

As I normally do, I've chosen Gateron reds for modifiers. Having used the board for a week or so now, I'll need to go back and swap one of the reds and greens around, to match the position I've chosen for right-shift.

![](http://imgur.com/Ilickz9.jpg)

I learned a new trick prior to this build: [stab clipping](https://www.youtube.com/watch?v=C6hPoe3srcw). Costar stabilizers are generally regarded as the best feeling stabilizers out there, but their multiple pieces, and freely mounted wire make them finnicky, and prone to rattle. Because of this, I've always used PCB-mount Cherry style stabs. Like many others, I've found Cherry style stabs to be a bit mushy. I've always considered the mushiness a worthy trade-off for not having to deal with finnicky Costars.

It turns out that by simply clipping off part of the stabilizer slider, the feel of a stabilized switch is entirely changed. I reap all the benefits of a Cherry slider, but I get the smooth action and feel of a Costar stab.

![](http://imgur.com/pYq8hYX.jpg)

![](http://imgur.com/l2moko8.jpg)

An eagle-eyed reader may notice that this board has two switches for the spacebar, rather than the standard single switch + stabilizer. Golbat can be built with two spacebars instead of one. After experimenting with a bottom-row backspace + spacebar on my Access-IS board, I chose to do the same with Golbat.

### The Code (kinda)
Programming this board is quite a bit different to what I've used before. The board doesn't use a GUI per-se, but it's not straight TMK either.

![](http://imgur.com/jB9uWhH.jpg)

At the end of the day, the board *is* running a version of TMK, but it's packaged and built using the TKG toolkit. Notably, this will be because the board uses the Kimera controller (the red daughter board on the PCB). Typical TMK-compatible boards use a Atmel controller soldered directly to the PCB, or they'll use the Teensy microcontroller. Kimera (near as I can tell) is a Teensy clone. Technically speaking, one *could* write a dedicated TMK firmware for this board, but that would take coding skills and patience far beyond what I possess.

Primarily, the firmware is build out on [TMK Keymap Generator](http://tkg.io/#) website. First, a new [Golbat specific matrix](http://pastebin.com/Bf2uQWHv) layout must be entered (to configure the colums and rows for the key matrix). Second, the keymap layout must be configured on [Keyboard Layout Editor](http://www.keyboard-layout-editor.com/#/gists/83b7eb12b3bccdf4c55d). A dedicated keymap must be laid out for each layer. Then the function keys are set on the TMK Keymap site, and a .eep file is downloaded. This .eep file is a hex encoded version of the entered keymap.

My keymap is below:

![](http://imgur.com/dECtsBf.jpg)   

**Layer 0**

``` c
["TAB","Q","W","E","R","T","Y","U","I","O","P","del"],
[{w:1.25},"fn6","A","S","D","F","G","H","J","K","L",{w:1.75},"enter"],
[{w:1.75},"shift","Z","X","C","V","B","N","M","<\n,",{w:1.25},">\n.","fn4"],
[{w:1.25},"no","alt",{w:1.25},"gui",{w:2.25},"fn2",{w:2.75},"fn1",{w:1.25},"fn3","fn5",{w:1.25},"no"]
```
![](http://imgur.com/OOCyGbU.jpg)    

**Layer 1**

```c
["esc","pgup","up","pgdn","home","T","Y","U","I","_\n-","+\n=","|\n\\"],
[{w:1.25},"ctrl","left","down","right","end","G","H","J","K",":\n;",{w:1.75},"\"\n'"],
[{w:1.75},"shift","mute","voldown","volup","prev","play","next","F13","<\n,",{w:1.25},">\n.","fn4"],
[{w:1.25},"no","alt",{w:1.25},"gui",{w:2.25},"fn2",{w:2.75},"fn1",{w:1.25},"fn3","fn5",{w:1.25},"no"]
```
![](http://imgur.com/YHmh9nl.jpg)    

**Layer 2**

```c
["TAB","!\n1","@\n2","#\n3","$\n4","%\n5","^\n6","&\n7","*\n8","(\n9",")\n0","backspace"],
[{w:1.25},"fn6","A","S","D","F","G","H","J","{\n[","}\n]",{w:1.75},"\"\n'"],
[{w:1.75},"shift","fn7","fn8","fn9","V","B","N","M","<\n,",{w:1.25},">\n.","fn4"],
[{w:1.25},"no","alt",{w:1.25},"gui",{w:2.25},"fn2",{w:2.75},"fn1",{w:1.25},"fn3","fn5",{w:1.25},"no"]
```

**FN1** and **FN2** are momentary tap keys. They output space and backspace when tapped, and they call layer 1 when held.

**FN3** and **FN6** are momentary function keys, calling layer 2 when held.

**FN4** is a momentary tap key. It outputs **?** and **/** when tapped, and acts as RShift when held.

**FN5**, **FN7**, **FN8**, and **FN9** all control LED backlighting on the board, should I choose to add backlighting in the future.

### Flashing

![](http://i.imgur.com/tAlMP2Y.png.jpg)    
At this point, the TKG toolkit is used to flash the keymap and firmware on the Kimera controller. TKG is compatible with Macs, as well as Linux and Windows.

There are prerequisites:
+ [Homebrew](http://brew.sh/)
+ Lib-usb
+ [dfu programmer](http://www.uriahbaalke.com/?p=106)

To flash, we must first set up the TKG toolkit in terminal:

```
cd /directory/path/to/TKG-toolkit/mac

./setup.sh
```

Select Kimera Core, default firmware, atmel_dfu.

Then the keymap itself is flashed:

```
./reflash.sh /directory/path/to/downloadedeepfile/keymap.eep
```

After this, the board is rebooted and the firmware is uploaded.

The process is not desperately complicated. For the newbie just entering the hobby, the TKG process is significantly simpler than attempting to modify a keymap file directly, and then flash it. I did find that it's not a great process for iterating and refining a keymap layout. It takes much more time to go back and edit a keymap than it does with straight TMK.

### Finished

![](http://imgur.com/In3SBcP.jpg)

![](http://imgur.com/ukZeRnX.jpg)

As stated above, I haven't fallen in love with this board yet. Gateron greens are definitely a lovely switch. Nowhere near as sublime as [Zealios](https://www.reddit.com/r/MechanicalKeyboards/comments/4ax617/helpi_am_drunk_here_is_the_lowdown_on_zealios_76g/) of course, but they make for a fine switch. The click is lovely and annoying, the feel is good, I'm pleased.

The TKG firmware and programming process for Golbat is odd and complicated, but not the worst. The layout of the board is great. This layout probably reduces the board to the absolute minimum number of keys to retain full usefulness. The physical layout is great. Unlike Planck, I've picked up Golbat very quickly.

![](http://imgur.com/EV6HtOq.jpg)

What remains is color. I'm still not in love with this color plate. That is in no way a knock against the board itself, it's a knock against me for not realizing the color I was buying. In the days I've had Golbat, it has been growing on me, I'm just not in love yet. Perhaps as I use it more, I'll get there.

![](http://imgur.com/U97feQq.jpg)

At the end of the day though, Golbat is a fine board. The materials are great, the layout is great, and the programming experience should be simple enough for even a novice to get through. For only $125 shipped, Golbat is excellent value for money as a programmable aluminum 40% board.

I'm still learning to love it, but it's a fine board.

![](http://imgur.com/SyMPp47.jpg)

---
<p align="right">Typed on Golbat</p>
