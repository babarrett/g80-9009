## Keyboard direct to computer

* This keyboard requires a 12V power supply to operate and can be supplied from
the DB-15 HOST connector. (I don't know which pins)
* The Desk PC / WkSt port on the keyboard can be directly connected to the computer with DB9 to PS/2 cable. 

### Unknowns:

* What pins on the DB-15 are used for 12v?

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
* DB9 -> PS/2 PIN pin correspond to:
    * 1-> 4,
    * 7-> 3,
    * 8-> 1,
    * 9-> 5.  
