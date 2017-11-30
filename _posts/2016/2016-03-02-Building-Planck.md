---
layout: page
title: "Planck Build"
subheadline: "A 40% Ortholinear Keyboard"
teaser: "The Ortholinear keyboard concept has exploded within the keyboard community lately. Among the many that exist, those made by Jack Humbert's Planck and Atomic have proven to be incredibly popular. A recent group buy on Massdrop had hundreds of participants."
author: Morgan
categories:
  - keyboards
image:
    title:
    homepage:
    thumb:
    caption:
    caption_url:
breadcrumb: true
---

![Beginning Switch Install](http://imgur.com/duNnbCk.jpg)

> Ortholinear is a semi-made-up word that was originally coined (to my knowledge) by TypeMatrix as "ortho-linear" - this term got concatenated, became popular among the keyboard community, and eventually became the banner for a keyboard company!    It refers to keyboard layouts where the keys are aligned vertically and horizontally, compared to standard staggered keyboards. No studies have been done to test the ergonomics of ortholinear keyboards (versus a comparable staggered one), but the change can make it easier to design and visual custom keymaps, and may help relieve RSI symptoms.

[[OLKB]](http://ortholinearkeyboards.com/education)

The Ortholinear keyboard concept has exploded within the keyboard community lately. Among the many that exist, those made by Jack Humbert's [Planck](http://ortholinearkeyboards.com/planck) and [Atomic](http://ortholinearkeyboards.com/atomic) have proven to be incredibly popular. A recent group buy on [Massdrop](https://www.massdrop.com/buy/planck-mechanical-keyboard?mode=guest_open) had hundreds of participants. Nearly every custom keycap buy that is launched now has support for Planck or Atomic layouts in some way or another.

Atomic and Planck are both reduced size boards. Atomic being a 65% sized board, Planck a 40%. The typical board has 104 to 108 keys, Planck has a mere 48. Like most custom keyboards, Planck must rely on function layers to produce the full range of 100+ keys (should the user so desire). A function layer should be familiar to many laptop owners: you press the function key, and other keys change from doing one thing, to doing another. Many, if not _most_ custom keyboards employ some level of function keys, but unlike laptops, custom keyboards often have **multiple** function layers.

Planck's implementation of layers is quite novel and elegant. Unlike other boards that have arbitrary positions for function keys, with _x_ number of layers, and a stack and priority to memorize, Planck by default employs just three. The main layer, the lower layer, and the upper layer.

![Planck default layout](http://i.imgur.com/uSXjhWG.jpg)
[[source]](https://www.massdrop.com/buy/planck-mechanical-keyboard?mode=guest_open)

Planck comes shipped from OLKB with a very usable layout. For those who want to program it, Planck uses [QMK](https://github.com/jackhumbert/qmk_firmware), a fork of the popular [TMK](https://github.com/tmk/tmk_keyboard) firmware. QMK is clever, it employs the TMK core, but has lovely programming shortcuts built in. These shortcuts make it simple to modify a keymap, and succeed in making the code much more human-readable. For example, in TMK, to a macro of modifier keys would require a dedicated macro script + a function key dedicated to it. Below is a macro to key Ctrl+Alt+Del with one key:

```c
/*
 * Fn action definition
 */
const uint16_t PROGMEM fn_actions[] = {
    [0] = ACTION_LAYER_MOMENTARY(1),                  // Default Layer
    [1] = ACTION_LAYER_TOGGLE(1, FN1),          // Apple FN + Others Layer
};


/*
 * Macro definition
 */
const macro_t *action_get_macro(keyrecord_t *record, uint8_t id, uint8_t opt)
{
    switch (id) {
        case ALT_TAB:
            return (record->event.pressed ?
                    MACRO( D(LALT), D(LCTRL), D(KC_DEL), END ) :
                    MACRO( U(LALT), U(LCTRL), D(KC_DEL), END ));
    }
    return MACRO_NONE;
}
```

QMK vastly simplifies the process, modifiers can be chained, with no dedicated macro even being required - leading to much simpler code:

```c
LALT(LCTL(KC_DEL))
```

Or a simple method to make a key be shift while held, capslock when tapped:

```c
{MT(MOD_LSFT, KC_CAPS)
```

Again, with no dedicated macro or function layer required to make that happen.

I found the changes from TMK to QMK easy to grasp, and I was able to quickly adapt to using it. I'm seriously considering adapting my TMK keymaps for my Alps64 boards to QMK, just for prettier code.

The keymap I've configured for my Planck is below:

```c
 #define _QW 0
 #define _LW 1
 #define _RS 2
 #define _SH 3

 const uint16_t PROGMEM keymaps[][MATRIX_ROWS][MATRIX_COLS] = {
   // Defalt Layout
   /*
    * ,-----------------------------------------------------------------------.
    * |ESC  |Q    |W    |E    |R    |T    |Y    |U    |U    |O    |P    |BSPC |
    * |-----------------------------------------------------------------------|
    * |TAB  |A    |S    |D    |F    |G    |H    |J    |K    |L    |SCLN |QUOT |
    * |-----------------------------------------------------------------------|
    * |LSFT |Z    |X    |C    |V    |B    |N    |M    |COMM |DOT .|SLSH |ENT/RS|
    * |-----------------------------------------------------------------------|
    * |M0   |LCTL |LALT |LGUI |FNLW |SPC        |FNRS |LEFT |UP   |DOWN |RGHT |
    * `-----------------------------------------------------------------------'
    */
 [_QW] = { /* Qwerty */
   {KC_ESC,  KC_Q,    KC_W,    KC_E,    KC_R,    KC_T,    KC_Y,    KC_U,    KC_I,    KC_O,    KC_P,    KC_BSPC},
   {KC_TAB,  KC_A,    KC_S,    KC_D,    KC_F,    KC_G,    KC_H,    KC_J,    KC_K,    KC_L,    KC_SCLN, KC_QUOT},
   {MT(MOD_LSFT, KC_CAPS), KC_Z,    KC_X,    KC_C,    KC_V,    KC_B,    KC_N,    KC_M,    KC_COMM, KC_DOT,  KC_SLSH, MT(MOD_LSFT, KC_ENT) },
   {M(0),    KC_LCTL, MT(MOD_LALT, KC_CAPS), KC_LGUI, MO(_LW), LT(_SH, KC_SPC), LT(_SH, KC_SPC),  MO(_RS), KC_LEFT, KC_UP   , KC_DOWN,   KC_RGHT}
 },
 // RAISE
 /*
  * ,-----------------------------------------------------------------------.
  * |GRV  |1    |2    |3    |4    |5    |6    |7    |8    |9    |0    |BSPC |
  * |-----------------------------------------------------------------------|
  * |TAB  |A    |S    |D    |HOME |G    |H    |4    |5    |6    |MINS |BSLS |
  * |-----------------------------------------------------------------------|
  * |LSFT |Z    |X    |C    |END  |B    |N    |1    |2    |3    |SLSH |ENT/RS|
  * |-----------------------------------------------------------------------|
  * |M0   |LCTL |LALT |LGUI |FNLW |SPC        |0    |0    |.    |DOWN |RGHT |
  * `-----------------------------------------------------------------------'
  */
 [_LW] = { /* LOWER */
   {KC_GRV,  KC_1,      KC_2,      KC_3,      KC_4,      KC_5,      KC_6,      KC_7,    KC_8,    KC_9,    KC_0,    KC_BSPC},
   {KC_TRNS, KC_TRNS,   KC_TRNS,   KC_TRNS,   KC_HOME,   KC_TRNS,   KC_TRNS,   KC_4,    KC_5,    KC_6   , KC_MINS, KC_BSLS},
   {KC_TRNS, KC_TRNS,   KC_TRNS,   KC_TRNS,   KC_END,    KC_TRNS,   KC_TRNS,   KC_1,    KC_2,    KC_3   , KC_TRNS, KC_TRNS},
   {KC_TRNS, KC_TRNS,   KC_TRNS,   KC_TRNS,   KC_TRNS,   KC_TRNS,   KC_TRNS,   KC_0,    KC_0,    KC_DOT , KC_TRNS, KC_TRNS}
 },
 // LOWER
 /*
  * ,-----------------------------------------------------------------------.
  * |GRV  |1    |2    |3    |4    |5    |6    |7    |8    |9    |0    |DEL  |
  * |-----------------------------------------------------------------------|
  * |TAB  |MUTE |VOLD |VOLU |HOME  |G    |H   |J    |BSLS |=    |-    |"    |
  * |-----------------------------------------------------------------------|
  * |LSFT |MPRV |MPLY |MNXT |END  |B    |N    |F13  |BSLS |[    |]    |RSFT |
  * |-----------------------------------------------------------------------|
  * |M0   |LCTL |LALT |LGUI |FNLW |SPC        |FNRS |LEFT |UP   |DOWN |RGHT |
  * `-----------------------------------------------------------------------'
  */
 [_RS] = { /* RAISE */
   {KC_GRV,  KC_1,      KC_2,      KC_3,      KC_4,      KC_5,      KC_6,      KC_7,    KC_8,    KC_9,    KC_0,    KC_DEL},
   {KC_TRNS, KC_MUTE,   KC_VOLD,   KC_VOLU,   KC_HOME,   KC_TRNS,   KC_TRNS,   KC_TRNS, KC_BSLS, KC_EQL, KC_MINS,  KC_QUOT},
   {KC_TRNS, KC_MPRV,   KC_MPLY,   KC_MNXT,   KC_END,    KC_TRNS,   KC_TRNS,   KC_F13,  KC_BSLS, KC_LBRC, KC_RBRC, KC_TRNS},
   {KC_TRNS, KC_TRNS,   KC_TRNS,   KC_TRNS,   KC_TRNS,   KC_TRNS,   KC_TRNS,   KC_TRNS, KC_LEFT, KC_UP, KC_DOWN, KC_RGHT}
 },
 // Space FN
 /*
  * ,-----------------------------------------------------------------------.
  * |~    |!    |@    |#    |$    |%    |^    |&    |*    |(    |)    |DEL  |
  * |-----------------------------------------------------------------------|
  * |TAB  |A    |S    |D    |F    |G    |H    |J    |PIPE |+    |_    |QUOT |
  * |-----------------------------------------------------------------------|
  * |LSFT |Z    |X    |C    |V    |B    |N    |M    | |DOT .|SLSH |RSFT |
  * |-----------------------------------------------------------------------|
  * |M0   |LCTL |LALT |LGUI |FNLW |SPC        |FNRS |LEFT |UP   |DOWN |RGHT |
  * `-----------------------------------------------------------------------'
  */
 [_SH] = { /* SpaceFN/Shifted Layout */
 {KC_TILD, KC_EXLM, KC_AT,   KC_HASH, KC_DLR,  KC_PERC, KC_CIRC, KC_AMPR, KC_ASTR, KC_LPRN, KC_RPRN, KC_DEL},
 {KC_TAB,  KC_A,    KC_S,    KC_D,    KC_HOME,    KC_G,    KC_H,    KC_J,    KC_PIPE,    KC_PLUS,    KC_UNDS, KC_TRNS},
 {KC_LSFT, KC_Z,    KC_X,    KC_C,    KC_END,    KC_B,    KC_N,    KC_M,    KC_PIPE, KC_DOT,  KC_SLSH, KC_TRNS },
 {M(0),    KC_LCTL, KC_TRNS, KC_LGUI, MO(_LW), KC_TRNS, KC_TRNS, MO(_RS), KC_LEFT, KC_UP,   KC_DOWN,  KC_RGHT}
 },
 };

 const uint16_t PROGMEM fn_actions[] = {

 };

 const macro_t *action_get_macro(keyrecord_t *record, uint8_t id, uint8_t opt)
 {
   // MACRODOWN only works in this function
       switch(id) {
         case 0:
           if (record->event.pressed) {
             register_code(KC_RSFT);
             backlight_step();
           } else {
             unregister_code(KC_RSFT);
           }
         break;
       }
     return MACRO_NONE;
 };
```

## Assembly

My Planck was ordered from the Massdrop group buy. I selected a purple milled case bottom, a [MIT layout](http://ortholinearkeyboards.com/planck/planck-top-plate-mit) plate (this uses a 2u spacebar instead of 2 separate keys where space would go), and OEM profile blank white keycaps.

![All Parts](http://imgur.com/PFceR0N.jpg)

I selected the purple milled bottom to match a [Binge/HungerWorks](http://blog.hungerwork.studio/) artisan keycap I won during the initial Zealio [group buy](https://geekhack.org/index.php?topic=74807.0). I was wary after my purchase about whether I'd made the right decision - but seeing it in person assuaged all my fears. This thing is absolutely gorgeous.

![Milled Purple Bottom](http://imgur.com/dHwkE5F.jpg)

For this build I've employed three different switch types. Tactile 65g [Zealios](https://zealpc.net/products/zealio), linear [Gateron](https://deskthority.net/wiki/Gateron_KS-3_series) Reds. and a Cherry [MX Black](https://deskthority.net/wiki/Cherry_MX_Black). The Zealios have been placed on the alphanumeric keys, linear reds on the modifiers, Cherry black (which is a heavy switch) on space.
![Switch Install](http://imgur.com/s1ibLdT.jpg)

Assembly of Planck is incredibly straightforward. One might not think a 40%, QMK programmed custom keyboard would be a great introduction for someone getting into custom keyboards, but it really is. The PCB comes with all controller parts and diodes pre-soldered, so assembly is simply a process of placing the stabilizer (if using the MIT layout), placing switches in the plate, then soldering them to the PCB. It's dead simple board to assemble. I wish more were like it.

![Switches Installed](http://imgur.com/IDXNdEx.jpg)

The kit does ship with 48 white LEDs included. Not being a fan of LED backlighting on most boards, I opted to only install one - below my artisan keycap.

![Fully Assembled](http://imgur.com/JhUugWv.jpg)

Elegance and simplicity typify this keyboard. It's a pleasure to look at, and with the tactile zealios and adorable compact size it's a pleasure to type with. The ortholinear layout does take a few hours to acclimatize to, after years of touch typing on a staggered board, but it's easy to do. One might imagine so few keys to be a hurdle to overcome, but it really isn't, The upper/lower layer concept makes learning the function layers very easy.

![Planck compared to AEKII](http://imgur.com/JZ69wAH.jpg)

Planck compared to a full-sized Apple Extended Keyboard II.

At the moment I have the OEM blank keycaps installed - I may consider putting Granite keycaps on the board when those arrive this summer, but I haven't decided yet. Until then, it'll continue to look beautiful with the blanks and the Binge slow fi.

![Slow Fi](http://imgur.com/IxPYAx6.jpg)

---
<p align="right">Typed on Planck</p>
