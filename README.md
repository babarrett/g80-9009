# g80-9009
Cherry built keyboard, G80-9009, and similar model numbers, for Reuters. 
The Reuters model number is AK124. 

The variations in model numbers seem to reflect some specialized key labeling,
some language variation in 3 of the main keys (for USA they are labeled "~ `",
"| \", and "blank" near the left shift), and finally technology. I have seen 
photos of a G8-9039HAAUS that is all surface mount technology.

Presumption:
Reuters is an old and current leading newswire service.
All of the specialized keys are for trading functions.
(Open Orders, Cancel orders, Bid, Offer, Change)

What do traders need? Financial markets move on news. Clearly they need a portal
into the trading system (or network) and they need access to up to date news. So
then, the "workstation" port is for the trading and the "PC" port is for the
news.

Two keys in the upper-right (Desk PC, Wkst) allow the trader to switch the
keyboard from the desktop PC to Workstation, and back.

It:

* Was available in the 1990's. I have seen REUTERS logos created in 1965 (the
"dot" wordmark) and in 1996 the rounded piece – or roundel – was developed. 1999
the dots in the name gave way to a solid all-caps font with an orange dotted
semi-circle, and a solid blue semicircle.
* has 149 available keys
* has a, primarily text, LCD display
* can create macros on the fly that are stored in the keyboard. 
* can select any 1 of 4 screens
* can select any 1 of 2 workstations with a kmd3, or 4(?) for a "Breakout Box"
* can perform calculations within the keyboard, displaying the results on the LCD display

---
**CAUTION!** Not everything in here has been verified, and even if it has been
verified your keyboard and revision could be different. The voltages are all, as
far as I know, low 5V and 12V. It seems to me very unlikely that these voltages 
will harm you, but reversing + and - could destroy some of your electronics.

---
## Connection Methods

Let's start with what I presume everyone cares most about. "How to I connect
this to my computer?"

As near as I can tell there are three ways and one variation for connecting this
keyboard to a modern computer:

1. Yangdigi's [controller card](../master/method-1-yangdigi-controller.md "Yangdigi controller instructions")
    - A "drop in" solution
    - Ends up with a USB connection. No need for a further PS/2 to USB converter
    - Includes a Pro Micro (equivalent), running TMK software, allowing the mapping of all 149 keys.
    - Probably does not, but still might, require a 12V power connection to the keyboard
    - A good solution for getting up-and-running quickly, without much thinking
    or assembly required. A known solution. Very useful if some part of your
    keyboard's internals (other than the key matrixes) has failed. Unless the LCD
    display being operational was a significant motivation for acquiring this
    keyboard, this is likely your best and easiest choice.
2. [Directly](../master/method-2-direct.md  ) from the "Desk PC/Workstation"
    connector to a PS/2 connector
    - Very few parts, essentially one custom built DB-9 to PS/2 cable and
    - a 12V power connection to the keyboard (host port, DB-15)
    - Uses a passive PS/2 to USB adapter to get to USB, if needed.
    - A good solution for getting a keyboard with working display functions,
    while the keyboard itself is not programable and you cannot control the
    keymap. If the LCD display being operational was a significant motivation
    for acquiring this keyboard, and having the whole keymap and layers be
    programable is unimportant, this is likely your best choice. 
3. [Direct+Soarer](../master/method-3-direct+soarer.md  ) from the "Desk
    PC/Workstation" connector to a PS/2 connector
    - Few parts, essentially one custom built DB-9 to PS/2 cable and
    - a 12V power connection to the keyboard (host port, DB-15)
    - Uses an active Soarer PS/2 to USB converter. The Soarer adds the
    ability to remap keys, add macros, add additional function layers, and be
    able to toggle different layouts.
    - A good solution for getting everything you're likely to want out of the
    keyboard: working display functions, with in-keyboard programmability and
    keymap re-writing. If the LCD display being operational was a significant
    motivation for acquiring this keyboard, and you want it to be programable
    too, this is likely your best choice. 
