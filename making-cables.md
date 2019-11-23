## Making Cables

Depending on your connection method you may need to create two or more cables.

### Host port pins, for power

If you choose either option 2 (Direct) or 3 (Direct + Soarer) you'll need to
provide power to the keyboard via the DB-15 "Host" port on the back of the
keyboard. Below are the the results of Mwei measuring the voltages on a cable
from the breakout box, and my measurements of:

    * pins to the ground plane of the keyboard PCBs (Gnd)
    * pins to the fuse on the main keyboard PCB (assumed to be Vin, +12VDC)
    * and other pins that were connected together (pins 10 and 11, labeled: A). I don't know what these go to.

Furthermore I have visually traced the circuitboard of the AK125 breakout box and found:
pins 2, 3, 7, 10, and 11 go straight across the board to the "HOST_SYSTEM" connector.

From this I concluded that:
    * Pins 4 and 5, at least, should be used as ground
    * Pins 12, 13, and 14 should be used as power. (+12VDC)
    * None of the other pins are used for keyboard or mouse controls.

```
Keyboard
connector
DB-15M
                            AK125
Pin     Mwei    Bruce       Brkout  Use
------  ----    ------      ------  -------
Shield  .       Gnd

1       .       Gnd         Gnd     Gnd
2       .       .           HOST
3       .       .           HOST
4       Gnd     Gnd         Gnd     Gnd
5       Gnd     Gnd         Gnd     Gnd
6       Gnd     .           Gnd     Gnd
7       .       .           HOST
8       Gnd     .           N/C?

9       .       Gnd         Gnd
10      .       A           HOST
11      .       A           HOST
12      Vin     Vin         +12V    +12V
13      Vin     Vin         +12V    +12V
14      Vin     Vin         +12V    +12V
15      .       .           Gnd     Gnd
```
![The configuration](../master/images/Cherry%20G80-9009%20Power%20to%20DB15.png "DB-9 to Desk PC")

```
    Cable
DB-15F
Pin     Use
------  ---
1       Gnd
4       Gnd
5       Gnd
6       Gnd
15      Gnd

12      +12V
13      +12V
14      +12V
```

### Desk PC/Workstation Connector

If you choose either option 2 (Direct) or 3 (Direct + Soarer) you'll need to
connect the keyboard via the DB-9 "Desk PC/Workstation" port on the back of the
keyboard to a PS/2 connector.

If you are using the KVM method you may need to make one of these per outgoing
keyboard port as well. TBD.

The DB9 (male on keyboard) connects to a DB-9 (female on cable) and from there
to a PS/2 conector (male on cable). This then gets inserted into either the
female PS/2 conector on the computer or the the female PS/2 conector on the
Soarer converter.


The Desk PC/Workstation Connector (DB-9F) on keyboard goes to
to DB-9M connector on cable, and from there to the PS/2 M end of the cable.

![The configuration](../master/images/Cherry%20G80-9009%20DB9%20to%20PS2.png "DB-9 to Desk PC")

I have tried the first cable, the Desk PC to PS/2. That works fine.

```
DB-9F   Signal name     PS/2 male
----    -----------     ---------
Shield  Ground          Shield
8       +Keyboard Data  1
9       Clock           5
```

You'll have to create this cable yourself.


TODO: Very likely: You may be able to use more pins for Sun Systems keyboard
protocol connection. I'm hoping that the Sun workstation keyboard connections
will support more of the "colored" keys on the keyboard.

There are a number of Sun kbd interface to USB adapters available, including
TMK based ones from Hasu. [For sale](https://geekhack.org/index.php?topic=72052.0)

TODO: Create, configure, and test.
```
DB-9F   Signal name     Sun 8 pin mini DIN, male
----    -----------     ---------
2       Sun kbd Xmt     6
3       Sun kbd Rcv     8
7       Sun mouse TX/RX 4
```

TODO: Likely: You may be able to use more pins for another, third, computer
connection. Uses a PS/s keyboard connector. I thought this would work for
**Generic-Workstation**, but it didn't. Needs more research and testing, perhaps
some logic analyzer work.

```
DB-9F   Signal name     PS/2 male
----    -----------     ---------
4       +Keyboard Data  1       Wkst-Generic
5       Clock           5       Wkst-Generic
6       +5V             4
```

TODO: Test: May be able to use more pins for a mouse connection, but really why
bother, unless ou want the KVM feature to work with a single mouse.

-------------------------------------------

## Summary

### Keyboard Connectors:

|Type   | Kbd connector name |
|------ |--------------------|
| DB15-M| Host               |
| DB9-F | Desk PC/Workstation|
| DB9-M | Mouse IN           |

## Host:

Used for power/ground only, so far

| Pin | Function    | Connection |
|:---:|-------------|---------|
|  1  | N/C         | -       |
|  2  | Unknown     | HOST-SYSTEM |
|  3  | Unknown     | HOST-SYSTEM |
|  4  | Ground      | Power supply |
|  5  | Ground      | Power supply |
|  7  | Unknown     | HOST-SYSTEM |
|  8  | N/C         | -        |
|  10 | Unknown     | HOST-SYSTEM |
|  11 | Unknown     | HOST-SYSTEM |
|  12 | Power +12V  | Power supply |
|  13 | Power +12V  | Power supply |
|  14 | Power +12V  | Power supply |
|  15 | N/C         | -        |


## Desk PC/Workstation

TODO: re-verify this list

| Pin | Function     | Connection |
|:---:|--------------|------------|
||To **Desk-PC-KBD**, PS/2 protocol (known working)|
|  8  | Kbd Data     | (Brown) |
|  9  | Kbd Clock    | (Green) |
||To **Wkst-Generic**, PS/2 protocol|
|  4  | Kbd Data(?) to pin 1  | (Brown) |
|  5  | Kbd Clock(?) to pin 5 | (Green) |
|  6  | Power +5V  to pin 4 | (Yellow) |
||To **Wkst-PC-KBD**, Serial protocol <br>and **Wkst-PC-Mouse**, Serial protocol |
|  1  | Mouse, UNKNOWN. TODO: double check. <br>Used for kbd to sense presence of Wkst mouse? |
|  2  | Kbd TX       |
|  3  | Kbd RX       |
|  6  | Power +5V    |
|  7  | Mouse TX     |
||To **Workstation-SUN**, Sun Serial protocol (inverted) |
|  2  | Kbd TX, Signal is inverted between here and Workstation-SUN |
|  3  | Kbd RX       |
|  6  | Power +5V    |
|  7  | Mouse TX, Signal is inverted between here and Workstation-SUN |

