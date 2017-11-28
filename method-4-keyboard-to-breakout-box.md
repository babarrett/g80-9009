## Keyboard to Breakout Box

![The configuration](../master/images/Cherry%20G80-9009%20KVM.png "KVM connect diagram")

### There are two "KVM" Boxes:

* KMD-3		https://geekhack.org/index.php?topic=36702.0
* Reuters Breakout Box

### What it is:

* User Anfauglir (Jaws of Thirst) had access to a Reuters Breakout Box
* Here: https://www.ptt.cc/bbs/Key_Mou_Pad/M.1499538853.A.F7F.html
* This keyboard requires a 12V power supply to operate and can be supplied from
the DB-15 HOST connector.
* The usual configuration is: 
    - The Keyboard Desk PC/WorkStation port to KVM
    - The "Host" port to KVM
    - The desktop mouse (PS/2) to the KVM
    - The rest of the connections go from the KVM to the Keyboard, and
    Mouse connectors on the (multiple) attached computers.
* The output keyboard ports on the KVM can be connected, via adapters, to the
(multiple) attached computers.
* DB9 -> PS/2 adapter pinout is: 
    * 1-> 4,
    * 7-> 3,
    * 8-> 1,
    * 9-> 5.  
    See [Making Cables](../master/making-cables.md "Cable making instructions")
* Special keys are totally available. 
* Scrn1/2/3/4 keys may be usable. I don't know how yet.

### Pros:
* Everything works as designed, once you convert the serial keyboard out port(s)
of the KVM to PS/2, and from there to USB, if needed.
* Simple solution in terms of hardware, if you can locate the boxes and cables. 
    - Do not have to open the keyboard
    - No special controller needed
    - Power-supply likely included with the KVM so you don't have to make one
* The built in functions, display commands (on the fly macro creation,
calculator) still work.
* The keyboard and mouse switching would work, so you get a 2 or 3
station KVM "for free."

### Cons:

* Almost impossible to find the breakout boxes, and if you do it's likely you
won't find the right cables. (There also seems to be no documentation on the
cable pinouts)
* You have to create a custom cable, which shouldn't be too bad.
* You'll need another converter if you want to get from PS/2 to USB. 
* You'll have to use a Soarer (or similar?) converter if you want to get to USB and have a programmable keyboard.
An [ebay](http://www.ebay.com/itm/NEW-PS-2-to-USB-Soarers-Converter-Adapter-Remapping-Macros-NKRO-Support-/282575686221) link.

### Unknowns:

* The inside og the breakout box is **very** simple. One 5V regulator, one 
Hex inverter, a simple PCB, and all the connectors.

### Breakout Box Connectors:

```
    The currently available connection method: (Update: the mouse has been working
    properly) http://i.imgur.com/WrXa1Tl.jpg 

           (Unknown, speculation is
            it is SUN workstations)-- DIN8 F --+                    +------ (4pin 12V power supply)
                                               |                    |
    +------------+                     +---(Work Station-Sun)-----(Power)---+
    |  Reuters   |                     |              Reuters                |
    |   AK124    |                     |         AK125 Breakout Box          |
    |            |                     |                                     |
    |         (Host) --- DB15F --- (AK125-System)                       (HOST-SYSTEM)--(DB15M can supply power too?)
    |            |                     |                                     |      
    |    (Desk PC/WkSt) -- DB9M -- (AK125-Desk-PC-Workstation)               |
    |            |                     |                                     |
    |            |                     |                           (Workstation-Generic)--(DB9F maybe third computer)
    |        (Mouse) ----- DB9F -- (AK125-Mouse)                             |
    |            |                     |                                     |
    |            |                     |                           (Workstation-PC-Mouse)--(DB9M)
    +------------+                     |                                     | Then the second machine
                                       |                                     |    mouse PS/2
                                       |                                     |
       (actual mouse,                  |                                     |
       PS/2, sitting  -- PS/2 F --- (Mouse IN)                     (Workstation-PC-KBD)----(DB9M)
       on the desktop)           positioned above                            | Then the second machine
                                  AK125-Mouse                                |    Keyboard PS/2
                                       |                                     |
                                       +-(Desk-PC-Mouse)-------(Desk-PC-KBD)-+
                                               |                      |
      First computer mouse  ------- DB9M ------+                      |
         Keyboard, PS/2  ------------------- DB9M --------------------+
```

The Breakout Box only contains 2 ICs:
    * L7805CV - 5V regulator
    * SN7496 Hex inverter - These TTL hex inverter buffers/drivers feature
    high-voltage open-collector outputs for interfacing with high-level circuits
    (such as MOS) or for driving high-current loads (such as lamps or relays), and
    also are characterized for use as inverter buffers for driving TTL inputs. The
    SN7406 has a minimum breakdown voltage of 30 V. The maximum sink current is 
    40 mA for the SN7406s.

    
TODO: logical diagram

### kmd3 Connectors

Lots of info available here:
    https://deskthority.net/workshop-f7/looking-for-handyman-to-mod-g80-9009hau-t3931.html
   
Application note, 2006:
    http://www.industrycortex.com/datasheets/profile/1250934827
    
Ports on the box:

Front
* Dealing KYBD, DB25-male
* Key pad/Kybd, DB9-female
* PS/2 Mouse

Back
* Power (3 pin, round connector)
* PS/2 Kybd and Mouse to Desk PC
* Kybd data to Dealing system, DB-25 female
* Serial mouse data to dealing system, DB-9, female


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
    about theater is a thick, black cable
    coming from a black "brick". (Power supply??) Labeled with a paper sticker saying 
    "REUTERS EQUIPMENT." This seems likely where the keyboard is being powered from.
    b) Thin cable DB-9 likely, adjacent to 1st cable. Enters the keyboard at approximately
    the F20 key location.
    https://www.youtube.com/watch?v=r_-dMFUNv-k

### Photos:

* Shots of 4 kmd3's: https://deskthority.net/f-o-r-s-a-l-e-f58/g80-9009hau-4x-kmd3-t4023.html
* Connecting up a G80-9009. Includes Breakout Box and pinouts for PS/2. https://www.ptt.cc/bbs/Key_Mou_Pad/M.1499538853.A.F7F.html