4. With (rare) [KVM](../master/method-4-keyboard-to-breakout-box.md) boxes
    - These are KVM switches (keyboard, video and mouse)
    - kdm3 (keyboard, display and mouse)
    - Reuters Breakout Box
    - Covered here in less detail as the boxes are so rare.
    

## Method vs features  

| Feature                      | Controller | Direct | Direct+Soarer | KVM  |
| ---------------------------- |:----------:| :-----:| :------------:| :---:|
| Maps all 149 keys            | y | n(141?) | n(141?) | n(141?) |
| Display functions work       | n | y | y | y |
| Req. hand-made power on Host | n | y | y | n |
| Lock LEDs work               | n? | y? | n? | y? |
| Requires "rare" KVM box      | n | n | n | y |
| Support kbd-only switching   | n | n | n | y |


---
## Costs for Keyboard and parts to assemble

| Item                            |   Price | Controller | Direct | Direct+Soarer | KVM  |
| ------------------------------- |--------:|:----------:| :-----:| :------------:| :---:|
| G80-9009 Keyboard*              | $111.01 |    Y       |  Y     |     Y         |  Y   |
| Yang Controller*                |  $57.25 |    Y       |        |               |      |
| PS/2 cable, 6' Male to Male     |   $3.62 |            |  Y     |               |      |
| 12VDC/500mA, Jameco             |  $11.95 |            |  Y     |     Y         |  Y   | 
| DB-15 extension cable, 6'       |   $5.95 |            |  Y     |     Y         |  Y   |
| DB-9, Female,SOLDER CUP 22AWG   |   $0.85 |            |  Y     |     Y         |  Y   |
| DB-9, Hood, metalized           |   $0.85 |            |  Y     |     Y         |  Y   |
| PS/2 to USB Soarer's Converter  |  $39.99 |            |        |     Y         |      |
| KVM box                         |       † |            |        |               |  Y   |
| TOTALS                          |         |   $168.26  | $134.23 |   $170.60    | $130.61† |

\* International shipping from China allocated among these two items.

† Does not include the price of the KVM box, if available.

---
## Physical Attributes

### Physical Specifications:

* Shipping weight ~ 2570g
* Shipping dimensions: 54.6 * 30.8 * 9.2 cm
* 2.4Kg, 4Kg shipping weight
* Width
* Height
* Depth
* 12V 500mA = 6W on the label on the bottom, but Meow Wei (Youtube) found 12V (12.6V measured), 2.5A.
    - DB15 Female 
    - In the following, "ø" represents others pins, not used or used for non-power/ground reasons.
```
            • +12V, Vin on pins: 12, 13, 14
                ø,  ø,   ø,   -,   -,   -,   ø,   - 
                  ø,   ø,   ø,  12,  13,  14,  ø
            • GND, on pins: 4, 5, 6, 8﻿
                ø,  ø,   ø,   4,   5,   6,   ø,  8 
                  ø,   ø,   ø,   +,   +,   +,  ø
```
* but 5v ??mA powered by Yang's USB controller for the keyboard matrix, only.

### Switches

* MX Clear switches, 149 of them. 
* High force at end of stroke to discourage bottoming out.
* Diode soldered into every switch.

### Caps:

Most are Double-shot ABS. "Super thick." TODO: measure once in hand

* The 11 caps with (LED) windows are pad-printed.
    * Caps Lock
    * Scroll Lock
    * Num Lock
    * (4) Scrn 1-4
    * Desk PC
    * Calc
    * Setup
    * Wkst
* There are 2 more LEDs adjacent to the space bar, but no windows to shine through.
* 10u space bar.
* In spite of the odd bottom row with the extended spacebar, and stepped Caps Lock, pretty much everything will fit on a modern board.


### Case:

