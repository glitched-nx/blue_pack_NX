![Banner](/examples/quickReBoot/quickReBoot_banner.png?raw=true)

<h2 align="center" style="color:#3e60ee;">Ultrahand Overlay - Custom Package</h2>

- Dieses Custom Package enthält vordefinierte Reboot-Befehle, die sich auf Boot/INI-Konfigurationseinträge beziehen, die vom `Hekate Bootloader` benötigt werden. Es führt einen sofortigen Neustart vom aktuellen Atmosphere CFW direkt zu Deiner Auswahl über das `Ultrahand Overlay`-Menü durch.

  - Neustart zu einem anderen konfigurierten Switch OS, wie Stock OFW, LineageOS, Lakka, Linux, etc.
  - Neustart zu Payload-Binaries wie TegraExplorer, Lockpick_RCM, Payload Tools, etc.
  - Führe einen direkten Neustart zum aktuellen Atmosphere CFW oder zwischen emuMMC/sysMMC durch.
  - Neustart zu Hekate UMS:
    - Montiere die Switch SD-Karte als USB-Massenspeichergerät.

<h2 align="center" style="color:#3e60ee;">Wie verwende ich quickReBoot?</h2>

- Öffne zuerst das Ultrahand Overlay-Menü, indem Du Deine konfigurierte **Key Combo** oder die Standardkombination **`L+DDOWN+RS`** drückst.
  - Im Ultrahand Overlay drücke den **`Rechts > Richtungstaste`** auf dem linken Joy-Con, um zum Paketmenü zu navigieren, wo Du quickReBoot findest. Drücke **`A`** auf das Paket, um das quickReBoot-Menü zu öffnen.

- Wenn du das Ultrahand Overlay in dein Setup integriert hast, kannst du das quickReBoot-Paket an deine Hekate Bootloader-Konfigurationen anpassen.

- Die folgende Anleitung soll dir helfen, die Konfigurationen, Reboot-Boot-Befehle, Reboot-INI-Befehle, Payloads und andere Konfigurationen in quickReBoot oder bei der Erstellung deines eigenen Ultrahand Overlay-Pakets besser zu verstehen.

<h1 align="center" style="color:#3e60ee;">quickReBoot > Konfigurations-Anleitung</h1>

<h4 align="center" style="color:#3e60ee;">Hekate Bootloader - Beispiele für Boot-Konfigurationseinträge & INI-Dateien mit Boot-Konfigurationseintrag.</h4>

- Die folgenden Beispiele sind grundlegende Hekate Boot-Konfigurationseinträge, deren Bezeichnungen in eckigen Klammern "[ ]" definiert sind. Auf diese Boot-Einträge sind die Boot-Befehle des Pakets gerichtet.

  - #### Booteinträge > `hekate_ipl.ini` > Pfad: `sdmc:/bootloader/`

```ini
[Stock]
fss0=atmosphere/package3
stock=1
emummc_force_disable=1

[Atmo EMU]
fss0=atmosphere/package3
kip1patch=nosigchk
emummcforce=1

[Atmo SYS]
fss0=atmosphere/package3
kip1patch=nosigchk
emummc_force_disable=1
```


<h2 align="center" style="color:#3e60ee;">Boot-INI Dateien</h2>

* * #### Boot-INI > [android.ini](*) > Pfad: [sdmc:/bootloader/ini/](*)

```ini
[LineageOS]
l4t=1
boot_prefixes=switchroot/android/
id=SWANDR
icon=switchroot/android/icon_android_hue.bmp
logopath=switchroot/android/bootlogo_android.bmp
r2p_action=self
ddr200_enable=1
```

* * #### Boot-INI > [lakka.ini](*) > Pfad: [sdmc:/bootloader/ini/](*)

```ini
[Lakka]
l4t=1
boot_prefixes=lakka/boot/
id=SWR-LAK
icon=lakka/boot/icon_lakka_hue.bmp
logopath=lakka/boot/splash.bmp
r2p_action=self
```

<h2 align="center" style="color:#3e60ee;">package.ini - Boot Befehle</h2>

* * #### quickReBoot > [package.ini](*) > Pfad: [sdmc:/switch/.packages/quickReBoot/](*)

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
  - Benutzerdefinierte Bezeichnung, wie sie im Ultrahand Overlay-Menü angezeigt wird. `Stock OFW` bezieht sich auf den direkten Neustart in die Nintendo Switch -`Original Stock Firmware`.

    - `HOS` = `Horizon OS` = `Nintendo Switch - Original Stock Firmware` = `OFW` = `Stock`

