# Cherry G80-9009 / Reuters AK124 Keyboard

Cherry built keyboard, G80-9009, and similar model numbers for Reuters. The
Reuters model numbers are AK124 (common) and AK125 (latest, but uncommon.)

The variations in model numbers seem to reflect some specialized key labeling,
some language variation, and finally technology. I have seen photos of a
G8-9039HAAUS that is all surface mount technology.

Additional details are available:

1.  [Operations](../master/operations.md "Operations"): The keyboard features and
how to operate them.
2.  [Breakoutbox decoded](../master/breakoutbox-decoded.md "Breakoutbox decoded"):
"Dissecting" and examining an AK125 Breakout Box to determine it's functionality
and by extension the way the keyboard functions.
3.  [Making Cables](../master/making-cables.md "Making Cables"): How to make the
needed cables to connect the keyboard to computers via PS/2, RS232 serial, or
Sun serial protocols.

### Presumption:
Reuters is an old and current leading newswire service.
All of the specialized keys are for trading functions.
(Open Orders, Cancel orders, Bid, Offer, Change)

What do traders need? Financial markets move on news. Clearly they need a portal
into the trading system (or network) and they need access to up to date news. So
then, the "workstation" port is for the trading and the "PC" port is for the
news.

The keyboard is designed to work with a multi-connector "Breakout BOX" models
AK124 and AK125. The keyboard contains built-in circuitry, which in conjunction
with the Breakout Box forms a KM (Keyboard/Mouse) switch. Two keys in the
upper-right (Desk PC, Wkst) allow the trader to switch the keyboard and mouse
from the desktop PC to Workstation, and back.

It:

* Was available from about 1995 to 2005. I have seen REUTERS logos created in
1965 (the "dot" wordmark) and in 1996 the rounded piece – or roundel – was
developed. 1999 the dots in the name gave way to a solid all-caps font with an
orange dotted semi-circle, and a solid blue semicircle.
* has 149 total keys. Not all generate scan codes when in "Desk PC" mode.
* has a, primarily text, 100 x 584 pixel LCD display with 2 font sizes.
* can create up to 72 macros on the fly that are stored in the keyboard.
* can select any 1 of 4 screens (Indicated by keys, unverified. Mechanism reportedly
as being "a Reuters ISA four monitor graphics card" that aparently goes into the
rectangular space in the bottom of the keyboard.)
* can select any 1 of 2 workstations with a "Breakout Box"
* can use three different keyboard protocols. PS/2, RS232 Serial, and Sun serial.
Sun serial is an inverted version of RS232 serial. I've heard that "Workstation mode"
sends scan codes for almost all keys via 9600 bit/sec serial port. Sun's documentation
in 2000 says:

    The keyboard communicates with the system using asynchronous serial
    protocol with negative logic. The communication is full duplex at 1200 baud. The
    data has 1 start bit, 8 data bits, 1 stop bit and no parity.

* can, aparently, use three different mouse protocols (unverified). PS/2, RS232 Serial, and Sun serial.
* is supported by a third-party kmd3 switch as well
* can be emulated by the Wey Tec HK2000C keyboard.
* can perform calculations within the keyboard, displaying the results on the
LCD display

---
**CAUTION!** Not everything in here has been verified, and even if it has been
verified your keyboard and revision could be different. The voltages are all, as
far as I know, low 5V and 12V. It seems to me very unlikely that these voltages
will harm you, but reversing + and - could destroy some of your electronics.

Special thanks to mwei (Geekhack name) (Meow Wei, Youtube name). Without his
help much of my success would have been impossible. ALso, special thanks to
varszegimarcell (Geekhack name) for his additional assistance decoding the
breakout box.

---
## Connection Methods

Let's start with what I presume everyone cares most about. "How to I connect
this to my computer?"

As near as I can tell there are three or four ways and one variation for connecting this
keyboard to a modern computer:

