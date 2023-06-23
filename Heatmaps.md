# Heatmaps - am Beispiel Singapur


## Vorbereitung
### [listings.csv](https://github.com/s92854/DTM/files/11849362/listings.csv) & [neighbourhoods.geojson](https://github.com/s92854/DTM/files/11849370/neighbourhoods.zip) von [Airbnb](http://insideairbnb.com/get-the-data/) herunterladen.

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
enire_apt
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

