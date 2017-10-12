## g80-9009
Cherry keyboard, G80-9009. For Reuters. 149 keys. LCD display. Create macros on the fly. From the 1990's.
AK 124

MX Clear switches, 149 of them. High force at end of stroke to discourage bottoming out.
	Diode soldered into every switch.

###Caps:
Most are Double-shot ABS. "Super thick."

* The ones with (LED) windows are pad-printed.
* 11 "lock lights" + 2 more positions adjacent to the space bar.
* 10u space bar.
* Odd bottom row with the extended spacebar and stepped Caps Lock, pretty much everything will fit on a modern board.

PCB revisions I've seen:

* :02
* 5

###Models:

* G80-9009HAU
* G80-9009HAG - Youtube Video

###Serial numbers

I've seen, alphabetized: (They don't seem to have manufacture dates)

* G 000410   H30	G80-9009HAG / 02
* G 000707   P51    G8009039HAAUS / 07
            With Yours & Mine keys. #/3
* G 000780   H22	G80-9009HAU / 02	PCB Rev.05; Built March '95?
			With Zone + FMT... & 1/8
* G 002191   K33?	G80-9009HAU / 04?

* G 002439   M48	G80-9009HAG / 11	MX Clear switches
			Yours & Mine keys, no 1/8 on num pad
* G 003367   I21	G80-9009HAU / 07
* G 004796   J08	G80-9009HAU / 09
			With Zone + FMT on Yours and Mine keys & 1/8 on num pad
* G 007037   K02    G80-9009HAU / 10    
Mentioned in this thread: Easy AVR USB Keyboard Firmware and Keymapper (Nov 2013-Oct 2017+)
```
        https://geekhack.org/index.php?topic=51252.1650
```

###KVM Boxes:

* KMD-3		https://geekhack.org/index.php?topic=36702.0
* Reuters Breakout Box

---
##Attrubutes

###Physical Specs:

* 2.4Kg
* Width
* Height
* Depth
* 12V 500ma? or 5v?

###Case:

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

###Built-in functions

* Macros up to 80 characters
* Has calculator mode with memory, sqrt(), percent, etc.


###Custom Controller (Yang, yangdigi)

* 2 x 32 pin ribbon cables connect
* keyboard matrix to use/replacate is 16x10
* uses a 4 to 16 mux for the 16 lines (columns?)
* G80-9009HAU has two parts. Upper part is 6x10 and lower is 10x10. 
* Now I am using TMK to run 16x10 matrix. I want to try EasyAVR on it to make it easier to use.

###LCD:

* Displays "IBM PS/2" at some point.

###Connections

* Serial communications takes place across both connectors. The host can assert control at any time. 
* DB9 -> PS/2 PIN pin corresponds to:
    * 1-> 4,
    * 7-> 3,
    * 8-> 1,
    * 9-> 5.  
* Breakout box.
```
    The currently available connection method: (Update: the mouse has been working
    properly) http://i.imgur.com/WrXa1Tl.jpg 

           (Unknown, speculation is
            it is SUN workstations)--- DIN8 ---+                    +------ (4pin 12V power supply)
                                               |                    |
    +------------+                     +---(Work Station-Sun)-----(Power)---+
    |  Reuters   |                     |          Reuters                    |
    |   AK125    |                     |     AK125 Breakout Box              |
    |         (Host) --- DB15 --- (AK125-System)                       (HOST-SYSTEM)--(DB15 can supply power too)
    |            |                     |                                     |      
    |    (Desk PC/WkSt) -- DB9 -- (AK125-Desk-PC-Workstation)                |
    |            |                     |                                     |
    |            |                     |                           (Workstation-Generic)--(DB9
    |        (Mouse) ----- DB9 -- (AK125-Mouse)                              |             unknown)
    |            |                     |                                     |
    |            |                     |                           (Workstation-PC-Mouse)--(DB9)
    +------------+                     |                                     | Then the second machine
                                       |                                     |    mouse PS/2
                                       |                                     |
       (actual mouse,                  |                                     |
        PS/2, sitting  -- PS/2 --- (Mouse IN)                     (Workstation-PC-KBD)----(DB9)
        on the desktop)                |                                     | Then the second machine
                                       |                                     |    Keyboard PS/2
                                       |                                     |
                                       +-(Desk-PC-Mouse)-------(Desk-PC-KBD)-+
                                               |                      |
      Take the first computer    ----- DB9 ----+                      |
         Mouse / keyboard, PS/2  ----------------- DB9 ---------------+
```

