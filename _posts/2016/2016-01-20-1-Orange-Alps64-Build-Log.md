---
layout: page
title: "Alps Party 60% Board #1"
subheadline: "Build Log of my SKCM Orange Alps64"
teaser: "I'm very pleased with how this board turned out. My favorite board is still my white Alps64, but I will admit that it doesn't come anywhere close to looking as great as this board does. I've been running the orange Alps64 as my daily driver for a few weeks now, and will probably continue to do so until I complete my blue Alps64. "
author: Morgan
categories:
  - keyboards
image:
    title: http://imgur.com/A2SqBlg.jpg
    homepage: http://imgur.com/A2SqBlg.jpg
    thumb: http://imgur.com/A2SqBlg.jpg
    caption:
    caption_url:
breadcrumb: true
---

As detailed in a [previous post]({{ site.baseurl }}/2015-12-12-2-On-Becoming-A-Keyboard-Wonk/), the first board that prompted me to become a keyboard wonk was an Apple Extended Keyboard II with white alps switches. I had the privilege to join Hasu's round 2 [Alps PCB group buy](https://geekhack.org/index.php?topic=69740.0), from which I built my first custom keyboard. 

A few months ago, [BlueNalgene](https://geekhack.org/index.php?action=profile;u=41109) ran a much more comprehensive [group buy](https://geekhack.org/index.php?topic=75491.0) that included no only [Hasu's](https://geekhack.org/index.php?action=profile;u=3412) PCB, but also [JDCarpe](https://geekhack.org/index.php?action=profile;u=17386) designed plates, Matias switches, and stabilizers. Of course, I already had the one 60% alps board, but given that I had a few spare donor boards lying around, I couldn't help buy join this buy so I could build EVEN MORE awesome custom keyboards. 

For this build, I chose to use:

+ A [Dell AT101W](https://deskthority.net/wiki/Dell_AT101) layout plate - the layout that has pretty much become the standard for ANSI keyboards around the world
+ SKCM (complicated) vintage [orange alps](https://deskthority.net/wiki/Alps_SKCM_Orange) switches from a [AEK I](https://deskthority.net/wiki/Apple_Extended_Keyboard)
+ [Matias Click Switches](http://matias.ca/switches/click/)
+ [Matias Linear Switches](http://matias.ca/switches/linear/
+ A SCKCM (complicated) [white alps](https://deskthority.net/wiki/Alps_SKCM_White) switch. 
+ [Tai Hao Olivette Doubleshot ABS keycaps](https://www.massdrop.com/buy/alps-keycaps?mode=guest_open) (with a dolch spacebar)
+ [Royal Glam wood 60% case](https://www.massdrop.com/buy/royal-glam-60-wood-keyboard-case?mode=guest_open)

# Build Log

### Donor switches

![Donor AEK Image](http://imgur.com/DWhV23K.jpg)

Here I've began the process of desoldering the orange switches from a donor AEK I. No doubt about it, Apple did a damn fine job assembling and soldering this board back in the 80s. It took me ages to warm up the solder on these and get them all removed. 

Given that these were well used switches, there were irregularities in among them - some were simply tactile, some had developed a click as well. I ended up sorting out the clicky from the non (just so I could have uniform switch sound). 

### Prepping the plate

Hasu's PCB ships with all the SMT components presodered (controller, various ICs), but does _not_ have the diodes presoldered. The board is designed to use [1N4148](https://www.wikiwand.com/en/1N4148) through-hole diodes. The diodes must be inserted, secured, the soldered. For simplicity, I choose to use tape to secure them down prior to soldering.

![](http://imgur.com/S7jBQOy.jpg)
First rows of diodes placed.

![](http://imgur.com/VWBzyTe.jpg)
Diodes taped down, ready for solder.

![](http://imgur.com/egHWeD0.jpg)
Diodes all installed.

### Installing switches

For this build, I decided to run multiple switch types for the first time. 

+ Orange Alps for alphas (orange sliders)
+ A White Alps for Capslock - this was done for a distinctive feel. I would prefer a [lock switch](https://deskthority.net/wiki/Alps_SKCL_Lock), but didn't have one on-hand.
+ Matias Clicks (white sliders) on most row 1 mods.
+ Matias Linears (red sliders) for all other mods. 

![](http://imgur.com/vII11L9.jpg)
Switches installed in the plate.

![](http://i.imgur.com/cglvhHv.jpg)
Stabs installed. So purdy.

### Programming

Unlike a standard board made by an OEM, this keyboard is programmable, I can set any key to be anything I want it to be. This board runs Hasu's TMK firmware - an excellent, widely supported programming system. While the board is only 60% in size, by programming in firmware layers, it can be set up to do anything a full sized board can do. 

I've gone with the following layout for this build. 

```c
#include "keymap_common.h"

/*
 * Hasu
 */
const uint8_t PROGMEM keymaps[][MATRIX_ROWS][MATRIX_COLS] = {
/* 0: DEFAULT LAYER
 * ,-----------------------------------------------------------.
 * |Esc  |  1|  2|  3|  4|  5|  6|  7|  8|  9|  0|  -|  =|  #|Bsp|
 * |-----------------------------------------------------------|
 * |Tab  |  Q|  W|  E|  R|  T|  Y|  U|  I|  O|  P|  [|  ]|DEL  |
 * |-----------------------------------------------------------|
 * |Caps  |  A|  S|  D|  F|  G|  H|  J|  K|  L|  ;|  '|Enter   |
 * |-----------------------------------------------------------|
 * |Shft|  \|  Z|  X|  C|  V|  B|  N|  M|  ,|  .|  /|Shift |Esc|
 * |-----------------------------------------------------------'
 * |Ctrl|ALT |GUI |      Space/FN1    |FN2 |Alt |GUI |FN3/Ctrl |
 * `-----------------------------------------------------------'
 */
[0] =KEYMAP( \
    ESC, 1,   2,   3,   4,   5,   6,   7,   8,   9,   0,   MINS,EQL, NUHS, BSPC, \
    TAB, Q,   W,   E,   R,   T,   Y,   U,   I,   O,   P,   LBRC,RBRC,DEL, \
    CAPS,A,   S,   D,   F,   G,   H,   J,   K,   L,   SCLN,QUOT,ENT,  \
    LSFT,NUBS,Z,   X,   C,   V,   B,   N,   M,   COMM,DOT, SLSH,RSFT,ESC, \
    LCTL,LALT,LGUI,          FN1,                     FN2, RALT,FN3,RCTL),

  /* 0: MORGAN LAYER
  * ,-----------------------------------------------------------.
  * |GRV  |MUTE|VOLD|VOLU|MPRV|MPLY|MNXT| 7| 8| 9| 0| -| =/#|Bsp|
  * |-----------------------------------------------------------|
  * |Tab  |  Q| UP|  E|  R|  T|  Y|  U|  I|  O|  P|  [|  ]|  \  |
  * |-----------------------------------------------------------|
  * |Caps  |LEFT|DOWN|RIGHT|  F|  G|  H|  J|  K|  L|  ;|  '|Enter   |
  * |-----------------------------------------------------------|
  * |Shft|  \|  Z|  X|  C|  V|  B|  N|  M|  ,|  .|  /|Shift |Esc|
  * |-----------------------------------------------------------'
  * |Ctrl|Gui |Alt |         Space         |FN2 |Alt |GUI |Ctrl |
  * `-----------------------------------------------------------'
  */
 [1] =KEYMAP( \
     GRV,MUTE,VOLD,VOLU,MPRV,MPLY,MNXT,   7,   8,   9,   0,   MINS,PPLS, NUHS, BSPC, \
     TAB, Q,  UP,   E,HOME,   T,   Y,   4,   5,   6,PAST,   LBRC,RBRC,BSLS, \
     CAPS,LEFT,DOWN,RIGHT, END,   G,   H,   1,   2,   3,  PSLS,  QUOT,  ENT,  \
     LSFT,NUBS,Z,   X,   C,   V,   B,   N, F13,   COMM,DOT, SLSH,RSFT,ESC, \
     LCTL,TRNS,TRNS,          TRNS,                     TRNS, RALT,TRNS,TRNS),

  /* 0: DEFAULT LAYER
   * ,-----------------------------------------------------------.
   * |Esc  |  1|  2|  3|  4|  5|  6|  7|  8|  9|  0|  -|  =|  #|Bsp|
   * |-----------------------------------------------------------|
   * |Tab  |  Q|  W|  E|  R|  T|  Y|  U|  I|  O|  P|  [|  ]|DEL  |
   * |-----------------------------------------------------------|
   * |Caps  |  A|  S|  D|  F|  G|  H|  J|  K|  L|  ;|  '|Enter   |
   * |-----------------------------------------------------------|
   * |Shft|  \|  Z|  X|  FN4|  V|  B|  N|  M|  ,|  .|  /|Shift |Esc|
   * |-----------------------------------------------------------'
   * |Ctrl|ALT |GUI |      Space/FN1    |FN2 |Alt |FN3/GUI |Ctrl |
   * `-----------------------------------------------------------'
   */
  [2] =KEYMAP( \
   ESC, 1,   2,   3,   4,   5,   6,   7,   8,   9,   0,   MINS,EQL, NUHS, BSPC, \
   TAB, Q,   W,   E,   R,   T,   Y,   U,   I,   O,   P,   LBRC,RBRC,DEL, \
   CAPS,A,   S,   D,   F,   G,   H,   J,   K,   L,   SCLN,QUOT,ENT,  \
   LSFT,NUBS,Z,   X,   FN4,   V,   B,   N,   M,   COMM,DOT, SLSH,RSFT,ESC, \
   LCTL,LALT,LGUI,          TRNS,                     TRNS, RALT,TRNS,TRNS),

};


/* id for user defined function/macro */
enum function_id {
    NONE,
};

enum macro_id {
    COPY_TAB_PASTE,
};


/*
 * Fn action definition
 */
const uint16_t PROGMEM fn_actions[] = {
    [0]  = ACTION_LAYER_MOMENTARY(1),                  // Default
    [1]  = ACTION_LAYER_TAP_KEY(1, KC_SPC),            // MORGAN LAYER
    [2]  = ACTION_LAYER_TOGGLE(1),
    [3]  = ACTION_LAYER_MOMENTARY(2),                  // CMD Layer
    [4]  = ACTION_MACRO(COPY_TAB_PASTE),               // Copy tab paste in browser
};


/*
 * Macro definition
 */
const macro_t *action_get_macro(keyrecord_t *record, uint8_t id, uint8_t opt)
{
    switch (id) {
        case COPY_TAB_PASTE:
            return (record->event.pressed ?
                    MACRO( D(LGUI), T(C), T(T), T(V), U(LGUI), T(ENT), END ) :
                    MACRO( END ) );
    }
    return MACRO_NONE;
}
```

Note: the Space/FN1 key - I love this setup. During normal typing, the space bar is a space bar, but when it's held it activates the 2nd layer.  

### Nearing Completion

![](http://imgur.com/foItOtn.jpg)
Board installed in the Royal Glam wooden case. 

![](http://imgur.com/BmNR69N.jpg)

![](http://imgur.com/F5kpVRr.jpg)
Beginning to install switches

### Complete

![](http://imgur.com/DRvkxPK.jpg)

![](http://imgur.com/kz3qizG.jpg)

![](http://imgur.com/g029Brw.jpg)

I'm very pleased with how this board turned out. My favorite board is still my white Alps64, but I will admit that it doesn't come anywhere close to looking as great as this board does. I've been running the orange Alps64 as my daily driver for a few weeks now, and will probably continue to do so until I complete my blue Alps64. 

A note about flipped keys: you may notice the spacebar and a couple of the row 1 modifier keys are flipped around. I flip the spacebar because I am of the opinion a reversed spacebar simply feels better. The other two row 1 mod keys are flipped so that I can easily feel which is which when I'm going to the function layers. 

 ---
<p align="right">Typed on AEK II</p>