- `reboot`
  - Befehl

- `boot`
  - Verweist auf den Hekate Boot-Konfigurationseintrag in `sdmc:/bootloader/hekate_ipl.ini`.

- `Stock (OFW)`
  - Bezieht sich auf die benutzerdefinierte Bezeichnung, die im `hekate_ipl.ini`-File unter dem Boot-Konfigurationseintrag `[Stock (OFW)]` definiert ist. Dieser Bezeichnungsname ist im `package.ini` ohne [eckige Klammern] enthalten.

- #### Hinweis:

  - Der Bezeichnungsname muss exakt übereinstimmen; andernfalls wird der Boot-Eintrag nicht erkannt und Hekate wird geladen.

---

- `[Atmosphere emuMMC]`
  - Benutzerdefinierte Bezeichnung, wie sie im Overlay-Menü angezeigt wird. Bezieht sich auf den direkten Neustart in `Atmosphere emuMMC`. Wenn dies das aktuelle System ist, von dem Du neu starten möchtest, wird ein direkter Neustart durchgeführt.

    - `CFW` = `Custom Firmware` = `Atmosphère` = `AMS` =-> `NX` = `Switch Codename`

- `reboot`
  - Befehl

- `boot`
  - Verweist auf die Hekate Boot-Konfigurationseinträge in `sdmc:/bootloader/hekate_ipl.ini`.

- `Atmosphere (emuMMC)`
  - Bezieht sich auf die benutzerdefinierte Bezeichnung, die im `hekate_ipl.ini`-File unter dem Boot-Konfigurationseintrag `[Atmosphere (emuMMC)]` definiert ist. Dieser Bezeichnungsname ist im `package.ini` ohne Klammern enthalten.

- #### Hinweis:

  - Der Bezeichnungsname muss exakt übereinstimmen; andernfalls wird der Boot-Eintrag nicht erkannt und Hekate wird geladen.

---

<h3 align="center">quickReBoot - INI-Dateien</h3>

- `[LineageOS (Android)]` -> Benutzerdefinierte Bezeichnung, wie sie im Overlay-Menü angezeigt wird. Bezieht sich auf den direkten Neustart in `LineageOS (Android)`.

- `reboot`
  - Befehl

- `ini`
  - Verweist auf die INI-Dateien im Verzeichnis `sdmc:/bootloader/ini/`.

- `LineageOS`
  - Bezieht sich auf die benutzerdefinierte Bezeichnung, die in der Konfigurations-INI-Datei für die Boot-Konfiguration `[LineageOS]` definiert ist. Dieser Bezeichnungsname ist im `package.ini` ohne Klammern enthalten.

#### sdmc:/switch/.packages/quickReBoot/`package.ini`

```ini
[LineageOS - Android]
reboot ini LineageOS
```

- #### Hinweis

  - Der Dateiname `android.ini` ist benutzerdefiniert und kann frei gewählt werden.

---

<h3 align="center" style="color:#3e60ee;">quickReBoot - Payload BIN-Datei</h3>

```ini
[TegraExplorer]
reboot /bootloader/payloads/TegraExplorer.bin
```

- `[TegraExplorer]`
  - Benutzerdefinierte Bezeichnung, wie sie im Ultrahand Overlay erscheint.

- `reboot`
  - **reboot Befehl**

- `/Path/to/the/BIN-file/s/`
  - Benutzerdefiniert auf der SD-Karte. Der vorkonfigurierte ReBoot-Befehl ermöglicht einen direkten Neustart zu einem Payload aus dem Ultrahand Overlay.

---

*Wenn Du diese Anleitung gelesen und verstanden hast, kannst Du nun Boot-Konfigurationen bearbeiten und hinzufügen. Stelle jedoch sicher, dass die Verweise auf die Boot-Konfigurationseinträge, die im Hekate Bootloader definiert sind, korrekt im package.ini definiert sind. Bezeichnungsname, Pfad und Payload BIN-Datei können frei definiert werden. Das Gleiche gilt für die Boot-Konfigurationseinträge und INI-Konfigurationen.*

---

<p align="center">
  <a href="https://github.com/glitched-nx">quickReBoot - Konfigurations-Anleitung geschrieben von glitched-nx</a>
</p>
