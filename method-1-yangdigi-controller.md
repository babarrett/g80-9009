## Connection Method #1, Yangdigi's custom controller card to USB

![The configuration](../master/images/Cherry%20G80-9009%20Yang%20Controller.png "Yang Controller connect diagram")

## What it is:

* A "drop in" solution. A separate new electronic card that plugs into the
inside of the keyboard. Nothing needs to be changed on the keyboard. The process
is reversible.
* It takes all the power off the USB port. 
* Ends up with a USB connection. No need for a further PS/2 to USB converter
* Includes a Pro Micro (equivalent) running TMK software
    * It's 3.3v at 16Mhz.
    * Pro Micro 3.3v at 8Mhz can work well too.
    * If your Pro Micro is 8MHz, change F_CPU = 16000000 to F_CPU = 8000000 in Makefile
    * There is a USB Mini-b (5-pin) port on the controller card
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
* The USB connector on the controller is a USB Mini-b, (5 pin)
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
* Must open the keyboard case (but that's easy, 11 screws)
* Built-in functions, display commands (on the fly macro creation, calculator) do not work
* LEDs (caps, scroll, num) don't work

### Unknown, check when keyboard arrives

* Does buzzer work?
* What will the supply of these controllers be like in the future? They may not continue to be available.

---
### Installing the card

TODO: Photograph my install.

Note: You could elect to (re)program the controller first, the logistics may be
easier when it's outside of the keyboard.

How to install the card is in these saved PDFs of a Taobao for sale listing of the card.

* [this English PDF](../master/pdfs/Yangdigi-controller-to-USB-G80-9009.pdf "Yangdigi controller instructions") Google-translated from Chinese.
* [this Chinese PDF](../master/pdfs/Yangdigi-controller-to-USB-G80-9009_Chinese.pdf "Yangdigi controller Chinese instructions") with more complete photos.
    
I've "re-translated" the text below to improve the clarity. The steps still
correspond to the photos in the PDFs.

    Step 1: Remove the 11 screws on the back of the G80-9009, 4 along both the
        top and bottom edges one on each side, and one in the center. The four
        "screws" around the square in the base do not need to come out.
        
    Step 2: Raise the keyboard shell, lifting the front edge up with the back
        edge being used as a hinge. Notice there are several sets of wires and
        cables connecting the top and bottom halves. Notice that the upper and lower
        parts of the keyboard keys PCBs each has a gray ribbon-cable connected to
        the main PCB.
        
    Step 3: There is a transparent plastic piece to insulate the different 
        parts of the keyboard from each other. A single screw holds this in
        place and seems to ground the plastic, perhaps reducing electrical
        interference between the display electronics and the main PCB. Either
        gently pull back the plastic to revel the ends of the two, wide, ribbon
        cables, or remove the screw and entire plastic piece. Remove the ends of
        the two cables that attach to the main PCB. They are next to each other.
        
    Step 4: There are two sets of holes in the controller. Conect the controller
        to the main PCB by carefully placing two sets of holes over the two sets
        of pins coming out of the board. (Where you just removed the gray ribbon
        cables.) Make sure the pins and holes all line up. The card fit is
        relatively tight. If you want it to be even more secure you can solder
        two pins on the PCB to the two of the pads numbered J4 and J5. They are
        marked with square jumper pads. Unsoldering (if you ever change your
        mind) may prove dificult.
        
        It turns out that my cable from the lower, large, keyboard PCB was too
        short, even when flattened all the way out, to reach the closest row of
        pins on the controller. I had to move the controller toward the front of
        the keyboard to get it to reach, so not all main PCB pins fit into the 
        controller card. YMMV.
        
        You may want to add insulation beneth the Yang controller to prevent any 
        possible shorts.
        
    Step 5: Re-plug the origional ribbon-cables back into the new controller card. 
        The keyboard ribbon-cable(s) will need to be re-folded like the original
        bends to lie flat. In addition, when inserting make sure the connectors
        are straight, and make sure that all the pins are inserted into the
        corresponding holes. 

    With the controller and ribbon cables in place you will note a USB Mini-b
    conneector on the left of the controller board. Insert a USB Mini-b cable
    into that connector. The cable should be at least long enough to feed out
    the back of the keyboard, for example through the "mouse" opening as shown
    below. Your choice for USB Mini-b cable length are: A) You can use a short
    cable, just to exit the keyboard then add a USB an extension cable, or B)
    use a single, long cable. 

    Finally, you'll need to burn your firmware into the controller. The method is 
    using with TKG + KLE, very much like burning software for the gh60. See: 
        https://geekhack.org/index.php?topic=82693.msg2192963#msg2192963
    Select G80-9009HAU instead of gh60.

---
## Burning new firmware for the Yang (yangdigi) controller

TKG - TMK Keymap Generator instructions [here](../master/tkg-tmk-instructions.mds)

Here are GH60-9009 (Chinese) general instructions for you：[https://imgur.com/a/rfezG]

Go to [http://yang.tkg.io](http://yang.tkg.io) - Select English from top-right
drop-down.

If you don't know how to use this, read these first:

* [http://pan.baidu.com/s/1sltOsrV](http://pan.baidu.com/s/1sltOsrV)
* Password: ek5h

On the http://yang.tkg.io page there is a Permlink to the keyboard layout. Click
it to see the default software layout (assignment of keys).

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
