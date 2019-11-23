# Reuters AK 125 Breakout Box, decoded

## Process of developing this document

* By visual inspection of photographs of AK125
* Additional traces conectivity information from varszegimarcell (geekhack name)
* and reasoning.
* TODO: Add photos and wiring graphs

--------------------------------------------------------------------------------------
## Summary

### Things this taught us about the three keyboard connectors:

1. HOST:
    * Connects (straight through, we assume) to AK125 System, whatever that is.
    * 12DC (3 pins) and ground (6 pins) in.
    * 5 unknown pins that connect to the "HOST-SYSTEM" connector on the other
    side of the Breakout Box.
    * It may be that some of the unknown pins are used for either "Scrn"
    selection or Workstation protocol choices. TODO: TBD

2. Desk PC/Workstation:
    * Connects (straight through, we assume TBD) to AK125-Desk-PC-Workstation.
    * All 9 pins are used.
    * None of the pins is used to power the keyboard. (mine works fine only
    connected to the +12VDC in the Host connector.)
    * Pin 6, +5VDC will be present if some of the following are atached: TODO: True?
        * Workstation-Generic (it's pin 6)
        * Workstation-PC-Mouse (it'pin 1) TBD: Does it actually provide power?
        * Workstation-PC-KBD (it'pin 1) TBD: Does it actually provide power?
        * Workstation-SUN (Sun pin 8, TBD: should provide power.)
    That 5VDC power is supplied by each computer.
    * Keyboard TX and RX (pin 6) go to/come from both Workstation Sun and
    Workstation-PC-KBD at the same time. It doesn't make sense to have computers
    connected to both of these at once. Pick one (or none).
    * Mouse TX (pin 7) goes to/comes from both Workstation Sun and
    Workstation PC-Mouse at the same time. Again, it doesn't make sense to have
    computers connected to both of these at once. Pick one (or none).
    * PS/2 signals (pins 4,5) go to Workstation-Generic.
    * PS/2 signals (pins 8,9) go to Desk-PC-KBD. So these are separate and you
    could operate separate Workstation/Desk-PC at the same time without conclict.
    * TODO: The purpose and use of pin 1 is unknown, but it goes to (or comes
    from) pin 8 of Workstation-PC-Mouse.

3. Mouse
    * Receives Mouse (PS/2) data in from the breakout box, AK125-Mouse.
    * Passes the data back to the appropriate Desk PC or Workstation-Generic via
    this connector or uses the AK125-Desk-PC-Workstation connector for serial
    workstation protocol.


### Breakout Box Overview
The AK125 Breakout Box, in conjunction with the keyboard logic is capable
of being a two-port KVM. The ports are labeled "Desk PC" and "Wkst." Furthermore,
there are three posible "Workstation" ports available on the breakout box: TODO:  confirm this
    1. Workstation-Generic, kbd and mouse
    2. Workstation-PC-KBD & Workstation-PC-Mouse, together (RS232 communication)
    3. Workstation-SUN, kbd and mouse (Sun Serial communication)
The configuration / choice of which of these to select/use is done with the keyboad
setup screens.

The AK125 Breakout Box is fairly simple, mostly just tying different pins on
different connectors together. The AK124 keyboards, and I presume Breakout Boxes
seem to be much more common. I have not confirmed that the functionality and
design match, though the connectors are all labeled the same.

The complexity in the system is all handled within the keyboard. There are
no "decision-making" circuits or controls in the breakout box.

The kmd-3 "breakout box" is a different system, with different connectors,
contains many active components, and was created by a different company. It is
unlikely that this document will be of much help there.

The basic AK125 Breakout Box functionality is as follows:
* Keyboard input comes from the keyboard's "Desk PC/Workstation" connector. It
uses 3 sets of lines to talk to the four possible computer configurations available:
    1. Desk-PC-KBD, pins 8 & 9 (PS/2)
    2. Workstation-Generic, pins 4 & 5 (PS/2?+ or RS232?- TBD)
    3. Workstation-PC-KBD, pins 2 & 3 (RS232 Serial communication)
    4. Workstation-SUN, pins 2 & 3 (Sun Serial communication)
* Mouse input comes in the Mouse IN (PS/2) connector and is sent, unchanged,
to the AK-125 Mouse connector. That connector is connected to the Mouse
connector on the keybord. From there the mouse signals use 3 sets of
lines to talk to the different computers available:
    1. Desk-PC-Mouse (PS/2), from the keyboard Mouse connector
    2. Workstation-Generic (PS/2), from the keyboard Mouse connector
    3. Workstation using either Sun Serial or RS22 Serial communication), from
    the keyboard Desk PC/Workstation connector
* There are 5 pins of unknown purpose and direction from the AK125 System
connector to the HOST-SYSTEM connector.
* Power (+12VDC) is provided by the Power Supply connector.

Visual summary:
![Breakout visual summary](../master/images/breakout-sys-decoded.png "Breakout visual summary")

```
    * Red for keyboard data
    * Green for mouse data
    * Black for power and other
```

* The Breakout Box is Simple.
    * One IC (Hex Inverter): SN7406
    * One 5VDC regulator: L7805CV
    * Three bypass capacitors (for power systems)
    * Two pull-up resisters on inverter output lines.
    * 12 connectors, around the edge of the box.
    * There is so little to this box that this document is almost enough to
    recreate it, perhaps with even more convenient (PS/2) connectors, or
    built-in conversion to USB.
* It handles 3 different serial communication protocols (see below for
additional details)
    * Data and Clock (PS/2 protocol) input is through the lone PS/2 connector,
    output through two DB9 connectors.
    * Full duplex, 2-wire (TX and RX) RS232 serial communications for keyboard
    * Half duplex, 1-wire (TX) RS232 serial communications for mouse. Although
    this is also labeled with "RX" that direction appears not to be used.
    * Inverted, 1-wire (TX) RS232 serial communications for simulating a Sun keyboard to a Sun workstation
    * Inverted, 1-wire (RX) RS232 serial communications for simulating a Sun mouse to a Sun workstation
* The keyboard handles all the "smarts" of routing the generated (kbd) and pass-through (mouse) signals.


--------------------------------------------------------------------------------------
### Power, and sources

#### +12VDC
The main, required, voltage to power the AK125 kbd is +12VDC. The 12 volts needs
to be applied to pins 12, 13, and/or 14 of the keyboard's "HOST" connector. (All
three pins are tied together inside the kbd anyway.) When a breakout box is
involved the 12VDC comes from the "AK125 System" connector of the box.

The 12VDC can, conceivably enter the box one of 2 ways:
* (Confirmed) through the Power Supply connector, or
* (Possible, unknown) through the HOST-SYSTEM connector. If the HOST-SYSTEM does
provide +12VDC then there is no  need for a power supply to be connected to the
box. In fact it should not be connected.

### +5VDC Derived from the +12VDC power source
* Regardless of the source of the 12VDC (Power Supply or HOST-SYSTEM) the 5 volts
is derived from a 5 volt regulator powered by the 12 volts.
* The 5 volts are then used to:
    * Power an SN7406 inverter
    * Act, through a pull-up resistor, on the inverter output line going to the Sun RX/TX Mouse connector.
    * Act, through a pull-up resister, on the inverter output line going to the Sun TX Kbd connector.
    * Go to the +5VDC pin of the "Mouse IN" connector (PS/2), to power an external, shared, mouse.

#### +5VDC Derived from the workstations:
* Workstation-SUN connector (Pin 8)
* Pins 6(?) of Workstation-Generic and
* other pins from Workstation-PC-KBD, and
* Workstation-PC-Mouse.

It seems that all go to pin 6 of AK125 "Desk PC/Workstation.
TODO: Why? Perhaps it is used to detect Workstation presence?

### Protocols

TODO: Include more here. See summary for what to cover.

#### RS232 Serial
Earliest system, pre-PS/2. 1200 baud, fixed rate. One start and one stop bit. No parity.
RS232 standard pin assignments, should they prove useful, are:
```
    1 DCD
    2 RX
    3 TX
    4 DTR
    5 Ground
    6 DSR
    7 RTS
    8 CTS
    9 Ring indicator
```

#### Sun Serial (inverted TX and RX)
Sun's take on RS232 Serial, where they invert the TX and RX signals. TTL levels.
(+5VDC for zero, Ground for one) 1200 baud, fixed rate. One start and one stop
bit. No parity. Sun standard pin assignments, should they prove useful, are:
```
    Pin Function    Signal/Voltage
    --- --------    --------------
    1   Ground      0V
    2   Ground      0V
    3   Power       +5 Vdc
    4   RX/TX       Mouse
    5   RX          TTL
    6   TX          TTL
    7   Ground      0V
    8   Power       +5 Vdc
```

#### PS/2
Instead of transmitting at a fixed rate, say 1200 baud, the protocol uses one
wire as a clock (cycles once for every bit) and the other for data (+5VDC = 1 bit,
ground for zero bit).

Serial data at 10.0–16.7 kHz with 1 start bit, 8 data bits (LSB first), 1 parity
bit (odd), 1 stop bit, [1 ack bit (if host-to-device)]
When the host pulls the clock low, communication from the device is inhibited.


--------------------------------------------------------------------------------------
## Connectors
Starting at the top-left, and moving counter-clockwise.

![Breakout Box cover](../master/images/breakout-box-decoded.png "Breakout Box cover")

--------------------------------------------------------------------------------------
### Connectors names and mapping

The breakout Box includes 12 connectors as follows:

TODO: Add column: Direction WRT the box

|Type  | Name, on case             | Name, on PCB      | Kbd connector name| Protocol  | Dir'n |
|------| --------------------------|-------------------|---------------|-----------|------|
| ?    |  Power Supply             | (none)            |               | N/A       |In|
| 8DIN-F|  Workstation-SUN         | Wkst-SUN 8-pos.   |               | Sun       |Out|
| DB15-F|  AK125 System            | AK125 "HOST"      | Host          | N/A or unknown |??|
| DB9-M|  AK125-Desk-PC-Workstation| AK125 "Desk PC/Workstation" | Desk PC/Workstation | PS/2, Sun |In|
| PS/2-F|  Mouse IN                | Mouse IN 6-pos.   |          | PS/2     |In|
| DB9-F|  AK125-Mouse              | AK125 "Mouse"     | Mouse    | PS/2   |**In**/Out|
| DB9-M|  Desk PC-Mouse            | Desk PC-Mouse     |     | PS/2   |Out|
| DB9-M|  Desk-PC-KBD              | Desk PC KBD       |     | PS/2   |Out|
| DB9-M|  Workstation-PC-KBD       | Wkst-PC-KBD       |     | Serial |Out|
| DB9-M|  Workstation-PC-Mouse     | Wkst-PC-Mouse     |     | Serial |Out|
| DB9-F|  Workstation-Generic      | Wkst-Generic      |     | PS/2   |Out|
| DB15-M|  HOST-SYSTEM             | System            |     | Unknown|??|

#### Connectors with data predominately going *IN TO* the breakout box

* **Power supply**: 12VDC
* **Mouse-IN**: PS/2 mouse data enters the breakout box, is sent to the kbd via
AK125-Mouse, and distributed back to either the DESK-PC-Mouse or
Workstation-Generic connector.
* **AK125-Desk-PC-Workstation**: Keyboard (typed) data, and serial mouse data.
(But not PS/2 mouse data.)

#### Connectors with data predominately going *OUT OF* the breakout box
* **Workstation-SUN**: Kbd and Mouse data heading for a Sun Workstation (CPU).
The Sun thinks it's coming from a local keyboard and mouse.
* **Desk-PC-Mouse**: Mouse data flows to PS/2 connector on desktop system.
* **Desk-PC-KBD**: Keyboard data flows to PS/2 connector on desktop system.
* **Workstation-PC-KBD**: Keyboard data flows to an RS232 Serial connector on a
desktop system.
* **Workstation-PC-Mouse**: Mouse data flows to an RS232 Serial connector on a
desktop system.
* **Workstation-Generic**: Keyboard and Mouse data flows to a PS/2 connector on
a desktop "Workstation" system.



#### Connectors with *BIDIRECTIONAL* data
* **AK125-Mouse**: The "raw" PS/2 mouse data from "Mouse IN" exits the breakout
box here, and is sent to the keyboard. From there the mouse data either comes
back to this connector (for PS/2) or is sent to the AK125-Desk-PC-Workstation
connector, changed into a serial protocol.

#### Connectors with *UNKNOWN* direction
* **AK125 System**: +12VDC (and ground) is available from this connector to the
keyboard, but other pins are unknown. Most are shared with the HOST-SYSTEM
connector, direction unknown.
* **HOST-SYSTEM**: At least five signals shared with the "AK125 System"
connector. TODO: Find out more.


## Left side

### Power Supply
    +12VDC
    Ground plane

### Workstation-SUN
Sun Keyboard and mouse connector

| Pin | Function    | Dir'n   | Destination                                 | Protocol   | Comments  |
|:---:|-------------|---------|---------------------------------------------|------------|-----------|
|  4  | (RX/)TX mouse | From  | Pin 7 of AK125-Desk-PC-Workstation, inverted| Sun Serial, TTL | TX only   |
|     |             | Contact | Pin 9 of Workstation-PC-Mouse               | Serial     | .         |
|  5  | Kbd RX      | To      | Pin 3 of AK125-Desk-PC-Workstation          | Sun Serial, TTL | .         |
|     |             | Contact | Pin 8 of Workstation-PC-KBD                 | Serial     | .         |
|  6  | Kbd TX      | From    | Pin 2 of AK125-Desk-PC-Workstation, inverted| Sun Serial, TTL | .         |
|     |             | Contact | Pin 9 of Workstation-PC-KBD                 | Serial     | .         |
|  8  | Power, +5V  | To      | Pin 6 of AK125-Desk-PC-Workstation          | power      | .         |
|     |             | Contact | Pin 1 or 6?, maybe, of Workstation-Generic, and <br> Pin 1 of Workstation-PC-Mouse, and <br> Pin 1 of Workstation-PC-KBD | power      | TODO: Which pin? |


--------------------------------------------------------------------------------------
## Bottom

### AK125 System
Goes to Keyboard "HOST"

| Pin       | Function    | Dir'n   | Destination               | Protocol   | Comments  |
|:---------:|-------------|---------|---------------------------|------------|-----------|
|  1        | Ground      | To      | HOST-SYSTEM & Keyboard "HOST"| power      | .        |
|  4,5,6,9  | Ground      | To      | HOST-SYSTEM & Keyboard "HOST"| power      | .        |
|  15       | Ground      | To      | HOST-SYSTEM & Keyboard "HOST"| power      |NOT connected to <br>HOST-SYSTEM connector.|
|  12,13,14 | Power +12V | To       | HOST-SYSTEM & Keyboard "HOST"| power      | .        |
|* * * |
|  2,3      | Unknown     | ?       | HOST-SYSTEM               | other      |          |
|  7        | Unknown     | ?       | HOST-SYSTEM               | other      |          |
|  10,11    | Unknown     | ?       | HOST-SYSTEM               | other      |          |
|* * * |
|  8        | Unused?     | ?       | (none?)                   |            |          |


Six pins are grounded, three more carry +12VDC power. The remaining six all have
unknown functions.
```
    Only 12VDC is ever used to supply the keyboard. None of the pins go anywhere
    on the breakout board except to the HOST-SYSTEM & keyboard "HOST"
    connectors. Therefore, the ONLY KNOWN use for the host connector for our
    application is 12VDC power (and ground) to the kbd.

    There are a total of 5 pins of unknown functions that are still to be
    determined. Interestingly, 4 come in 2 pairs, on adjacent pins.
```

### AK125-Desk-PC-Workstation

TODO: Review, and double check all these. Indicate direction.

Summary: This connector does almost all of the "heavy lifting" for keyboard
functions. This connector goes to the "Desk PC/Wkst" connector on the kbd. Given
that the other two connectors on the keyboard are only used for mouse functions
and power, this is the main connector for keyboard use.

The pins coming from the keyboard, through this connector, end up extending out
to two systems, and three protocols:

* Desk-PC (PS/2)
* Workstation-Generic (PS/2)
* Workstation-PC (RS232 Serial)
* Workstation-SUN (Sun Serial)

The Workstation-Generic and Workstation-SUN are connected together. You cannot
send to one without sending to the other. This implies that you should connect
at most one of these as a workstation, but not both.

| Pin       | Function    | Dir'n   | Destination               | Protocol   | Comments  |
|:---------:|-------------|---------|---------------------------|------------|-----------|
||||To **Workstation-SUN connector**| | Sun Serial protocol |
|  2         | Kbd TX     | To      | Pin 6 of Workstation-SUN | Sun Serial | Pink: Signal is inverted between here and Workstation-SUN |
|  3         | Kbd RX     | From    | Pin 5 of Workstation-SUN | Sun Serial | Yellow |
|  6         | Power +5V  | From    | Pin 8 of Workstation-SUN | Power      | Orange |
|  7         | Mouse TX   | To      | Pin 4 of Workstation-SUN | Sun Serial | Lt. blue: Signal is inverted between here and Workstation-SUN |
||||To **Wkst-PC-KBD** and **Wkst-PC-Mouse connector**| | Serial protocol |
|  1         | Mouse, UNKNOWN| To?  | Pin 8 of Wkst-PC-Mouse   | Serial | Brown: TODO: double check. Used for kbd to sense presence of Wkst mouse? |
|  2         | Kbd TX     | To      | Pin 9 of Wkst-PC-KBD     | Serial | Pink |
|  3         | Kbd RX     | From    | Pin 8 of Wkst-PC-KBD     | Serial | Yellow |
|  6         | Power +5V  | Contact | Pin 1 of Wkst-PC-KBD &<br>Pin 1 of Wkst-PC-Mouse | Power      | Orange |
|  7         | Mouse TX   | To      | Pin 9 of Wkst-PC-Mouse   | Serial | Lt. blue |
||||To **Wkst-Generic** | | PS/2 protocol|
|  4         | Kbd Data(?) |To|Pin maybe 8 or 9 of Wkst-Generic| PS/2 | White: TODO: Test to determine right pin # |
|  5         | Kbd Clock(?)|To|Pin maybe 9 or 8 of Wkst-Generic| PS/2 | Black: TODO: Test to determine right pin # |
|  6         | Power +5V  | Contact | Pin 6? of Wkst-Generic   | Power | Orange |
||||To **Desk-PC-KBD** | | PS/2 protocol|
|  8         | Kbd Data   |To       | Pin 8 of Desk-PC-KBD     | PS/2 | green   |
|  9         | Kbd Clock  |To       | Pin 9 of Desk-PC-KBD     | PS/2 | purple  |


Results:
```
        One set of kbd data and clock using PS/2 protocol. (Pins 8, and 9 of
        this connector going to pins 8 and 9 of Desk PC Kbd.) The only thing we
        have working so far.

        2 Sun signals, TX and Mouse(TX), inverted as they go to the Sun keyboard connector.
        1 Sun signal, RX, NOT inverted as it comes from the Sun keyboard connector.
        1 Sun +5VDC. TODO: MAYBE THIS IS USED TO DETECT ANY WKST IS PRESENT?

        The "Sun Kbd TX signal" also goes to Wkst-PC-KBD pin 9, not inverted
        (serial)

        The Sun TX Mouse signal also goes to Workstation-PC-Mouse, pin 9

        One set of 2 pins (Serial protocol), pins 1, 7 go to
        Workstation-PC-Mouse, Pin 8, 9

        One set of 2 pins (PS/2), 4 and 5 go to Workstation-Generic, Pin 8?, 9?
        (8 = Sun +5VDC. 9 = Sun mouse TX)
```

### Mouse IN (PS/2)
Pins are PS/2 connector pins, not PCB order.

From connector to Breakout Box:

| Pin | Function    | Dir'n      | Destination            | Protocol | Comments  |
|:---:|-------------|------------|------------------------|----------|-----------|
| 1   | Mouse data  | To         | Pin 3 of AK125-Mouse   | PS/2  |          |
| 5   | Mouse Clock | To         | Pin 2 of AK125-Mouse   | PS/2  |          |

From connector to mouse:

| Pin | Function    | Dir'n      | Destination               | Protocol   | Comments  |
|:---:|-------------|------------|---------------------------|------------|-----------|
| 1   | Mouse data  | From mouse |    | PS/2  |          |
| 3   | Ground      | To mouse   |    | Power |          |
| 4   | +5VDC         | To mouse   |    | Power |          | from regulator
| 5   | Mouse Clock | From mouse |    | PS/2  |          |


### AK125-Mouse

The AK125-Mouse connector receives a PS/2 mouse signal from the Brekout box
"Mouse IN" connextor. The keboard logic then figures out where the mouse output
needs to be directed (which of the four sets of ports) and sends the needed
signals:
* back out the AK125-Mouse connector on the Breakout box for the PS/2 signals:
Desk-PC-Mouse and Workstation-Generic, or
* out to the AK125-Desk-PC-Workstation for the RS232 and Sun serial signals:
Workstation-Sun and Workstation-PC-Mouse.

All 9 pins are used.

| Pin | Function    | Dir'n| Destination              | Protocol   | Comments  |
|:---:|-------------|------|--------------------------|------------|-----------|
| 1   | ??          | ??   | Pin 1 of Desk-PC-Mouse<br> and Pin 1 of the Desk-PC-KBD    | ??         | TODO: PURPOSE?<br>Perhaps to detect power from Desk system? |
| 2   | Mouse Clock | From | Pin 5 of Mouse-IN        | PS/2  |          |
| 3   | Mouse data  | From | Pin 1 of Mouse-IN        | PS/2  |          |
| 4?  |             | To   | Pin 5 of Wkst Generic    |      |√ light blue |
| 5?  | Mouse data? | To   | Pin 8 of Desk-PC-Mouse   |      |√ pink:  |
| 6?  | Mouse Clock?| To   | Pin 6? of Desk-PC-Mouse  |      |√ white   |
| 7   |             | To   | Pin 4 of Wkst-Generic    |      |√ brown   |
| 8   |             | To   | Pin 3 of Wkst-Generic    |      |√ purple/dk blue  |
| 9   |             | To   | Pin 2 of Wkst-Generic    |      |√ grey         |

Results:

```
    Mouse data & clock to: Desk-PC-Mouse
    4 signals to Wkst-Generic. Mouse clock and data plus 2 more: UNKNOWN
    Pin 1 goes to Pin 1 of Desk-PC-Mouse and Desk-PC-KBD. Purpose: UNKNOWN
```

--------------------------------------------------------------------------------------
## Right side

### Desk-PC-Mouse

| Pin | Function    | Dir'n| Destination              | Protocol   | Comments  |
|:---:|-------------|------|--------------------------|------------|-----------|
| 1   | ??          | ??   | Pin 1 of AK125-Mouse     | ??  | Unknown use/signal. Power? |
| 6   | Mouse Clock?| From | Pin 6? of AK125-Mouse    | PS/2  |          |
| 8   | Mouse Data? | From | Pin 5? of AK125-Mouse    | PS/2  |          |


Results:
    Likely Desk PC will output PS/2 mouse info to here. Untested.


### Desk-PC-KBD

| Pin | Function    | Dir'n| Destination              | Protocol   | Comments  |
|:---:|-------------|------|--------------------------|------------|-----------|
| 1   | ??          | ??   | Pin 1 of AK125-Mouse <br> and Pin 1 of Desk-PC-KBD | ??  | Unknown use/signal. Power? |
| 8   | Kbd Data    | From | Pin 8 of AK125-Desk-PC-Workstation    | PS/2  |          |
| 9   | Kbd Clock   | From | Pin 9 of AK125-Desk-PC-Workstation    | PS/2  |          |

Results:
    This is PS/2 keyboard protocol, known to work.

--------------------------------------------------------------------------------------
## Top


### Workstation-PC-KBD
RS232 Serial protocol.

| Pin | Function    | Dir'n| Destination              | Protocol   | Comments  |
|:---:|-------------|------|--------------------------|------------|-----------|
| 1   | Sun +5V power| ??  | Pin 6 of AK125-Desk-PC-Workstation <br> and others | Power | Power, possibly used to check for presence of any workstation? |
| 8   | Kbd RX    | From | Pin 3 of AK125-Desk-PC-Workstation    | Serial  |          |
| 9   | Kbd TX    | From | Pin 2 of AK125-Desk-PC-Workstation    | Serial  |          |

Results:
    This is a keyboard (not mouse) RS232 Serial protocol port coming through a DB9.
    Pick this OR the Sun Din8, not both.

### Workstation-PC-Mouse
RS232 Serial protocol.

| Pin | Function     | Dir'n| Destination              | Protocol   | Comments  |
|:---:|--------------|------|--------------------------|------------|-----------|
| 1   | Sun +5V power| ??  | Pin 6 of AK125-Desk-PC-Workstation <br> and others | Power | Power, possibly used to check for presence of any workstation? |
| 8   | UNKNOWN      | ??  | Pin 1 of AK125-Desk-PC-Workstation    | Serial?  | Blue line on cover |
| 9   | Mouse TX     | From| Pin 7 of AK125-Desk-PC-Workstation    | Serial  |          |


Results:
    This is a mouse (not keyboard)  RS232 Serial protocol port coming through a DB9.
    Pick this OR the Sun Din8, not both.


### Workstation-Generic
PS/2 protocol (Data and Clock)

TODO: It's quite hard to map the pins going into this connector. Waiting for more info.

| Pin | Function     | Dir'n| Destination              | Protocol   | Comments  |
|:---:|--------------|------|--------------------------|------------|-----------|
| 6 or 1?| Sun +5V power| ??  | Pin 6 of AK125-Desk-PC-Workstation <br> and others | Power | Power, possibly used to check for presence of any workstation? |
| 2   | UNKNOWN      | ??  | Pin 9 of AK125-Mouse    | PS/2  | Gray |
| 3   | UNKNOWN      | ??  | Pin 8 of AK125-Mouse    | PS/2  | Blue  |
| 4   | UNKNOWN      | ??  | Pin 9 of AK125-Mouse    | PS/2  | Brown |
| 5   | UNKNOWN      | ??  | Pin 8 of AK125-Mouse    | PS/2  | Lt. Blue  |

| 7   | (none?)      | ??  |      | ?  |   |
| 8?  | UNKNOWN      | ??  | Pin 8 of AK125-Desk-PC-Workstation| ? | White? |
| 9?  | UNKNOWN      | From| Pin 4 of AK125-Desk-PC-Workstation| ? | Black? |

    Two mouse pins
    Two Kbd pins
    +5VDC if Sun keyboard is connected to Workstation-Sun

### HOST-SYSTEM

TODO: Mostly a pass through from the AK125 System connector.

| Pin       | Function    | Dir'n   | Destination               | Protocol   | Comments |
|:---------:|-------------|---------|---------------------------|------------|----------|
|  1        | Ground      | To      | HOST-SYSTEM & Keyboard "HOST"| power   | .        |
|  4,5,6,9  | Ground      | To      | HOST-SYSTEM & Keyboard "HOST"| power   | .        |
|  15       | NOT connected| To      | HOST-SYSTEM & Keyboard "HOST"| N/C    | |
|  12,13,14 | Power +12V | To       | HOST-SYSTEM & Keyboard "HOST"| power   | .        |
|* * * |
|  2,3      | Unknown     | ?       | AK125 System               | other     |          |
|  7        | Unknown     | ?       | AK125 System               | other     |          |
|  10,11    | Unknown     | ?       | AK125 System               | other     |          |
|* * * |
|  8        | Unused?     | ?       | (none?)                   |            |          |
