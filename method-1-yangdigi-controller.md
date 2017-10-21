## Connection Method #1, Yangdigi's custom controller card to USB

### What it is:

* A "drop in" solution. A separate new electronic card that plugs into the
inside of the keyboard. Nothing needs to be changed on the keyboard.
* Apparently it takes all the power off the USB port. TODO: confirm.
* ~~Might still require a 12V power connection to the keyboard~~
* Ends up with a USB connection. No need for a further PS/2 to USB converter
* Includes a Pro Micro (equivalent) running TMK software
    * It's 3.3v at 16Mhz.
    * Pro Micro 3.3v at 8Mhz can work well too.
    * If your Pro Micro is 8MHz, change F_CPU = 16000000 to F_CPU = 8000000 in Makefile
    * There is a USB port on the controller card
* The TMK enabled controller is programable. It adds the ability to remap keys,
add macros, add additional function layers, and be able to toggle different
layouts. Any key can be assigned any function or character.
* The TKG - TMK Keymap Generator [tkg.io] can be used to create new keyboard
layouts (no need to compile the firmware!)
    * https://geekhack.org/index.php?topic=82693.msg2192962
    * https://geekhack.org/index.php?topic=82693.msg2398215#msg2398215

* Available in world.taobao.com, search for G80-9009. Two are available today,
October 2017:
    * https://world.taobao.com/item/556346775610.htm?fromSite=main&spm=a230r.1.14.6.1cf2909ceoqXIX&ns=1&abbucket=18#detail
    * https://world.taobao.com/item/556373603543.htm?fromSite=main&spm=a230r.1.14.12.1cf2909ceoqXIX&ns=1&abbucket=18#detail
    * The (translated) title of those pages is: Old mechanical keyboard to
    change usb, Reuters cherry g80-9009hau replace the master, the whole key can
    be programmed - Question and Answer on Alibaba
    * The Chinese title is: 老机械键盘改usb，路透社樱桃g80-9009hau替换主控，全键可编程-淘宝网全球站
* It was created by "yangdigi" (Geekhack name)

### Details

* Making Stuff Together! / Re: Easy AVR USB Keyboard Firmware and Keymapper article: 
https://geekhack.org/index.php?topic=51252.msg2141040#msg2141040
* The G80-9009HAU has two groups of keys. Upper part is a 6x10 matrix (51 keys)
and the lower part is 10x10 (98 keys). Using a pro micro and one 74hc154 (4 to
16 mux) with TMK to run a 16x10 matrix using 4+10=14 pins.
* 2 x 32 pin ribbon cables connect to the top and bottom grpups of keys. (51 and 98 keys)
* uses a 4 to 16 mux for the 16 lines (columns?)
* Yang once said: "Now I am using TMK to run 16x10 matrix. I want to try EasyAVR
on it to make it easier to use."


---
### Pros

* Designed explicitly for the G80-9009
* "Drops right in"
* Makes it a USB keyboard
* Powered by USB, no external power needed
* Maps all 149 keys
* TKG - TMK Keymap Generator for ease of making and loading new keymaps
* Does not requite the "rare" KVMs and their cables, and their power supply
* As long as the keyboard keys and matrixes are intack this method will work. Good for "broken" boards.
* Nothing else to buy, but a USB cable. No hand-made cables

### Cons

