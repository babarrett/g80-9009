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
    * Inverted, 1-wire (TX) RS232 serial communications for simulating a Sun mouse to a Sun workstation
* The kbd handles all the "smarts" of routing the generated (kbd) and pass-through (    
    
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
* The  volts are then used to:
    * Power an inverter     TODO: which?
    * Act, through a pull-up resistor, on the inverter output line going to the Sun RX/TX Mouse.
    * Act, through a pull-up resister, on the inverter output line going to the Sun TX for the Sun Kbd.
    * Go to the +5V pin of the "Mouse IN" connector (PS/2), to power an external, shared, mouse.
    
### +5V Derived from the Workstation-SUN connector (Pin 8)
* goes to pin 6 of AK125 "Desk PC/Workstation
* also goes to pin 6(?) of Wkst-Generic

### Protocols

TODO: Include more here. See summary for what cover.

#### RS232 Serial
Earliest system, pre-PS/2. 1200 baud, fixed rate.

#### Sun Serial (inverted TX and RX)
Sun's take on RS232 Serial, where they invert the TX and RX signals. TTL levels.
(+5V becomes ground, Ground becomes +5V)

#### PS/2
Instead of transmitting at a fixed rate, say 1200 baud, the protocol uses one
wire as a clock (cycles for every bit) and the other for data (+5V = 1 bit,
ground for zero).




--------------------------------------------------------------------------------------
## Connectors
Starting at the top-left, and moving counter-clockwise.

--------------------------------------------------------------------------------------
### Connectors names and mapping

The breakout Box includes 12 connectors as follows:

| Name, on case                 | Name, on PCB          | Kbd connector name| Protocol  |
| ----------------------------- |-----------------------|---------------|-----------|
|  Power Supply                 | (none)                |               | N/A       |
|  Workstation-SUN              | Wkst-SUN 8-pos. female|               | Sun       |
|  AK125 System                 | AK125 "HOST" female   | Host          | N/A or unknown |
|  AK125-Desk-PC-Workstation    | AK125 "Desk PC/Workstation male| Desk PC/Workstation male | PS/2, Sun |
|  Mouse IN                     | Mouse IN 6-pos. female| Mouse         | PS/2     |
|  AK125-Mouse                  | AK125 "Mouse" female  |     | PS/2   |
|  Desk PC-Mouse                | Desk-PC-Mouse male    |     | PS/2   |
|  Desk-PC-KBD                  | Desk PC KBD male      |     | PS/2   |
|  Workstation-PC-KBD           | Wkst-PC-KBD male      |     | Serial |
|  Workstation-PC-Mouse         | Wkst-PC-Mouse male    |     | Serial |
|  Workstation-Generic          | Wkst-Generic female   |     | PS/2   |
|  HOST-SYSTEM                  | System male           |     | Unknown |



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
    Ground

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
    4   RX/TX mouse, but only using TX. Comes after being inverted. From: 
            Pin 7 of Desk PC/Wkst and 
            Pin 9 of Workstation-PC-Mouse
    5   Kbd RX (TTL) From:
            Pin 3 of Desk PC/Wkst  
            Pin 8 of Workstation-PC-KBD
    6   Kbd TX (TTL), looks like TX only. Comes after being inverted. From:
            Pin 2 of Desk PC/Wkst  
            Pin 9 of Workstation-PC-KBD
    8   Power, +5V to: 
            Pin 6 of Desk PC/Wkst  
            Pin ? maybe 6? of Wkst-Generic
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
    4, 5, 6 are grounded. 
    7 Goes to HOST-SYSTEM male. 
    8 is N/C
    9 ground
    10 Goes to HOST-SYSTEM male
    11 Goes to HOST-SYSTEM male
    12, 13, 14 are +12V, and do to HOST-SYSTEM male
    15 grounded     Note: NOT connected to HOST-SYSTEM connector.
```
    
Much is known, none is very interesting:
```
    Only 12V ever used on the board. (Well, +5V can come in from the Sun
    connector or the 5V regulator, but those are minor.)
    None of the pins go anywhere else on the board.
    Therefore, the ONLY known use for the host connector for our application is
    12V power (and ground) to the kbd.
```

### AK125-Desk-PC-Workstation

TODO: Review, and double check all these.

Goes to the "Desk PC/Wkst" connector on the kbd.
| Pin       | Function    | Dir'n   | Destination               | Protocol   | Comments  |
|:---------:|-------------|---------|---------------------------|------------|-----------|
|To Workstation-SUN connector| | | | | |
|  2         | Kbd TX     | To      | Pin 6 of Workstation-SUN | Sun Serial | Signal is inverted between here and Workstation-SUN |
|  3         | Kbd RX     | From    | Pin 5 of Workstation-SUN | Sun Serial |  |
|  6         | Power +5V  | From    | Pin 8 of Workstation-SUN | Power      |  |
|  7         | Mouse TX   | To      | Pin 6 of Workstation-SUN | Sun Serial | Signal is inverted between here and Workstation-SUN |
|To Wkst-PC-KBD and -Mouse connector| | | | | |
|  1         | UNKNOWN    | To      | Pin 8 of Wkst-PC-Mouse   | Serial |  |
|  2         | Kbd TX     | To      | Pin 9 of Wkst-PC-KBD     | Serial |  |
|  3         | Kbd RX     | From    | Pin 5 of Wkst-PC-KBD     | Serial |  |
|  6         | Power +5V  | Contact | Pin ? of Wkst-PC-KBD &<br>Pin ? of Wkst-PC-Mouse | Power      |  |
|  7         | Mouse TX   | To      | Pin 9 of Wkst-PC-Mouse | Serial |  |
|    |       |  |    |      |          |

```
        1      (+) Workstation-PC-Mouse, Pin 8. TODO: USE IN UNKNOWN
        2   (*)(§) Sun Kbd TX, Pin 6, inverted and Wkst-PC-KBD pin 9
        3   (*)(§) Sun Kbd RX, Pin 5,          and Wkst-PC-KBD pin 8
        4   (^) [white] Wkst-Generic (unknown which pin, maybe 8 or 9) PS/2 protocol
        5   (^) [black] Wkst-Generic (unknown which pin, maybe 8 or 9) PS/2 protocol
        6   (*) Sun power +5V, pin 8,          and Workstation-Generic pin unknown, maybe 6
        7   (*)(+) Sun Mouse RX/TX, pin 4, inverted and Workstation-PC-Mouse, pin 9
        8   (=) [green]  Desk-PC-KBD, pin 8. PS/2 KBD DATA,  to Desk PC Kbd, pin 8(?)
        9   (=) [purple] Desk-PC-KBD, pin 9. PS/2 KBD CLOCK  to Desk PC Kbd, pin 9(?)
```

Results:
```
        One set of kbd data and clock using PS/2 protocol. (Pins 8, and 9 of
        this connector going to pins 8 and 9 of Desk PC Kbd.) The only thing we
        have working so far.

        2 Sun signals, TX and Mouse(TX), inverted as they go to the Sun keyboard connector.
        1 Sun signal, RX, NOT inverted as it comes from the Sun keyboard connector.
        1 Sun +5V. TODO: MAYBE THIS IS USED TO DETECT SUN KBD PRESENT?

        The Sun Kbd TX signal also goes to (or comes from) Wkst-PC-KBD pin 9,
        not inverted
        The Sun TX Mouse signal also goes to (or comes from)
        Workstation-PC-Mouse, pin 9


        One set of 2 pins (Serial protocol), pins 1, 7 go to
        Workstation-PC-Mouse, Pin 8, 9

        One set of 2 pins (protocol??), 4 and 5 go to Workstation-Generic, Pin
        8?, 9? (8 = Sun +5V. 9 = Sun mouse TX)
```    
    

### Mouse IN (PS/2)
Pins are PS/2 connector pins, not PCB order
```
    1   Data Pin 3 of AK125-Mouse
    4   +5V to power the mouse (from regulator)
    5   CLK to Pin 2 of AK125-Mouse
    3   Gnd
```
  
### AK125-Mouse

This distributes the PS/2 protocol mouse signals from the kbd to other connectors.
```
    1   to Pin 1 of Desk-PC-Mouse   TODO: PURPOSE?
    2   from pin 5 of Mouse IN (PS/2 CLK)
    3   From pin 1 of Mouse IN (PS/2 data)
    
    4?  [light blue] pin 3 of Wkst Generic
    5?  [pink] pin 8 of Desk-PC-Mouse
    6?  [white] to pin 6? of Desk-PC-Mouse
    7   [brown] to pin 4 of Wkst Generic
    8   [blue] to pin 3 of Wkst Generic
```

--------------------------------------------------------------------------------------
## Right side

### Desk-PC-Mouse
```
    1   Desk PC KBD pin 1, AK125 Mouse pin 1. Unknown use/signal
    8   Desk PC/Wkst pin 8, mouse Data??
    9   Desk PC/Wkst pin 9??, mouse Clock??
```

Results:
    Likely Desk PC will output PS/2 mouse info to here.
    
    
### Desk-PC-KBD
```
    1   Desk PC mouse pin 1, AK125 Mouse pin 1. Unknown use/signal
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
    8   RX, not inverted
    9   TX, not inverted
```
 
Results:
    This is a keyboard (not mouse) RS232 Serial protocol port coming through a DB9.
    
    Pick this OR the Sun Din8, not both.

### Workstation-PC-Mouse
RS232 Serial protocol.
```
    1   Sun +5V power
    8   Desk PC/Wkst pin 1, unknown use.
    9   Desk PC/Wkst pin 7, an RS232 Serial protocol TX Mouse
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
