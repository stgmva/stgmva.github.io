---
layout: page
#
# Content
#
subheadline: ""
title: "Orange Alps solar Log"
teaser: "Alps Orange"
categories:
  - design
tags:
  - design
#
# Styling
#
image:
  header: ""
  thumb: "you-can-delete-me-thumb.png"
  homepage: "you-can-delete-me-homepage.png"
  caption: "Caption?"
  url: "http://phlow.de/"
---

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
```
