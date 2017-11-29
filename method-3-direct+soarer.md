## Connection Method #3, Keyboard direct to computer and a Soarer PS/2 to USB converter

![The configuration](../master/images/Cherry%20G80-9009%20Direct+Soarer.png "Direct+Soarer connect diagram")

### What it is:

* This method enhances Method #2 by adding Soarer PS/2 to USB converter
* The result is a keyboard with full programability and the built-in functions of the G80-9009.
* This keyboard requires a 12V power supply to operate and can be supplied from
the DB-15 HOST connector.
* The Desk PC / WkSt port on the keyboard can be directly connected to the
computer with a DB9 to PS/2 passive cable and a Soarer PS/2 to USB converter.

The Soarer converters are available on 
[ebay](http://www.ebay.com/itm/NEW-PS-2-to-USB-Soarers-Converter-Adapter-Remapping-Macros-NKRO-Support-/282575686221).

### Pros:
* Has the greatest capability of the 4 proposed methods. (Well, probably matched
by the method #4 breakout box solution.)
    - The Soarer converter is programable. It adds the ability to remap keys,
    add macros, add additional function layers, and be able to toggle different
    layouts. Any key can be assigned any function or character.
    - The built in functions, display commands (on the fly macro creation,
    calculator) should still work. TODO: Test
* The built in functions, display lighting up, commands (on the fly macro creation,
calculator) all work. 
* Simple solution in terms of hardware. 
    - Do not have to open the keyboard case
    - No special controller needed
    - Need to create a DB-9 to PS/2 cable
    - Need to add a PS/2 to USB adapter or Soarar, if you want USB
    - No additional boxes (kdm3, Breakout Box) and their special cables needed
* Fairly cheap hardware solution
* Lock LEDs (caps, num) work

### Cons:

* You lose the use of 48 keys on the keyboard. They do not send scan
codes. These are all the colored keys (except the num pad), F13-F24, and the
cluster of keys in the top-right. 
* So you are left with 101 keys that work.
* You have to create a custom DB0 to PS/2 cable, which shouldn't be too hard.
* You'll have to purchase and wire up a 12V, 500mA power-supply to a DB-15.
* Lock LED for scroll does not work
* "Wkst" mode does not generate any scan codes

### Unknowns:

* I'm still working on getting "Wkst" mode to generate all (most) scan codes

### Connectors:

```
    +-----+
    |photo|
    +-----+
```
            
```
   Reuters AK124 Keyboard
   
   (Host) ---------- DB15 <--- 12V power and ground to the keyboard
   (Desk PC/WkSt) -- DB9 ----> (to 6 pin DIN PS/2) ---> (PS/2 to USB Soarer converter) ---> to computer
   (Mouse) --------- DB9 ----- (not connected)
```
### Connections

See [Making Cables](../master/making-cables.md "Cable making instructions")

Even though this seems to be a video of a kmd3 connection it looks like
there is useful information for "direct connection and Soarer conversion:"

* Using kmd3. Quick demo, types on computer. Includes Set-up and macro definition. 
Cherry G80-9039HAAUS / Reuters AK124. 2 cables coming off the rear: 
    a) 15? pin D connector to another 15 pin D that seems to only being used as
    a junction box, attached to the keyboard at about the F17 and F18 key area.
    Also joining that second D connecter is a thick, black cable coming from a
    black "brick". (Power supply??) Labeled with a paper sticker saying "REUTERS
    EQUIPMENT." This seems likely where the keyboard is being powered from.
    HOST connector.
    b) Thin cable DB-9 likely, adjacent to 1st cable. Enters the keyboard at approximately
    the F20 key location. Desk PC/Workstation connector.
    https://www.youtube.com/watch?v=r_-dMFUNv-k

---
### Keyboard direct to PS/2

In the comments of the Chyrosran22 Youtube review. https://www.youtube.com/watch?v=N8FXw_QelQc

