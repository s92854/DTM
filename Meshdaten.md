# Einführung von Meshdaten: Erstellung von Wetterkarten
## 1. Daten herunterladen
* Wetterdaten von [Copernikus](https://cds.climate.copernicus.eu/#!/home) herunterladen
* Beispieldaten [hier](https://github.com/s92854/DTM/files/11975547/may2023.zip) herunterladen

## 2. Netzlayer in QGIS laden
* .grib Datei: bei neueren Versionen per Drag&Drop oder Layer > Layer hinzufügen > Netzlayer hinzufügen
* Wenn das Wahlfenster erscheint, die zweite Option mit dem Netzlayersymbol wählen (erste ist als Rasterlayer hinzufügen)
* Falls nichts zu sehen ist: Layergestaltung > Gradient > Farbverlauf ändern --> sinnvolle Farbverläufe für alle drei Gruppen
* Windrichtungen anzeigen: Gruppe 10 metre wind [m/s] Pfeil rechts daneben anklicken

<img width="779" alt="image" src="https://github.com/s92854/DTM/assets/134683810/c506dda5-aac9-40f1-9a00-73c044a2dcd4">

* bei Vektorenoptionen einige Customizations möglich

## 3. Zeitinformationen
Zeitanimation und Beschriftung wie in [Animationen](https://github.com/s92854/DTM/blob/main/Animationen.md) erklärt
* hinzufügen der Uhrzeit
```
'Luftbewegungen' || '\n' || format_date(@map_start_time, 'dd MMMM yyyy') || '\n' || format_date(@map_start_time,'HH:mm') || ' Uhr'
```

## 4. Farbverlauf
* Verlauf für Temperatur in etwa so:

<img width="439" alt="image" src="https://github.com/s92854/DTM/assets/134683810/5d42889c-52fd-4edc-acb8-49f2a00e6046">

## 5. Netzlayer erstellen

![image](https://github.com/s92854/DTM/assets/134683810/78e0cf84-cde5-4eee-8819-59befbaff784)

* Neuen Netzlayer erstellen mit folgendem Ausdruck:
```
 average_aggr (  "2 metre temperature [C]" )
```
