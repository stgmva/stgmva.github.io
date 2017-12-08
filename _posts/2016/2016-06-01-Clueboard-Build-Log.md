---
layout: page
title: "Clueboard Build Log"
subheadline: ""
teaser: "Enter Clueboard. Designed by Skullydazed, Clueboard is a 65% PCB designed precisely to the same dimensions as Leopold's F660. Clueboard supports a wide variety of layouts, and most importantly to me, support Hasu's TMK firmware."
author: Morgan
categories:
  - keyboards
image:
    title: http://imgur.com/opdEe1Z.jpg
    homepage: http://imgur.com/opdEe1Z.jpg
    thumb: http://imgur.com/opdEe1Z.jpg
    caption:
    caption_url:
breadcrumb: true
---

![]()

When I first got into this hobby - mechanical keyboards, one of the first boards to catch my eye was Leopold's [F660](https://mechanicalkeyboards.com/shop/index.php?l=product_detail&p=1172). The F660 is like many other 60% boards, insomuch that it lacks a ten-key or a function row, but _unlike_ many others, it has integrated arrow keys. Like most boards I've looked at, I quickly dismissed it because it was not programmable.

Enter [Clueboard](http://clueboard.co/). Designed by [Skullydazed](https://geekhack.org/index.php?action=profile;u=43824), Clueboard is a 65% PCB designed precisely to the same dimensions as Leopold's F660. Clueboard supports a wide variety of layouts, and most importantly to me, support Hasu's [TMK](https://github.com/tmk/tmk_keyboard) firmware.

Unlike builds I've done in the past, I was able to source all the parts for my Clueboard in a day. Fortunately I already had suitable switches and keycaps in my stock; pcb, plate, case, and frame all happened to be readily available for order the same day I discovered Clueboard.

### The Parts

+ Clueboard 2.0 PCB
+ Clueboard Aluminum Plate
+ PCB Mount Switches
+ Massdrop [Aluminum Leopold Case](https://www.massdrop.com/buy/aluminum-case-for-leopold-fc660m?mode=guest_open)
+ 65g Zealio Switches
+ Gateron Reds (mods)
+ Cherry MX Black (spacebar)
+ [Originative Carbon Black](https://www.massdrop.com/buy/originative-carbon-black-keycaps?mode=guest_open) Keycaps

### The Build

Build for this board was fairly straightforward. The Clueboard 2.0 PCB for this build comes out of the box with all necessary SMD components already soldered (controller, diodes, etc) - so it's basically a deal of install switches in plate, solder switches, and finish. There was one hairy moment towards the end, but nothing too desperately complicated.

![](http://imgur.com/xVwU26V.jpg)

Like other MX mount builds I've done in the past, I opted for a mix of switches. I've used 65g Zealios [(the way to your feelios)](https://www.reddit.com/r/MechanicalKeyboards/comments/4ax617/helpi_am_drunk_here_is_the_lowdown_on_zealios_76g/) on alphas, with Gateron Reds for modifiers, and a Cherry MX Black on spacebar. Initially I only deployed reds on the shift keys, but after I experienced some binding on Enter with a Zealio installed, I switched it for a red.

![](http://imgur.com/y3AJqnB.jpg)

This build uses Cherry style PCB-mount stabilizers, which I've lubricated with [Finish Line Extreme Flouro](http://www.amazon.com/Finish-Line-Extreme-Fluoro-Syringe/dp/B002L5UL92?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o01_s00) teflon lube. Zealios come lubricated from the factory, and I'm satisfied with the smoothness of Gateron reds and my broken-in MX Blacks, so I felt no need to lubricate the switches.

![](http://imgur.com/jatmvVK.jpg)

### The Shift Problem

The only issues I encountered with this build were the shift keys. I did not realize that the Leopold arrangement of Clueboard meant modified shift key sizes. Left shift was normal, but the Leopold layout does not accommodate the standard 2.75u right shift key; instead it uses a 2.5u. My Originative Carbon Black keycaps did not come with an alternate shift key, so I improvised, installing a 1.5u menu key (repurposed for shift), and a 1u blank for HHKB style function toggle.

<img align="right" src="http://imgur.com/YVwxnco.jpg">
The other issue that popped up was that a switch installed in the L Shift position would not register at all. I attempted modifying the keymap, and desoldering and installing a new switch (in the thought that perhaps the switch was a dud). As it turns out, there must be an error with the wiring of the PCB, it was only after I took a wild guess and shorted ISO L Shift that the switch in L Shift functioned as normal. In the end it's not a big deal, no custom keyboard would be complete without at least one bodge job.

### The Code

Skullydazed did a great job designing Clueboard's PCB. Not only does it perfectly fit the Leopold layout, it also supports modern features like LED backlighting (on limited keys), and RGB underglow. Given that I was not deploying any LEDs for this build, I opted to trim down the keymap quite a bit, eliminating all Skully's default macros and LED support.

The below keymap uses just two layers, a base and function layer. It has a Mac-centric bottom row, and uses SpaceFN and a function toggle next to left shift.

```c


#include "clueboard2.h"

#define _BL 0
#define _FL 1

const uint16_t PROGMEM keymaps[][MATRIX_ROWS][MATRIX_COLS] = {
  /* Keymap _BL: (Base Layer) Default Layer
   * ,--------------------------------------------------------------------------.  ,----.
   * |Esc |   1|   2|   3|   4|   5|   6|   7|   8|   9|   0|   -|   =|   \| DEL|  |PGUP|
   * |--------------------------------------------------------------------------|  |----|
   * |   Tab|   Q|   W|   E|   R|   T|   Y|   U|   I|   O|   P|   [|   ]|   BSPC|  |PGDN|
   * |--------------------------------------------------------------------------|  `----'
   * |Capslck|   A|   S|   D|   F|   G|   H|   J|   K|   L|   ;|   '|   # |  Ent|
   * |-----------------------------------------------------------------------------.
   * |Shift|  NO|   Z|   X|   C|   V|   B|   N|   M|   ,|   .|   /|   SHIFT|F1|  UP|
   * |------------------------------------------------------------------------|----|----.
   * | Ctrl|  Gui|  Alt|   NO|       SPACE/F0          NO|  Alt| Ctrl|  _FL|LEFT|DOWN|RGHT|
   * `----------------------------------------------------------------------------------'
   */
[_BL] = KEYMAP(
  KC_ESC,  KC_1,    KC_2,   KC_3,   KC_4,   KC_5,   KC_6,   KC_7,   KC_8,   KC_9,    KC_0,     KC_MINS,  KC_EQL,   KC_GRV,  KC_DEL,   KC_HOME, \
  KC_TAB,  KC_Q,    KC_W,   KC_E,   KC_R,   KC_T,   KC_Y,   KC_U,   KC_I,   KC_O,    KC_P,     KC_LBRC,  KC_RBRC,  KC_BSPC,           KC_END,  \
  KC_CAPS, KC_A,    KC_S,   KC_D,   KC_F,   KC_G,   KC_H,   KC_J,   KC_K,   KC_L,    KC_SCLN,  KC_QUOT,  KC_NUHS,  KC_ENT,                     \
  KC_LSFT, KC_LSFT, KC_Z,   KC_X,   KC_C,   KC_V,   KC_B,   KC_N,   KC_M,   KC_COMM, KC_DOT,   KC_SLSH,  KC_RSFT,  F(1),     KC_UP,            \
  KC_LCTL, KC_LALT, KC_LGUI, KC_NO,          F(0),F(0),                        KC_NO,  KC_LGUI,  KC_RALT,  KC_RCTL, KC_LEFT, KC_DOWN, KC_RGHT),

  /* Keymap _FL: Function Layer
   * ,--------------------------------------------------------------------------.  ,----.
   * | GRV|MUTE|VOLD|VOLU|MPRV|MPLY|MNXT|   7|   8|   9|   0|   -|   +|    | Del|  |BLIN|
   * |--------------------------------------------------------------------------|  |----|
   * |      |    |  UP|    |HOME  |    |    |  4|   5|   6|   |    |    |       |  |BLDE|
   * |--------------------------------------------------------------------------|  `----'
   * |       |LEFT|DOWN|RIGHT| END|    |    |   1|   2|   3|    |    |     |     |
   * |-----------------------------------------------------------------------------.
   * |     |    |    |    |    |    |    |    |   0|    |    |    |     |     |PGUP|
   * |------------------------------------------------------------------------|----|----.
   * |     |     |     |     |         |         |     |     |     |  _FL|HOME|PGDN| END|
   * `----------------------------------------------------------------------------------'
   */
[_FL] = KEYMAP(
  KC_GRV,  KC_MUTE, KC_VOLD,KC_VOLU, KC_MPRV,KC_MPLY,KC_MNXT,KC_7,   KC_8,   KC_9,    KC_0,     KC_MINS,  KC_PPLS,   KC_TRNS, KC_DEL,           KC_TRNS, \
  KC_TRNS, KC_TRNS, KC_UP,  KC_TRNS, KC_HOME,KC_TRNS,KC_TRNS,KC_4,   KC_5,   KC_6,    KC_PAST,  KC_TRNS,  KC_TRNS,  KC_TRNS,                   KC_TRNS, \
  KC_TRNS, KC_LEFT, KC_DOWN,KC_RIGHT,KC_END, KC_TRNS,KC_TRNS,KC_1,   KC_2,   KC_3,    KC_PSLS,  KC_TRNS,  KC_TRNS,  KC_TRNS,                           \
  KC_TRNS, KC_TRNS, KC_TRNS,KC_TRNS, KC_TRNS,KC_TRNS,KC_TRNS,KC_0,   KC_TRNS,KC_TRNS, KC_TRNS,  KC_TRNS,  KC_TRNS,  KC_TRNS,          KC_PGUP,         \
  KC_TRNS, KC_TRNS, KC_TRNS, KC_TRNS,        KC_TRNS,KC_TRNS,                        KC_TRNS,  KC_TRNS,  KC_TRNS,  KC_RCTL, KC_HOME, KC_PGDN, KC_END),

};

const uint16_t PROGMEM fn_actions[] = {
  [0]  = ACTION_LAYER_TAP_KEY(_FL, KC_SPC),
  [1]  = ACTION_LAYER_TOGGLE(_FL),
};
```

### Case and Keycaps

![](http://imgur.com/hrwIyDz.jpg)

For me the highlight of this build (other than the _killer_ Leopold layout) are the case and keycaps. Skullydazed's Clueboard store does have brilliant acrylic plates and cases available, but I wanted to go for a more traditional Leopold look. At the time I was sourcing parts for this build, I already had Originative Carbon Black keycaps on hand, so I chose a complimentary red color for the rest of the board. I've used a red aluminum case purchased from Massdrop, and in my opinion it looks absolutely brilliant.

![](http://imgur.com/MobZrfD.jpg)

The case is tapered slightly, giving the board a lovely angle. The angle is shallow, but still raises the keys adequately, so no extra feet are required, but it is still raked high enough to give an aggressive look. The one issue with the case was the fit of the PCB & plate. The true Leopold must be significantly thicker than Clueboard. Initially after installing the board in the case I noticed 1-2mm of vertical play between the plate and case. This was quickly resolved with padding around all four corners.

![](http://imgur.com/sxBLHkd.jpg)

I find the contrast between the red and the 'murdered out' black keycaps fantastic. I do wish the [ABS](https://deskthority.net/wiki/Keycap_construction#ABS) [doubleshot](https://deskthority.net/wiki/Double-shot_molding) Carbon Blacks were a bit thicker, but coupled with Zealio's amazing tactile switches they still feel great to type on.  
![](http://imgur.com/dMMpR25.jpg)

![](http://imgur.com/SFfgBbe.jpg)

![](http://imgur.com/1iNdGn2.jpg)

I anticipate that this board will usurp my [Satan GH60]({{ site.baseurl }}/2016-04-19-Satan-GH60-Build-Log) to become my new daily driver.

---
<p align="right">Typed on Clueboard</p>
