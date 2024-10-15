## Umzug auf eine größere SD-Karte

Das Ziel dieses Vorgangs ist es, den Speicherplatz der Switch-SD-Karte zu erweitern, um hauptsächlich mehr Spiele speichern zu können. Dabei soll sichergestellt werden, dass installierte Spiele, Spielstände, Profile und der emuMMC, ob als Partition oder als SD-Datei, korrekt auf die neue, größere SD-Karte übertragen werden.

Die Vorgehensweise unterscheidet sich je nachdem, ob der `emuMMC` als `Partition` oder als `SD-Datei` auf der alten SD-Karte vorhanden ist.

Für diese Methode benötigst du [Hekate](https://github.com/CTCaer/hekate/releases/), sowohl zum Sichern als auch zum Wiederherstellen des `emuMMC`. Stelle sicher, dass Hekate auf der SD-Karte vorhanden ist.

### **Anleitung:**

Zuerst solltest du überprüfen, ob du ein dateibasiertes oder partitioniertes emuMMC hast:

1. Wechsle in den RCM-Modus und lade das Hekate-Payload.
    - Wenn du eine `Switch mit ModChip` verwendest, kannst du einfach die Switch einschalten, vorausgesetzt, Hekate ist in `payload.bin` umbenannt und befindet sich zusammen mit `boot.dat` und `boot.ini` im Root-Verzeichnis der SD-Karte.
2. Tippe auf die Schaltfläche `emuMMC`.
3. Unter `emuMMC Info & Selection` überprüfe den Text neben `Type`.
    - Wenn du ein emuMMC hast, sollte dort entweder `SD Raw Partition` oder `SD File` stehen.

-----

#### **Wenn du ein emuMMC `SD-File` oder kein emuMMC verwendest und keine Partition mit Hekate erstellt hast...**

1. Wechsle in den RCM-Modus und lade das Hekate-Payload.
    - Wenn du eine `Switch mit ModChip` verwendest, kannst du einfach die Switch einschalten, vorausgesetzt, Hekate ist in `payload.bin` umbenannt und befindet sich zusammen mit `boot.dat` und `boot.ini` im Root-Verzeichnis der SD-Karte.
2. Navigiere zu `Tools` > `USB Tools` > `SD Card` und verbinde die Switch über USB mit dem PC.
3. Kopiere den Inhalt der SD-Karte auf deinen PC.
4. Greife mit einem SD-Kartenleser oder Ähnlichem auf die neue SD-Karte zu.
5. Formatiere die `neue SD-Karte` in FAT32 (Clustergröße 64Kb) mit einem `Partition Manager` oder einem kleinen Tool wie [SD Formatter](https://www.sdcard.org/downloads/formatter_4/).
6. Kopiere die Dateien vom PC oder direkt von der alten SD-Karte auf die neue SD-Karte.
7. Entferne das `UMS`-Gerät sicher über das Betriebssystem deines Computers.


1. Wechsle in den RCM-Modus und lade das Hekate-Payload.
   - Wenn du eine Switch mit ModChip verwendest, kannst du einfach die Switch einschalten, vorausgesetzt, Hekate ist in `payload.bin` umbenannt und befindet sich zusammen mit `boot.dat` und `boot.ini` im Root-Verzeichnis der SD-Karte.

-----

2. Im Hauptmenü von Hekate, tippe auf `Tools`, dann auf `Backup eMMC`. Stelle sicher, dass `SD emuMMC Raw Partition` unten auf dem Bildschirm auf `ON` gesetzt ist.

3. Sichere sowohl `SD emuMMC BOOT0 & BOOT1` als auch `SD emuMMC RAW GPP`. Beachte, dass der Vorgang für `SD emuMMC RAW GPP` etwas länger dauern kann.

4. Sobald beide Sicherungen abgeschlossen sind, kehre zum Hauptmenü zurück. Navigiere zu `Tools` > `USB Tools` > `SD Card` und verbinde die Switch über USB mit deinem PC.

5. Falls Windows dich auffordert, ein Laufwerk zu formatieren, ignoriere dies. Öffne stattdessen das zugängliche Laufwerk mit dem Inhalt der SD-Karte.

6. Kopiere den gesamten Inhalt der alten SD-Karte auf deinen PC.

7. Bereite die neue SD-Karte wie bei der Ersteinrichtung vor:
   - Lade das aktuelle `blue pack NX` von [diesem Link](https://github.com/glitched-nx/blue_pack_NX/releases/latest) herunter.
   - Entpacke die Datei `blue_pack_NX.zip` in das Hauptverzeichnis der neuen SD-Karte.
   - **Beachte:** Kopiere jetzt noch **KEINE** Daten der alten SD-Karte auf die neue, außer den CFW-Daten aus der ZIP-Datei. Du kannst [blue_pack_nx.zip](https://github.com/glitched-nx/blue_pack_NX/releases/latest/download/blue_pack_nx.zip) oder ein anderes CFW-Paket verwenden, das du bevorzugst.

8. Folge den Anweisungen, um die neue SD-Karte für ein emuMMC-Setup zu partitionieren.

-----

## Partitionieren der SD-Karte für ein emuMMC (Raw Partition - Setup)

- Starte die Switch mit Hekate.

**Achtung:** Die Partitionierung *löscht* alle Daten auf der SD-Karte, *wenn* der Inhalt 2 GB überschreitet! Bleibt er darunter, werden alle Daten zwischengespeichert und nach der Partitionierung wiederhergestellt. Die Ordner `emuMMC` und `Nintendo` werden daher erst nach der Partitionierung auf die neue SD-Karte kopiert.

### Anleitung:

1. Navigiere zu `Tools` > `Partition SD card`.
2. Stelle den `emuMMC (RAW)`-Schieberegler in der Mitte der Leiste auf `29 FULL`.
   - Wenn du eine OLED-Switch verwendest, stelle den `emuMMC (RAW)`-Schieberegler auf `58 FULL`.
   - Falls du später Android und/oder Linux installieren möchtest, partitioniere die SD-Karte hier entsprechend, indem du die Schieberegler während dieses Schritts verschiebst. Wir empfehlen, die Schieberegler für `Android (USER)` und `Linux (EXT4)` auf mindestens 16 GB einzustellen.
3. Navigiere unten rechts zu `Next Step` und wähle im erscheinenden Menü `Start` aus.
   - Für Android: Wähle `Legacy`-Partitionierung für Android 10/11 und `Dynamic`-Partitionierung für Android 13+. Beachte, dass Legacy- und Dynamic-Partitionierung **nicht** miteinander kompatibel sind.

**Warnung:** Wenn die SD-Karte nicht angezeigt wird oder Windows sich über ein nicht lesbares Laufwerk beschwert, formatiere sie nicht! Dies ist wahrscheinlich die emuMMC-Partition. Nach der Partitionierung der SD-Karte wird sie auf dem PC als zwei Laufwerke angezeigt. Verwende das zugängliche Laufwerk. Falls die SD-Karte überhaupt nicht angezeigt wird, stelle sicher, dass du ein USB-Kabel verwendest, das Daten übertragen kann, und überprüfe, ob Windows (falls du es verwendest) einen Laufwerksbuchstaben der FAT32-Partition der SD zugewiesen hat.

![sd_partition_erista](.guides/images/sd_partition_erista.png)

-----

9. Nachdem dies abgeschlossen ist, starte Hekate und navigiere zu `Tools` > `USB Tools` > `SD Card`. Verbinde dann die Switch über USB mit deinem PC.

10. Kopiere das Backup von `sdmc:/backup`, das du zuvor von der alten SD-Karte mit Hekate erstellt und auf deinem PC gespeichert hast, auf die neue SD-Karte.

11. Navigiere auf der neuen SD-Karte zu `sdmc:/backup/<xxxxxxxx>/`. Verschiebe das Verzeichnis `emummc` in das Verzeichnis `/restore` und bleibe im aktuellen Verzeichnis.

**Baumstruktur `(alte) sdmc:/backup/...` vor dem Verschieben:**

```ini
SWITCH SD: (Kopie auf dem PC)
|
backup
    | 
    |   
    \---xxxxxxxx    <--[(1) Öffne das Verzeichnis mit der 8-stelligen Zeichenfolge]
        |       
        +---emummc  <--[(2a) Verschiebe das "emummc" Verzeichnis (mit der Maus) runter auf "restore" (siehe 2b unten)]
        |       rawnand.bin.00   
        |       rawnand.bin.01
        |       rawnand.bin.02
        |       rawnand.bin.03            <--(Anzahl der Files variiert je nach größe der Partition)
        |       rawnand.bin.04
        |       rawnand.bin.05
        |       rawnand.bin.06  
        |       BOOT0
        |       BOOT1
        |       
        \---restore  <--[(2b) Verschiebe es direkt über das "restore" Verzeichnis (lass die Maustaste los)]
            +---partitions
            \---emummc
```

**Baumstruktur `(neue) sdmc:/backup/...` nach dem Verschieben, für Restore:**

```ini
SWITCH SD: (nachher) 
|
backup
    | 
    |   
    \---xxxxxxxx
        |              
        \---restore
            +---partitions
            \---emummc
                    rawnand.bin.00
                    rawnand.bin.01
                    rawnand.bin.02
                    rawnand.bin.03
                    rawnand.bin.04
                    rawnand.bin.05
                    rawnand.bin.06
                    BOOT0
                    BOOT1
```

-----

11. Entferne das `UMS`-Gerät sicher über das Betriebssystem deines Computers.

12. Gehe zu `Tools` und wähle `Restore eMMC`. Stelle sicher, dass die Option `SD emuMMC Raw Partition` unten auf dem Bildschirm auf `ON` gesetzt ist.

13. Beginne mit der Wiederherstellung des Backups, indem du sowohl `SD emuMMC BOOT0 & BOOT1` als auch `SD emuMMC RAW GPP` auswählst. Beachte, dass die Wiederherstellung von `SD emuMMC RAW GPP` etwas länger dauern kann.
    - Es ist entscheidend, dass die Option `SD emuMMC Raw Partition` bei beiden aktiviert ist, um zu vermeiden, dass du versehentlich den sysMMC veränderst.

14. Dein emuMMC ist nun erfolgreich auf der neuen SD-Karte wiederhergestellt. Du kannst es über `Launch` -> `Atmosphere FSS0 emuMMC` in Hekate starten.
