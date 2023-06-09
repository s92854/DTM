# Heatmaps - am Beispiel Singapur


## Vorbereitung: Datendownloads
### 1. [listings.csv](https://github.com/s92854/DTM/files/11849362/listings.csv) & [neighbourhoods.geojson](https://github.com/s92854/DTM/files/11849370/neighbourhoods.zip) von [Airbnb](http://insideairbnb.com/get-the-data/) herunterladen
### 2. Boundary-[Shapefile](https://github.com/s92854/DTM/files/11857227/singapore.zip) von Singapur von [Stanford EarthWorks](https://earthworks.stanford.edu/catalog/stanford-pg798kr1205) herunterladen

&nbsp;

## In QGIS

### 1. csv-Datei hinzufügen
![image](https://github.com/s92854/DTM/assets/134683810/0a9fd00c-aff5-41ff-8e5b-d148b8d01264)
* Projektion noch nicht ändern

* EPSG Code auf ```24500``` umstellen

![image](https://github.com/s92854/DTM/assets/134683810/8c7dd1f2-ef70-4c54-9ac2-4953260dc8d2)

### 2. Layer 4 Mal duplizieren
* anschließend umbennenen und nach Eigenschaften filtern

Namen:
```
entire_apt
```
```
private_room
```
```
shared_room
```
```
hotel_room
```

&nbsp;

Filter:
```
"room_type" = 'Entire home/apt'
```
```
"room_type" = 'Private room'
```
```
"room_type" = 'Shared room'
```
```
"room_type" = 'Hotel room'
```
![image](https://github.com/s92854/DTM/assets/134683810/a3e1afc1-ec38-43a7-b56b-4a55a62277d9)

### 3. Hexagongitter erzeugen
* Vektor --> Forschungswerkzeuge --> Gitter erzeugen
* Hexagone auswählen
* Mit dem Online-[Rechner](https://rechneronline.de/pi/sechseck.php) die Diagonalenlänge ausrechnen

![image](https://github.com/s92854/DTM/assets/134683810/73cdb4c2-2a58-4303-a1ad-d8a7d95819c2)

![image](https://github.com/s92854/DTM/assets/134683810/daf1e6b1-0479-43d1-911a-aee698940e27)
* Gitterausdehnung nicht vergessen ;)

### 4. Zentroide
* Zentroide für jeden Room-Layer bilden
* Rooms nach Position selektieren

![image](https://github.com/s92854/DTM/assets/134683810/f63f1d63-8a18-4707-ac45-69ab06cbd55f)

### 5. Attribute nach Position verknüpfen
* Werkzeug "Attribute nach Position verknüpfen (Zusammenfassen)" und Preis wählen
* wieder für alle vier durchführen

![image](https://github.com/s92854/DTM/assets/134683810/b633e2a0-c9a4-434e-8158-3ed75b2a28c7)

### 6. Erstellen der Heatmap
* Zentroid-Layer --> Eigenschaften --> Symbolisierung --> Heatmap --> Farbverlauf
* Erste Farbe auf Transparent setzen und weitere Punkte durch Doppelklick unter die Farbleiste hinzufügen

![image](https://github.com/s92854/DTM/assets/134683810/8b06c86b-2d6b-4dc5-a78a-9d4a4bf3e5e3)

* Stil Copy-Paste auf die anderen Ebenen

![image](https://github.com/s92854/DTM/assets/134683810/b9d62037-7ebf-460c-a7d4-ce6f2661c54c)


### 7. Singapurs Boundary-Layer hinzufügen und Drucklayout erstellen
