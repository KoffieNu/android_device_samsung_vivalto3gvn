Copyright 2014 - The CyanogenMod Project
===================================

Device configuration for Samsung Galaxy V SM-G313HZ (vivalto3gvn)

		instruction how to build

I think you already set up build enviroment so I will skip this.
First go to your working dir/build/tools/device and open in gedit makerecoveries.sh
Find line 
		make -j16 recoveryzip
and replace it with
		make recoveryzip
beacause it wont eat your RAM and build will be faster


After you finshed repo sync go in your working dir/device/
and create folder /samsung/vivalto3gvn and copy content of vivalto3gvn
that you downloaded from here.

For build recovery, run this command in terminal from your working dir 

		. build/envsetup.sh
		lunch cm_vivalto3gvn-userdebug && make recoveryimage

Your build will start and you will find your recovery.img in your working dir/out/target/product/vivalto3gvn

To make it flashable via ODIN you have to make it recovery.tar.md5
Navigate with terminal where you save your recovey.img .
For example cd android/out/target/product/vivalto3gvn
where android is name of your working dir
and run command:

		tar -H ustar -c recovery.img > recovery.tar
		md5sum -t recovery.tar >> recovery.tar
		mv recovery.tar recovery.tar.md5
        
An now you got recovery.tar.md5 ready to be flashed usin ODIN selected as PDA file

And for build rom, run this command in terminal from your working dir 

		. build/envsetup.sh && brunch vivalto3gvn

Good luck and Happy building. (^_^)/



To apply patches 
for example:  audio.patch
 got to frameworks/av  copy the patch in that directory and open 
terminal and run command 
where 1st command is to apply patch and 
the 2nd for to revert the patches which applied earlier

		patch -p1 < audio.patch
		patch -R -p1 <audio.patch

# Patches for vivalto3gvn

NOTE: To download these patches as plain text, add *.patch* suffix to the link.

* [external/sepolicy](https://github.com/ngoquang2708/android_external_sepolicy/compare/ngoquang2708:f00429df5685a46aa4f4694dab8f68d6d5645cd0...cm-13.0)
* [external/tinyalsa](https://github.com/ngoquang2708/android_external_tinyalsa/compare/ngoquang2708:2bfd5e839b369c09c549cb92030a3bc56e40afb1...cm-13.0)
* [frameworks/av](https://github.com/ngoquang2708/android_frameworks_av/compare/ngoquang2708:fbef511c958b5f1b3e015d032dcac4ed7cc84876...cm-13.0)
* [frameworks/base](https://github.com/ngoquang2708/android_frameworks_base/compare/ngoquang2708:80b060dcd0e7fea444a4745932e09cd1b35d306b...cm-13.0)
* [frameworks/native](https://github.com/ngoquang2708/android_frameworks_native/compare/ngoquang2708:508eb7749a4ce988d4d1a97377254add24b9bc40...cm-13.0)
* [frameworks/opt/telephony](https://github.com/ngoquang2708/android_frameworks_opt_telephony/compare/ngoquang2708:a94ae667a6cefaef2f4c87787dafabdd5458f047...cm-13.0)
* [hardware/libhardware](https://github.com/ngoquang2708/android_hardware_libhardware/compare/ngoquang2708:397277cc4ee0764184d3a5eaeea9f3dd26c996ab...cm-13.0)
* [system/core](https://github.com/ngoquang2708/android_system_core/compare/ngoquang2708:64caba3c021a9b86f093476b343df9bd3d3a4dbb...cm-13.0)
* [system/media](https://github.com/ngoquang2708/android_system_media/compare/ngoquang2708:92d65f3fd2fdf37b3593ba60a50cd5f551e7f238...cm-13.0)
* [Patch for OpenGAPPS (included in frameworks/base)](https://github.com/TeamExodus/frameworks_base/commit/9c36be651e83fb039a262682839bd920b033007a)
