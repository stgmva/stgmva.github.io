---
layout: page
title: "Kinesis Contoured Model 110"
subheadline: ""
teaser: "A few days I added a Kinesis Countoured Model 110 to my collection. The predecessor to the Advantage and the Advantage 2, this model is over 20 years old."
author: Morgan
categories:
  - keyboards
breadcrumb: true
---
![](http://imgur.com/9pCXqKb.jpg)

A few days I added a [Kinesis](https://www.kinesis-ergo.com/) Countoured Model 110 to my collection. The predecessor to the Advantage and the Advantage 2, this model is over 20 years old.

I got the board for a steal on [/r/mechmarket](https://www.reddit.com/r/mechmarket). The seller said the board was not functional, producing only a beeping tone when plugged in. I figured that if all else, even if the built-in electronics weren't functional that I could hand wire a matrix for it. Much to my surprise, using my PS/2 to USB adapter, the board is fully functional.

![](http://imgur.com/Ji4qdVn.jpg)

The Kinesis is notable for its split design and ergonomic keywells.

[ErgoDox]({{ site.baseurl }}/ErgoDox_Omnibus) derives much of its design from the Kinesis. Given that I've been using an ErgoDox as my daily driver at work for some time, using the Kinesis (albiet briefly) has proven fairly easy.

![](http://imgur.com/eScRdV0.jpg)

From the side you can see the sculpting of the keywells. At first glance the sculpting appears haphazard, but in using it, the sculpting has proven to be brilliant. Clearly a lot of time and effort went into this design by the Kinesis engineers.

![](http://imgur.com/Cp1dn8M.jpg)

Standard for Kinesis boards of the time, this one has plate mount [Cherry MX browns](https://deskthority.net/wiki/Cherry_MX_Brown). I've never actually had a full board with browns before. They have a decent tactile bump, at 45g they're light, but not too light. I did notice that they are quite scratchy, a common complaint about Cherry browns.

![](http://imgur.com/Q1G1waG.jpg)

As I said, the board is over 20 years old. Tag dates it to circa 1993.

![](http://imgur.com/jqEzns5.jpg)

The I/O includes a PS/2 port for connecting to your PC, and 2 RJ-11 jacks used with optional foot switches.

![](http://imgur.com/o5IbEyE.jpg)

Cracking the board open, you can see how nuts the internal electronics are. By my count there are 7 PCBs inside, including the control electronics.

![](http://imgur.com/GQhuySV.jpg)

Each keywell has this separated PCB design, terminating in a ribbon cable connected to the 'main' PCB.

Each side of the board also has 9 rubber membrane keys. These also terminate in a ribbon cable also connected to the main PCB.

The main PCB contains the keys for the thumb cluster. Each keywell PCB connects to it. The control electronics connect to this board.

![](http://imgur.com/AxiPTsd.jpg)

The main control electronics are pretty crazy. With jumper cables on several of the circuits. Not sure if this is due to errors during design, or if the jumpers are intentional.

Of course, I can't leave well alone, so I have modifications planned for this board.

+ Swap in Gateron switches.
  + I am thinking I'll put in Gateron Browns, but I have a few different switches on order, so I may find myself installing Gatistotles or Zealios instead.

+ Replace control electronics.
  + Given that the board is fully functional in its current state, I'd like to keep most of the existing PCBs in place. I'm hoping that I can sort out the pin configuration for the the keywell & membrane PCBs and wire them to a Teensy microcontroller, granting me modern USB connectivity, and full programability using TMK/QMK.

+ Keycaps
  + The stock sculpted DCS profile keycaps are great, but I may want to swap in all DSA profile or SA profile keys. I haven't decided yet.

---
<p align="right">Typed on Blue Alps64</p>
