# RLCD-DMG

Ordering and build information for they Bytendo RLCD (Reflective Liquid Crystal Display) DMG display replacement kit. The driver kit is only sold at the [Bytendo Ko-Fi](https://ko-fi.com/bytendo). Please read this README before purchasing.

## What is it?

The Bytendo RLCD DMG kit is an LCD replacement mod, designed to evoke the original Gameboy experience with a modern technology. The RLCD is a 1-bit monochrome display from Sharp, model number LS032B7DD01. The panel is very similar to the one in the Playdate console, but higher resolution. The source data is captured using an RP2040, then integer scaled up and dithered to simulate the Gameboy's 2-bit greyscale. All this happens fast enough to ensure a 60Hz refresh rate with only about 2 frames of lag, similar to IPS kits on the market. If there is enough interest I'll do a comparison.

> [!IMPORTANT]
> * The display is monochrome. It's normally "white" with black pixels, and greyscale is simulated with dithering
> * The display area is smaller than the OEM display.
> * There is no backlight. It's a purely reflective LCD, old school style
> * You must use an aftermarket power board, like the [DMGC PWR](https://github.com/MouseBiteLabs/Game-Boy-DMG-Color/tree/main/DMGC-PWR-01) 
> * The install requires shell modification, similar to Q5 installs. Details below

> [!WARNING]
> The RLCD is not included in the kit; I am not able to resell the panels.

They are currently available on [Aliexpress](https://www.aliexpress.com/item/1005006990424168.html?spm=a2g0o.productlist.main.5.4d197730mSHqFq&algo_pvid=dea5008d-0f81-494d-aab5-6f4624ba662d&algo_exp_id=dea5008d-0f81-494d-aab5-6f4624ba662d-2&pdp_npi=4%40dis%21USD%2132.92%2132.92%21%21%2132.92%2132.92%21%40211b813f17299659042513636eacc5%2112000038968470241%21sea%21CH%212760562420%21X&curPageLogUid=bwWWYRypVC4U&utparam-url=scene%3Asearch%7Cquery_from%3A) and I've also seen them on Ebay. They are extremely thin and liable to break if handled improperly. Please read the entire README to minimize risk.

> [!CAUTION]
> Don't buy the Sharp LS032B7DD02, even though on paper it looks almost the same. The max refresh rate is lower than the 01 panel and frames are dropped.

## How do I install it?

The driver board comes with the firmware installed and all functions are tested. 

## How do I get it?

The driver kit is only sold at the [Bytendo Ko-Fi](https://ko-fi.com/bytendo). Please check price and availability there.

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