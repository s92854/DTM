# Ursprungslinien
## Vorbereitung
### 1. Daten von [unhcr](https://www.unhcr.org/refugee-statistics/download/?url=J4giYT) oder direkt als [.csv Datei](https://github.com/s92854/DTM/files/11703394/query_data.zip) herunterladen.

<img width="914" alt="image" src="https://github.com/s92854/DTM/assets/134683810/900b1c77-8a9a-44d0-bd21-920bd20f7130">

### 2. [Daten](https://github.com/s92854/DTM/files/11703469/ne_110m_admin_0_countries.zip) von [Natural Earth](https://www.naturalearthdata.com/downloads/110m-cultural-vectors/) herunterladen
<img width="476" alt="image" src="https://github.com/s92854/DTM/assets/134683810/af5d6b86-93ef-46bd-b327-ccf7fcc90668">


## In QGIS
### 1. CSV Datei hinzufügen
<img width="656" alt="image" src="https://github.com/s92854/DTM/assets/134683810/47db4686-728c-4bdb-a776-117682d9fe3a">

### 2. Natural Earth Daten mit Flüchtlingsdaten verknüpfen
<img width="623" alt="image" src="https://github.com/s92854/DTM/assets/134683810/4750adcd-950d-4e4d-b369-8d32536f0761">

### 3. Zentroide erstellen
* Vektor -> Geometriewerkzeuge -> Zentroide
<img width="869" alt="image" src="https://github.com/s92854/DTM/assets/134683810/d4009b62-8f98-4192-9422-1e7b5cd40b11">

### 4. Attributtabelle der Zentroide bearbeiten
<img width="656" alt="image" src="https://github.com/s92854/DTM/assets/134683810/32a5d5d3-d4a7-406e-b412-be143ebf1c53">

* Alle Löschen, bis auf die letzten 5 (Year, Country of Origin, Country_1, Country_2, Refugees under UNHCR's mandate)

<img width="525" alt="image" src="https://github.com/s92854/DTM/assets/134683810/845f93e0-d3ae-4f8b-9906-2766a52ece47">

* Spalten, die alle *NULL* sind, löschen
  - entweder in Attributtabelle manuell sortieren und selektieren, oder durch Ausdruck wählen

```
"Refugees under UNHCR's mandate" > 0
```

### 5. Anpassungen

* Country_2 Namen ändern
  - Bolivia (Plurinational State of) --> Bolivia
  - United Kingdom of Great Britain and Northern Ireland --> UK
  - Serbia and Kosovo: S/RES/1244 (1999) --> Serbien

* Frankreich, Norwegen verschieben
<img width="502" alt="image" src="https://github.com/s92854/DTM/assets/134683810/43468025-5163-4807-af45-f7a987edd97d">

### 6. x und y Koordinaten berechnen

<img width="634" alt="image" src="https://github.com/s92854/DTM/assets/134683810/b7bf9df3-1d39-4923-8eba-5d23b16f1002">

```
$x
```

<img width="634" alt="image" src="https://github.com/s92854/DTM/assets/134683810/e75241c9-2188-4c9d-842d-67b777a58521">

```
$y
```


### 7. Ukraine-Zentroid speichern
* erneut Zentroide der Länder berechnen
* Zentroid der Ukraine auswählen
* Exportieren über: "Gewählte Objekte speichern als"
<img width="505" alt="image" src="https://github.com/s92854/DTM/assets/134683810/77072890-5246-452a-8f90-ef536cca8e62">

### 8. Attributtabelle bearbeiten
<img width="697" alt="image" src="https://github.com/s92854/DTM/assets/134683810/79bea61f-6f8a-4508-be9e-67a3c034c1e1">

* Alle Spalten außer SOVEREIGNT löschen
* x und y Koordinaten berechnen (wieder über ```$x``` und ```$y```)


### 9. x_origin und y_origin Spalten im Länder-Layer hinzufügen
<img width="634" alt="image" src="https://github.com/s92854/DTM/assets/134683810/3a59ccde-a941-4c30-9f48-3157a5033595">
<img width="634" alt="image" src="https://github.com/s92854/DTM/assets/134683810/8ca93e50-c93b-4796-95fc-e6a7189f28b3">

* x = ```31.229```
* y = ```49.149```



### 10. Linien erzeugen
* Plug In "Shape Tools" installieren
* Vektor --> Shape Tools --> XY to line

<img width="702" alt="image" src="https://github.com/s92854/DTM/assets/134683810/cc87c9c0-02e6-4160-8386-f62a287415ba">

<img width="960" alt="image" src="https://github.com/s92854/DTM/assets/134683810/04bbf33a-4da0-4a0d-927f-0d6f7b2cb718">

Zwischenergebnis sollte in etwa so aussehen:

<img width="522" alt="image" src="https://github.com/s92854/DTM/assets/134683810/f646ad8b-f408-4ca0-a5d6-15572a37adcd">



### 11. Benutzerkoordinatensystem erstellen
* Einstellungen --> Benutzerdefiniertes KBS
* Folgenden Code eingeben:
```
+proj=ortho +lat_0=49.149 +lon_0=31.229 +x_0=0 +y_0=0 +a=6371000 +b=6371000 +units=m +no_defs
```

<img width="596" alt="image" src="https://github.com/s92854/DTM/assets/134683810/738b3522-d8ef-4ade-ac27-a36889941af0">

* KBS anwenden

Mit geänderter Hintergrundfarbe sieht das Zwischenergebnis dann so aus:

<img width="354" alt="image" src="https://github.com/s92854/DTM/assets/134683810/af6caea6-88d2-49eb-a6f6-3fd7d7ca789e">


### 12. Ukraine Punkt
*  Layer erneut speichern als Shapefile
*  Eigenes KBZ anwenden

### 13.

```
buffer(make_point(0,0), 6350000, 20)
```

<img width="620" alt="image" src="https://github.com/s92854/DTM/assets/134683810/95df866a-b0e5-48e8-a6e5-6a2320f40b86">

<img width="617" alt="image" src="https://github.com/s92854/DTM/assets/134683810/95daa596-d8f3-4133-b526-e8834d545705">

<img width="251" alt="image" src="https://github.com/s92854/DTM/assets/134683810/6373aa3f-f4de-428e-8e42-107ae12b7b87">




<img width="627" alt="image" src="https://github.com/s92854/DTM/assets/134683810/a4c622ec-3177-4264-9c2e-a4d596705282">

<img width="618" alt="image" src="https://github.com/s92854/DTM/assets/134683810/e2460c99-ab1a-4117-a461-d33c5994305d">

<img width="626" alt="image" src="https://github.com/s92854/DTM/assets/134683810/d6fce18e-2970-4bb2-bd4c-1a418400867a">

<img width="626" alt="image" src="https://github.com/s92854/DTM/assets/134683810/6179d9d1-0d1c-4d73-875f-39ae460480b6">

<img width="626" alt="image" src="https://github.com/s92854/DTM/assets/134683810/924fd014-b3b9-4937-aa20-0f9c63178592">
