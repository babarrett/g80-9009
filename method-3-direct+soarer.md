## Keyboard direct to computer

* This keyboard requires a 12V power supply to operate and can be supplied from
the DB-15 HOST connector. (I don't know which pins)
* The Desk PC / WkSt port on the keyboard can be directly connected to the computer with DB9 to PS/2 cable. 

### Pros:
* Simplest solution in terms of hardware. 
    - Do not have to open the keyboard
    - No special controller needed
    - No additional boxes (kdm3, Breakout Box) needed
    - Need to create a DB-9 tp PS/2 cable
* Likely, the built in functions, display commands (on the fly macro creation,
calculator) still work.

### Cons:

* You have to create a custom cable, which shouldn't be too bad.
* You'll need another converter if you want to get to USB. 
* You'll have to use a Soarer (or similar?) converter if you want to get to USB and programmable. 
An [ebay](http://www.ebay.com/itm/NEW-PS-2-to-USB-Soarers-Converter-Adapter-Remapping-Macros-NKRO-Support-/282575686221) link.

### Unknowns:

* May, likely does, require an additional 12V power-supply 
* Unknown what pins on the DB-15 are used for 12v and ground. 

### Connectors:

```
    +------------+ 
    |  Reuters   | 
    |   AK124    | 
    |  Keyboard  | 
    |         (Host) --- DB15 --- (Used for 12V power)
    |            | 
    |    (Desk PC/WkSt) -- DB9 -- (to PS/2) --- 6 pin DIN --- (to PS/2 to USB adapter)
    |            |
    |        (Mouse) ----- DB9 -- (noot connected)              
    |            |
    +------------+
```
### Connections

* Serial communications takes place across both connectors. The host can assert control at any time. 
* DB9 (male on keyboard, female on connector) -> PS/2 PIN pin (female on computer, male on cable) correspond to:
    DB9 ---->>---- PS/2 male
    ]≣≣≣≣≣≣≣≣≣≣≣≣|◼
    * 1-> 4     +5V
    * 7-> 3     Ground
    * 8-> 1     +Keyboard Data
    * 9-> 5     Clock
    
    I can't locate any of these that are commercially made. Likely you'll have t wire it yourself.

Even though this seems to be a video of a kmd3 connection it looks like
there is useful information for "direct connection:"

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

