# Bivariante Choropletenkarte in QGIS
&nbsp;
## Vorbereitung: Download der Daten
&nbsp;
<img width="902" alt="image" src="https://github.com/s92854/DTM/assets/134683810/00579201-59db-469c-96ab-e86047554cfb">
[World Happiness Report 2023](https://www.kaggle.com/datasets/ajaypalsinghlo/world-happiness-report-20239)

[WHR2023.csv](https://github.com/s92854/DTM/files/11633163/WHR2023.csv)

[World_Countries_(Generalized).zip](https://github.com/s92854/DTM/files/11633167/World_Countries_.Generalized.zip)
&nbsp;
### 1. .csv-Datei und Countries Shapefile hinzufügen
<img width="659" alt="image" src="https://github.com/s92854/DTM/assets/134683810/84fae49e-e9c2-47dd-aaeb-d46e2a66cbdf">

### 2. "COUNTRY" und "Country name" verknüpfen
<img width="620" alt="image" src="https://github.com/s92854/DTM/assets/134683810/75ab7af1-47b5-44f0-8b6c-10ece963656c">

### 3. Layer mit Verknüpfungen als Shapefile exportieren

### 4. Layer duplizieren
* Eines in "Background" und das andere in z.B. "Happy" umbenennen
* Background Layer unter Happy Layer ziehen
* Farbe des Background Layers dunkler machen


### 5. "Happy" --> Einstellungen --> Quelle --> Abfrageerstellung
<img width="622" alt="image" src="https://github.com/s92854/DTM/assets/134683810/255e1d65-6805-431c-a3c0-c3ea76e18310">
&nbsp;

Abfrage hinzufügen:
```
"WHR2023_La" IS NOT NULL
```
Zwischenergebnis sollte in etwa so aussehen:

&nbsp;
<img width="558" alt="image" src="https://github.com/s92854/DTM/assets/134683810/736f6c30-e6aa-474a-a2a8-1632384d7ec4">

&nbsp;

### 6.