###The Yang (yangdigi) controller
New USB controller.

yang.tkg.io - Select English from top-right drop-down.

If you don't know how to use this, please read these first: http://pan.baidu.com/s/1sltOsrV Password: ek5h

Select Keyboard = 80_9009HAU

- Name:       80-9009HAU
- Max layers: 5
- Max Fns:    32
- Firmware:   (empty)

Permalink (KLE) http://kle.ydkb.io/##@_name=G80-9009HAU&author=YANG&notes=tkg%E7%BD%91%E5%9D%80%EF%BC%9Ahttps%2F:%2F%2F%2F%2Fyang.tkg.io%0A%0A%E5%88%B7%E5%9B%BA%E4%BB%B6%E6%95%99%E7%A8%8B%EF%BC%9Ahttp%2F:%2F%2F%2F%2Fpan.baidu.com%2F%2Fs%2F%2F1sltOsrV%20%E5%AF%86%E7%A0%81%2F:%20ek5h%20%0A%E5%A6%82%E4%BD%95%E5%88%B7%E6%9C%BA%E8%AF%B7%E5%8F%82%E8%80%83%20TKG%E5%9C%A8%E7%BA%BF%E5%88%B7%E6%9C%BA%E6%95%99%E7%A8%8Bv3.0.pdf%20%E4%B8%AD%E7%9A%84%E7%AC%AC%E5%9B%9B%E9%83%A8%E5%88%86%EF%BC%8CRAWHID%E5%9C%A8%E7%BA%BF%E5%88%B7%E6%9C%BA%0A%E5%A6%82%E4%BD%95%E5%88%B6%E4%BD%9C%E5%B8%83%E5%B1%80%EF%BC%8C%E4%BC%9A%E5%88%B7GH60%E7%9A%84%E8%AF%9D%E5%A4%A7%E8%87%B4%E6%98%AF%E7%9B%B8%E5%90%8C%E7%9A%84%EF%BC%8C%E4%B8%8D%E4%BC%9A%E5%88%B7%E8%AF%B7%E5%8F%82%E7%9C%8B%20GH60%E7%AD%89%E9%94%AE%E7%9B%98%E4%BD%BF%E7%94%A8KLE%E5%92%8CTKG%E7%BC%96%E8%BE%91%E9%94%AE%E4%BD%8D%E8%AF%B4%E6%98%8Ev2.0.pdf%0A%0A%E4%BD%BF%E7%94%A8RAWHID%E9%9C%80%E8%A6%81%E4%BD%BF%E7%94%A8%E6%B5%8B%E8%AF%95%E7%89%88%E7%9A%84Chrome%20App%EF%BC%8C%E6%96%87%E4%BB%B6%E5%9C%A8%E5%85%B1%E4%BA%AB%E9%87%8C%EF%BC%8Ctkg-chrome-app-0.8beta-rawhid.crx%3B&@_x:19%3B&=vol%20dn&=vol%20up&_x:0.5%3B&=btn3&=btn1&=mouse%20up&=btn2%3B&@_w:2%3B&=ESC&_x:17&w:2%3B&=MUTE&_x:0.5%3B&=F5&=mouse%20left&=mouse%20down&=mouse%20right%3B&@_y:1&w:2%3B&=ESC&_x:0.5%3B&=ESC&_x:0.5%3B&=F1&=F2&=F3&=F4&_x:0.75%3B&=F5&=F6&=F7&=F8&_x:0.75%3B&=F9&=F10&=F11&=F12&_x:0.5&w:2%3B&=PrtSc&=Pause%0ABreak&_x:0.5%3B&=F9&=F10&=F11&=F12%3B&@_w:2%3B&=ESC&_x:0.5%3B&=Esc&_x:0.5%3B&=F1&=F2&=F3&=F4&_x:0.75%3B&=F5&=F6&=F7&=F8&_x:0.75%3B&=F9&=F10&=F11&=F12&_x:0.5%3B&=PrtSc&=Scroll%20Lock&=Pause%0ABreak&_x:0.5&w:2%3B&=vol%20dn&_w:2%3B&=vol%20up%3B&@_y:0.5%3B&=F1&=F2&_x:0.5%3B&=%C2%AC%0A%60&=!%0A1&=%22%0A2&=%C2%A3%0A3&=$%0A4&=%25%0A5&=%5E%0A6&=%2F&%0A7&=*%0A8&=(%0A9&=)%0A0&=%2F_%0A-&=+%0A%2F=&_w:2%3B&=Backspace&_x:0.5%3B&=Insert&=Home&=PgUp&_x:0.5%3B&=Num%20Lock&=%2F%2F&=*&=-%3B&@=F3&=F4&_x:0.5&w:1.5%3B&=Tab&=Q&=W&=E&=R&=T&=Y&=U&=I&=O&=P&=%7B%0A%5B&=%7D%0A%5D&_x:0.25&w:1.25&h:2&w2:1.5&h2:1&x2:-0.25%3B&=Enter&_x:0.5%3B&=Delete&=End&=PgDn&_x:0.5%3B&=7%0AHome&=8%0A%E2%86%91&=9%0APgUp&_h:2%3B&=+%3B&@=F5&=F6&_x:0.5&w:1.75%3B&=Caps%20Lock&=A&=S&=D&=F&=G&=H&=J&=K&=L&=%2F:%0A%2F%3B&=%2F@%0A'&=~%0A%23&_x:5.25%3B&=4%0A%E2%86%90&=5&=6%0A%E2%86%92%3B&@=F7&=F8&_x:0.5&w:1.25%3B&=Shift&=%7C%0A%5C&=Z&=X&=C&=V&=B&=N&=M&=%3C%0A,&=%3E%0A.&=%3F%0A%2F%2F&_w:2.75%3B&=RShift&_x:1.5%3B&=%E2%86%91&_x:1.5%3B&=1%0AEnd&=2%0A%E2%86%93&=3%0APgDn&_h:2%3B&=PEnter%3B&@=F9&=F10&_x:0.5&w:1.5%3B&=Ctrl&=Win&=Alt&_w:8%3B&=Space&=RAlt&=RWin&_w:1.5%3B&=RCtrl&_x:0.5%3B&=%E2%86%90&=%E2%86%93&=%E2%86%92&_x:0.5&w:2%3B&=0%0AIns&=.%0ADel

