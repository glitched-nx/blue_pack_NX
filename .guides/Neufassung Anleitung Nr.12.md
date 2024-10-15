<div style="text-align: center;">
  <h1 style="color: #0055BB;"><strong><em>blue pack NX - AIO CFW PACK</em></strong></h1>
  <p style="color: #0055FF;"><em>- Neufassung - Anleitung Nr.: 12 -- Für den Wechsel / Upgrade zum aktuellen blue pack NX -</em></p>
</div>

*Ziel dieser Anleitung ist es, einen manuellen Wechsel oder ein Upgrade von einem anderen oder älteren Atmosphere CFW-Setup zum `blue pack NX - AIO CFW PACK` mit anschließenden Firmware Update durchzuführen.*

*Vorbereitend sollte ein Teil der vorhandenen CFW-Daten von der SD-Karte bereinigt werden.*

*Wie das geht und welche Daten bereinigt werden, erfährst du in dieser Anleitung. *

---

<div align="center">
<div style="text-align: center; color: red;">VORSICHT</div>
<p style="color: #FF0000;"><em>Formatiere die SD-Karte nicht, da dadurch dein CFW-Setup, deine Spielstände und installierte Spiele unwiderruflich gelöscht werden.</em></p>
<p style="color: #00AA00;"><em>Dein Setup, deine Spiele und Spielstände bleiben unversehrt, wenn du dieser Anleitung folgst.</em></p>
</div>

---

1. *Starte in den Hekate Bootloader und* ***`verbinde deine Switch per USB-Kabel mit dem PC.`***

2. *Aktiviere die `Hekate UMS`-Funktion, um die SD-Karte in deiner Switch als `USB-Massenspeicher` nutzen zu können:*
   - *Navigiere im Hekate-Menü zu `Tools`, wähle `USB Tools` und dann `SD Card`, um die Funktion zu aktivieren.*

3. *Auf deinem PC sollte nun ein Laufwerk mit dem Namen "SWITCH SD" erscheinen. Öffne dieses Laufwerk und positioniere das Fenster so, dass du den gesamten Inhalt im Blick hast.*

4. *Die folgende Ordner- und Dateistruktur zeigt den Inhalt deiner SD-Karte.*
    - *Markierungen geben an, was gelöscht werden soll und was auf der SD-Karte verbleiben soll.*
   - *Der Inhalt entspricht der Grundstruktur der `blue_pack_NX.zip`-Datei.*
   - *Und den Ordnern* ***`emuMMC`*** *und* ***`Nintendo`*** *auf der SD-Karte, die unverändert bleiben.*

5. *Lösche nur die Ordner und Dateien, die mit* `<-[LÖSCHEN]` *gekennzeichnet sind.*
    - ***`Wichtig:`*** *Die Ordner* ***`emuMMC`*** *und* ***`Nintendo`*** *dürfen* ***`NICHT`*** *gelöscht werden.*

---
```ini
[SD-Karte]
|
+---atmosphere        <--[LÖSCHEN]
+---bootloader         <--[LÖSCHEN]
+---config             <--[LÖSCHEN]
|
+---emuMMC              <--[NICHT LÖSCHEN]
+---Nintendo            <--[NICHT LÖSCHEN]
|
+---NSPs (Tools)       <--[LÖSCHEN]
|
+---switch                          [Nicht löschen - falls vorhanden]
|       |                              |  |  |  |
|       |---\                          |  |  |  |
|           JKSV                    <--/  |  |  |
|           Linkalhod               <-----/  |  |
|           tinfoil                 <--------/  |
|           retroarch_switch.nro    <-----------/
|
|---boot.dat          <--[LÖSCHEN]
|---boot.ini          <--[LÖSCHEN]
|---exosphere.ini     <--[LÖSCHEN]
|---hbmenu.nro        <--[LÖSCHEN]
|---payload.bin       <--[LÖSCHEN]
```

- *Ordner und Dateien, die sich zusätzlich auf der SD-Karte befinden, sind für ein Upgrade nicht relevant. Diese gehören vermutlich zu erweiterten Setups wie Android, Lakka etc. und sollten unverändert bleiben, wenn du dir nicht sicher bist.*

