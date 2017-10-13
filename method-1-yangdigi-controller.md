## Connection Method #1, Yangdigi's controller card to USB

### What it is:

* A separate new electronic card that plugs into the inside of the keyboard. Nothing needs to be changed on the keyboard.
* Available in world.taobao.com, search for G80-9009. Two are available today:
    * https://world.taobao.com/item/556346775610.htm?fromSite=main&spm=a230r.1.14.6.1cf2909ceoqXIX&ns=1&abbucket=18#detail
    * https://world.taobao.com/item/556373603543.htm?fromSite=main&spm=a230r.1.14.12.1cf2909ceoqXIX&ns=1&abbucket=18#detail
    * The (translated) title of those pages is: Old mechanical keyboard to change usb, Reuters cherry g80-9009hau replace the master, the whole key can be programmed - Question and Answer on Alibaba
    * The Chinese title is: 老机械键盘改usb，路透社樱桃g80-9009hau替换主控，全键可编程-淘宝网全球站
* The board includes a Pro Micro
    * It's 3.3v at 16Mhz.
    * Pro Micro 3.3v at 8Mhz can work well too.
    * If your Pro Micro is 8MHz, change F_CPU = 16000000 to F_CPU = 8000000 in Makefile
* The board runs TMK software. It is programable. Any key can be assigned any function or character.
* The TKG - TMK Keymap Generator [tkg.io] can be used to create new keyboard layouts (no need to compile the firmware!)
    * https://geekhack.org/index.php?topic=82693.msg2192962
    * https://geekhack.org/index.php?topic=82693.msg2398215#msg2398215
* It was created by "yangdigi"
* There is a USB port on the controller card
* **Aparently** it takes all the power off the USB port. I have not confirmed this.
* Making Stuff Together! / Re: Easy AVR USB Keyboard Firmware and Keymapper article: https://geekhack.org/index.php?topic=51252.msg2141040#msg2141040
* The G80-9009HAU has two parts. Upper part is a 6x10 matrix and the lower part
is 10x10. I use a pro micro and one 74hc154 (4 to 16 mux). I am using TMK to run
a 16x10 matrix.

---
### Installing the card

How to install the card is in [this PDF](pdf/Yangdigi%20controller%20instructions%20to%20USB%20for%20G8-9009.pdf "Yangdigi controller instructions").


---

### Troubleshooting:
Q: Having a small issue with this, everything works perfectly as according to this
image with the exception of the pipe/backslash key. It performs the same action
as #/~ which I have next to my enter key.

A: Please write that key in the format according to http://tkg.io/#help
