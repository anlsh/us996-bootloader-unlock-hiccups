LG V20 Unlock/TWRP Install Guide (US996 ONLY)
=======================================

While there are several good guides out there on how to unlock US996, but even so I ran into some (admittedly rather small) hiccups along the way.

<!-- This guide is meant to be absolutely comprehensive. Please feel free to submit pull requests if you run into issues mentioned here. -->
This guide is meant to document some of these hiccups so that others will have a more complete picture of what to expect. Most of this stuff isn't mentioned in the guides I've found online and/or takes a tiny bit of googling to track down.

Check you have the correct model of phone
--------------------------
Unfortunately there are actually two different models of the v20 both with the "US996" model

1. The US Cellular model, which is NOT supported by LG's official unlock tool
2. A "real" US996, which is sold carrier-unlocked and can be easily bootloader-unlocked

With the phone in hand, the most reliable way to check which model you have is [1] to remove the battery and check the sticker on the phone underneath: the US cellular model will be labeled UCL996, whereas a bootloader-unlockable phone will be labeled US996.

Unlocking the phone's bootloader
-------------------------------------

Follow the instructions listed in the "Unlocking the Bootloader" section [here](https://wiki.lineageos.org/devices/us996/install), this describes things pretty much perfectly. If you can't enter fastboot, see Hiccup 2

**Hiccup 0:** After unlocking the bootloader, you'll be greeted with a scary-looking screen saying something about corruption, telling you to lock the bootloader, and saying to hit the power button to pause boot.

I hadn't seen any references to this in any of the guides, so I was pretty spooked when I saw it the first time: don't be. From what I can tell, there is absolutely nothing to fear from this screen. I've never actually tried pausing the boot process though, so maybe be careful not to hit the power button when it pops up.

From what I can tell though, there's no way to bypass this screen: it will appear on every subsequent boot, be it recovery, fastboot, or normal mode. Just an inconvenience really, but nonetheless a bit irritating.

**Hiccup 1:** After unlocking the bootloader, the first boot will be much longer than usual. Give it 2-3 minutes

Installing TWRP
------------------------------------------

You can follow steps 1-9 of the "Installing a Custom Recovery** section of the the [DroidViews tutorial](https://www.droidviews.com/install-twrp-root-lg-v20-us996/) (don't flash SuperSU yet), but keep the following things in mind.

**Hiccup 2:** If you're using the `adb reboot recovery` command to enter fastboot, then for whatever reason this command might simply stop working: for me it started taking me to [this](https://www.blogtechtips.com/wp-content/uploads/2016/08/No-command-pic.jpg) screen.
1. If you want to boot normally, just remove and re-insert the battery.

2. The new behavior may or may not be permanent (at the very least, it doesn't fix itself and I don't care enough to hunt for a fix), but no worries: you can still enter fastboot by holding the volume down buttom for a few seconds and then (while still holding volume down) inserting a usb cable (the other end of which must be connected to a computer). The computer might need to have adb/fastboot (and if you're on windows [ugh] the correct drivers) for this to work, but if you're at this point then you've figured that all out already.

**Hiccup 3:** You need to enter recovery mode **on the very next boot** after flashing TWRP. If you dont, the system will erase TWRP and you might be confused later when you try to enter it and can't. You can always reflash it though, so it's not a big deal

**Hiccup 4:** Trying to enter recovery mode (via the volume + power key combo described in the links) might not bring you to TWRP immediately. Instead I getto the factory reset screen. Just select "yes" twice and you'll be brought to TWRP. Doing so won't actually wipe anything, so don't be afraid to do it now or in the future.

**Hiccup 5:** Upon entering TWRP, you might be greeted (either immediately before or after the slider shown in Step 8 of the DroidViews tutorial) by a screen asking for a "password" (something about encryption). Just press "cancel**, step 9 of the DroidViews tutorial takes care of this.

**Hiccup 6:** After installing TWRP and trying to boot into the normal OS, you might be blocked by a screen which says something about Android being unable to access encrypted data and has a single button telling you to "repair android" or some nonsense.

Dont worry: turn off the phone by popping the battery, then plop it back in and get to fastboot via the volume+power method (adb isn't an option since USB debugging probably has been disabled during step 9).

1. Lock your bootloader by the command(s) described in step 4 of [this webpage](https://www.theandroidsoul.com/relock-bootloader-fastboot-android/) (don't reboot like it tells you to though!)

2. Re-unlock the bootloader as described in step 6 of the [LineageOS tutorial](https://wiki.lineageos.org/devices/us996/install)

3. Reboot to normal OS, everything should work fine (though your device will have been wiped in the process, so you'll have the standard android setup screens to deal with)

Conclusion
-------------------
That describes all of the non-standard issues I dealt with. You can now boot back into TWRP and flash SuperSU (steps 10 onwards of the DroidViews tutorial) to get root access

References
---------------
[[1]](https://www.reddit.com/r/lgv20/comments/7raqby/lg_v20_model_numbers/)
