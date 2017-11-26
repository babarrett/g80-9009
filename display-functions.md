## Display Functions and Operations available on the G80-9009 keyboard

### What this is:

These tests were done with the keyboard powered up through the Host port, but
not connected through PS/2 or USB to a computer.

These are available with connection methods 2, 3, and 4, but not 1.

## Built-in functions

### LCD:

* On power-on, displays in order:
    * **REUTERS** all caps, in center of LCD
    * Clearing FLASH-Code. Please wait...
    * Clearing FLASH-emergency-parameter space. Please wait . . . 
    * Version 1.20L01Ref4

If you ignore the keyboard for a while the display lighting will go off.

* Interaction with Desk PC and Wkst keys:
    * Desk PC turns on its LED while turring off the Wkst LED.
    * Desk PC changes the first line of the display to Source:  **DESK PC**.
    * Desk PC changes the F1-F12 LCD labels to F1-F12
    * Desk PC changes the second row (13-24) LCD labels to blank.
    * Wkst turns on its LED while turring off the Desk PC LED.
    * Wkst changes the first line of the display to Source:  **WORKSTATION**
    * Wkst changes the F1-F12 LCD labels to F1-F12
    * Wkst changes the second row (13-24) LCD labels to F13-F24.

* Interaction with other Window/LED keys:
    * Calc, illuminates Calc LED, enters Calc mode, see below.
    * Setup, see below.
    * Scrn 1-4, no apparent effect.
    * Scroll lock, Num Lock, Caps Lock, no apparent effect
    
    
DESK PC
WORKSTATION
IBM PS/2



### Calculator Mode
Has calculator mode with memory, ```√⎺```, percent, etc. Access by tapping the "Calc" key.
When in Calc mode the Calc, Num Lock, and Caps lock LEDs are illuminated and cannot be extinguished.
When in Calc mode the current memory number (1-8) and value is displayed.
EXP is used for entering 10 to the X scaling. example: 1 3 EXP 2 = 1300.
It's a floating-point calculator. Largest representable number seems to be 9.000 E+1000.
To exit Calc mode you must press the Desk PC or Wkst key.

Keys that operate in Calc mode:

* Numeric pad: 0-9
* Keys on main keyboard: 0=9, +, -, /, *, =, Enter (=)
* Numeric pad: Operations: +, -, /, *, "Enter" (=)
* F1-F12 (functions as displayed, see below)
* The Reset key resets the Calculator back to start, including **all** 8 memories. 
* Pressing either Shift key reveals Setup, M Up, M down for F1, F11, and F12. Memories numbered 1-8 are available.
* Pressing either Control key clears the display of the Calc F1-F12 keys, but seems to have no other effect.

Calc Setup

* Shift + F1 enters Calc Setup mode.
* There is only 1 item to adgujust: "Fixed point," by which they mean set the
number of digits to display to the right of the decimal. The range is 0 to 8.
* Each Left-arrow press increases the number of digits by 1, while each Right-arrow reduces it by one.
* Either Enter key will exit setup.
* The Reset key does **not** reset the display formatting.

```
        Source: CALC
                                MEM1 = 1,069.069
        +-------------------------------+       +-------------------------------+       +-------------------------------+
        | M     | M     | M+    | M-    |       | M     | C     | CE    | %     |       | 1/x   | √⎺    | EXP   | +/-   |
        | In    | out   |       |       |       | clear |       |       |       |       |       |       |       |       |
        +-------------------------------+       +-------------------------------+       +-------------------------------+
```

### Set up options:

1. Macros up to 80 characters, stored in F1-F24
2. Changing the Legends for macro sets

The Legends and Macros get set for either the Desk PC, or Workstation. Select the one you want before pressing Setup.

```
USER SETUP MENU
    Macro Definition
        MACRO DEFINITION > Set [33]: DESK PC
            Program Key
                Which key do you want to program >  Tap one of the F keys, 1-24, for example F14
                Enter Soft Key Name of F14: LOREMIPSUM
                Enter the desired macro (max. 80 char.) and confirm with F14 (enter text)
                Busy with Flash! (Writing)
        
            Delete key
            
    Select Desk PC Legend

        Source: IBM PS/2
        +-------------------------------+       +-------------------------------+       +-------------------------------+
        |  `:   |       | RIGHT | ALT   |       | PAUSE |       | END   | NUM   |       | PAGE  | SCRLL | PAGE  | PRINT |
        |       |       | CNTRL | GRAPH |       |       |       |       | LOCK  |       | UP    | LOCK  | DOWN  | SCRN  |
        |-------------------------------|       |-------------------------------|       |-------------------------------|
        | F1    | F2    | F3    | F4    |       | F5    | F6    | F7    | F8    |       | F9    | F10   | F11   | F12   |
        |       |       |       |       |       |       |       |       |       |       |       |       |       |       |
        +-------------------------------+       +-------------------------------+       +-------------------------------+

```
  