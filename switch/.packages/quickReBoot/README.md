## quickReLoader - ultraHAND Boot Package

- This package contains commands for quickly reloading or rebooting the Hekate boot/INI configurations to switch between different payloads, such as Atmosphère, Stock, Android, Lakka, etc.
- Quickly reboot to Hekate by mounting the SD card to connect the Switch to the PC as a USB Mass Storage Device.

---

### quickReLoader - config examples

```ini
[OFW Stock]
reboot boot Stock
``` 

`[OFW Stock]` = Display name shown in the overlay menu.

`reboot` = Reboot to Hekate (Command).

`boot` = Points to the boot entries in `sdmc:/bootloader/hekate_ipl.ini`.

`Stock` = Refers to the boot config `[Stock]` entry in the `hekate_ipl.ini` file.

## Example: `sdmc:/bootloader/hekate_ipl.ini`

```ini
[Stock]
fss0=atmosphere/package3
stock=1
emummc_force_disable=1
```

---

```ini
[LineageOS - Android]
reboot ini LineageOS
```

`[LineageOS (Android)]` = Display name shown in the overlay menu.

`reboot` =  Reboot to Hekate (Command).

`ini` = Points to the INI files in the `sdmc:/bootloader/ini/` directory.

`LineageOS` = Refers to the `[LineageOS]` boot config INI file. See the example below!

#### Note: The file name `android.ini` is user-defined and can be chosen freely

## Example: `sdmc:/bootloader/ini/android.ini`

```ini
[LineageOS]
l4t=1
boot_prefixes=switchroot/android/
id=SWANDR
icon=bootloader/res/icon_android_hue.bmp
logopath=bootloader/boot/lineageOS_bootlogo.bmp
r2p_action=bootloader
ddr200_enable=0
usb3_enable=1
```

---

```ini
[TegraExplorer]
reboot /bootloader/payloads/TegraExplorer.bin
```

`[TegraExplorer]` = Display name shown in the overlay menu.

`reboot` = Reboot command with a direct path to payload.

`/bootloader/payloads/TegraExplorer.bin` = Directly reboots into TegraExplorer.
