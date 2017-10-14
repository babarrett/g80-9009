## Connection Method #1, Yangdigi's custom controller card to USB

### What it is:

* A "drop in" solution. A separate new electronic card that plugs into the inside of the keyboard. Nothing needs to be changed on the keyboard.
* Might still require a 12V power connection to the keyboard
* Ends up with a USB connection. No need for a further PS/2 to USB converter
* Includes a Pro Micro running TMK software
    * It's 3.3v at 16Mhz.
    * Pro Micro 3.3v at 8Mhz can work well too.
    * If your Pro Micro is 8MHz, change F_CPU = 16000000 to F_CPU = 8000000 in Makefile
    * There is a USB port on the controller card
* The board runs TMK software. It is programable. Any key can be assigned any function or character.
* The TKG - TMK Keymap Generator [tkg.io] can be used to create new keyboard layouts (no need to compile the firmware!)
    * https://geekhack.org/index.php?topic=82693.msg2192962
    * https://geekhack.org/index.php?topic=82693.msg2398215#msg2398215

* Available in world.taobao.com, search for G80-9009. Two are available today, October 2017:
    * https://world.taobao.com/item/556346775610.htm?fromSite=main&spm=a230r.1.14.6.1cf2909ceoqXIX&ns=1&abbucket=18#detail
    * https://world.taobao.com/item/556373603543.htm?fromSite=main&spm=a230r.1.14.12.1cf2909ceoqXIX&ns=1&abbucket=18#detail
    * The (translated) title of those pages is: Old mechanical keyboard to
change usb, Reuters cherry g80-9009hau replace the master, the whole key can be
programmed - Question and Answer on Alibaba
    * The Chinese title is: 老机械键盘改usb，路透社樱桃g80-9009hau替换主控，全键可编程-淘宝网全球站
* It was created by "yangdigi" (Geekhack name)
* **Aparently** it takes all the power off the USB port. I have not confirmed this.

### Details
* Making Stuff Together! / Re: Easy AVR USB Keyboard Firmware and Keymapper article: https://geekhack.org/index.php?topic=51252.msg2141040#msg2141040
* The G80-9009HAU has two parts. Upper part is a 6x10 matrix (51 keys) and the lower part
is 10x10 (98 keys). Using a pro micro and one 74hc154 (4 to 16 mux) with TMK to run
a 16x10 matrix.
* 2 x 32 pin ribbon cables connect to the top and bottom keyboard halves. (51 and 98 keys)
* keyboard matrix to use/replacate is 16x10
* uses a 4 to 16 mux for the 16 lines (columns?)
* G80-9009HAU has two parts. Upper part is 6x10 and lower is 10x10. 
* Now I am using TMK to run 16x10 matrix. I want to try EasyAVR on it to make it easier to use.


---
### Installing the card

How to install the card is in [this PDF](../master/pdfs/Yangdigi-controller-to-USB-G80-9009.pdf "Yangdigi controller instructions"). 
It is a printed PDF of a Taobao for sale listing of the card.


---
### Pros

* Designed to work together
* "Drops right in"
* Makes it a USB keyboard
* Apparently does not requir an additional power supply


### Cons

* More expensive than the Direct method

### Unknown

* Can the USB actually provide enough power?
* Do the built in functions (on the fly macro creation, calculator) still work?
---

### Troubleshooting:
Q: Having a small issue with this, everything works perfectly as according to this
image with the exception of the pipe/backslash key. It performs the same action
as #/~ which I have next to my enter key.

A: Please write that key in the format according to http://tkg.io/#help
