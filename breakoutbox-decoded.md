# Reuters AK 125 Breakout Box, decoded

## Process of developing this document

* TODO: Add photos and wiring graphs
* By visual inspection of photographs of AK125
* and reasoning.
    
--------------------------------------------------------------------------------------
## Summary

### Overview
The AK125 Breakout Box is fairly simple, mostly just tying different pins on
different connectors together. The AK124 keyboards and I presume Breakout Boxes
seem to be much more common. I have not confirmed that the functionality and
design match, though the connectors are all labeled the same.

The complexity in the system is all handled within the keyboard.

The knd-3 "breakout box" is a different system, with different connectors, and
many active components created by a different company. It is unlikely that this
document will be of much help there.

* The Breakout Box is Simple.
    * One IC (Hex Inverter): SN7406
    * One 5V regulator: L7805CV
    * Three bypass capacitors (for power systems)
    * Two pull-up resisters on inverter output lines.
    * 12 connectors
    * There is so little to this box that this document is almost enough to
    recreate it, perhaps with even more convenient connectors.
* It handles 3 different serial communication protocols (see below for
additional details)
    * Data and Clock (PS/2 protocol) sometimes through the lone PS/2 connector,
    more often through DB9 connectors.
    * Full duplex, 2-wire (TX and RX) RS232 serial communications for keyboard
    * Half duplex, 1-wire (TX) RS232 serial communications for mouse. Although this is also labeled with "RX" that direction appears not to be used.
    * Inverted, 1-wire (TX) RS232 serial communications for simulating a Sun keyboard to a Sun workstation
    * Inverted, 1-wire (RX) RS232 serial communications for simulating a Sun mouse to a Sun workstation
* The kbd handles all the "smarts" of routing the generated (kbd) and pass-through (mouse) signals/
    
Visual summary:
![Breakout visual summary](../master/images/breakout-decoded.png "Breakout visual summary")

* Red for keyboard data
* Green for mouse data
* Black for power and other

--------------------------------------------------------------------------------------
### Power, and sources

#### +12V
The main, required, voltage to power the AK125 kbd is +12V. The 12 volts needs
to be applied to pins 12, 13, and/or 14 of the keyboard's "HOST" connector. (All
three pins are tied together inside the kbd anyway.) When a breakout box is
involved the 12V comes from the "AK125 System" connector of the box.

The 12V can, conceivably enter the box one of 2 ways:
* (Confirmed) through the Power Supply connector, or
* (Possible, unknown) through the HOST-SYSTEM connector. If the HOST-SYSTEM does
provide +12V then there is no  need for a power supply to be connected to the
box. In fact it should not be connected.

### +5V Derived from the +12V power source
* Regardless of the source of the 12V (Power Supply or HOST-SYSTEM) the 5 volts
is derived from a 5 volt regulator powered by the 12 volts.
* The 5 volts are then used to:
    * Power an SN7406 inverter
    * Act, through a pull-up resistor, on the inverter output line going to the Sun RX/TX Mouse connector.
    * Act, through a pull-up resister, on the inverter output line going to the Sun TX Kbd connector.
    * Go to the +5V pin of the "Mouse IN" connector (PS/2), to power an external, shared, mouse.
    
### +5V Derived from the workstations:
* Workstation-SUN connector (Pin 8)
* Pins 6(?) of Workstation-Generic and 
* other pins from Workstation-PC-KBD, and 
* Workstation-PC-Mouse.

It seems that all go to pin 6 of AK125 "Desk PC/Workstation. TODO: Why?
Detecting Workstation presence?

### Protocols

TODO: Include more here. See summary for what to cover.

#### RS232 Serial
Earliest system, pre-PS/2. 1200 baud, fixed rate. One start and one stop bit. No parity.

#### Sun Serial (inverted TX and RX)
Sun's take on RS232 Serial, where they invert the TX and RX signals. TTL levels.
(+5V for zero, Ground for one)
1200 baud, fixed rate. One start and one stop bit. No parity.

#### PS/2
Instead of transmitting at a fixed rate, say 1200 baud, the protocol uses one
wire as a clock (cycles once for every bit) and the other for data (+5V = 1 bit,
ground for zero bit).




--------------------------------------------------------------------------------------
## Connectors
Starting at the top-left, and moving counter-clockwise.

