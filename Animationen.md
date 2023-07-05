# Animationen in QGIS - Am Beispiel der Perseiden

## KML Version

## 1. Daten herunterladen
* Mit Hilfe der [Meteormap](https://tammojan.github.io/meteormap/) Meteordaten heraussuchen und die entsprechende [.kml Datei](https://github.com/s92854/DTM/files/11958878/meteors_whole_August.zip) herunterladen

## 2. Daten in QGIS laden
* Layer > Layer hinzufügen > Vektordatenlayer hinzufügen

![image](https://github.com/s92854/DTM/assets/134683810/68f33db2-aaed-434d-8034-84739ccf5c9a)

## 3. Darstellung
* Den Layergestaltungstab einschalten

![image](https://github.com/s92854/DTM/assets/134683810/fe471236-9a5e-4103-a6fb-73f7c786cfc5)

* Design der Meteorschauer (Perseiden) wählen

![image](https://github.com/s92854/DTM/assets/134683810/3edbc214-0634-4c68-bbce-88b409aa1be7)
![image](https://github.com/s92854/DTM/assets/134683810/3f7360d9-35da-4df5-9ccc-b5074cd81918)

* In **Einfache Füllung**, **Zeicheneffekte** wählen
* **Äußeres Glühen**: Standardwerte, Mischmodus: Dunkler

![image](https://github.com/s92854/DTM/assets/134683810/890487fe-7187-496f-8730-916ec4097635)

* Rechtsklick auf **meteors** Layer > Alle Stile kopieren
* Rechtsklick auf **meteors whole August** Layer > Alle Stile einfügen

## 4. Zeitliche Animation
* Eigenschaften von **meteors whole August** --> Zeitlich --> Dynamische Zeitsteuerung

![image](https://github.com/s92854/DTM/assets/134683810/246bc012-1fd9-4c7f-b61e-897d10647fa5)

* Zeitsteuerungsfenster einblenden

![image](https://github.com/s92854/DTM/assets/134683810/b39d905e-6c68-4770-b311-45f5f7d37b14)

* Auf Animierte Zeitnavigation umstellen, und 1,0 Tage statt Stunden einstellen

![image](https://github.com/s92854/DTM/assets/134683810/a9fbab00-eabc-4174-89ff-356a4e0252c5)

* Über goldenes Zahnrad ist Bildrate (fps) einstellbar (am besten 2-4)

## 5. Animation speichern

![image](https://github.com/s92854/DTM/assets/134683810/4d97fb27-7c9a-4a30-b5ab-c1725e1faed5)

## 6. Temporären Layer erstellen
* Über Layer > Layer erstellen > Temporären Layer erstellen (hier Name: legende)

![image](https://github.com/s92854/DTM/assets/134683810/e961a435-bf89-4e8f-8b9e-2b4e687f3e79)

* Rechts neben dem Editierstift: Punktobjekt hinzufügen
* Punkt bei Großbritanien hinzufügen

![image](https://github.com/s92854/DTM/assets/134683810/081c7d8b-c143-4f93-9a54-827cc5ba625b)

* Layergestaltung > Beschriftungen > Einzelne Beschriftung > Ausducksdialog

![image](https://github.com/s92854/DTM/assets/134683810/d65f2286-a62b-46da-ac64-c1b0ceae32a2)

Ausdruck eingeben:
```
'Sternschnuppen' || '\n' || format_date(@map_start_time, 'dd MMMM yyyy')
```

## 7. Design
* Passende Schrift, Schriftgröße, Schriftfarbe, etc. vergeben
* Farbe des Punktes auf transparent stellen

![image](https://github.com/s92854/DTM/assets/134683810/6d243785-3e22-4e70-b26d-1aacd5190da9)

## 8. Schriftanimation
* Eigenschaften **Legende** Layer > Zeitlich > Dynamische Zeitsteuerung
* Umstellen auf **Nur Layer neuzeichnen**
* Layer als Shapedatei exportieren

## 9. Urheberrechtsnachweis hinzufügbar
* Schriftart, -farbe, etc., sowie den Urhebertext anpassen

![image](https://github.com/s92854/DTM/assets/134683810/bc36c361-59f6-4b99-8596-2b9c2d4f71ca)

## 10. Photoshop: Stapelskripting
* In Photoshop: Datei > Skripten > Deien in Stapel laden
* Alle (29) Bilder der Animation auswählen

![image](https://github.com/s92854/DTM/assets/134683810/10e453c8-c17a-4258-995e-bbfca33d5a9a)

* In QGIS: Neue Variante der Animation erstellen
  * Warum auch immer werden die Zeicheneffekte nicht mit exportiert
* In Photoshop: Animationen2 als Batch reinladen
* Fenster > Zeitleiste einblenden
* Zeitleiste auf Frame-Animation umstellen
* Frame-Animation erstellen > 3 Striche > Frames aus Ebenen erstellen

![image](https://github.com/s92854/DTM/assets/134683810/c388ba86-53fb-41b8-bdb0-72a06370cab7)

* Um Animation zu verlangsamen: Alle Frames auswählen > bei einem Pfeil nach unten > gewünschte Anzeigedauer einstellen
* Für Umkehr der Animation: Drei Striche > Frames umkehren

![image](https://github.com/s92854/DTM/assets/134683810/7e7f0dcb-6313-4ff5-b0bc-10068299a783)

* Export: Datei > Export > Für Web speichern

## Endergebnis

![Animation_slow](https://github.com/s92854/DTM/assets/134683810/479c8b2a-94bc-4060-8cd2-1b7effb3fc52)

&nbsp;

## CSV Version

[//]: # (Timestamp Video: 01:43:00 - ca. 01:46:00)
[//]: # (--> warum genau die Daten?)

## 1.
* neues Projekt in QGIS erstellen
* gerade heruntergeladene [Meteordaten]() als .csv Datei mit Punktgeometrie einfügen

![image](https://github.com/s92854/DTM/assets/134683810/7fa97f44-57e1-4cae-a4f8-76b1d9b3f5d8)

* Layergestaltung > **Einfach Markierung** in **Geometriegenerator** ändern
* Geometrietyp: LineString/MultiLineString
* Abfrage einfügen:

```
make_line($geometry, make_point("LonEnd", "LatEnd"))
```

