

Taken from:
    [https://geekhack.org/index.php?topic=82693.msg2192963#msg2192963](https://geekhack.org/index.php?topic=82693.msg2192963#msg2192963)
    
TKG - TMK Keymap Generator [tkg.io] (no need to compile the firmware)

TKG is available at: tkg.io.  It is a work of Kai Ryu. 
I just help to open this topic for discussion and ideas sharing.

About TMK Keymap Generator
TMK Keymap Generator, aka TKG, is a generator that can convert layout created by
keyboard-layout-editor into an available keymap for TMK Keyboard Firmware
Collection.
You can make a keyboard layout by keyboard-layout-editor as you like, copy the
Raw Data and paste them into TKG, set some Fn keys as you want, and click
Download button then you will get the configurations what can works with your
TMK Firmware inside keyboard. It is quite easy to use. No need to compile the
firmware.
TKG is an open source software published under WTFPL. You can find the codes on
GitHub.

Update the Driver
1. Download tkg-toolkit at https://github.com/kairyu/tkg-toolkit.
2. Push the reset button and make sure the dfu bootloader appearing at "Devices
and Printers".
3. Open zadig (in the tool folder of TKG-ToolKit). Click "Options>List all
devices" from the menu to enable the option.
4. Select "ATm32U4DFU" in the drop down list. ( Please be careful to ensure to
select the dfu but not "GH60 or other keybaord name")
5. Select "WinUSB" as the driver. (Usually "WinUSB" is the default option)
6. Click "Install" button and wait for the installation finishing.

How to Use
1. Make your layout at http://www.keyboard-layout-editor.com/
2. Open http://tkg.io. Chosse your Keybarod and paste your layout's url or raw
data here.
3. Set your Fn fuctions and LEDs. LEDs are configurable.
4. Download .eep file to reflash or burn .eep file online.

Here is a GH60 (Chinese) instruction for you：https://imgur.com/a/rfezG
Big THANKS to sakai4eva.

Guide for burning .eep file online is on #1.
139848-0

Currently supported boards (listed on the site)

Special Thanks:
Ian Prest, the author of keyboard-layout-editor. tmk, the author of TMK Keyboard
Firmware Collection. And also thanks to my wife and my newborn son.

Report Bugs

If you found any bug, please contact me freely by email(kai1103@gmail.com), or
file a issue via GitHub. Any comments or requests are welcome too.
« Last Edit: Thu, 06 October 2016, 06:37:58 by yangdigi »

Posts: 54
Location: China
View Profile  Personal Message (Offline)

Re: TKG - TMK Keymap Generator [tkg.io]
« Reply #1 on: Wed, 08 June 2016, 17:55:35 »

How to burn .eep file online

1.Chrome is recommended. Install TKG Chrome App from Chrome Web Store.

2.Make your layout at Keyboard-Layout-Editor and TKG.

Now there are three ways to update.

### 1. For dfu booloader
Make sure you have already installed the driver for ATm32U4DFU.

Push the reset button (usually on the back of the keyboard) then TKG will find your device and display its name.
    139293-0

Click ’burn .eep file’ button. Your device can be reflashed within a few seconds.
    139295-1

While holding shift of another keyboard, ‘burn .eep file‘ changes to ’burn .hex
file‘. With this you can burn hex individually instead.

### 2. For HID Bootloader

Manual installing driver is not needed for this type of bootloader.  Current
support boards: CW40, ErgoDone, RedScarf II+

Two keys (usually the keys of matrix(0,0) and (0,1)) are needed.
    149831-2

While holding the key of matrix(0,0), insert your usb cable into keyboard. The
'burn .eep file' button will be green(clickable). click it to update your
keymap. You can confirm the keyboard connects correctly by finding your
keyboard's name with 'HID EEPROM' in the dropdown menu.

While holding the keys of matrix(0,0) and (0,1) together , insert your usb cable
into keyboard. The dropdown menu shows your keyboard's with 'HID FLASH'. Hold
shift of another keyboard, click 'burn .hex file' to reflash keyboard firmware. 

Usually burning .eep is enough. 

### 3. For RawHID(beta)
Special firmware is required to support this function. Just click ‘burn .eep
file‘ to update keymap. No need for extra operations with your keyboard.

---
Re: TKG - TMK Keymap Generator [tkg.io]
« Reply #2 on: Wed, 08 June 2016, 17:55:49 »

Here is one example that how I use TKG. It is a complex one and you can see what TKG can do.
My Keyboard layout:http://www.keyboard-layout-editor.com/#/gists/bf8248eb6dd0416ecf2dbdf18b5ad4a0

One tip:
You can export your fn settings and save them to Keyboard Properties of Keyboard-Layout-Editor.
Next time when you use tkg, just import them.

-------------------------------------------

git clone https://github.com/kairyu/tkg-toolkit.git