TODO: Insert small photo of the cover.
--------------------------------------------------------------------------------------
### Connectors names and mapping

The breakout Box includes 12 connectors as follows:

TODO: Add column: Direction WRT the box

| Name, on case                 | Name, on PCB          | Kbd connector name| Protocol  | Dir'n |
| ----------------------------- |-----------------------|---------------|-----------|------|
|  Power Supply                 | (none)                |               | N/A       |In|
|  Workstation-SUN              | Wkst-SUN 8-pos. female|               | Sun       |Out|
|  AK125 System                 | AK125 "HOST" female   | Host          | N/A or unknown |??|
|  AK125-Desk-PC-Workstation    | AK125 "Desk PC/Workstation male| Desk PC/Workstation male | PS/2, Sun |In|
|  Mouse IN                     | Mouse IN 6-pos. female|          | PS/2     |In|
|  AK125-Mouse                  | AK125 "Mouse" female  | Mouse    | PS/2   |**In**/Out|
|  Desk PC-Mouse                | Desk-PC-Mouse male    |     | PS/2   |Out|
|  Desk-PC-KBD                  | Desk PC KBD male      |     | PS/2   |Out|
|  Workstation-PC-KBD           | Wkst-PC-KBD male      |     | Serial |Out|
|  Workstation-PC-Mouse         | Wkst-PC-Mouse male    |     | Serial |Out|
|  Workstation-Generic          | Wkst-Generic female   |     | PS/2   |Out|
|  HOST-SYSTEM                  | System male           |     | Unknown|??|

#### Connectors with data predominately going *IN TO* the breakout box

* **Power supply**: 
* **Mouse-IN**: PS/2 mouse data enters the breakout box, is sent to the kbd via
AK125-Mouse, and distributed back to either the DESK-PC-Mouse or
Workstation-Generic connector.

#### Connectors with data predominately going *OUT OF* the breakout box
* **Workstation-SUN**: Kbd and Mouse data heading for a Sun Workstation (CPU).
* **Desk-PC-Mouse**: Data flows to PS/2 connector on desktop system.
* **Desk-PC-KBD**: Data flows to PS/2 connector on desktop system.
* **Workstation-PC-KBD**: Data flows to an RS232 Serial connector on a desktop system.
* **Workstation-PC-Mouse**: Data flows to an RS232 Serial connector on a desktop system.
* **Workstation-Generic**: Data flows to a PS/2 connector on a desktop "Workstation" system.



#### Connectors with *BIDIRECTIONAL* direction
* **AK125-Desk-PC-Workstation**: 
* **AK125 System**: +12V (and ground) is available in this connector, but other
pins are unknown. Most pass through to the HOST-SYSTEM connector.
* **AK125-Mouse**: 

#### Connectors with *UNKNOWN* direction
* **HOST-SYSTEM**: TODO: 


## Left side

### Power Supply
    +12V
    Ground plane

### Workstation-SUN
Sun Keyboard and mouse connector

| Pin | Function    | Dir'n   | Destination                     | Protocol   | Comments  |
|:---:|-------------|---------|---------------------------------|------------|-----------|
|  4  | RX/TX mouse | From    | Pin 7 of Desk PC/Wkst, inverted | Sun Serial | TX only   |
|     |             | Contact | Pin 9 of Workstation-PC-Mouse   | Serial     | .         |
|  5  | Kbd RX      | From    | Pin 3 of Desk PC/Wkst           | Sun Serial | .         |
|     |             | Contact | Pin 8 of Workstation-PC-KBD     | Serial     | .         |
|  6  | Kbd TX      | From    | Pin 2 of Desk PC/Wkst           | Sun Serial | .         |
|     |             | Contact | Pin 9 of Workstation-PC-KBD     | Serial     | .         |
|  8  | Power, +5V  | To      | Pin 6 of Desk PC/Wkst           | power      | .         |
|     |             | To(?)   | Pin 6?, maybe, of Wkst-Generic  | power      | TODO: Which pin? |

