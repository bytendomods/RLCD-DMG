# RLCD-DMG

Ordering and build information for they Bytendo RLCD (Reflective Liquid Crystal Display) DMG display replacement kit. The driver kit is only sold at the [Bytendo Ko-Fi](https://ko-fi.com/bytendo). Please read this README before purchasing.

## What is it?

The Bytendo RLCD DMG kit is an LCD replacement mod, designed to evoke the original Gameboy experience, but with a much faster pixel response. The RLCD is a 1-bit monochrome display from Sharp, model number LS032B7DD01, which is similar to the one used in the Playdate console. The source data is captured using an RP2040, then integer scaled 2x and dithered to simulate the Gameboy's 2-bit greyscale. All this happens fast enough to ensure a 60Hz refresh rate with about 2 frames of lag, similar to IPS kits on the market.

> [!IMPORTANT]
> * **The RLCD is not included in the kit**; I am not able to resell the panels
> * **The display is monochrome.** It's normally "white" with black pixels, and greyscale is simulated with dithering
> * The display area is **smaller than the OEM** display
> * **There is no backlight**. It's a purely reflective LCD, old school style
> * You must use an **aftermarket power board**, like the [DMGC PWR](https://github.com/MouseBiteLabs/Game-Boy-DMG-Color/tree/main/DMGC-PWR-01) 
> * The install requires **shell modification**, similar to Q5 installs. Details below

The RLCDs are currently available on [Aliexpress](https://www.aliexpress.com/item/1005006990424168.html?spm=a2g0o.productlist.main.5.4d197730mSHqFq&algo_pvid=dea5008d-0f81-494d-aab5-6f4624ba662d&algo_exp_id=dea5008d-0f81-494d-aab5-6f4624ba662d-2&pdp_npi=4%40dis%21USD%2132.92%2132.92%21%21%2132.92%2132.92%21%40211b813f17299659042513636eacc5%2112000038968470241%21sea%21CH%212760562420%21X&curPageLogUid=bwWWYRypVC4U&utparam-url=scene%3Asearch%7Cquery_from%3A) and I've also seen them on Ebay. They are extremely thin and liable to break if handled improperly. Please read the entire README to minimize risk.

> [!CAUTION]
> Don't buy the Sharp LS032B7DD02, even though on paper it looks almost the same. The max refresh rate is lower than the 01 panel and frames are dropped.

## Installation

The install process is similar to other display replacement kits. 

### Shell Trimming

You need to modify the front shell to make space for the panel, following the trimming in the images. There are two posts that need to be removed, and some ridges that might damage the RLCD if the shell is flexed. Below is an example trim of an OEM shell, done using a razor.

![image](img/oem-shell-trim.jpeg)

Another way to do it is to use a file and simple exand the viewing area as shown. You still need to remove the posts.

![image](img/cgs-shell-trim.jpeg)

The prototype shell was milled by a fellow modder, Oldirdey, who offers his custom milling services on the [Gameboy Discord](https://discord.com/invite/gameboy). His work is extremely clean and professional, and any scratches you see in my build are because I did them. The extra space made by the milling is really nice, and I think makes it look super clean. If you are doing an opaque shell though you can get away with hacking at it with a razor and nobody will know your crimes.

### Mounting the RLCD

Once the kit is tested, you can 

The LCD is extremely delicate, and the ribbon is easy to rip off the panel. All of the panels I've recieved had a plastic film on both the front and the back. Leave the front film on until the very last step!

* Clean your workspace so it is free from debris, or anything that might put pressure on the RLCD
* Place a soft lint free cloth, or something similar, over the now clean work space
* Remove only the back plastic film on the RLCD. Leave the front one on.
* Using thin double sided tape, secure the RLCD panel to the bracket. If you attempt to remove the panel once the tape is in place, it's likely to crack the panel
* Flip the bracket so that is RLCD down on the soft cloth. Be sure not to put pressure on the panel.
* Attach the IPS board ribbon to the driver board. Doing this before install minimizes the chances that you damage the RLCD.
* The PCB slides into the bracket from the "top" to the "bottom". Once inserted, you can optionally secure it with a little bit of kapton tape.
* Bend the RLCD ribbon just enough to slide into the FPC on the driver board. Secure the FPC lock.
* Leave the plastic protection film on the front of the RLCD.

## Testing the Driver Board

With the RLCD panel and driver PCB mounted, it's time to test the connections. All driver boards are flashed and tested before shipping, but it's still a good idea to test things.

TODO: Image of the test setup

The RLCD will show a bit of noise (random pixels) when it boots, then it will quickly clear and show the black frame. This means the driver board has booted and is running properly. If you don't quickly see the normal "Nintento" logo, that means the driver board isn't getting a clean GB LCD signal. Usually this is an issue with the 21 pin ribbon from the CPU to the button board. I've found they fail over time with repeated insertions, so be careful. Try reseating this ribbon cable first.

If you see nothing on the RLCD, no noise or anything, then either the board hasn't booted or the RLCD isn't connected properly. Check both the RLCD ribbon and the input to the driver board from the GB.

* Connect the driver board to the IPS board and test to make sure the RLCD is working

### Flashing Firmware

The driver board comes with the firmware installed and all functions are tested. Optionally you can build a debug board to flash future firmware updates, or write fully custom firmware. It's basically a pico, afterall :) The debugger gerbers are [here](debug/BYT_DBG_v0.2.zip).

Here are the steps to flash the firmware using USB.

1. Attach the 10p ribbon to the driver board with the contacts facing the PCB (bottom contacts)
2. Attach the USB-C cable to the debugger cable, don't plug it into your PC yet
3. Insert the 10p ribbon into the debugger board, contacts facing the PCB (bottom contacts). Make sure the ribbon is lined up properly, it can be easy to have it unseat
4. While holding down the BOOTSEL button on the debugger, plug the USB-C cable into your PC

If all goes well, you should see the driver board show up as a mass storage device on your PC. Drag and drop the compiled UF2 file; it will eject itself when finished. After it is ejected you can disconnect all the cables.

## How do I get it?

The driver kit is only sold at the [Bytendo Ko-Fi](https://ko-fi.com/bytendo). At the moment I'll be making them to order, so you will have to register interest.

# Attribution

* [MGB/DMG Schematics](https://github.com/Gekkio/gb-schematics/blob/main/MGB-xCPU/schematic/MGB-xCPU.pdf), by [Gekkio](https://github.com/Gekkio)
  * Used to understand the LCD pinout 
* [DMG Scans](https://bitbuilt.net/forums/index.php?threads/dmg-gameboy-scan.4479/) by [Wesk](https://bitbuilt.net/forums/index.php?members/wesk.1486/)
  * Used to build the RLCD bracket and virtually test fit things
* ["I connected Gameboy LCD to ESP32 and Raspberry Pi. And then ..."](https://www.youtube.com/watch?v=gNlBDF8KRfo&t=411s) YouTube video by kgsws
  * Used to understand the LCD signal and it's nuances
* [jamo_mods](https://ko-fi.com/jamo_mods)
  * For the MGB Breakout Board. First PCB manufactured to connect the MGB to the pico
  * For the software help and debugging frenzy
* [MGGC](https://discord.com/invite/modded-gameboy-club-923851711498551327)
  * For the encouragement, love, and support 

## FAQ

### What about lag?

It's fair to say the lag is somewhere around 2 frames.

The source data from the gameboy is ~60Hz, which means each frame lasts 16.67 milliseconds. The driver captures a whole frame, then the source data is scaled and dithered to a 2x framebuffer in about 4 milliseconds. The data is then sent out to the RLCD in about 10 milliseconds, which means the end to processing takes about 14 milliseconds. Given pixel response times are not instant, it's fair to say that the percieved lag is around 2 frames. 

I've done side by side comparisons, where the data is split and sent to an OEM display and the RLCD kit at the same time. The OEM pixel response time is so slow, any lag introduced by the capture process is basically not noticable.

### What about battery life?

I tested using an an EZ-Flash JR running the iG battery test ROM.

* LADDA 1900 AAs: ~25 hrs
* LADDA 2650 AAs: ~30 hrs

### Is it e-ink?

No
