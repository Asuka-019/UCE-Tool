# UCE Tool

[简体中文](README.zh-CN.md) | [English](README.en.md) | **Deutsch** | [日本語](README.ja.md) | [Français](README.fr.md)

UCE Tool ist die Desktop-Anwendung für USB-C Explorer. Sie bietet Live-Messwerte, E-Marker-Abfragen, PD-Erkennung und -Aufzeichnung, Geräteeinstellungen für Farben sowie Firmware-Updates.

## Installation und Verbindung

Laden Sie das passende Windows- oder macOS-Paket von der [Release-Seite](https://github.com/Tamako-zz/UCE-Tool/releases/latest) herunter. Entpacken und starten Sie die Windows-Anwendung bzw. installieren Sie die Mac-App im Ordner „Programme“.

Verbinden Sie das Gerät über ein datenfähiges USB-Kabel mit dem Computer. Klicken Sie links auf die Gerätekarte, um die Verbindung herzustellen. Ein erneuter Klick auf die verbundene Karte trennt die Verbindung; ein Klick auf eine andere Karte wechselt das Gerät. Die Gerätesuche stellt keine automatische Verbindung her.

## Dashboard

Öffnen Sie das **Dashboard** und klicken Sie auf das Startsymbol, um Messwerte und Kurven anzuzeigen. Über die Kanalsteuerung lassen sich Kurven auswählen, Abtastrate und Zeitbereich ändern sowie die Aufzeichnung anhalten oder löschen.

## E-Marker

Schließen Sie das Kabel entsprechend der Gerätebeschriftung an und öffnen Sie **E-Marker**. Klicken Sie auf **Lesen**, um die gemeldeten Kabeldaten anzuzeigen. Die kontinuierliche Abfrage starten und beenden Sie mit derselben Schaltfläche. Entfernen Sie vor der kontinuierlichen Abfrage entsprechend dem Hinweis der Anwendung angeschlossene Verbraucher vom Ausgang.

Unter **Erkennungsverlauf** finden Sie die Ergebnisse dieser Sitzung. Sie können sie nach Excel exportieren oder löschen. Nicht gemeldete oder nicht erkannte Felder werden als unbekannt angezeigt.

## PD-Erkennung

Schließen Sie das zu prüfende Ladegerät an und öffnen Sie **PD-Erkennung**. Starten Sie die Erkennung, lesen und bestätigen Sie die Warnung. Die Seite zeigt PDOs und ihre einzelnen Prüfergebnisse; mit derselben Schaltfläche lässt sich eine laufende Prüfung stoppen. Der Verlauf kann angezeigt, nach Excel exportiert oder gelöscht werden.

**Während der Prüfung kann die Spannung steigen. Trennen Sie vor dem Start alle Verbraucher vom Ausgang.**

## PD-Analysator

Verbinden Sie die Prüfschaltung gemäß den Anschlussmarkierungen des Geräts. Öffnen Sie den **PD-Analysator** und starten Sie die Aufzeichnung; dieselbe Schaltfläche beendet sie. Wählen Sie ein Paket aus, um darunter Header und Datenobjekte anzusehen. Die Trennlinie zwischen Liste und Details ist verschiebbar.

Mit dem GoodCRC-Schalter lassen sich GoodCRC-Pakete ein- und ausblenden. Der Excel-Export enthält auch ausgeblendete GoodCRC-Pakete.

## Themenkonfiguration

Wählen Sie mit den Pfeilen eine Geräteansicht und klicken Sie auf einen Farbbereich oder die Hintergrundfarbe.

- **Standard wiederherstellen** setzt die Farben zurück.
- **Vom Gerät lesen** lädt die aktuellen Farben.
- **Auf Gerät anwenden** wendet die Farben vorübergehend an.
- **Auf Gerät speichern** behält die Farben auch nach einem Neustart bei.

## Firmware und Einstellungen

Öffnen Sie **Firmware-Update**, rufen Sie die verfügbaren Versionen ab und wählen Sie die passende Firmware. Folgen Sie den Hinweisen und halten Sie das Gerät bis zum Abschluss verbunden und eingeschaltet.

In den Einstellungen können Sie die Sprache ändern und Geräteinformationen anzeigen. Über die Seitenleiste wechseln Sie zwischen hellem und dunklem Modus. Aufzeichnungen gelten für die aktuelle Sitzung und sollten bei Bedarf vor dem Schließen exportiert werden. Ist das Gerät beschäftigt, beenden Sie zunächst andere Prüfungen oder Aufzeichnungen.

## Weitere Hinweise

### Anwendung starten und Gerät verbinden

Die Anwendungspakete für Windows und macOS benötigen für die normale Verwendung keine separate Python-Installation. Wählen Sie auf dem Mac das Paket für Apple Silicon oder Intel. Falls macOS den ersten Start blockiert, prüfen Sie die Herkunft und erlauben Sie die App unter **Systemeinstellungen → Datenschutz & Sicherheit**.

Verbinden Sie die Datenschnittstelle des Geräts mit dem Computer. Ein reines Ladekabel kann das Gerät mit Strom versorgen, ohne eine Datenverbindung herzustellen. Die Seitenleiste zeigt Gerätename, verkürzte Seriennummer und APP-Version; die vollständige Seriennummer steht in den Geräteinformationen. Im BOOT-Modus ist eine Firmware-Wiederherstellung möglich, für Messung und Erkennung muss die Geräteanwendung laufen.

### Dashboard ablesen

VBUS bezeichnet die Spannung, IBUS den Strom und POWER die Leistung. D+ / D− und CC1 / CC2 zeigen die jeweiligen Signalspannungen. Für Spannung, Strom und Leistung gelten getrennte Skalen. Bewegen Sie den Mauszeiger über das Diagramm, um Messpunkte anzusehen; `--` bedeutet, dass an dieser Stelle kein Wert vorliegt.

Die Abtastrate ist auf 1, 10 oder 50 Messungen pro Sekunde einstellbar, der angezeigte Zeitraum auf 10, 30, 60 oder 120 Sekunden. Beim Anhalten bleibt die Anzeige stehen; beim Fortsetzen werden wieder Messwerte aufgenommen. Löschen entfernt den angezeigten Verlauf.

### E-Marker- und PD-Ergebnisse

Welche E-Marker-Felder verfügbar sind, hängt vom Kabel und von der Firmware ab. Angezeigt werden können Kabeltyp, Strom, maximale Spannung, Datenrate, PD-Version, TBT, EPR sowie Länge oder Latenz. Eine aus der Latenz geschätzte Länge ist keine physische Messung. Die E-Marker-Rohdaten stehen unterhalb der Kabelinformationen.

Die PD-Erkennung liest die angebotenen PDOs und zeigt einzelne Prüfzustände, sofern die Firmware sie meldet. Ein angebotenes Profil bedeutet nicht automatisch, dass dessen Prüfung bestanden wurde. Mit den Reitern über den Ergebnissen wechseln Sie zwischen Ergebnis und Verlauf. Falls eine Funktion nicht unterstützt wird, verwenden Sie eine passende Gerätefirmware.

Die E-Marker- und PD-Verläufe gelten für die aktuelle Sitzung. **Verlauf löschen** entfernt die aktuelle Liste; der Excel-Export erstellt eine `.xlsx`-Datei. Speichern Sie benötigte Ergebnisse vor dem Schließen.

### PD-Aufzeichnungen lesen

Die Tabelle zeigt unter anderem Nachrichtentyp, SOP-Kanal, Nachrichten-ID, Richtung, Objektanzahl, PD-Revision, verstrichene Zeit, Spannungs-/Strommesswert, Rohdaten und Hinweise. Nach Auswahl einer Zeile werden Header und verfügbare Datenobjektfelder darunter aufgeschlüsselt. Bei vielen Feldern kann der Detailbereich horizontal und vertikal gescrollt werden.

Attach und Detach sind Verbindungsereignisse; Hard Reset ist ein Rücksetzereignis auf der überwachten PD-Verbindung. Kann die Bedeutung eines Feldes nicht sicher bestimmt werden, können Rohwerte angezeigt werden. Bei Kabelnachrichten wird die Kommunikation zwischen Port und Stecker angegeben, wenn der genaue Sender nicht bekannt ist.

Das Ausblenden von GoodCRC betrifft nur die Anzeige: Der Excel-Export enthält auch diese Pakete.

### Farben und Firmware

Ändern Sie Farben zunächst in der Vorschau. **Auf Gerät anwenden** dient zur vorübergehenden Kontrolle; mit **Auf Gerät speichern** bleiben sie nach dem Ausschalten erhalten. **Vom Gerät lesen** ersetzt die Vorschau durch die aktuellen Gerätefarben; **Standard wiederherstellen** setzt die Werte im Editor zurück.

Rufen Sie für ein Firmware-Update die Versionen ab, wählen Sie ein zum Gerät passendes Paket und beachten Sie Fortschritt und Ergebnis. Trennen Sie währenddessen weder Strom noch Datenkabel. Die Aktualisierung der UCE-Tool-Anwendung selbst ist ein separater Vorgang im Menü „Über“.

### Fehlerbehebung

- **Kein Gerät sichtbar:** Stromversorgung, Datenkabel und Anschluss prüfen und erneut verbinden. Eine angezeigte Karte muss angeklickt werden.
- **Gerät beschäftigt:** andere E-Marker-Abfragen, PD-Erkennungen, Aufzeichnungen oder Updates beenden und deren Abschluss abwarten.
- **Kein E-Marker-Ergebnis:** Kabel und Anschluss prüfen. Nicht jedes Kabel besitzt einen E-Marker; manche Daten werden nicht gemeldet.
- **Keine Pakete sichtbar:** Geräteverbindung, gestartete Aufzeichnung und Prüfanschlüsse prüfen. Prüfen, ob GoodCRC ausgeblendet ist.
- **Update oder Export fehlgeschlagen:** angezeigten Fehler, Speicherplatz, Firmwareauswahl und Verbindung prüfen und erneut versuchen.