* More expensive than the Direct method (Price of controller > price of power-supply)
* Must open the keyboard case (but that's easy, 9 screws)
* Display functions do not work (calculator, macros)

### Unknown

* Apparently does not require an additional power supply. TODO: test
* Can the USB actually provide enough power? Likely only for the matrix scan + TMK functions
* Do the built in functions, display commands (on the fly macro creation, calculator) still work? Likely not.
* Lock LEDs (caps, scroll, num) might, or might not work
* What will the supply of these controllers be like in the future?

---
### Installing the card

TODO: recheck all this when I get my keyboard.

How to install the card is in [this PDF](../master/pdfs/Yangdigi-controller-to-USB-G80-9009.pdf "Yangdigi controller instructions"). 
It is a printed PDF of a Taobao for sale listing of the card.

I've "re-translated" the text to improve the clarity.


    Step 1: Remove the screws on the back of the G80-9009, 4 along both the top and bottom
        edges and one in the center. The four "screwes" around the square in the base
        do not need to come out.
    Step 2: Raise the keyboard shell, notice the upper and lower parts of the
        keyboard. Each has a gray ribbon-cable connected to the main PCB.
    Step 3: There is a transparent plastic piece to insulate the different 
        parts of the keyboard from each other. Gently pull it back to revel the
        ends of the two, wide, ribbon cables. Remove the ends of the two cables 
        that attach to the main PCB. They are next to each other.
    Step 4: There are two of female headers coming out of the bottom of the controller. 
        Conect the controller to the main PCB by carefully placing the two  female 
        headers onto the two sets of pins coming out of the board.
        Be careful not to bend the original pins. Make sure they all line up (no 
        extra pins hanging off the end of the connector).
        The card fits relatively tight. If you want it to be even more secure you
        you can solder PCB to the J4 and J5 marked square jumper pads.
    Step 5: Re-plug the origional ribbon-cables back into the new controller card. 
        The keyboard ribbon-cable(s) will need to be re-folded like the original
        bends to lie flat. In addition, when inserting make sure the
        connectors are straight, and make sure that all the pins are
        inserted into the corresponding holes. Then add a miniUSB cable. A) You
        can use a short cable, just to exit the keyboard then add a USB an
        extension cable, or B) use a single, ling cable.

    (TODO: rewrite this)
    The following figure is to use an extension of the line, the external exposed
    that the small head is microUSB connector, plug a microUSB line can be used.
 
    The rest is to set the button, and burn firmware method gh60 almost, with TKG + KLE,
    full keyboard programmable, support multi-layer layout, support special keys. In
    yang.tkg.io inside, select G80-9009HAU, the bottom will have a link to explain
    how to burn firmware.



---
### Burning new firmware for the Yang (yangdigi) controller

TKG - TMK Keymap Generator instructions [here](../master/tkg-tmk-instructions.mds)

Here are GH60-9009 (Chinese) general instructions for you：[https://imgur.com/a/rfezG]

Go to [http://yang.tkg.io](http://yang.tkg.io) - Select English from top-right drop-down.

If you don't know how to use this, read these first:

* [http://pan.baidu.com/s/1sltOsrV](http://pan.baidu.com/s/1sltOsrV)
* Password: ek5h

On the http://yang.tkg.io page there is a Permlink to the keyboard layout. Click it to see the default software layout (assignment of keys).

Select Keyboard = 80_9009HAU from the drop-down list.

    - Name:       80-9009HAU
    - Max layers: 5
    - Max Fns:    32
    - Firmware:   (empty)

(3 layers) Copy raw code, paste it back in the page, "Simple"

Download .c and/or .epp file(s)


---

### Troubleshooting:
Q: Having a small issue with this, everything works perfectly as according to this
image with the exception of the pipe/backslash key. It performs the same action
as #/~ which I have next to my enter key.

A: Please write that key in the format according to http://tkg.io/#help


---
### Videos:

* Working G80-9009HAU to Windows pad (Surface?) key test and typing. Uses yangdigi controller. https://v.qq.com/x/page/v019406oqmc.html
* Demo of Yang conversion. Using Windows pad (surface?) Same as above, but "Flash." https://www.xiaobaiban.net/video/play-JESdXA5_2B0eZvfsKGvp6tqRccTMcF3jPN.htm
Video Description: be the world's first change this stuff it, giant keyboard.
Did not destroy any one button, take the hole board made a master control,
connected to the original 9009 above the two keyboard use.

### Photos:

* Geekhack, Easy AVR USB Keyboard Firmware and Keymapper. Actually the start of
*yangdigi's* Pro Micro and mux. yangdigi's "rats nest" photos of early
development of his controller. https://geekhack.org/index.php?topic=51252.1650
