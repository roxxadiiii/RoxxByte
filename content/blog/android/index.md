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
## Verify connection
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

# Understanding ADB

ADB stands for `Android Debug Bridge`.It is a tool that lets your computer communicate with your Adnroud phone through a USB cable.
It was Built for developers but anyone can use it.It gives us access to settings and controls that are hidden from the normal Settings app - without rooting our phones.

when we type a command on out computer , out phone listen to it and executes the command. thats ADB in the lamen words.


# Checking Battery Health
this section mostly belong to the users which have old phones and have issues about the low SOT(Screen On Time).
But for fun anybody can run see where your battery actually stands.Run this command

```bash
adb shell dumpsys battery
```
- we will see and output like this:
```
Current Battery Service state:
  AC powered: false
  USB powered: true
  level: 85
  scale: 100
  health: 2
  temperature: 280
```
- What to look for:

| Field | What it means |
|---|---|
| `level` | Current battery percentage |
| `health: 2` | Battery is good |
| `health: 4` | Battery is dead |
| `health: 7` | Battery is overheating |
| `temperature` | Divide by 10 to get °C (280 = 28°C) |

If your health is `2` you are good to go ahead with optimization.
If it is anything else,the battery itself is the problem - no ADB command can fix degraded hardware.

# Debloating
Bloatware are apps that come preinstalled on your phone that we never asked for and probably never use - but they sit in the background,consuming RAM and draining your battery silently.

The good news?? You can remove them withoud root.

## Find the app's package name:

### The Easy Way:

- Install it from playstore [Package name viewer](https://play.google.com/store/apps/details?id=com.csdroid.pkg&hl=en-US&pli=1)

### The Linux Way:

- In shell run:
```
adb shell pm list packages | grep -i "keyword"
```

replace `keyword` with part of the app name.For example:

