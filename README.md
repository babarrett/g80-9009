## g80-9009
Cherry built keyboard, G80-9009. For Reuters. 149 keys. LCD display. Create macros on
the fly. From the 1990's. Model number AK 124


---
## Connection Methods

Let's start with what I presume everyone cares most about. "How to I connect this to my computer?"

As near as I can tell there are three ways:

1. Yangdigi's [controller card](../master/method-1-yangdigi-controller.md "Yangdigi controller instructions")
    - A "drop in" solution
    - Might still require a 12V power connection to the keyboard
    - Ends up with a USB connection. No need for a further PS/2 to USB converter
    - Includes a Pro Micro running TMK software
2. [Directly](../master/method-2-direct.md  ) from the "Desk PC/Workstation" connector to a PS/2 connector
    - Very few parts, essentially one DB-9 to PS/2 cable
    - Might still require a 12V power connection to the keyboard
    - Requires a PS/2 to USB adapter if you want USB
3. With (rare) [Breakout boxes](../master/method-3-keyboard-to-breakout-box.md)
    - aa
    - bb

---
## Specifications

### Switches
* MX Clear switches, 149 of them. 
* High force at end of stroke to discourage bottoming out.
* Diode soldered into every switch.


### Caps:
Most are Double-shot ABS. "Super thick."

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
* Lower (main 09 keys) are PCB mounted
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
### Physical Specs:

* 2.4Kg, 4Kg shipping weight
* Width
* Height
* Depth
* 12V 500mA = 6W on the label on the bottom but 5v ??mA powered by Yang's USB.
* Shipping weight ~ 2570g
* Shipping dimensions: 54.6 * 30.8 * 9.2 cm


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


### KVM Boxes:

* KMD-3		https://geekhack.org/index.php?topic=36702.0
* Reuters Breakout Box

---
## Attrubutes



### Built-in functions

* Macros up to 80 characters
* Has calculator mode with memory, sqrt(), percent, etc.


### LCD:

* Displays "IBM PS/2" at some point.

### Connections

* Serial communications takes place across both connectors. The host can assert control at any time. 
* DB9 -> PS/2 PIN pin corresponds to:
    * 1-> 4,
    * 7-> 3,
    * 8-> 1,
    * 9-> 5.  
* Breakout box.

### Videos:

* Review: https://www.youtube.com/watch?v=N8FXw_QelQc
* Working G80-9009HAU to Windows pad (Surface?) key test and typing. Uses yangdigi controller. https://v.qq.com/x/page/v019406oqmc.html
* Demo of Yang cobnversion? https://www.xiaobaiban.net/video/play-JESdXA5_2B0eZvfsKGvp6tqRccTMcF3jPN.htm
* Quick demo, types on computer. Includes Set-up and macro definition. Cherry G80-9039HAAUS / Reuters AK124. https://www.youtube.com/watch?v=r_-dMFUNv-k
    
### Photos:

* Same photos also here: http://tieba.baidu.com/photo/p?kw=%E6%9C%BA%E6%A2%B0%E9%94%AE%E7%9B%98%E4%B9%8B%E5%AE%B6&flux=1&tid=3742466012
* Deskthority: Reuters Battlecruiser (Cherry G80-9009HAU) https://deskthority.net/photos-f62/reuters-battlecruiser-cherry-g80-9009hau-t753.html

### Disassembly and Yang's development:
* Geekhack, Easy AVR USB Keyboard Firmware and Keymapper. Actually the start of *yangdigi's* Pro Micro and mux: https://geekhack.org/index.php?topic=51252.msg2140927#msg2140927
* More on *yangdigi's* controller development? with photos. http://tieba.baidu.com/p/4489516023
* More photos with disassembly: http://www.kbdmania.net/xe/photo/7635809
* Huge teardown article with photos, here: https://tieba.baidu.com/p/3742466012?red_tag=3259945445
* More disassembly, with Breakout Box: https://www.wstx.com/p-15490
* Connecting up a G80-9009. Includes Breakout Box and pinouts for PS/2. https://www.ptt.cc/bbs/Key_Mou_Pad/M.1499538853.A.F7F.html

### Other Links: For Sale

* https://www.hxlstore.com/buy-g80-9009.html
* https://world.taobao.com/item/12254371144.htm
* $111.11 each, Min. order 10: http://www.taodepot.com/item/13621819071
* $130.49 + $8 https://www.hxlstore.com/13080915768.shtml ; https://www.hxlstore.com/buy-g80-9009.html ; $76 - $130
* Purchasing: Search google for: G80-9009HAU site=world.taobao.com
    * Controllers (3 sellers) in mainland China
    * https://world.taobao.com/item/550082036900.htm?fromSite=main&spm=a230r.1.14.19.7a40d2157HVjcO&ns=1&abbucket=18#detail
    * ¥238 = $36.16
    * Keyboard: https://world.taobao.com/item/35486837384.htm?fromSite=main&spm=a230r.1.14.31.7a40d2157HVjcO&ns=1&abbucket=18#detail
    * ¥328 = $49.59

---
## Available Modifications

Vineshroom (Youtube name) You can make MX Clear switches feel a whole lot more
tactile by swapping the springs with Cherry MX Black springs. These are
currently one of my favorite switches. I find them to be very similar to Black
Alps, but they're more consistent and snappy than Black Alps IMO.

---
from Chyros youtube review:    https://www.youtube.com/watch?v=N8FXw_QelQc

Meow Wei -- 2 months ago (edited)
I have one [G80-9009] currently in use (with original setup, kmd3 box).

You need to use a 12v 500mA adapter which converts to 15-pin D connector (I have
an original adapter so I don't know what the pins are), and a cable from 9-pin D
connector to PS/2. If anyone of you have this keyboard and interested I may
write a documentation on this keyboard.

The kmd3 or adapter box is not necessary. But if you have one, you can switch
keyboard and mouse input between 2 computers on the keyboard.﻿

### Keyboard direct to PS/2, Modification #3

In the comments of the Chyrosran22 Youtube review. https://www.youtube.com/watch?v=N8FXw_QelQc

---

### Sources/reference material

* https://geekhack.org/index.php?topic=51252.1650
