Build-Instructions
==================

Building AOKP 4.2.2 for the HP Touchpad

mkdir aokp

cd aokp

repo init -u https://github.com/AOKP/platform_manifest.git -b jb-mr1

repo sync 

(wait for repo to sync)

cd external/tinyalsa 

git pull http://review.cyanogenmod.org/CyanogenMod/android_external_tinyalsa refs/changes/46/33646/1 (needed until merged)

git clone all my repo’s and place them in the directory indicated by the name and rename them appropriately 

. build/envsetup.sh

lunch

pick the number associated with aokp_tenderloin-userdebug

make bootimage

mkimage -A ARM -O Linux -T RAMDisk -C none -n "CM-.. tenderloin Ramdisk" -d /home/***pathto***/aokp/out/target/product/tenderloin/ramdisk.img /home/***pathto***/aokp/out/target/product/tenderloin/ramdisk.ub

mkimage -A arm -O linux -T multi -C none -n "CM-..  tenderloin Multiboot" -d /home/***pathto***/android/aokp/out/target/product/tenderloin/kernel:/home/***pathto***/aokp/out/target/product/tenderloin/ramdisk.ub /home/***pathto***/aokp/out/target/product/tenderloin/boot.img

make -4 otapackage
