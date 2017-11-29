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

According to the breakout box, the port 2, 3, 7 is also connected to the
upstream system. There could be some data activity going on.

```
Keyboard 
connector
DB-15M                           
Pin     Mwei    Bruce       Use 
------  ----    ------      --- 
Shield  .       Gnd             

1       .       Gnd             
2       .       .               
3       .       .               
4       Gnd     Gnd         Gnd 
5       Gnd     Gnd         Gnd 
6       Gnd     .               
7       .       .               
8       Gnd     .               

9       .       Gnd             
10      .       A               
11      .       A               
12      Vin     Vin         +12V
13      Vin     Vin         +12V
14      Vin     Vin         +12V
15      .       .               
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
 DB-9F to PS/2 M Cable (Desk PC)
DB-9F   Signal name     PS/2 male
----    -----------     ---------
Shield  Ground          Shield
7       Ground          3
8       +Keyboard Data  1
9       Clock           5

   DB-9F to PS/2 M Cable (Wkst)
DB-9F   Signal name     PS/2 male
----    -----------     ---------
Shield  Ground          Shield
7       Ground          3
2       +Keyboard Data  1
3       Clock           5
    
```
TODO: May be able to add pins for a second and third computer connection. If not
here, then on the "Host" port. 

I can't locate any of these that are commercially made. Likely you'll have to wire it yourself.