```
    4   RX/TX mouse, but only using TX. Sent after being inverted. From: 
            Pin 7 of Desk PC/Wkst.
            Also connected to Pin 9 of Workstation-PC-Mouse, uninverted.
    5   Kbd RX (TTL) To:
            Pin 3 of Desk PC/Wkst
            Also connected to Pin 8 of Workstation-PC-KBD
    6   Kbd TX (TTL). Comes after being inverted. From:
            Pin 2 of Desk PC/Wkst  
            Also connected to Pin 9 of Workstation-PC-KBD
    8   Power, +5V to: 
            Pin 6 of Desk PC/Wkst  
            Pin ? maybe 6? of Wkst-Generic. TODO: Determine pin.
```

--------------------------------------------------------------------------------------
## Bottom

### AK125 System                                                        
Goes to Keyboard "HOST"

| Pin       | Function    | Dir'n   | Destination               | Protocol   | Comments  |
|:---------:|-------------|---------|---------------------------|------------|-----------|
|  1        | Ground      | To      | HOST-SYSTEM & Keyboard "HOST"| power      | .        |
|  4,5,6    | Ground      | To      | HOST-SYSTEM & Keyboard "HOST"| power      | .        |
|  15       | Ground      | To      | HOST-SYSTEM & Keyboard "HOST"| power      |NOT connected to <br>HOST-SYSTEM connector.|
|  12,13,14 | Power +12V | To       | HOST-SYSTEM & Keyboard "HOST"| power      | .        |
|  2        | Unknown     | ?       | HOST-SYSTEM               | other      |          |
|  3        | Unknown     | ?       | HOST-SYSTEM               | other      |          |
|  7        | Unknown     | ?       | HOST-SYSTEM               | other      |          |
|  10       | Unknown     | ?       | HOST-SYSTEM               | other      |          |
|  11       | Unknown     | ?       | HOST-SYSTEM               | other      |          |

```
    1 ground 
    2 Goes to HOST-SYSTEM male
    3 Goes to HOST-SYSTEM male
    4, 5, 6 are grounded. Go to Kbd "HOST" connector and HOST-SYSTEM
    7 Goes to HOST-SYSTEM male. 
    8 is N/C
    9 ground
    10 Goes to HOST-SYSTEM male
    11 Goes to HOST-SYSTEM male
    12, 13, 14 are +12V, and go to HOST-SYSTEM and KBD HOST
    15 grounded     Note: NOT connected to HOST-SYSTEM connector.
```
    
Much is known, none is very interesting:
```
    Only 12V ever used on the board. (Well, the 12V drives the +5V regulator for
    a little on-board and Mouse-IN power. 5V can come in from the Sun connector.)
    None of the pins go anywhere else on the board.
    Therefore, the ONLY KNOWN use for the host connector for our application is
    12V power (and ground) to the kbd.
```

### AK125-Desk-PC-Workstation

TODO: Review, and double check all these. Indicate direction.

Summary: This connector does almost all of the "heavy lifting" for keyboard
functions. This connector goes to the "Desk PC/Wkst" connector on the kbd. Given
that the other two connectors on the keyboard are only used for mouse functions
and power, this is the main connector.

The pins coming from the keyboard, through this connector, end up extending out 
to two systems, and three protocols:

* Desk PC (PS/2)
* Workstation-PC (PS/2)
* Workstation-Generic (RS232 Serial)
* Workstation-SUN (Sun Serial)

| Pin       | Function    | Dir'n   | Destination               | Protocol   | Comments  |
|:---------:|-------------|---------|---------------------------|------------|-----------|
||||To **Workstation-SUN connector**|
|  2         | Kbd TX     | To      | Pin 6 of Workstation-SUN | Sun Serial | Signal is inverted between here and Workstation-SUN |
|  3         | Kbd RX     | From    | Pin 5 of Workstation-SUN | Sun Serial |  |
|  6         | Power +5V  | From    | Pin 8 of Workstation-SUN | Power      |  |
|  7         | Mouse TX   | To      | Pin 6 of Workstation-SUN | Sun Serial | Signal is inverted between here and Workstation-SUN |
||||To **Wkst-PC-KBD** and **Wkst-PC--Mouse connector**|
|  1         | UNKNOWN    | To      | Pin 8 of Wkst-PC-Mouse   | Serial | TODO: double check. Used for kbd to sense presence of Wkst? |
|  2         | Kbd TX     | To      | Pin 9 of Wkst-PC-KBD     | Serial |  |
|  3         | Kbd RX     | From    | Pin 5 of Wkst-PC-KBD     | Serial |  |
|  6         | Power +5V  | Contact | Pin ? of Wkst-PC-KBD &<br>Pin ? of Wkst-PC-Mouse | Power      |  |
|  7         | Mouse TX   | To      | Pin 9 of Wkst-PC-Mouse | Serial |  |
||||To **Wkst-Generic** PS/2 protocol|
|  4  | Kbd Data(?) |To|Pin maybe 8 or 9 of Wkst-Generic    | PS/2 | White         |
|  5  | Kbd Clock(?) |To|Pin maybe 9 or 8 of Wkst-Generic   | PS/2 | Black         |
||||To **Desk-PC-KBD** PS/2 protocol|
|  8  | Kbd Data |To |Pin 8 of Desk-PC-KBD  | PS/2 | green         |
|  9  | Kbd Clock |To|Pin 9 of Desk-PC-KBD  | PS/2 | purple         |

```
        1      (+) Workstation-PC-Mouse, Pin 8. TODO: USE IN UNKNOWN  ????POWER?????
        2   (*)(§) Sun Kbd TX, Pin 6, inverted and Wkst-PC-KBD pin 9 RS232 Serial
        3   (*)(§) Sun Kbd RX, Pin 5,          and Wkst-PC-KBD pin 8 RS232 Serial
        4   (^) [white] Wkst-Generic (unknown which pin, maybe 8 or 9) PS/2 protocol
        5   (^) [black] Wkst-Generic (unknown which pin, maybe 9 or 8) PS/2 protocol
        6   (*)(^) Sun power +5V, pin 8, IN   and Workstation-Generic pin unknown, maybe 6
        7   (*)(+) Sun Mouse RX/TX, pin 4, inverted and to Workstation-PC-Mouse, pin 9
        8   (=) [green]  Desk-PC-KBD, pin 8. PS/2 KBD DATA
        9   (=) [purple] Desk-PC-KBD, pin 9. PS/2 KBD CLOCK0
```

Results:
```
        One set of kbd data and clock using PS/2 protocol. (Pins 8, and 9 of
        this connector going to pins 8 and 9 of Desk PC Kbd.) The only thing we
        have working so far.

        2 Sun signals, TX and Mouse(TX), inverted as they go to the Sun keyboard connector.
        1 Sun signal, RX, NOT inverted as it comes from the Sun keyboard connector.
        1 Sun +5V. TODO: MAYBE THIS IS USED TO DETECT ANY KBD PRESENT?

        The "Sun Kbd TX signal" also goes to Wkst-PC-KBD pin 9, not inverted
        (serial)

        The Sun TX Mouse signal also goes to Workstation-PC-Mouse, pin 9

        One set of 2 pins (Serial protocol), pins 1, 7 go to
        Workstation-PC-Mouse, Pin 8, 9

        One set of 2 pins (PS/2), 4 and 5 go to Workstation-Generic, Pin 8?, 9?
        (8 = Sun +5V. 9 = Sun mouse TX)
```    
    

### Mouse IN (PS/2)
Pins are PS/2 connector pins, not PCB order.

From connector to Breakout Box:

| Pin | Function    | Dir'n      | Destination               | Protocol   | Comments  |
|:---:|-------------|------------|---------------------------|------------|-----------|
| 1   | Mouse data  | To         | Pin 3 of AK125-Mouse   | PS/2  |          |
| 5   | Mouse Clock | To         | Pin 2 of AK125-Mouse   | PS/2  |          |

From connector to mouse:

| Pin | Function    | Dir'n      | Destination               | Protocol   | Comments  |
|:---:|-------------|------------|---------------------------|------------|-----------|
| 1   | Mouse data  | From mouse |    | PS/2  |          |
| 3   | Ground      | To mouse   |    | Power |          |
| 4   | +5V         | To mouse   |    | Power |          |
| 5   | Mouse Clock | From mouse |    | PS/2  |          |

```
    1   Data Pin 3 of AK125-Mouse in
    3   Gnd
    4   +5V to power the mouse (from regulator) out
    5   CLK to Pin 2 of AK125-Mouse out
```
  
### AK125-Mouse

