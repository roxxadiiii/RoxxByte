+++
authors = ["Aditya Kumar"]
title = "Android ADB 101"
description = "Android ADB 101 is your no-nonsense guide to make your android usefull again using Android Debug Bridge — no root required. Learn how to optimize battery life, restrict background apps, debloat your device, and tweak performance settings that the standard Android UI never exposes. Whether you're a curious beginner or a tinkerer who loves the terminal, these simple ADB commands will give you real control over your Android device. Your battery will thank you."
date = 2026-04-06
[taxonomies]
tags = ["linux","terminal","android","aosp","adb","custom-rom"]
[extra]
toc = true
hot = true
toc_inline = true
toc_ordered = true
trigger = " Try these on your own risk — always know the revert command before you apply anything."
+++
# Prerequisites
## On you Computer
- Make sure `android-sdk-platform-tool` , `android-tools` and `android-udev` or equivalent should be installed in your computer and you can whoogle it if you want to install it for your favorite distros.
- A working USB cable
- Terminal / Command Prompt access
## On your Android Device
- Go to `Settings -> About Phone`
- Tap `Build Number` more than 7 times to unlock Developers options
- Go to `Settings -> Developers Options` 
- Enable `USB debugging`
## verify connection
- once plugged your phone in your PC , run this in your terminal 
```bash
adb devices
```
- You should see your device listed like below:
```
List of devices attached
XXXXXXXX    device
```
- If it says `unauthorized` - check your phone screen and tap `Allow` on the phone.

- Now you are ready to soft brick your device............. Just kidding