(3 layers) Copy raw code, paste it back in the page, "Simple"

Download .c and/or .epp file(s)

Burn firmware.

Assembly instructions:

The installation method is as follows.

    Step 1: Remove the screws on the back of the G80-9009, surrounded by the middle
        and the middle one. A few pieces of that square can not twist.
    Step 2: Raise the keyboard shell, notice the upper and lower parts of the
        keyboard, each have a cable connected to the main PCB.
    Step 3: Remove the two cables.
    Step 4: the link to replace the master put up, the previous pin corresponding to
        the host above the hole, slowly installed, do not bend the original needle.
        After loading into the card is also relatively tight, if you want to fix a
        little more fixed, you can PCB on the J4 and J5 marked square pad to welding.
    Step 5: the original two pin re-plug back to the new master, the bottom of the
        keyboard cable need to re-fold the original bend. In addition, when inserted do
        not crooked. Make sure that all the pins are inserted into the corresponding
        holes. USB, then use the miniUSB line, you can use a long line, you can also use
        an extension line.

    The following figure is to use an extension of the line, the external exposed
    that the small head is microUSB connector, plug a microUSB line can be used.
 
    The rest is to set the button, and burn firmware method gh60 almost, with TKG + KLE,
    full keyboard programmable, support multi-layer layout, support special keys. In
    yang.tkg.io inside, select G80-9009HAU, the bottom will have a link to explain
    how to burn firmware.


###Videos:

* Review: https://www.youtube.com/watch?v=N8FXw_QelQc
* Working G80-9009HAU to Windows pad (Surface?) key test and typing. Uses yangdigi controller. https://v.qq.com/x/page/v019406oqmc.html
* Demo of Yang cobnversion? https://www.xiaobaiban.net/video/play-JESdXA5_2B0eZvfsKGvp6tqRccTMcF3jPN.htm
* Quick demo, types on computer. Includes Set-up and macro definition. Cherry G80-9039HAAUS / Reuters AK125. https://www.youtube.com/watch?v=r_-dMFUNv-k
    
###Photos:

* Same photos also here: http://tieba.baidu.com/photo/p?kw=%E6%9C%BA%E6%A2%B0%E9%94%AE%E7%9B%98%E4%B9%8B%E5%AE%B6&flux=1&tid=3742466012
* Deskthority: Reuters Battlecruiser (Cherry G80-9009HAU) https://deskthority.net/photos-f62/reuters-battlecruiser-cherry-g80-9009hau-t753.html

###Disassembly and Yang's development:
* Geekhack, Easy AVR USB Keyboard Firmware and Keymapper. Actually the start of *yangdigi's* Pro Micro and mux: https://geekhack.org/index.php?topic=51252.msg2140927#msg2140927
* More on *yangdigi's* controller development? with photos. http://tieba.baidu.com/p/4489516023
* More photos with disassembly: http://www.kbdmania.net/xe/photo/7635809
* Huge teardown article with photos, here: https://tieba.baidu.com/p/3742466012?red_tag=3259945445
* More disassembly, with Breakout Box: https://www.wstx.com/p-15490
* Connecting up a G80-9009. Includes Breakout Box and pinouts for PS/2. https://www.ptt.cc/bbs/Key_Mou_Pad/M.1499538853.A.F7F.html

###Other Links: For Sale

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
##Connection Methods

1. Yangdigi's controller card
2. With (rare) Breakout boxes
3. Directly

###Connection Method #1, Yangdigi's controller card

(notes)

Re: TKG - TMK Keymap Generator [tkg.io] (no need to compile the firmware)
    https://geekhack.org/index.php?topic=82693.msg2398215#msg2398215

That Pro Micro is a Chinese clone one from taobao. It's 3.3v but 16Mhz quartz.
Pro Micro 3.3v with 8Mhz quartz can work well too.

If your Pro Micro is 8MHz, change F_CPU = 16000000 to F_CPU = 8000000 in Makefile

Having a small issue with this, everything works perfectly as according to this image with the exception of the pipe/backslash key. It performs the same action as #/~ which I have next to my enter key.

* Please write that key in the format according to http://tkg.io/#help

TKG - TMK Keymap Generator [tkg.io] (no need to compile the firmware)
    https://geekhack.org/index.php?topic=82693.msg2192962#msg2192962

Re: TKG - TMK Keymap Generator [tkg.io]
    https://geekhack.org/index.php?topic=82693.msg2192963#msg2192963

G80-9009 "Rat's nest"
    Making Stuff Together! / Re: Easy AVR USB Keyboard Firmware and Keymapper
    https://geekhack.org/index.php?topic=51252.msg2141040#msg2141040

    I use a pro micro and one 74hc154.

---
##Available Modifications
You can make MX Clear switches feel a whole lot more tactile by swapping the
springs with Cherry MX Black springs. These are currently one of my favorite
switches. I find them to be very similar to Black Alps, but they're more
consistent and snappy than Black Alps IMO.

from Chyros youtube review:    https://www.youtube.com/watch?v=N8FXw_QelQc

Meow Wei
2 months ago (edited)
I have one currently in use (with original setup).

You need to use a 12v 500mA adapter which converts to 15-pin D connector (I have
an original adapter so I don't know what the pins are), and a cable from 9-pin D
connector to PS/2. If anyone of you have this keyboard and interested I may
write a documentation on this keyboard.

The kmd3 or adapter box is not necessary. But if you have one, you can switch
keyboard and mouse input between 2 computers on the keyboard.﻿

---
Users with this board:
    Chyros (youtube reviews)