1. Yangdigi's [controller card](../master/method-1-yangdigi-controller.md "Yangdigi controller instructions")
    - A "drop in" solution
    - Ends up with a USB connection. No need for a further PS/2 to USB converter
    - Requires a USB to USB Mini-5 (5 pin) cable
    - Includes a Pro Micro (equivalent), running TMK software, allowing the
    mapping of all 149 keys. This includes special "workstation" keys that do
    not generate scancodes in "normal" use, and all keys that work in
    "Workstation" mode, but not in the "Desk PC" mode.
    - Gets power from the USB connector. Does not require a 12V power connection
    to the keyboard.
    - Requires disassembly of your keyboard case.
    - This is a good solution for getting up-and-running quickly, without much
    thinking or assembly required. A known solution. Very useful if some part of
    your keyboard's internals (other than the key matrixes) has failed. Unless
    the LCD display being operational was a significant motivation for acquiring
    this keyboard, this is likely your best and easiest choice.
    - The biggest disadvantage is that these controllers are now **very** scarse,
    hard to come by.
2. [Direct](../master/method-2-direct.md  ) from the "Desk PC/Workstation"
    connector to a PS/2 connector
    - Very few parts, essentially one custom built DB-9 to PS/2 cable and
    - a 12V power-supply and connection to the keyboard (host port, DB-15)
    - Uses a passive PS/2 to USB adapter to get to USB, if needed.
    - Special "workstation" keys do not generate scancodes.
    - Fairly inexpensive solution.
    - A good solution for getting a keyboard with working display functions,
    while the keyboard itself is not programable and you cannot control the
    keymap. If the LCD display being operational was a significant motivation
    for acquiring this keyboard, and having the whole keymap and layers be
    programable is unimportant, this is likely your best choice.
    - The "PC Desk" setting does not send scan codes for 35 keys, and only sends
    keyboard programmed macros for F13-F24. I've assigned these to Shft+F1
    through Shift+f12. I then use host-side software to take action on these keys.s
    - It is presumed that using the Wkst setting will cause the additional keys
    to send scan codes, but the additional wiring and other needs for this are
    unknown.
3. [Direct+Soarer](../master/method-3-direct+soarer.md  ) from the "Desk
    PC/Workstation" connector to a PS/2 connector.
    This is like the "Direct," plus using the Soarer converter for layers and key mapping.
    - Few parts, essentially one custom built DB-9 to PS/2 cable and
    - a 12V power connection to the keyboard (host port, DB-15)
    - Uses an active Soarer PS/2 to USB converter. The Soarer adds the
    ability to remap keys, add macros, add additional function layers, and be
    able to toggle different layouts.
    - The "PC Desk" setting does not send scan codes for 35 keys, and only sends
    keyboard programmed macros for F13-F24.
    - Special "workstation" keys do not generate scan codes with the "Desk PC"
    setting and we do not yet know how to get that to happen. Perhaps using the
    "Sun" Soarer converter, and reconfiguring the keyboard and adapter wiring
    will start supporting the additional "Workstation" keys. TBD
   - A good solution for getting everything you're likely to want out of the
    keyboard except using every key: working display functions, with in-keyboard
    programmability and keymap re-writing. If the LCD display being operational
    was a significant motivation for acquiring this keyboard, and you want it to
    be programable too, this is likely your best choice.
