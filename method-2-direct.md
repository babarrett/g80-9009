## Connection Method #2, Keyboard direct to computer

![The configuration](../master/images/Cherry%20G80-9009%20Direct.png "Direct connect diagram")

### What it is:

* This keyboard requires a 12V, 500mA power supply to operate. The power is
supplied to the keyboard through the DB-15 "HOST" connector.
* The Desk PC / WkSt port on the keyboard can be directly connected to the
computer with:
    - a DB9 to PS/2 passive cable. 
    - a DB9 to PS/2 passive cable and a PS/2 to USB passive adapter.
    - a DB9 to PS/2 passive cable and a Soarer PS/2 to USB converter.
    (See the next method: Direct+Soarer method #3 for information on this this option.) 
* Can End up with a PS/2 or USB option, your choice

---
### Pros:

* The built in functions, display lighting up, commands (on the fly macro creation,
calculator) all work. 
* Simple solution in terms of hardware. 
    - Do not have to open the keyboard case
    - No special controller needed
    - No additional boxes (kdm3, Breakout Box) needed
    - Need to create a DB-9 to PS/2 cable
    - Need to create a 12V 500mA power-supply to DB-15 cable
    - Need to add a PS/2 to USB adapter, if you want USB
* Cheapest hardware solution
* Lock LEDs (caps, num) work

### Cons:

* You lose the use of 48 keys on the keyboard. They do not send scan
codes. These are all the colored keys (except the num pad), F13-F24, and the
cluster of keys in the top-right. 
* So you are left with 101 keys that work.
* You have to create a custom cable, which shouldn't be too hard to do.
* You'll have to purchase and wire up a 12V, 500mA power-supply to a DB-15.
* You'll need another converter if you want to get from PS/2 to USB. 
* Lock LED for scroll does not work
* "Wkst" mode does not generate any scan codes

### Unknowns:

* I'm still working on getting "Wkst" mode to generate all (most) scan codes

---

```
   Reuters AK124 Keyboard
   
   (Host) ---------- DB15 <--- 12V power and ground to the keyboard
   (Desk PC/WkSt) -- DB9 ----> (to 6 pin DIN PS/2) ---> (PS/2 to USB adapter) ---> to computer
   (Mouse) --------- DB9 ----- (not connected)
```
### Connections

See [Making Cables](../master/making-cables.md "Cable making instructions")

Even though this seems to be a video of a kmd3 connection it looks like
there is useful information for "direct connection:"

TODO: Link?

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
### Keyboard direct to PS/2 mention

In the comments of the Chyrosran22 Youtube review. https://www.youtube.com/watch?v=N8FXw_QelQc

