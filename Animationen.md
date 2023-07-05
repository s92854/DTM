# Animationen in QGIS - Am Beispiel der Perseiden

## 1. Daten herunterladen
* Mit Hilfe der [Meteormap](https://tammojan.github.io/meteormap/) Meteordaten heraussuchen und die entsprechende [.kml Datei](https://github.com/s92854/DTM/files/11958878/meteors_whole_August.zip) herunterladen

## 2. Daten in QGIS laden und bereinigen
* Layer --> Layer hinzufügen --> Vektordatenlayer hinzufügen

![image](https://github.com/s92854/DTM/assets/134683810/68f33db2-aaed-434d-8034-84739ccf5c9a)

* Layer exportieren und Attributtabelle öffnen
* Alle *NULL* Spalten löschen

![image](https://github.com/s92854/DTM/assets/134683810/088a4056-beb3-4e3d-8922-a6f341b31371)

## 2. Darstellung
* Den Layergestaltungstab einschalten

![image](https://github.com/s92854/DTM/assets/134683810/fe471236-9a5e-4103-a6fb-73f7c786cfc5)

* Design der Meteorschauer (Perseiden) wählen

![image](https://github.com/s92854/DTM/assets/134683810/3edbc214-0634-4c68-bbce-88b409aa1be7)
![image](https://github.com/s92854/DTM/assets/134683810/3f7360d9-35da-4df5-9ccc-b5074cd81918)

* In **Einfache Füllung**, **Zeicheneffekte** wählen
* **Äußeres Glühen**: Standardwerte, Mischmodus: Dunkler

![image](https://github.com/s92854/DTM/assets/134683810/890487fe-7187-496f-8730-916ec4097635)

* Rechtsklick auf **meteors** Layer --> Alle Stile kopieren
* Rechtsklick auf **meteors whole August** Layer --> Alle Stile einfügen

## 3. Zeitliche Animation
* Eigenschaften von **meteors whole August** --> Zeitlich --> Dynamische Zeitsteuerung

![image](https://github.com/s92854/DTM/assets/134683810/246bc012-1fd9-4c7f-b61e-897d10647fa5)

* Zeitsteuerungsfenster einblenden

![image](https://github.com/s92854/DTM/assets/134683810/c9cfaf3c-471c-4fa7-9048-8ee9b31efcf8)