4. With (rare) [keyboard and mouse switch](../master/method-4-keyboard-to-breakout-box.md) boxes
    - These are KM switches (keyboard and mouse)
    - Special "Desk PC" and "Wkst" keys select the type of computer to talk to.
    The attached KM box will output three different protocols for the Wkst
    computer.
    - Reuters Breakout Box
    - kdm3 (keyboard, display and mouse)
    - See [Breakoutbox decoded](../master/breakoutbox-decoded.md "Breakoutbox
    decoded") for much more information.
5. With new, replacement, breakout box.
    This is currently under development, but I now believe is possible to achieve. The AK125
    breakout boxes are, electrically, very simple. One 5V regulator, one inverter DIP chip, a
    couple capacitors, traces and connectors. Plus a 12VDC power supply.

## Method vs features

| Feature                      | Controller | Direct | Direct+Soarer | KVM  |
| ---------------------------- |:----------:| :-----:| :------------:| :---:|
| Maps all 149 keys            | y | n(102) | n(102) | y? |
| Display functions work       | n | y | y | y |
| Req. hand-made power to Host | n | y | y | n |
| Lock LEDs work               | n | y* | y? | y? |
| Requires "rare" KM box       | n | n | n | y |

\* Caps lock and Scroll lock can be set by the computer. Num Lock is controlled by the keyboard.


---
## Costs for Keyboard and parts to assemble

This is one datapoint, based upon my experience.

| Item                            |   Price | Controller | Direct | Direct+Soarer | KVM  |
| ------------------------------- |--------:|:----------:| :-----:| :------------:| :---:|
| G80-9009 Keyboard*              | $111.01 |    Y       |  Y     |     Y         |  Y   |
| Yang Controller*                |  $57.25 |    Y       |        |               |      |
| PS/2 cable, 6' Male to Male     |   $3.62 |            |  Y     |     Y         |      |
| 12VDC/500mA, Jameco             |  $11.95 |            |  Y     |     Y         |  Y   |
| DB-15 extension cable, 6'       |   $5.95 |            |  Y     |     Y         |  Y   |
| DB-9, Female,SOLDER CUP 22AWG   |   $0.85 |            |  Y     |     Y         |  Y   |
| DB-9, Hood, metalized           |   $0.85 |            |  Y     |     Y         |  Y   |
| PS/2 to USB Soarer's Converter  |  $39.99 |            |        |     Y         |      |
| KM box                          |       † |            |        |               |  Y   |
| TOTALS                          |         |   $168.26  | $134.23 |   $170.60    | $130.61† |

\* International shipping from China allocated among these two items.

† Does not include the price of the KVM box, if available.

---
## Physical Attributes

### Physical Specifications:

* Shipping weight ~ 2570g
* Shipping dimensions: 54.6 * 30.8 * 9.2 cm
* 2.4Kg, 4Kg shipping weight
* Width: 20"
* Height: 3-1/4"
* Depth: 10"
* 12V 500mA = 6W on the label on the bottom, but Meow Wei (Youtube) found 12V
(12.6V measured), 2.5A. I have powered mine, successfully so far, with 12V at 500ma.

### Host port pins, for power

If you choose either option 2 (Direct) or 3 (Direct + Soarer) you'll need to
provide power to the keyboard via the DB-15 "Host" port on the back of the
keyboard.

See [Making Cables](../master/making-cables.md "Cable making instructions")


### Desk PC/Workstation pins

If you choose either option 2 (Direct) or 3 (Direct + Soarer) you'll need to
connect the keyboard via the DB-9 "Desk PC/Workstation" port on the back of the
keyboard to a PS/2 connector.

See [Making Cables](../master/making-cables.md "Cable making instructions")

Note: There are some additional signals on the pins on the Desk PC/Workstation
connector that map to the Workstation connectors on the Breakout Box. These map
to the three different protocols supported by the keyboard and box: PS/2, RS232
serial, and Sun serial. I still haven't figured out what enables these signals,
still working on that. Quite possibly it's PC and Workstation keys on the keyboard.

See [Breakout Box Decoded](../master/breakoutbox-decoded.md "Breakout Box
Decoded") for more.

### Switches

* MX Clear switches, 149 of them.
* High force at end of stroke to discourage bottoming out.
* Diode soldered into every switch.
* Some switches are very stiff, especially:
    - Interrupt
    - Contact
    - Accept
    - ABBR
    - Deal
    - Cancel Orders
* There are no "home row" bumps on the F or J keys.

### Caps:

Most are Double-shot ABS. "Super thick." TODO: measure once in hand

* The 11 caps with (LED) windows are pad-printed.
    * Caps Lock
    * Scroll Lock
    * Num Lock
    * (4) Scrn 1-4
    * Desk PC
    * Wkst
    * Calc
    * Setup
* There are 2 more LEDs adjacent to the space bar, but no windows to shine through.
* 10u space bar.
* In spite of the odd bottom row with the extended spacebar, and stepped Caps
Lock, pretty much everything will fit on a modern board.
* There are some key caps that vary by locale:


    | Country  | Top-left | Shift-2 | Shift-3 | Near return  | Near shift |
    | -------- |:--------:| :------:| :------:| :-----------:| :---------:|
    | USA      | `, ~     | @       | #       | ', " and \\, \| | "blank" |
    | UK       | `, ¬, \| | "       | £       | ', @ and #, ~ | \\, \|    |


### Case:

* Top (51) keys are plate mounted
* Lower (main 98 keys) are PCB mounted
* The lower PCB is dropped into the case, held in place left/right and
  top/bottom by plastic molding. There are no bolts, screws, or rivits.
* Flip-out feet on bottom, at back. Single position. TODO: how high?
* There is an "Expansion module" area accessable from the bottom of the keyboard.
    * I've seen one reference to a "Reuters ISA four monitor graphics card." I presume it goes into
    this area. I've never seen one though. If that's what goes here then the keyboard becomes a
    complete KVM switch system with the screen buttons controlling these.
    * It is under the rectangular plate on the bottom (4 screws)
    * The space is 4.75" across, 3.25" front to back, 0.75" deep.
    * There are 4 plastic standoffs, as though to support a small PCB within the module area.
    * Within it is a 25 x 2 pin ribbon cable, normal 0.1" centers, one end connected to the keyboard PCB.
    * There's removable back pannel plate is 2.5" wide and 0.75" high,
    intended for the expansion module access. (Covering a hole that is a bit
    smaller.)
    * This would make a nice space for a custom controller board, if we needed one.
* Although the back of the keyboard slopes inward toward the top, the connectors
are parallel to the desk (base), so they are at an angle to the back.
* The Reset button acts like a temporary power Off/On cycle.
* Back of keyboard, left to right has the following: [Photos from imgur](http://i.imgur.com/lwkKiGb.jpg)
```
        [Grill]    [Knob]   [Knob]      [button]
        Buzzer     Volume   Contrast    Reset

        Then, 3 ports                               [Female DB-9]   [Male DB-9]     [Male DB-15]
                                                     Mouse           Desk PC/        Host
                                                                     Workstation
```

TODO: Verify

The mouse port accepts a PS/2 mouse signal in from the Brekout box. The keyboard
logic then figures out where the mouse output needs to be directed (which of the
four sets of ports) and sends the needed signals:

    * back out the mouse connector to the Breakout box for the PS/2 signals:
    Desk-PC-Mouse and Workstation-Generic, or
    * out the AK125-Desk-PC-Workstation for the RS232 and Sun serial signals:
    Workstation-Sun and Workstation-PC-Mouse.
---
### Models:

* G80-9009HAU
* G80-9009HAG - Youtube Video
* G80-9039HAAUS - Newer, SMT PCBs. AK125
* G80-9035 - comment on youtube review

---

### Key use groups

It seems to me that keys on this keyboard fall into 4 groups:

1. "Normal keys" When struck their keycode is sent out the "Desk PC /
Workstation" DB-9 port as PS/2 protocol. These are A-Z, 0-9, punctuation, etc.
Normal keyboard operation. Also includes modifiers like Shift, Command (Mac),
and Control. F1-F12 are also in this group and Print Scrn, Scroll Lock, and Pause
are mapped to F13-F15, on Macintoshes.

2. Keys sent to control the keyboard modes itself. "Calc" puts the keyboard into
calculator mode (Use Desk PC or Wkst to exit calc mode) and "SetUp" lets you define
macros, etc. These will never generate scan codes out the "Desk PC /
Workstation" or "Host" ports, they are handled within the keyboard itself.

3. "KVM" keys that control the switch boxes themselves. For example "Scrn 4" to
change display to Screen 4. Also "Desk PC" and "Wkst" to select at least which
computer to attach the keyboard to. (TODO: unverified) They may also change
which screen gets displayed. These may work in a couple different ways: (Unknown which.)
    * Send some form of signal out the "Host" port on the keyboard to the KM box.
    This could be done by changing the Host pins. Maybe by setting them high or low.
    * For the screen/monitor selection it seems the kbd PCB controls the video
    card, selecting which monitor input goes to the to video out. (Assumed, not verified.)
These will also never generate scan codes out the "Desk PC / Workstation" port.

4. It looks like ABBR is another case we know little about. If the workstations
come with special "workstation" functions that are activated by keys not found
on "normal" keyboards. So pressing ABBR may get passed through the breakout
box to the Workstation port, but never to the "Desk PC / Workstation" port.
There may be other keys that behave this way.

Most colored keys don't generate scan codes with the Desk PC setting. It
looks like of the 149 keys on the keyboard, **most** except the cluster of 8 at
the top-right could be available with the Wkst setting. It's also possible that
the F13-F24 don't send scan codes directly, but only play back your
pre-programmed keyboard macros.

A description of [Display Functions](../master/display-functions.md "Display Functions documentation")
available on the G80-9009 keyboard.

---
### Remaining open questions:

1. Are the Yang controllers still generally available? Where?
2. What are the non-power, non-ground pins on the Host connector used for? What protocol?
3. Which keys will still not be sent out the "Desk PC / Workstation" port when
using the "Direct" method and Wkst setting?
4. What triggers the buzzer? Bad Calc keys, bad macro definition keys, others?
5. Do the LEDs work without a KM box? Yes for Caps, Scroll, and Num with "direct" method.


---
### Videos:

* Chyrosran22's [Cherry G80-9009 HAG
Review](https://www.youtube.com/watch?v=N8FXw_QelQc) Published on Feb 28, 2016.
A detailed overview of the keyboard, but with little about the operation. His
keyboard was never powered up.
* Chyrosran22's [Cherry G80-9009 review Redux, Cherry MX Clear](https://www.youtube.com/watch?v=lUVVxrL6VGU)
Published on Sep 6, 2019. Working keyboard with Breakout Box and keyboard AK125.


### Photos:

* Total teardown article with photos, [here](https://tieba.baidu.com/p/3742466012?red_tag=3259945445)
* Deskthority: Reuters Battlecruiser (Cherry G80-9009HAU) Great *overview* set of photos,
all angles. [Photos](https://deskthority.net/photos-f62/reuters-battlecruiser-cherry-g80-9009hau-t753.html)
* Same photos also here (tieba.baidu.com): [Photos](http://tieba.baidu.com/photo/p?kw=%E6%9C%BA%E6%A2%B0%E9%94%AE%E7%9B%98%E4%B9%8B%E5%AE%B6&flux=1&tid=3742466012)
* More photos some of the PCB. [Photos](http://www.kbdmania.net/xe/photo/7635809)

### Disassembly and Yang's development:
* *yangdigi's* early controller development with [Photos](http://tieba.baidu.com/p/4489516023) All in Japanese.
* Only four more photos including a Breakout Box in the original keyboard box: [Photos](https://www.wstx.com/p-15490)

---
## Available Modifications

Vineshroom (Youtube name) You can make MX Clear switches feel a whole lot more
tactile by swapping the springs with Cherry MX Black springs. These are
currently one of my favorite switches. I find them to be very similar to Black
Alps, but they're more consistent and snappy than Black Alps IMO.


### Terms:
* Soarer PS/2 USB converter -- For sale on Amazon: https://www.ebay.com/itm/282575686221
* Hasu PS/2 to USB converted (I haven't tried) -- https://geekhack.org/index.php?topic=72052.msg1751398

## Places to search for keyboards

Add List of urls to be used for searching for sale items

| Where | Notes |  |
| ------------------ | ---------------- | --------- |
| [eBay.com](https://eBay.com)  | Soarer PS/2 USB converter, and others      |
| [item.taobao.com](https://item.taobao.com/item.htm?spm=a230r.1.14.325.THFAVS&id=13621819071)      | Still available Nov 2019| China |
| [world.taobao.com](https://world.taobao.com)     | | |
| [www.taodepot.com](https://www.taodepot.com)  |  Min Order Quantity: 10   | China |
| [www.hxlstore.com](https://www.hxlstore.com)  |  (https://www.hxlstore.com/buy-g80-9009.html)   |    | China |
| [https://shop35553647.taobao.com](https://shop35553647.taobao.com)  |  Yang store, for Yang controller. | click on "shop positive stuff" in upper left   |