The AK125-Mouse connector receives a PS/2 mouse singnal from the Brekout box
"Mouse IN" connextor. The keboard logic then figures out where the mouse output
needs to be directed (which of the four sets of ports) and sends the needed
signals:
* back out the AK125-Mouse connector on the Breakout box for the PS/2 signals:
Desk-PC-Mouse and Workstation-Generic, or
* out to the AK125-Desk-PC-Workstation for the RS232 and Sun serial signals:
Workstation-Sun and Workstation-PC-Mouse.

All 9 pins are used.

| Pin | Function    | Dir'n      | Destination               | Protocol   | Comments  |
|:---:|-------------|------------|---------------------------|------------|-----------|
| 1   | ??          | ??         | Pin 1 of Desk-PC-Mouse<br> and Pin 1 of the Desk-PC-KBD    | ??         | TODO: PURPOSE?<br>Perhaps to detect power from Desk system? |
| 2   | Mouse Clock | From       | Pin 5 of Mouse-IN         | PS/2  |          |
| 3   | Mouse data  | From       | Pin 1 of Mouse-IN         | PS/2  |          |
| 4   |       | To  | Pin 5 of Wkst Generic    |      |√ light blue |
| 5   |       | To  | Pin 8 of Desk-PC-Mouse   |      |√ pink  |
| 6   |       | To  | Pin 6? of Desk-PC-Mouse  |      |√ white   |
| 7   |       | To  | Pin 4 of Wkst-Generic    |      |√ brown   |
| 8   |       | To  | Pin 3 of Wkst-Generic    |      |√ purple/dk blue  |
| 9   |       | To  | Pin 2 of Wkst-Generic    |      |√ grey         |


```
    1   to Pin 1 of Desk-PC-Mouse   TODO: PURPOSE?
    2   from pin 5 of Mouse IN (PS/2 CLK)
    3   From pin 1 of Mouse IN (PS/2 data)
    
    4?  [light blue] pin 5 of Wkst Generic
    5?  [pink] pin 8 of Desk-PC-Mouse
    6?  [white] to pin 6? of Desk-PC-Mouse
    7   [brown] to pin 4 of Wkst Generic
    8   [blue] to pin 3 of Wkst Generic
```

--------------------------------------------------------------------------------------
## Right side

### Desk-PC-Mouse
```
    1   Desk PC KBD pin 1, AK125 Mouse pin 1. Unknown use/signal. Power?
    8   Desk PC/Wkst pin 8, mouse Data??
    9   Desk PC/Wkst pin 9??, mouse Clock??
```

Results:
    Likely Desk PC will output PS/2 mouse info to here. Untested.
    
    
### Desk-PC-KBD
```
    1   Desk PC mouse pin 1, AK125 Mouse pin 1. Unknown use/signal. Power?
    8   Desk AK125-Desk-PC-Workstation pin 8, Kbd Data.
    9   Desk AK125-Desk-PC-Workstation pin 9, Kbd Clock.
```

Results:
    This is PS/2 keyboard protocol, known to work.

--------------------------------------------------------------------------------------
## Top
 
 
### Workstation-PC-KBD
RS232 Serial protocol.

```
    1   Sun +5V power
    8   RX, not inverted, from Workstation ports. We're simulatuing a kbd.
    9   TX, not inverted, to Workstation ports. We're simulatuing a kbd.
```
 
Results:
    This is a keyboard (not mouse) RS232 Serial protocol port coming through a DB9.
    Pick this OR the Sun Din8, not both.

### Workstation-PC-Mouse
RS232 Serial protocol.
```
    1   Sun +5V power
    8   AK125-Desk-PC/Wkst pin 1, unknown use.
    9   AK125-Desk-PC/Wkst pin 7, an RS232 Serial protocol TX Mouse
```

Results:
    This is a mouse (not keyboard)  RS232 Serial protocol port coming through a DB9.
    Pick this OR the Sun Din8, not both.

 
 
### Workstation-Generic
PS/2 protocol (Data and Clock)
```
    Two mouse pins
    Two Kbd pins
    +5V if Sun keyboard is connected to Workstation-Sun
```
TODO: more here

 
### HOST-SYSTEM
 
TODO: Mostly a pass through from the AK125 System connector. 
