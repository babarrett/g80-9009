## Display Functions and Operations available on the G80-9009 keyboard

### What this is:

This information was determined when the keyboard was powered up through the
Host port, but not connected through PS/2 or USB to a computer.

These are available with connection methods 2, 3, and 4, but not 1.

## Built-in functions

### LCD:

* On power-on, displays in order:
    * **REUTERS** all caps, in center of LCD
    * Clearing FLASH-Code. Please wait...
    * Clearing FLASH-emergency-parameter space. Please wait . . . 
    * Version 1.20L01Ref4

If you ignore the keyboard for five minutes the display lighting will go off.

* Interaction with Desk PC and Wkst keys:
    * Desk PC turns on its LED while turring off the Wkst LED.
    * Desk PC changes the first line of the display to Source:  **DESK PC**.
    * Desk PC changes the F1-F12 LCD labels to F1-F12
    * Desk PC changes the second row (13-24) LCD labels to blank. (or your set values)
    * Wkst turns on its LED while turring off the Desk PC LED.
    * Wkst changes the first line of the display to Source:  **WORKSTATION**
    * Wkst changes the F1-F12 LCD labels to F1-F12
    * Wkst changes the second row (13-24) LCD labels to F13-F24.

* Interaction with other Window/LED keys:
    * Calc, illuminates Calc, Caps Lock, and Num Lock, LEDs, enters Calc mode, see below.
    * Setup, see below.
    * Scrn 1-4, no apparent effect.
    * Scroll lock, Num Lock, Caps Lock, no apparent effect
    
16 legends sets are available.
None support F13-F24 on Desk PC setting

```
Position    Lable
31          WORKSTATION
32          IBM PS/2
33          DESK PC
34-48       blank
```

### Calculator Mode

Enter Calc mode with the Calc key. Exit with either "Desk PC" or Wkst."

Num Lock and Caps Lock are illuminated and cannot be turned off in Calc mode.

Shift changes:
    * F1  -> Setup. Allows changing of decimals from 0 to 8 places. Left/Right arrow to change. Either Enter key to set and exit.
    * F11 -> M up.  Select a memory form 1 to 8
    * F12 -> M down Select a memory form 1 to 8

Has calculator mode with memory, ```√⎺```, percent, etc. Access by tapping the "Calc" key.
When in Calc mode the Calc, Num Lock, and Caps lock LEDs are illuminated and cannot be extinguished.
When in Calc mode the current memory number (1-8) and value is displayed.
EXP is used for entering 10 to the X scaling. example: 1 3 EXP 2 = 1300.
It's a floating-point calculator. Largest representable number seems to be 9.000 E+1000.

Keys that operate in Calc mode:

* Numeric pad: 0-9, decimal, +, -, /, *, "Enter" (=)
* Keys on main keyboard: 0-9, decimal, +, -, /, *, =, Enter (=)
* "=" without another operation and number repeats the last operation. Example: 1 * 2 = is 2. =, =, = makes 16.
* Backspace deletes the most recent digit entered. 1,2,3, Backspace, Backspace yields "1."
* Delete clears the current (pending) operation and entry.
* The Clear key (above Esc) clears the current amounts showing, current calculation, but not memories.
* F1-F12 (functions as displayed, see below)
* Reset key (red) clears the current entry, calculation, and **all** 8 memories. It does not change the decimal setting.
* Pressing either Shift key reveals Setup, M Up, M down for F1, F11, and F12. Memories numbered 1-8 are available.
* Pressing either Control key clears the display of the Calc F1-F12 keys, but seems to have no other effect.
* Arrow keys (Left/Right) are only used to set number of decimals, while in setup mode.

Calc Setup

* Shift + F1 enters Calc Setup mode.
* There is only 1 item to adjust: "Fixed point," by which they mean set the
number of digits to display to the right of the decimal. The range is 0 to 8.
* Each Left-arrow press increases the number of digits by 1, while each Right-arrow reduces it by one.
* Either Enter key will exit setup.

```
        Source: CALC
                                MEM1 = 1,069.069
        +-------------------------------+       +-------------------------------+       +-------------------------------+
        | M     | M     | M+    | M-    |       | M     | C     | CE    | %     |       | 1/x   | √⎺    | EXP   | +/-   |
        | In    | out   |       |       |       | clear |       |       |       |       |       |       |       |       |
        +-------------------------------+       +-------------------------------+       +-------------------------------+
```