* Top (51) keys are plate mounted
* Lower (main 99 keys) are PCB mounted
* Flip-out feet on bottom, at back
* Under the rectangular plate on the bottom (4 screws) is a 27 x 2 pin ribbon cable, not connected. For expansion module?
* Back of keyboard, left to right has the following: [Photos from imgur](http://i.imgur.com/lwkKiGb.jpg)
```
    [Grill]    [Knob]   [Knob]      [button]
    Buzzer     Volume   Contrast    Reset 
    
    Then, 3 ports                               [Female DB-9]   [Male DB-9]     [Male DB-15]
                                                 Mouse           Desk PC/        Host
                                                                 Workstation     
```
---
### Models:

* G80-9009HAU
* G80-9009HAG - Youtube Video
* G80-9039HAAUS
* G80-9035 - comment on youtube review

---

### Key use groups
It seems to me that keys on this keyboard fall into 3 groups:

1. "Normal keys" When struck their keycode is sent out the "Desk PC /
Workstation" port. These are A-Z, 0-9, punctuation, etc. Normal keyboard
operation. 

2. Keys sent to control the keyboard modes itself. "Cacl" puts the keyboard into
calculator mode (Likely exits the calc mode too) and "SetUp" lets you define
macros, etc. These will never generate scan codes out the "Desk PC /
Workstation" port, they are handled within the keyboard itself.

3. "KVM" keys that control the switch boxes themselves. For example "Scrn 4" to
change display to Screen 4. Also "Desk PC" and "Wkst" to select at least which
computer to attach the keyboard to. Probable which screen got displayed too.
These will send signals (I have no ideas which) out the "Host" port. These will
also never generate scan codes out the "Desk PC / Workstation" port.

So it looks like of the 149 keys on the keyboard, all but the cluster of 8 at
the top-right could be available. It's also possible that the F1-F24 don't send 
scan codes directly, but only play back your pre-programmed keyboard macros.
TODO: To be determined.

A description of [Display Functions](../master/display-functions.md "Display Functions documentation") available on the G80-9009 keyboard.  

---
### Videos:

* Chyrosran22's [Cherry G80-9009 HAG
Review](https://www.youtube.com/watch?v=N8FXw_QelQc) Published on Feb 28, 2016.
A detailed overview of the keyboard, but with little about the operation. His
keyboard was never powered up.

    
### Photos:

* Total teardown article with photos, [here](https://tieba.baidu.com/p/3742466012?red_tag=3259945445)
* Deskthority: Reuters Battlecruiser (Cherry G80-9009HAU) Great *overview* set of photos,
all angles. [Photos](https://deskthority.net/photos-f62/reuters-battlecruiser-cherry-g80-9009hau-t753.html)
* Same photos also here (tieba.baidu.com): [Photos](http://tieba.baidu.com/photo/p?kw=%E6%9C%BA%E6%A2%B0%E9%94%AE%E7%9B%98%E4%B9%8B%E5%AE%B6&flux=1&tid=3742466012)
* More photos some of the PCB. [Photos](http://www.kbdmania.net/xe/photo/7635809)

### Disassembly and Yang's development:
* *yangdigi's* early controller development with [Photos](http://tieba.baidu.com/p/4489516023)
* Only four more photos including a Breakout Box in the original keyboard box: [Photos](https://www.wstx.com/p-15490)

---
## Available Modifications

Vineshroom (Youtube name) You can make MX Clear switches feel a whole lot more
tactile by swapping the springs with Cherry MX Black springs. These are
currently one of my favorite switches. I find them to be very similar to Black
Alps, but they're more consistent and snappy than Black Alps IMO.

## Places to search for keyboards

### Terms:
* Soarer PS/2 USB converter

### Web sites:
Add List of urls to be used for searching for sale items

| Where | Notes |  |
| ------------------ | ---------------- | --------- |
| [eBay.com](eBay.com)  | Soarer PS/2 USB converter, and others      |
| [item.taobao.com](item.taobao.com)      | | |
| [world.taobao.com](world.taobao.com)     | | |
| [www.taodepot.com](www.taodepot.com)  |  Min Order Quantity: 10   | China |
| [www.hxlstore.com](www.hxlstore.com)  |  (https://www.hxlstore.com/buy-g80-9009.html)   |    | China |
| [https://shop35553647.taobao.com](https://shop35553647.taobao.com)  |  Yang store, for Yang controller. | click on "shop positive stuff" in upper left   |


