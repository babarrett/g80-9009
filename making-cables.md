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

Furthermore I have visually traced the circuitboard of the AK12 breakout box and found:
pins 2, 3, 7, 10, and 11 go straight across the board to the "HOST_SYSTEM" connector.

From this I concluded that:
    * Pins 4 and 5 should be used as ground
    * Pins 12, 13, and 14 should be used as power. (+12V)
    * None of the other pins are used for keyboard or mouse controls.

```
Keyboard 
connector
DB-15M                        
                            AK125   
Pin     Mwei    Bruce       Brkout  Use 
------  ----    ------      ------  -------
Shield  .       Gnd             

1       .       Gnd         Gnd    
2       .       .           HOST    
3       .       .           HOST    
4       Gnd     Gnd         Gnd     Gnd 
5       Gnd     Gnd         Gnd     Gnd 
6       Gnd     .           Gnd         
7       .       .           HOST
8       Gnd     .           N/C

9       .       Gnd         Gnd   
10      .       A           HOST
11      .       A           HOST
12      Vin     Vin         +12V    +12V
13      Vin     Vin         +12V    +12V
14      Vin     Vin         +12V    +12V
15      .       .           Gnd     
```
```
    Cable
DB-15F 
Pin     Use 
------  --- 
4       Gnd 
5       Gnd 

12      +12V
13      +12V
14      +12V          
```

### Desk PC/Workstation Connector

If you choose either option 2 (Direct) or 3 (Direct + Soarer) you'll need to
connect the keyboard via the DB-9 "Desk PC/Workstation" port on the back of the
keyboard to a PS/2 connector.

If you are using the KVM method you may need to make one of these per outgoing
keyboard port as well.

The DB9 (male on keyboard) connects to a DB-9 (female on cable) and from there
to a PS/2 conector (male on cable). This then gets inserted into either the
female PS/2 conector on the computer or the the female PS/2 conector on the
Soarer converter.


The Desk PC/Workstation Connector (DB-9F) on keyboard goes to 
to DB-9M connector on cable, and from there to the PS/2 M end of the cable.
![The configuration](../master/images/Cherry%20G80-9009%20DB9%20to%20PS2.png "DB-9 to Desk PC")

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

TODO: Likely: You may be able to use more pins for a third computer connection.
```
DB-9F   Signal name     PS/2 male
----    -----------     ---------
4       Data or clock   1       Wkst-Generic
5       Data or clock   5       Wkst-Generic
```

TODO: Test: May be able to use more pins for a mouse connection, but really why
bother?

I have tried the first cable, the Desk PC to PS/2. That works fine.
I am about to try this one, which should allow both Desk PC and Wkst 
modes to transmit key strokes. I hope.

To be wired like this:



