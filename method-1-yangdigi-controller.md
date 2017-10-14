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
### Burning new firmware for the Yang (yangdigi) controller

Go to http://yang.tkg.io - Select English from top-right drop-down.

If you don't know how to use this, please read these first: http://pan.baidu.com/s/1sltOsrV Password: ek5h

Select Keyboard = 80_9009HAU

- Name:       80-9009HAU
- Max layers: 5
- Max Fns:    32
- Firmware:   (empty)

Permalink to [Keyboard Layout editor](http://kle.ydkb.io/%23%23%40_name%3DG80-9009HAU%26author%3DYANG%26notes%3Dtkg%25E7%25BD%2591%25E5%259D%2580%25EF%25BC%259Ahttps%252F%3A%252F%252F%252F%252Fyang.tkg.io%250A%250A%25E5%2588%25B7%25E5%259B%25BA%25E4%25BB%25B6%25E6%2595%2599%25E7%25A8%258B%25EF%25BC%259Ahttp%252F%3A%252F%252F%252F%252Fpan.baidu.com%252F%252Fs%252F%252F1sltOsrV%2520%25E5%25AF%2586%25E7%25A0%2581%252F%3A%2520ek5h%2520%250A%25E5%25A6%2582%25E4%25BD%2595%25E5%2588%25B7%25E6%259C%25BA%25E8%25AF%25B7%25E5%258F%2582%25E8%2580%2583%2520TKG%25E5%259C%25A8%25E7%25BA%25BF%25E5%2588%25B7%25E6%259C%25BA%25E6%2595%2599%25E7%25A8%258Bv3.0.pdf%2520%25E4%25B8%25AD%25E7%259A%2584%25E7%25AC%25AC%25E5%259B%259B%25E9%2583%25A8%25E5%2588%2586%25EF%25BC%258CRAWHID%25E5%259C%25A8%25E7%25BA%25BF%25E5%2588%25B7%25E6%259C%25BA%250A%25E5%25A6%2582%25E4%25BD%2595%25E5%2588%25B6%25E4%25BD%259C%25E5%25B8%2583%25E5%25B1%2580%25EF%25BC%258C%25E4%25BC%259A%25E5%2588%25B7GH60%25E7%259A%2584%25E8%25AF%259D%25E5%25A4%25A7%25E8%2587%25B4%25E6%2598%25AF%25E7%259B%25B8%25E5%2590%258C%25E7%259A%2584%25EF%25BC%258C%25E4%25B8%258D%25E4%25BC%259A%25E5%2588%25B7%25E8%25AF%25B7%25E5%258F%2582%25E7%259C%258B%2520GH60%25E7%25AD%2589%25E9%2594%25AE%25E7%259B%2598%25E4%25BD%25BF%25E7%2594%25A8KLE%25E5%2592%258CTKG%25E7%25BC%2596%25E8%25BE%2591%25E9%2594%25AE%25E4%25BD%258D%25E8%25AF%25B4%25E6%2598%258Ev2.0.pdf%250A%250A%25E4%25BD%25BF%25E7%2594%25A8RAWHID%25E9%259C%2580%25E8%25A6%2581%25E4%25BD%25BF%25E7%2594%25A8%25E6%25B5%258B%25E8%25AF%2595%25E7%2589%2588%25E7%259A%2584Chrome%2520App%25EF%25BC%258C%25E6%2596%2587%25E4%25BB%25B6%25E5%259C%25A8%25E5%2585%25B1%25E4%25BA%25AB%25E9%2587%258C%25EF%25BC%258Ctkg-chrome-app-0.8beta-rawhid.crx%253B%26%40_x%3A19%253B%26%3Dvol%2520dn%26%3Dvol%2520up%26_x%3A0.5%253B%26%3Dbtn3%26%3Dbtn1%26%3Dmouse%2520up%26%3Dbtn2%253B%26%40_w%3A2%253B%26%3DESC%26_x%3A17%26w%3A2%253B%26%3DMUTE%26_x%3A0.5%253B%26%3DF5%26%3Dmouse%2520left%26%3Dmouse%2520down%26%3Dmouse%2520right%253B%26%40_y%3A1%26w%3A2%253B%26%3DESC%26_x%3A0.5%253B%26%3DESC%26_x%3A0.5%253B%26%3DF1%26%3DF2%26%3DF3%26%3DF4%26_x%3A0.75%253B%26%3DF5%26%3DF6%26%3DF7%26%3DF8%26_x%3A0.75%253B%26%3DF9%26%3DF10%26%3DF11%26%3DF12%26_x%3A0.5%26w%3A2%253B%26%3DPrtSc%26%3DPause%250ABreak%26_x%3A0.5%253B%26%3DF9%26%3DF10%26%3DF11%26%3DF12%253B%26%40_w%3A2%253B%26%3DESC%26_x%3A0.5%253B%26%3DEsc%26_x%3A0.5%253B%26%3DF1%26%3DF2%26%3DF3%26%3DF4%26_x%3A0.75%253B%26%3DF5%26%3DF6%26%3DF7%26%3DF8%26_x%3A0.75%253B%26%3DF9%26%3DF10%26%3DF11%26%3DF12%26_x%3A0.5%253B%26%3DPrtSc%26%3DScroll%2520Lock%26%3DPause%250ABreak%26_x%3A0.5%26w%3A2%253B%26%3Dvol%2520dn%26_w%3A2%253B%26%3Dvol%2520up%253B%26%40_y%3A0.5%253B%26%3DF1%26%3DF2%26_x%3A0.5%253B%26%3D%25C2%25AC%250A%2560%26%3D%21%250A1%26%3D%2522%250A2%26%3D%25C2%25A3%250A3%26%3D%24%250A4%26%3D%2525%250A5%26%3D%255E%250A6%26%3D%252F%26%250A7%26%3D%2A%250A8%26%3D%28%250A9%26%3D%29%250A0%26%3D%252F_%250A-%26%3D%2B%250A%252F%3D%26_w%3A2%253B%26%3DBackspace%26_x%3A0.5%253B%26%3DInsert%26%3DHome%26%3DPgUp%26_x%3A0.5%253B%26%3DNum%2520Lock%26%3D%252F%252F%26%3D%2A%26%3D-%253B%26%40%3DF3%26%3DF4%26_x%3A0.5%26w%3A1.5%253B%26%3DTab%26%3DQ%26%3DW%26%3DE%26%3DR%26%3DT%26%3DY%26%3DU%26%3DI%26%3DO%26%3DP%26%3D%257B%250A%255B%26%3D%257D%250A%255D%26_x%3A0.25%26w%3A1.25%26h%3A2%26w2%3A1.5%26h2%3A1%26x2%3A-0.25%253B%26%3DEnter%26_x%3A0.5%253B%26%3DDelete%26%3DEnd%26%3DPgDn%26_x%3A0.5%253B%26%3D7%250AHome%26%3D8%250A%25E2%2586%2591%26%3D9%250APgUp%26_h%3A2%253B%26%3D%2B%253B%26%40%3DF5%26%3DF6%26_x%3A0.5%26w%3A1.75%253B%26%3DCaps%2520Lock%26%3DA%26%3DS%26%3DD%26%3DF%26%3DG%26%3DH%26%3DJ%26%3DK%26%3DL%26%3D%252F%3A%250A%252F%253B%26%3D%252F%40%250A%27%26%3D%7E%250A%2523%26_x%3A5.25%253B%26%3D4%250A%25E2%2586%2590%26%3D5%26%3D6%250A%25E2%2586%2592%253B%26%40%3DF7%26%3DF8%26_x%3A0.5%26w%3A1.25%253B%26%3DShift%26%3D%257C%250A%255C%26%3DZ%26%3DX%26%3DC%26%3DV%26%3DB%26%3DN%26%3DM%26%3D%253C%250A%2C%26%3D%253E%250A.%26%3D%253F%250A%252F%252F%26_w%3A2.75%253B%26%3DRShift%26_x%3A1.5%253B%26%3D%25E2%2586%2591%26_x%3A1.5%253B%26%3D1%250AEnd%26%3D2%250A%25E2%2586%2593%26%3D3%250APgDn%26_h%3A2%253B%26%3DPEnter%253B%26%40%3DF9%26%3DF10%26_x%3A0.5%26w%3A1.5%253B%26%3DCtrl%26%3DWin%26%3DAlt%26_w%3A8%253B%26%3DSpace%26%3DRAlt%26%3DRWin%26_w%3A1.5%253B%26%3DRCtrl%26_x%3A0.5%253B%26%3D%25E2%2586%2590%26%3D%25E2%2586%2593%26%3D%25E2%2586%2592%26_x%3A0.5%26w%3A2%253B%26%3D0%250AIns%26%3D.%250ADel)

All encoded
    * [Actual link](http://kle.ydkb.io/##@_name=G80-9009HAU&author=YANG¬es=tkg%E7%BD%91%E5%9D%80%EF%BC%9Ahttps%2F:%2F%2F%2F%2Fyang.tkg.io%0A%0A%E5%88%B7%E5%9B%BA%E4%BB%B6%E6%95%99%E7%A8%8B%EF%BC%9Ahttp%2F:%2F%2F%2F%2Fpan.baidu.com%2F%2Fs%2F%2F1sltOsrV%20%E5%AF%86%E7%A0%81%2F:%20ek5h%20%0A%E5%A6%82%E4%BD%95%E5%88%B7%E6%9C%BA%E8%AF%B7%E5%8F%82%E8%80%83%20TKG%E5%9C%A8%E7%BA%BF%E5%88%B7%E6%9C%BA%E6%95%99%E7%A8%8Bv3.0.pdf%20%E4%B8%AD%E7%9A%84%E7%AC%AC%E5%9B%9B%E9%83%A8%E5%88%86%EF%BC%8CRAWHID%E5%9C%A8%E7%BA%BF%E5%88%B7%E6%9C%BA%0A%E5%A6%82%E4%BD%95%E5%88%B6%E4%BD%9C%E5%B8%83%E5%B1%80%EF%BC%8C%E4%BC%9A%E5%88%B7GH60%E7%9A%84%E8%AF%9D%E5%A4%A7%E8%87%B4%E6%98%AF%E7%9B%B8%E5%90%8C%E7%9A%84%EF%BC%8C%E4%B8%8D%E4%BC%9A%E5%88%B7%E8%AF%B7%E5%8F%82%E7%9C%8B%20GH60%E7%AD%89%E9%94%AE%E7%9B%98%E4%BD%BF%E7%94%A8KLE%E5%92%8CTKG%E7%BC%96%E8%BE%91%E9%94%AE%E4%BD%8D%E8%AF%B4%E6%98%8Ev2.0.pdf%0A%0A%E4%BD%BF%E7%94%A8RAWHID%E9%9C%80%E8%A6%81%E4%BD%BF%E7%94%A8%E6%B5%8B%E8%AF%95%E7%89%88%E7%9A%84Chrome%20App%EF%BC%8C%E6%96%87%E4%BB%B6%E5%9C%A8%E5%85%B1%E4%BA%AB%E9%87%8C%EF%BC%8Ctkg-chrome-app-0.8beta-rawhid.crx%3B&@_x:19%3B&=vol%20dn&=vol%20up&_x:0.5%3B&=btn3&=btn1&=mouse%20up&=btn2%3B&@_w:2%3B&=ESC&_x:17&w:2%3B&=MUTE&_x:0.5%3B&=F5&=mouse%20left&=mouse%20down&=mouse%20right%3B&@_y:1&w:2%3B&=ESC&_x:0.5%3B&=ESC&_x:0.5%3B&=F1&=F2&=F3&=F4&_x:0.75%3B&=F5&=F6&=F7&=F8&_x:0.75%3B&=F9&=F10&=F11&=F12&_x:0.5&w:2%3B&=PrtSc&=Pause%0ABreak&_x:0.5%3B&=F9&=F10&=F11&=F12%3B&@_w:2%3B&=ESC&_x:0.5%3B&=Esc&_x:0.5%3B&=F1&=F2&=F3&=F4&_x:0.75%3B&=F5&=F6&=F7&=F8&_x:0.75%3B&=F9&=F10&=F11&=F12&_x:0.5%3B&=PrtSc&=Scroll%20Lock&=Pause%0ABreak&_x:0.5&w:2%3B&=vol%20dn&_w:2%3B&=vol%20up%3B&@_y:0.5%3B&=F1&=F2&_x:0.5%3B&=%C2%AC%0A%60&=!%0A1&=%22%0A2&=%C2%A3%0A3&=$%0A4&=%25%0A5&=%5E%0A6&=%2F&%0A7&=*%0A8&=(%0A9&=)%0A0&=%2F_%0A-&=+%0A%2F=&_w:2%3B&=Backspace&_x:0.5%3B&=Insert&=Home&=PgUp&_x:0.5%3B&=Num%20Lock&=%2F%2F&=*&=-%3B&@=F3&=F4&_x:0.5&w:1.5%3B&=Tab&=Q&=W&=E&=R&=T&=Y&=U&=I&=O&=P&=%7B%0A%5B&=%7D%0A%5D&_x:0.25&w:1.25&h:2&w2:1.5&h2:1&x2:-0.25%3B&=Enter&_x:0.5%3B&=Delete&=End&=PgDn&_x:0.5%3B&=7%0AHome&=8%0A%E2%86%91&=9%0APgUp&_h:2%3B&=+%3B&@=F5&=F6&_x:0.5&w:1.75%3B&=Caps%20Lock&=A&=S&=D&=F&=G&=H&=J&=K&=L&=%2F:%0A%2F%3B&=%2F@%0A'&=~%0A%23&_x:5.25%3B&=4%0A%E2%86%90&=5&=6%0A%E2%86%92%3B&@=F7&=F8&_x:0.5&w:1.25%3B&=Shift&=%7C%0A%5C&=Z&=X&=C&=V&=B&=N&=M&=%3C%0A,&=%3E%0A.&=%3F%0A%2F%2F&_w:2.75%3B&=RShift&_x:1.5%3B&=%E2%86%91&_x:1.5%3B&=1%0AEnd&=2%0A%E2%86%93&=3%0APgDn&_h:2%3B&=PEnter%3B&@=F9&=F10&_x:0.5&w:1.5%3B&=Ctrl&=Win&=Alt&_w:8%3B&=Space&=RAlt&=RWin&_w:1.5%3B&=RCtrl&_x:0.5%3B&=%E2%86%90&=%E2%86%93&=%E2%86%92&_x:0.5&w:2%3B&=0%0AIns&=.%0ADel)
    * [encoded link](http%3A%2F%2Fkle.ydkb.io%2F%23%23%40_name%3DG80-9009HAU%26author%3DYANG)
    * [Http unencoded](http://kle.ydkb.io/##@_name=G80-9009HAU&author=YANG&%26notes%3Dtkg%25E7%25BD%2591%25E5%259D%2580%25EF%25BC%259Ahttps%252F%3A%252F%252F%252F%252Fyang.tkg.io%250A%250A%25E5%2588%25B7%25E5%259B%25BA%25E4%25BB%25B6%25E6%2595%2599%25E7%25A8%258B%25EF%25BC%259Ahttp%252F%3A%252F%252F%252F%252Fpan.baidu.com%252F%252Fs%252F%252F1sltOsrV%2520%25E5%25AF%2586%25E7%25A0%2581%252F%3A%2520ek5h%2520%250A%25E5%25A6%2582%25E4%25BD%2595%25E5%2588%25B7%25E6%259C%25BA%25E8%25AF%25B7%25E5%258F%2582%25E8%2580%2583%2520TKG%25E5%259C%25A8%25E7%25BA%25BF%25E5%2588%25B7%25E6%259C%25BA%25E6%2595%2599%25E7%25A8%258Bv3.0.pdf%2520%25E4%25B8%25AD%25E7%259A%2584%25E7%25AC%25AC%25E5%259B%259B%25E9%2583%25A8%25E5%2588%2586%25EF%25BC%258CRAWHID%25E5%259C%25A8%25E7%25BA%25BF%25E5%2588%25B7%25E6%259C%25BA%250A%25E5%25A6%2582%25E4%25BD%2595%25E5%2588%25B6%25E4%25BD%259C%25E5%25B8%2583%25E5%25B1%2580%25EF%25BC%258C%25E4%25BC%259A%25E5%2588%25B7GH60%25E7%259A%2584%25E8%25AF%259D%25E5%25A4%25A7%25E8%2587%25B4%25E6%2598%25AF%25E7%259B%25B8%25E5%2590%258C%25E7%259A%2584%25EF%25BC%258C%25E4%25B8%258D%25E4%25BC%259A%25E5%2588%25B7%25E8%25AF%25B7%25E5%258F%2582%25E7%259C%258B%2520GH60%25E7%25AD%2589%25E9%2594%25AE%25E7%259B%2598%25E4%25BD%25BF%25E7%2594%25A8KLE%25E5%2592%258CTKG%25E7%25BC%2596%25E8%25BE%2591%25E9%2594%25AE%25E4%25BD%258D%25E8%25AF%25B4%25E6%2598%258Ev2.0.pdf%250A%250A%25E4%25BD%25BF%25E7%2594%25A8RAWHID%25E9%259C%2580%25E8%25A6%2581%25E4%25BD%25BF%25E7%2594%25A8%25E6%25B5%258B%25E8%25AF%2595%25E7%2589%2588%25E7%259A%2584Chrome%2520App%25EF%25BC%258C%25E6%2596%2587%25E4%25BB%25B6%25E5%259C%25A8%25E5%2585%25B1%25E4%25BA%25AB%25E9%2587%258C%25EF%25BC%258Ctkg-chrome-app-0.8beta-rawhid.crx%253B%26%40_x%3A19%253B%26%3Dvol%2520dn%26%3Dvol%2520up%26_x%3A0.5%253B%26%3Dbtn3%26%3Dbtn1%26%3Dmouse%2520up%26%3Dbtn2%253B%26%40_w%3A2%253B%26%3DESC%26_x%3A17%26w%3A2%253B%26%3DMUTE%26_x%3A0.5%253B%26%3DF5%26%3Dmouse%2520left%26%3Dmouse%2520down%26%3Dmouse%2520right%253B%26%40_y%3A1%26w%3A2%253B%26%3DESC%26_x%3A0.5%253B%26%3DESC%26_x%3A0.5%253B%26%3DF1%26%3DF2%26%3DF3%26%3DF4%26_x%3A0.75%253B%26%3DF5%26%3DF6%26%3DF7%26%3DF8%26_x%3A0.75%253B%26%3DF9%26%3DF10%26%3DF11%26%3DF12%26_x%3A0.5%26w%3A2%253B%26%3DPrtSc%26%3DPause%250ABreak%26_x%3A0.5%253B%26%3DF9%26%3DF10%26%3DF11%26%3DF12%253B%26%40_w%3A2%253B%26%3DESC%26_x%3A0.5%253B%26%3DEsc%26_x%3A0.5%253B%26%3DF1%26%3DF2%26%3DF3%26%3DF4%26_x%3A0.75%253B%26%3DF5%26%3DF6%26%3DF7%26%3DF8%26_x%3A0.75%253B%26%3DF9%26%3DF10%26%3DF11%26%3DF12%26_x%3A0.5%253B%26%3DPrtSc%26%3DScroll%2520Lock%26%3DPause%250ABreak%26_x%3A0.5%26w%3A2%253B%26%3Dvol%2520dn%26_w%3A2%253B%26%3Dvol%2520up%253B%26%40_y%3A0.5%253B%26%3DF1%26%3DF2%26_x%3A0.5%253B%26%3D%25C2%25AC%250A%2560%26%3D%21%250A1%26%3D%2522%250A2%26%3D%25C2%25A3%250A3%26%3D%24%250A4%26%3D%2525%250A5%26%3D%255E%250A6%26%3D%252F%26%250A7%26%3D%2A%250A8%26%3D%28%250A9%26%3D%29%250A0%26%3D%252F_%250A-%26%3D%2B%250A%252F%3D%26_w%3A2%253B%26%3DBackspace%26_x%3A0.5%253B%26%3DInsert%26%3DHome%26%3DPgUp%26_x%3A0.5%253B%26%3DNum%2520Lock%26%3D%252F%252F%26%3D%2A%26%3D-%253B%26%40%3DF3%26%3DF4%26_x%3A0.5%26w%3A1.5%253B%26%3DTab%26%3DQ%26%3DW%26%3DE%26%3DR%26%3DT%26%3DY%26%3DU%26%3DI%26%3DO%26%3DP%26%3D%257B%250A%255B%26%3D%257D%250A%255D%26_x%3A0.25%26w%3A1.25%26h%3A2%26w2%3A1.5%26h2%3A1%26x2%3A-0.25%253B%26%3DEnter%26_x%3A0.5%253B%26%3DDelete%26%3DEnd%26%3DPgDn%26_x%3A0.5%253B%26%3D7%250AHome%26%3D8%250A%25E2%2586%2591%26%3D9%250APgUp%26_h%3A2%253B%26%3D%2B%253B%26%40%3DF5%26%3DF6%26_x%3A0.5%26w%3A1.75%253B%26%3DCaps%2520Lock%26%3DA%26%3DS%26%3DD%26%3DF%26%3DG%26%3DH%26%3DJ%26%3DK%26%3DL%26%3D%252F%3A%250A%252F%253B%26%3D%252F%40%250A%27%26%3D%7E%250A%2523%26_x%3A5.25%253B%26%3D4%250A%25E2%2586%2590%26%3D5%26%3D6%250A%25E2%2586%2592%253B%26%40%3DF7%26%3DF8%26_x%3A0.5%26w%3A1.25%253B%26%3DShift%26%3D%257C%250A%255C%26%3DZ%26%3DX%26%3DC%26%3DV%26%3DB%26%3DN%26%3DM%26%3D%253C%250A%2C%26%3D%253E%250A.%26%3D%253F%250A%252F%252F%26_w%3A2.75%253B%26%3DRShift%26_x%3A1.5%253B%26%3D%25E2%2586%2591%26_x%3A1.5%253B%26%3D1%250AEnd%26%3D2%250A%25E2%2586%2593%26%3D3%250APgDn%26_h%3A2%253B%26%3DPEnter%253B%26%40%3DF9%26%3DF10%26_x%3A0.5%26w%3A1.5%253B%26%3DCtrl%26%3DWin%26%3DAlt%26_w%3A8%253B%26%3DSpace%26%3DRAlt%26%3DRWin%26_w%3A1.5%253B%26%3DRCtrl%26_x%3A0.5%253B%26%3D%25E2%2586%2590%26%3D%25E2%2586%2593%26%3D%25E2%2586%2592%26_x%3A0.5%26w%3A2%253B%26%3D0%250AIns%26%3D.%250ADel)
    


(3 layers) Copy raw code, paste it back in the page, "Simple"

Download .c and/or .epp file(s)

Burn firmware.

Assembly instructions:

The installation method is as follows.

    Step 1: Remove the screws on the back of the G80-9009, surrounded by the middle
        and the middle one. A few pieces of that square can not twist.
    Step 2: Raise the keyboard shell, notice the upper and lower parts of the
        keyboard, each have a cable connected to the main PCB.
    Step 3: Remove the two cables.
    Step 4: the link to replace the master put up, the previous pin corresponding to
        the host above the hole, slowly installed, do not bend the original needle.
        After loading into the card is also relatively tight, if you want to fix a
        little more fixed, you can PCB on the J4 and J5 marked square pad to welding.
    Step 5: the original two pin re-plug back to the new master, the bottom of the
        keyboard cable need to re-fold the original bend. In addition, when inserted do
        not crooked. Make sure that all the pins are inserted into the corresponding
        holes. USB, then use the miniUSB line, you can use a long line, you can also use
        an extension line.

    The following figure is to use an extension of the line, the external exposed
    that the small head is microUSB connector, plug a microUSB line can be used.
 
    The rest is to set the button, and burn firmware method gh60 almost, with TKG + KLE,
    full keyboard programmable, support multi-layer layout, support special keys. In
    yang.tkg.io inside, select G80-9009HAU, the bottom will have a link to explain
    how to burn firmware.




---

### Troubleshooting:
Q: Having a small issue with this, everything works perfectly as according to this
image with the exception of the pipe/backslash key. It performs the same action
as #/~ which I have next to my enter key.

A: Please write that key in the format according to http://tkg.io/#help
