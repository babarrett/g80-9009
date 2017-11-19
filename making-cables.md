## Making Cables

Depending on your connection method you may need to create two or more cables.

### Host port pins, for power

If you choose either option 2 (Direct) or 3 (Direct + Soarer) you'll need to
provide power to the keyboard via the DB-15 "Host" port on the back of the
keyboard. Below are the the results of Mwei measuring the voltages on a cable
from the breakout box, and my measurements of:

* pins to the ground plane of the keyboard PCBs (Gnd)
* pins to the fuse on the main keyboard PCB (assumed to be Vin, +12VDC)
* and other pins that where connected together (A). I don't know what these go to.

From this I concluded that Pins 4 and 5 should be used as ground, 
and that pins 12, 13, and 14 should be used as power. (+12V)

TODO: Test with power-supply wired.

```
                                    Standard 
Pin     Mwei    Bruce       Use     Conductor color
------  ----    ------      ---     ---------------
Shield  .       Gnd                 bare wire

1       .       Gnd                 white
2       .       .                   brown
3       .       .                   green
4       Gnd     Gnd         Gnd     YELLOW
5       Gnd     Gnd         Gnd     GRAY
6       Gnd     .                   pink
7       .       .                   blue
8       Gnd     .                   red

9       .       Gnd                 black
10      .       A                   violet
11      .       A                   gray-pink
12      Vin     Vin         +12V    RED-BLUE
13      Vin     Vin         +12V    WHITE-GREEN
14      Vin     Vin         +12V    BROWN-GREEN
15      .       .                   white-yellow
```

### Desk PC/Workstation pins

If you choose either option 2 (Direct) or 3 (Direct + Soarer) you'll need to
connect the keyboard via the DB-9 "Desk PC/Workstation" port on the back of the
keyboard to a PS/2 connector.

If you are using the KVM method you may need to make one of these per outgoing
keyboard port as well.

The DB9 (male on keyboard) connects to a DB-9 (female on cable) and from there
to a PS/2 conector (male on cable). This then gets inserted into either the
female PS/2 conector on the computer or the the female PS/2 conector on the
Soarer converter.


```
DB-9    Signal name     PS/2 male
----    -----------     ---------
1       +5V             4
7       Ground          3
8       +Keyboard Data  1
9       Clock           5
    
```
I can't locate any of these that are commercially made. Likely you'll have to wire it yourself.

