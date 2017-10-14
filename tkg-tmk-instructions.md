

Taken from:
    https://geekhack.org/index.php?topic=82693.msg2192963#msg2192963
    
LESS


Special Thanks
Ian Prest, the author of keyboard-layout-editor.
tmk, the author of TMK Keyboard Firmware Collection.
And also thanks to my wife and my newborn son.

Report Bugs
If you found any bug, please contact me freely by email(kai1103@gmail.com), or file a issue via GitHub. Any comments or requests are welcome too.
« Last Edit: Thu, 06 October 2016, 06:37:58 by yangdigi »
Report to moderator     Logged
 Offline yangdigi
Thread Starter
 
Posts: 54
Location: China
View Profile  Personal Message (Offline)

Re: TKG - TMK Keymap Generator [tkg.io]
« Reply #1 on: Wed, 08 June 2016, 17:55:35 »
QuoteMulti-Quote
How to burn .eep file online
1.Chrome is recommended. Install TKG Chrome App from Chrome Web Store.
2.Make your layout at Keyboard-Layout-Editor and TKG.

Now there are three ways to update.
[  1. For dfu booloader  ]
Make sure you already install driver for ATm32U4DFU.
Push the reset button(usually on the back of the keyboard) then tkg will find your device and display its name.
LESS
139293-0

Click ’burn .eep file’ button. Your device can be reflashed within a few seconds.
LESS
139295-1

While holding shift of another keyboard, ‘burn .eep file‘ changes to ’burn .hex file‘. With this your can burn hex individually.

[  2. For HID Bootloader  ] 
Manual installing driver is not needed for this type of bootloader.  Current support boards: CW40, ErgoDone, RedScarf II+
Two keys (usually the keys of matrix(0,0) and (0,1)) are needed.
LESS
149831-2

While holding the key of matrix(0,0), insert your usb cable into keyboard. The 'burn .eep file' button will be green(clickable). click it to update your keymap. You can confirm the keyboard connects correctly by finding your keyboard's name with 'HID EEPROM' in the dropdown menu.
LESS


While holding the keys of matrix(0,0) and (0,1) together , insert your usb cable into keyboard. The dropdown menu shows your keyboard's with 'HID FLASH'. Hold shift of another keyboard, click 'burn .hex file' to reflash keyboard firmware. 
LESS


Usually burning .eep is enough. 

[  3. For RawHID(beta)  ]
Special firmware is to required to support this function. Just click ‘burn .eep file‘ to update keymap. No need for extra operations with your keyboard.
LESS

« Last Edit: Thu, 06 October 2016, 06:40:39 by yangdigi »
Report to moderator     Logged
 Offline yangdigi
Thread Starter
 
Posts: 54
Location: China
View Profile  Personal Message (Offline)

Re: TKG - TMK Keymap Generator [tkg.io]
« Reply #2 on: Wed, 08 June 2016, 17:55:49 »
QuoteMulti-Quote
Here is one example that how I use TKG. It is a complex one and you can see what TKG can do.
My Keyboard layout:http://www.keyboard-layout-editor.com/#/gists/bf8248eb6dd0416ecf2dbdf18b5ad4a0
LESS
139277-0
139279-1

One tip:
You can export your fn settings and save them to  Keyboard Properties of Keyboard-Layout-Editor.
Next time when you use tkg, just import them.
LESS
139281-2



