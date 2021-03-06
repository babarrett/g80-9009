# Reuters AK 124 and AK 125 Keyboard Operations
## (Cherry G80-9009)

## Keyboard layout:

This is the keyboard layout for the UK version of keyboard:

![Default keyboard Legends-UK](../master/images/Cherry%20G80-9009%20Default%20Legends-UK.png "Default keyboard Legends-UK")

## Power-on sequence:

* On power-on, displays in order:
    * **REUTERS** all caps, in center of LCD
    * Clearing FLASH-Code. Please wait...
    * Clearing FLASH-emergency-parameter space. Please wait . . .
    * Version 1.20L01Ref4

If you ignore the keyboard for five minutes the display lighting will go off.

## Special key usage

WEY, who create and sell similar keyboards define some of their special keys as follows (terms replaced with the G80-9009 labels):

        Yours -	 Opens the YOURS window in matching
        Mine -	 Opens the MINE window in matching
        Bid -	 Opens the BID window in matching
        Offer -	 Opens the OFFER window in matching
        Reset -	 Reset values in the current opened window in matching
        F## -	 Macro keys that can be programmed to generate a string or function
        Contact -	 Used to contact a counterparty in Dealing
        Accept -	 accepts a conversation call from a counterparty in Dealing Confirm -	 Confirms a conversation deal in Dealing
        Deal -	 Opens the deal window in Dealing
        Tranfr -	 Transfers a dealing conversation to colleague
        Interrupt -	 Interrupts the Dealing conversation to place in send mode
        Xmit -	 transfers conversation to counterparty
        End cont -	 Ends a dealing conversation

## Set up options:

1. Macros up to 80 characters, with name you assign, stored in F1-F24.
2. You can also store macros in Shift+Fn, and Control+Fn
3. TODO: Can you change the Legends for macro sets?

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

            Delete key Used to clear a macro and it's label.

    Select Desk PC Legend

        Source: IBM PS/2
        +-------------------------------+   +-------------------------------+   +-------------------------------+
        |  `:   |       | RIGHT | ALT   |   | PAUSE |       | END   | NUM   |   | PAGE  | SCRLL | PAGE  | PRINT |
        |       |       | CNTRL | GRAPH |   |       |       |       | LOCK  |   | UP    | LOCK  | DOWN  | SCRN  |
        |-------------------------------|   |-------------------------------|   |-------------------------------|
        | F1    | F2    | F3    | F4    |   | F5    | F6    | F7    | F8    |   | F9    | F10   | F11   | F12   |
        |       |       |       |       |   |       |       |       |       |   |       |       |       |       |
        +-------------------------------+   +-------------------------------+   +-------------------------------+

```
16 legends sets are available.
None support F13-F24 on Desk PC setting

## Calculator Mode:

These are the keys available in Calculator Mode:

![Calculator mode keys](../master/images/Cherry%20G80-9009%20Calculator%20mode%20keys.png "Calculator mode keys")

It's a floating-point calculator. Largest representable number seems to be 9.000 E+1000.

Has eight memories, ```√⎺```, percent, etc. functions.

Enter Calc mode with the Calc key. Exit with either "Desk PC" or "Wkst" keys.

Calc, Num Lock and Caps Lock LEDs are illuminated in Calc mode, and cannot be turned off .

* Number keys, both sets, both decimal points, +, -, /, and = all work as expected.
* Backspace deletes the most recent digit entered. 1,2,3, Backspace, Backspace yields "1."
* Clear clears the current calculation, but not memories.
* Delete clears the current (pending) operation and entry.
* Reset clears the current entry, calculation, and memories. It does not change the decimal setting.
* Both Enter keys are used for "=". "=" without another operation and number
repeats the last operation. Example: 1 * 2 = is 2. =, =, = makes 16.
* Reset key (red) clears the current entry, calculation, and **all** 8 memories. It does not change the decimal setting.
24 24 24* Pressing either Control key clears the display of the Calc F1-F12 keys, but seems to have no other effect.
* Arrow keys (Left/Right) are only used to set number of decimals, while in setup mode.
* F1-F12 function keys are used for
```
        +--------------------+  +-----------------------+  +-----------------------+
        | M  | M   | M+ | M- |  | M     | C   | CE | %  |  | 1/x | √⎺  | EXP | +/- |
        | In | out |    |    |  | clear |     |    |    |  |     |     |     |     |
        +--------------------+  +-----------------------+  +-----------------------+
          F1   F2    F3   F4      F5      F6    F7   F7       F9   F10   F11   F12
```

When in Calc mode the current memory number (1-8) and value is displayed.
EXP is used for entering 10 to the X scaling. Example: 1 3 EXP 2 = 1300.
Negative exponents can be entered as well: 1 3 EXP 4 5 +/- = 1.3E-044


Setup operations, accessible by taping the Shift key:

    * Shift+F1  -> Setup. Allows changing of decimals from 0 to 8 places.
    Left/Right arrow to change. Either Enter key to set and exit.
    * Shift+F11 -> M up.  Select a memory form 1 to 8
    * Shift+F12 -> M down Select a memory form 8 to 1

Arrow keys (Left/Right) are only used to set number of decimals, while in setup mode.


## Defining Macros

The Control keys display the Control+F1 to Control+F12 macro legends.
The Shift keys display the Shift+F1 to Shift+F12 macro legends.
Either Enter key can be used for programming macros.

## Using Macros

TODO: fill in

## Selecting Desc PC legend

TODO: fill in


## Desk PC vs. Wkst selections

With Wkst selected you can... but need to connect... TODO: complete when known.

### Keyboard mode (Desk PC)

Keys that operate in Keyboard mode:

* Keys on main keyboard, except bottom row, all
* Control is Control, Alt and Alt Graph are Command.
* Numeric pad, all
* F1-F12
* The 2 key shifted is @
* The 3 key shifted is #
* The ' key shifted is "
* The # key unshifted is \, and shifted is | << I should swap key caps for this.
* The \ key unshifted is §, and shifted is ±
* The reset button (not key)  on the back of the keyboard acts like a temporary
power Off/On cycle.


Keys that do **not** operate in Keyboard mode:

* ABBR and Deal on the bottom row
* All colored keys on the keyboard, except "0" and "Enter" on the numeric pad.
* The entire first column from Interrupt to Raise Ordrs
* Clear (above Esc)
* F13-F24
* The entire top-right grouping of 11 keys from Hold to Scrn 4.

With Desk PC selected you can not use a subset of the keys on the board, as indicated here:

![Unavailable keys in Desk PC mode](../master/images/Cherry%20G80-9009%20Unavailable%20keys%20in%20Desk%20mode.png "Unavailable keys in Desk PC mode")

### Keyboard mode (Wkst)

* No scan codes are sent out the Desk PC/Workstation port. Still working on this.