- *Öffne das Verzeichnis `switch` und lösche alles außer `tinfoil`, `linkalho` und `JKSV`, da diese wichtige Daten wie Backups und Shop-Adressen enthalten könnten. Falls `retroarch_switch.nro` vorhanden ist und im Hauptverzeichnis Ordner wie `ROMS` existieren, sollten diese nicht gelöscht werden, da die Datei zu Retroarch gehört. Sollten noch weitere Ordner vorhanden sein, die nicht durch das blue pack ersetzt werden, wie Homebrew-Spiele oder Mods, sollten auch diese nicht gelöscht werden.*

---

6. *Kehre anschließend zum Hauptverzeichnis der SD-Karte zurück.*

7. *Lade das neueste blue pack NX [HIER](https://github.com/glitched-nx/blue_pack_NX/releases/latest) herunter.*

8. *Entpacke den gesamten Inhalt der Datei `blue_pack_NX.zip` in das Hauptverzeichnis der SD-Karte. Bestätige die Aufforderung zum Ersetzen von Dateien mit "Ja".*

9. *Die SD-Karte ist nun bereit und kann sicher vom PC entfernt werden.* 
    - *Klicke dazu mit der rechten Maustaste auf das Switch-SD-Laufwerk.*
    - *Wähle "Auswerfen" aus dem Kontextmenü.*
    - *Entferne das USB-Kabel erst nach dem sicheren Auswerfen.*

10. *Wechsle in Hekate zurück zum `Home`-Bildschirm und führe einen Reload durch, indem du den `Reload`-Button unten im Hekate-Homescreen berührst und bestätigst.*

11. *Der Arbeitsspeicher wird durch den Reload mit den neuen Daten der SD-Karte geladen und Hekate wird neu gestartet.*
    - *Nach dem Reload muss die Uhrzeit in Hekate neu eingestellt werden.*

12. *Starte über das Launch-Menü `atmosphere blue emu`.*
    - *Achte darauf, dass die Systemuhrzeit korrekt eingestellt ist. Falls dies nicht der Fall ist, kannst du sie im Homebrew-Menü mit der App `SwitchTime` korrigieren. Starte die App und drücke nacheinander `Y` -> `A` -> `+`, bei aktiver Internetverbindung.*
    - *Hinweis: Stelle die Uhrzeit nicht manuell ein, da Tinfoil sonst den Download verweigert, weil die Uhrzeit falsch ist.*

---

- ***Firmware downloaden und mit `Daybreak Quick` aktualisieren***
    - *Lade die aktuelle Switch Firmware mit dem `NX-Firmware-Loader` im Homebrew Menü herunter.*
    - *Die Firmware wird nach dem Download automatisch entpackt und als `Firmware` Ordner im Hauptverzeichnis der SD-Karte abgelegt.*
    - *Schließe den `NX-Firmware-Loader` mit der **`+`** Taste.*
    - *Zurück im Homebrew Menü.*

- ***Öffne `Daybreak Quick`.***
    - *Wähle **`Weiter`** zum Update.*
    - *Wähle das Verzeichnis mit der `Firmware` aus und bestätige.*
    - *Mit `Update starten` wird der Firmwareupdate-Vorgang sofort gestartet.*
    - *Danach auf `Switch neustarten`, um das Update abzuschließen.*
    - *Hekate wird startet*
    - *Starte `atmosphere blue emu` wieder über das Launch-Menü.*

---

*Deine Switch startet nun mit der aktuellsten CFW und Firmware.*
*Um den aktuellen Stand der System- oder Atmosphere-Version deiner Switch zu überprüfen, öffne die Systemeinstellungen. Navigiere ganz nach unten zu "Konsole" und wähle dann rechts "System-Update" aus.*

*Aktuelle Systemversion* [**1x.x.x**](*) | *blue* [**1.x.x**](*) | *E*

<img alt="GitHub Tag" src="https://img.shields.io/github/v/tag/glitched-nx/blue_pack_nx?style=plastic&logoSize=auto&label=blue pack NX - Aktuellste Release-Version&labelColor=%23abc4ff&color=%230d3ce6">

```
https://github.com/glitched-nx/blue_pack_NX/releases/latest
```
