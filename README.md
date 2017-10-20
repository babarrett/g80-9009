# g80-9009
Cherry built keyboard, G80-9009, and similar model numbers, for Reuters. 
The Reuters model number is AK124. 

Presumption:
Reuters is an old and a leading newswire service.
All of the specialized keys are for trading functions.
(Open Orders, Cancel orders, Bid, Offer, Change)

What do traders need? Financial markets move on news. Clearly they a portal into
the trading system (or network) and they need access to up to date news. So
then, the "workstation" is for the trading and the "PC" is for the news.

Two keys in the upper-right (Desk PC, Wkst) allow the trader to switch the
keyboard from the desktop PC to Workstation, and back.

It:

* Was available in the 1990's. I have seen REUTERS logos created in 1965 (the
"dot" wordmark) and in 1996 the rounded piece – or roundel – was developed. 1999
the dots in the name gave way to a solid all-caps font, followed by an orange
dotted semi-circle, and a solid blue semicircle.
* has 149 available keys
* has a, primarily text, LCD display
* can create macros on the fly that are stored in the keyboard. 
* can select any 1 of 4 screens
* can select any 1 of 2 workstations with a kmd3, or 4(?) for a "Breakout Box"
* can perform calculations within the keyboard, displaying the results on the LCD display


---
## Connection Methods

Let's start with what I presume everyone cares most about. "How to I connect
this to my computer?"

As near as I can tell there are three ways and one variation for connecting this
keyboard to a modern computer:

1. Yangdigi's [controller card](../master/method-1-yangdigi-controller.md "Yangdigi controller instructions")
    - A "drop in" solution
    - Ends up with a USB connection. No need for a further PS/2 to USB converter
    - Includes a Pro Micro, running TMK software, allowing the mapping of all 149 keys.
    - Probably does not, but still might, require a 12V power connection to the keyboard
    - A good solution for getting up-and-running quickly, without much thinking
    or assembly required. A known solution. Unless the LCD display being
    operational was a significant motivation for acquiring this keyboard, this is
    likely your best choice.
2. [Directly](../master/method-2-direct.md  ) from the "Desk PC/Workstation" connector to a PS/2 connector
    - Very few parts, essentially one DB-9 to PS/2 cable
    - Likely requires a 12V power connection to the keyboard (host port)
    - Uses a passive PS/2 to USB adapter
3. [Direct+Soarer](../master/method-3-direct+soarer.md  ) from the "Desk PC/Workstation" connector to a PS/2 connector
    - Requires one DB-9 to PS/2 cable
    - Likely requires a 12V power connection to the keyboard (host port)
    - Uses an active Soarer PS/2 to USB converter. The Soarer adds the
    ability to remap keys, add macros, add additional function layers, and be
    able to toggle different layouts 
4. With (rare) [KVM](../master/method-4-keyboard-to-breakout-box.md) boxes
    - These are KVM switches (keyboard, video and mouse)
    - kdm3 (keyboard, display and mouse)
    - Reuters Breakout Box

## Method vs features  

| Feature                      | Controller | Direct | Direct+Soarer | KVM  |
| ---------------------------- |:----------:| :-----:| :------------:| :---:|
| Maps all 149 keys            | y | n | n | n |
| Display functions work       | n | y | y | y |
| Req. hand-made power on Host | n | y | y | n |
| Support kbd-only switching   | n | n | n | y |
| Lock LEDs work               | n? | y | n? | y? |
| Requires "rare" KVM box      | n | n | n | y |

---
## Physical Attributes

### Physical Specifications:

* Shipping weight ~ 2570g
* Shipping dimensions: 54.6 * 30.8 * 9.2 cm
* 2.4Kg, 4Kg shipping weight
* Width
* Height
* Depth
* 12V 500mA = 6W on the label on the bottom but 5v ??mA powered by Yang's USB.

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
    * (4) Scrn1-4
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
* Under the rectangulat plate on the bottom (4 screws) is a 27 x 2 pin ribbon cable, not connected. For expansion modual?
* Back of keyboard, left to right has the following: http://i.imgur.com/lwkKiGb.jpg
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

### Serial numbers

I've seen, sorted: (They don't seem to have manufacture dates.)

* G 000410   H30	G80-9009HAG / 02    ~$127/ea. 10 minimum
            Yours & Mine keys, and 1/8 on num pad
* G 000707   P51    G80-9039HAAUS / 07  https://www.ptt.cc/bbs/Key_Mou_Pad/M.1499538853.A.F7F.html
            With Yours & Mine keys. #/3
* G 000883   R31    G80-9039HAAUS / 07  $71 https://world.taobao.com/item/531556526722.htm
* G 000780   H22	G80-9009HAU / 02	PCB Rev.05; Built March '95?
			With Zone + FMT... & 1/8
* G 002033   K33	G80-9009HAG / 10    Yangdigi owns, in instructions for controller
* G 002191   K33?	G80-9009HAU / 04?

* G 002439   M48	G80-9009HAG / 11	MX Clear switches
			Yours & Mine keys, no 1/8 on num pad
* G 003367   I21	G80-9009HAU / 07
* G 004796   J08	G80-9009HAU / 09
			With Zone + FMT on Yours and Mine keys & 1/8 on num pad
* G 007037   K02    G80-9009HAU / 10    
Mentioned in this thread: Easy AVR USB Keyboard Firmware and Keymapper (Nov 2013-Oct 2017+)
++ * G 008113   K37    G80-9009HAU / 10    https://world.taobao.com/item/13080915768.htm
			With Zone + FMT on Yours and Mine keys & 1/8 on num pad
            $74 @ https://world.taobao.com; $134 @ https://www.hxlstore.com/13080915768.shtml


---

### Built-in functions

* Macros up to 80 characters
* Has calculator mode with memory, sqrt(), percent, etc.


### LCD:

* Displays "IBM PS/2" at some point.

### Videos:

* Chyrosran22's Cherry G80-9009 HAG Review Published on Feb 28, 2016. A detailed
overview of the keyboard, but with little about the operation:
https://www.youtube.com/watch?v=N8FXw_QelQc

    
### Photos:

* Total teardown article with photos, here: https://tieba.baidu.com/p/3742466012?red_tag=3259945445
* Deskthority: Reuters Battlecruiser (Cherry G80-9009HAU) Great *overview* set of photos,
all angles. https://deskthority.net/photos-f62/reuters-battlecruiser-cherry-g80-9009hau-t753.html
* Same photos also here: http://tieba.baidu.com/photo/p?kw=%E6%9C%BA%E6%A2%B0%E9%94%AE%E7%9B%98%E4%B9%8B%E5%AE%B6&flux=1&tid=3742466012
* More photos some of PCB: http://www.kbdmania.net/xe/photo/7635809

### Disassembly and Yang's development:
* *yangdigi's* early controller development with photos. http://tieba.baidu.com/p/4489516023
* Only four more photos including a Breakout Box in the original keyboard box: https://www.wstx.com/p-15490

---
## Available Modifications

Vineshroom (Youtube name) You can make MX Clear switches feel a whole lot more
tactile by swapping the springs with Cherry MX Black springs. These are
currently one of my favorite switches. I find them to be very similar to Black
Alps, but they're more consistent and snappy than Black Alps IMO.

