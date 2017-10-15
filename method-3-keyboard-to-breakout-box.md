## Keyboard to Breakout Box, Modification #3

* User Anfauglir (Jaws of Thirst) had access to a Reuters Breakout Box
* Here: https://www.ptt.cc/bbs/Key_Mou_Pad/M.1499538853.A.F7F.html
* This keyboard requires a 12V power supply to operate and can be supplied from
the DB-15 HOST connector. (I don't know which pins)
* The Desk PC / WkSt port on the keyboard can be directly connected to the computer with DB9 to PS/2 cable. 
* DB9 -> PS/2 PIN pin corresponds to:
    * 1-> 4,
    * 7-> 3,
    * 8-> 1,
    * 9-> 5.  
* Special keys are basically un-responsive. 
* Scrn1/2/3/4 keys have a light but he cannot determine how to use them. 
* There is no Windows (Command) Key on the keyboard. (Currently in the macOS will be specified to 
the Command Command, Caps Lock assigned to Option) 
* It is said to have NKRO, unconfirmed.

### Unknowns:

* Are the DB-9 and DB-15 cables from keyboard to Breakout Box straight through?
* What pins on the DB-15 are used for 12v?

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


### kmd3

Lots of info available here:
    https://deskthority.net/workshop-f7/looking-for-handyman-to-mod-g80-9009hau-t3931.html
    
    