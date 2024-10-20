![Banner](/examples/quickReBoot/quickReBoot_banner.png?raw=true)

<h2 align="center" style="color:#3e60ee;">Ultrahand Overlay - Custom Package</h2>

- This custom package contains predefined reboot commands referring to boot/INI configuration entries required by the `Hekate Bootloader`. It performs an instant reboot from the current Atmosphere CFW directly to your selection via the `Ultrahand Overlay` menu.

  - Reboot to another configured Switch OS, such as Stock OFW, LineageOS, Lakka, Linux, etc.
  - Reboot to payload binaries like TegraExplorer, Lockpick_RCM, Payload Tools, etc.
  - Perform a direct reboot to the current Atmosphere CFW or between emuMMC/sysMMC.
  - Reboot to Hekate UMS:
    - Mount the Switch SD-Card as a USB Mass Storage Device.

<h2 align="center" style="color:#3e60ee;">How to Use quickReBoot?</h2>

- First, open the Ultrahand Overlay menu by pressing your configured **Key Combo** or the default **`L+DDOWN+RS`**.
  - In the Ultrahand Overlay, press the **`Right > direction Button`** on the left Joy-Con to navigate to the Package menu, where you will find quickReBoot. Press **`A`** on the Package to open the quickReBoot menu.

- If you have integrated Ultrahand Overlay into your setup, you can customize the quickReBoot package to match your Hekate Bootloader configurations.

- The following guide should help you better understand the configurations, reboot boot commands, reboot INI commands, payloads, and other configurations in quickReBoot, or your own Ultrahand Overlay Package creation.

<h1 align="center" style="color:#3e60ee;">quickReBoot > Konfigurations-Anleitung</h1>

<h4 align="center" style="color:#3e60ee;">Hekate Bootloader - Examples for Boot Configuration Entries & Boot INI Files with Boot Configuration Entry</h4>

* * ### Boot Config Entries > [hekate_ipl.ini](*) > Path: [sdmc:/bootloader/](*)

```ini
[Stock(OFW)]
fss0=atmosphere/package3
stock=1
emummc_force_disable=1

[AMS(emuMMC)]
fss0=atmosphere/package3
emummcforce=1
atmosphere=1

[AMS(emuMMC)]
fss0=atmosphere/package3
atmosphere=1
emummc_force_disable=1
```

### Boot-config entry edited in [android.ini](*) located in path [sdmc:/bootloader/ini/](*)

```ini
[LineageOS]
l4t=1
boot_prefixes=switchroot/android/
id=SWANDR
icon=switchroot/android/icon_android_hue.bmp
logopath=switchroot/android/bootlogo_android.bmp
r2p_action=self
ddr200_enable=1

[Lakka]
l4t=1
boot_prefixes=lakka/boot/
id=SWR-LAK
icon=lakka/boot/icon_lakka_hue.bmp
logopath=lakka/boot/splash.bmp
r2p_action=self
```

<h2 align="center" style="color:#3e60ee;">package.ini - boot commands</h2>

- ### Package-configs edited in [package.ini](*) located in path [sdmc:/switch/.packages/quickReBoot/](*)

```ini
[<<>> quickReBoot <<>>]

[Mount UMS SD-Card >>]
reboot UMS

[Reboot >> Hekate]
reboot

[quick >> Shutdown]
shutdown


[ReBoot > Boot-Entry >>]

[Stock OFW]
reboot boot Stock

[Atmo emuMMC]
reboot boot Atmo EMU

[Atmo sysMMC]
reboot boot Atmo SYS


[ReBoot > Boot-INI >>]

[LineageOS 21 / Android 14]
reboot ini LineageOS

[LaKKa]
reboot ini Lakka


[ReBoot > Payload]

[TegraExplorer]
reboot /bootloader/payloads/TegraExplorer.bin

[Reboot > Update]
reboot /bootloader/update.bin
```

---

- `[Stock OFW]`
  - Custom label as it displays in the Ultrahand Overlay menu. `Stock OFW` refers to reboot directly into the Nintendo Switch -`Original Stock Firmware`.

    - `HOS` = `Horizon OS` = `Nintendo Switch - Original Stock Firmware` = `OFW` = `Stock`

- `reboot`
  - Command

- `boot`
  - Points to the Hekate boot-config entry located in `sdmc:/bootloader/hekate_ipl.ini`.

- `Stock (OFW)`
  - Refers to the custom label defined in the `hekate_ipl.ini` file under the boot configuration entry `[Stock (OFW)]`. This label name is included in the `package.ini` without [square brackets]

- #### Note:

  - The label name must match exactly; otherwise, the boot entry will not be recognized and Hekate will be loaded

---

- `[Atmosphere emuMMC]`
  - Custom label as it displays in the overlay menu. Refers to reboot directly into `Atmosphere emuMMC`. If this is the current system you want to reboot from, it will perform a direct reboot.

    - `CFW` = `Custom Firmware` = `Atmosphère` = `AMS` =-> `NX` = `Switch Codename`

- `reboot`
  - Command

- `boot`
  - Points to the Hekate boot-config entries in `sdmc:/bootloader/hekate_ipl.ini`.

- `Atmosphere (emuMMC)`
  - Refers to the custom label defined in the `hekate_ipl.ini` file under the boot configuration entry `[Atmosphere (emuMMC)]`. This label name is included in the `package.ini` without brackets.

- #### Please note:

  - The label name must match exactly; otherwise, the boot entry will not be recognized and Hekate will be loaded

---

<h3 align="center">quickReBoot - INI-files</h3>

- `[LineageOS (Android)]` -> Custom label as it displays in the overlay menu. Refers to reboot directly into `LineageOS (Android)`.

- `reboot`
  - Command

- `ini`
  - Points to the INI-files in the `sdmc:/bootloader/ini/` directory.

- `LineageOS`
  - Refers to the custom label defined in the config INI file for the boot configuration `[LineageOS]`. This label name is included in the `package.ini` without brackets.

#### sdmc:/switch/.packages/quickReBoot/`package.ini`

```ini
[LineageOS - Android]
reboot ini LineageOS
```

- #### Note

  - The file name `android.ini` is user-defined and can be chosen freely

---

<h3 align="center" style="color:#3e60ee;">quickReBoot - Payload BIN-file</h3>

```ini
[TegraExplorer]
reboot /bootloader/payloads/TegraExplorer.bin
```

- `[TegraExplorer]`
  - Custom label as it appears in the Ultrahand Overlay.

- `reboot`
  - **reboot command**

- `/Path/to/the/BIN-file/s/`
  - Custom located on the SD Card. The preconfigured quickReBoot command allow a direct reboot to a payload from Ultrahand Overlay.

---

*If you have read and understood this guide, you can now edit and add boot configurations. However, ensure that the references to the boot configuration entries defined in the Hekate bootloader are correctly defined in the package.ini. Label name, path and payload BIN-file can be freely defined. The same applies to the boot config entries and INI configs*.

---

<p align="center">
  <a href="https://github.com/glitched-nx">quickReBoot - Configuration Guide - Written by glitched-nx</a>
</p>
