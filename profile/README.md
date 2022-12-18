Team Denominators
=======================
[WebSite]()

This project includesAndroid fullstack which involves our own Custom Android OS and an Application.

# PandoraOS

- A free and open-source aftermarket distribution, based on the Android Open-Source Platform(AOSP), aiming to give you the cleanest possible alternative and a perfectly stable, smooth and beautiful experience right out of the box.


### Problem Statements
- In some devices like Realme and Xiaomi, while setting up these devices for the first time, the software asks the user for a consent in order to provide personalised ads based on the user content. This implies that the user will not have any idea about the information that will be sent to the OEM.
- In most of android devices, OEMs provide extra services or frameworks that run during the background of userspace, which drains a lot amount ouf the battery thus decreasing life expectancy of the android device.
- The extra bloatware applications and servies that are provided in many distributions tend to introduce UI glitches and lags that slows down the system.

- We aim to
    - Work on the ROM to make it extremely stable; we believe in the user not facing any issues regarding their device, flash and forget.
    - To be really minimalistic and beautiful right out of the box. We merge patches from master and other sources to give you the best performance out of your device.
    - Ship without any sort of bloat, and many hardening patches are in the process of being merged to give you the most secure and bloatfree experience possible.
    - Provide AOSP security patches, Linux and CodeAurora tags being merged within hours of its release, you are sure to receive the latest security fixes and updates on your device as soon as possible!
- Source Code is publicly available to sync and compile at our [GitHub Organization](https://github.com/Team-Deno).

# Robust Battery App
[![Android CI](https://github.com/ProjectRobust/RobustBatteryService/actions/workflows/android.yml/badge.svg)](https://github.com/ProjectRobust/RobustBatteryService/actions/workflows/android.yml)
<br/><br/>
[Source Code](https://github.com/ProjectRobust/RobustBatteryService)
<br/>

- This is our inline app that we ship with the OS itself.
- Our app Robust Battery shows information such as the condition of the device, device temperature, voltage and current while charging the device.
- All of the information is displayed without using any third party API and using Android’s default BatteryManager system service.
- This app is a foreground service which means it will run in foreground on top of the background thread layer and display important info via notification. We have plans to add more information to our notification service like temperature, voltage, current and estimated time of charge and discharge, etc.
- Now you might think that since our app runs always in the foreground there might be two most common issues related to the app.
    - First, the app might consume more battery since it is always running. But it doesn’t. Since most of the information displayed via notification channel is text and the whole data is taken from Android’s native SystemServiceManager so BatteryUsage is minimal.
    - Second, you might think that our app might take in permissions, we do not. We plan to use Android’s own local database to store the usage patterns and not track it.

## PandoraOS CodeBase
**The repositories below are listed according to decreasing priorities.**
<br/>
**The testing device used for bringup of Custom ROM is Redmi Note 8(Codename :- ginkgo).**

[ci_scripts](https://github.com/Team-Deno/scripts) :- This repository contains the shell script that is used by the CI to build PandoraOS. The script is made specifically for ginkgo device. The script downloads and checks out the source code, the script also has an option to give your build updates on telegram. The script asks for necessary build flavors that are needed according to the user.

[platform_manifest](https://github.com/Team-Deno/platform_manifest) :- The initial repository of AOSP project, it contains the list of repositories tracked from [android.googlesource.com](http://android.googlesource.com) and additional repositories tracked from our own organization.
This repository is used to download the source code of AOSP. Since there are more than 1000 repositories that are required for building android, rather than cloning each repository individually, the ‘repo’ command enables us to sync these repositories in one go. The ‘repo’ package finds a default.xml on the given remote in order to start syncing the repositories, this default.xml can track other XMLs for more additional repositories that may be required for device specific configurations.
