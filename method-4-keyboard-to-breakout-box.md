## Keyboard to Breakout Box

### There are two "KVM" Boxes:

* KMD-3		https://geekhack.org/index.php?topic=36702.0
* Reuters Breakout Box

### What it is:

* User Anfauglir (Jaws of Thirst) had access to a Reuters Breakout Box
* Here: https://www.ptt.cc/bbs/Key_Mou_Pad/M.1499538853.A.F7F.html
* This keyboard requires a 12V power supply to operate and can be supplied from
the DB-15 HOST connector. (I don't know which pins)
* The usual configuration is: 
    - The Keyboard Desk PC/WorkStation port to KVM
    - The "Host" port to KVM
    - The desktop mouse (PS/2) to the KVM
    - The rest of the connections go from the KVM to the Keyboard, Video, and
    Mouse connectors on the (multiple) attached computers.
* The output keyboard ports on the KVM can be connected, via adapters, to the
(multiple) attached computers.
* DB9 -> PS/2 adapter pinout is, likely (unconfirmed):
    * 1-> 4,
    * 7-> 3,
    * 8-> 1,
    * 9-> 5.  
* Special keys are totally available. 
* Scrn1/2/3/4 keys are usable. 

### Pros:
* Everything works as designed, once you convert the serial keyboard out port(s)
of the KVM to PS/2, and from there USB, if needed.
* Simple solution in terms of hardware, if you can locate the boxes and cables. 
    - Do not have to open the keyboard
    - No special controller needed
* The built in functions, display commands (on the fly macro creation,
calculator) still work.
* The screen, keyboard and mouse switching would work, so you get a 2 or 3
station KVM "for free."

### Cons:

* Almost impossible to find the breakout boxes, and if you do it's likely you
won't find the right cables. (There also seems to be no documentation on the
cable pinouts)
* You have to create a custom cable, which shouldn't be too bad.
* You'll need another converter if you want to get to USB. 
* You'll have to use a Soarer (or similar?) converter if you want to get to USB and programmable. 
An [ebay](http://www.ebay.com/itm/NEW-PS-2-to-USB-Soarers-Converter-Adapter-Remapping-Macros-NKRO-Support-/282575686221) link.

### Unknowns:

* (none)

### Connectors:

```
    The currently available connection method: (Update: the mouse has been working
    properly) http://i.imgur.com/WrXa1Tl.jpg 

           (Unknown, speculation is
            it is SUN workstations)--- DIN8 ---+                    +------ (4pin 12V power supply)
                                               |                    |
    +------------+                     +---(Work Station-Sun)-----(Power)---+
    |  Reuters   |                     |              Reuters                |
    |   AK124    |                     |         AK125 Breakout Box          |
    |            |                     |                                     |
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

TODO: logical diagram

### kmd3

Lots of info available here:
    https://deskthority.net/workshop-f7/looking-for-handyman-to-mod-g80-9009hau-t3931.html
   
Application note, 2006:
    http://www.industrycortex.com/datasheets/profile/1250934827
    
---
From comments after Chyros youtube review:    https://www.youtube.com/watch?v=N8FXw_QelQc

Meow Wei -- 2 months ago (edited)
I have one [G80-9009] currently in use (with original setup, kmd3 box).

You need to use a 12v 500mA adapter which converts to 15-pin D connector (I have
an original adapter so I don't know what the pins are), and a cable from 9-pin D
connector to PS/2. If anyone of you have this keyboard and interested I may
write a documentation on this keyboard.

The kmd3 or adapter box is not necessary. But if you have one, you can switch
keyboard and mouse input between 2 computers on the keyboard.﻿

### Reuters Breakout Box

TODO: links to web page

### Videos

* Using kmd3. Quick demo, types on computer. Includes Set-up and macro definition. 
Cherry G80-9039HAAUS / Reuters AK124. 2 cables coming off the rear: 
    a) 15? pin D connector to another 15 pin D, attached to the keyboard at 
    about the F5 and F6 key area. Also joining that second D connecter is a thick, black cable
    coming from a black "brick". (Power supply??) Labeled with a paper sticker saying 
    "REUTERS EQUIPMENT." This seems likely where the keyboard is being powered from.
    b) Thin cable DB-9 likely, adjacent to 1st cable. Enters the keyboard at approximately
    the F20 key location.
    https://www.youtube.com/watch?v=r_-dMFUNv-k

### Photos:

* Shots of 4 kmd3's: https://deskthority.net/f-o-r-s-a-l-e-f58/g80-9009hau-4x-kmd3-t4023.html
* Connecting up a G80-9009. Includes Breakout Box and pinouts for PS/2. https://www.ptt.cc/bbs/Key_Mou_Pad/M.1499538853.A.F7F.html
