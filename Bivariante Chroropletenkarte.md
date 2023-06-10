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
* bei "Namenspräfix": Text entfernen
<img width="622" alt="image" src="https://github.com/s92854/DTM/assets/134683810/a8ed61f7-03ec-4143-a01a-c93c9f6e50fd">


### 3. "Felder überarbeiten", falls flasche Eigenschaften
* in "Decimal (double)" konvertieren
* konvertierter Layer mit Verknüpfungen als Shapefile exportieren
<img width="869" alt="image" src="https://github.com/s92854/DTM/assets/134683810/63c07d41-d527-4b30-82e4-9a12816db2ac">


### 4. Layer duplizieren
* Eines in "Background" und das andere in z.B. "Happy" umbenennen
* Background Layer unter Happy Layer ziehen
* Farbe des Background Layers dunkler machen


### 5. "Happy" --> Einstellungen --> Quelle --> Abfrageerstellung
<img width="622" alt="image" src="https://github.com/s92854/DTM/assets/134683810/255e1d65-6805-431c-a3c0-c3ea76e18310">
&nbsp;

Abfrage hinzufügen:
```
"Ladder sco" IS NOT NULL
```
Zwischenergebnis sollte in etwa so aussehen:

&nbsp;
<img width="558" alt="image" src="https://github.com/s92854/DTM/assets/134683810/736f6c30-e6aa-474a-a2a8-1632384d7ec4">


### 6. Abgestuft kategorisieren (Quantile)
* "Happiness" in "BIP" umbenennen und "Logged GDP" auswählen
<img width="623" alt="image" src="https://github.com/s92854/DTM/assets/134683810/18cdef86-d746-490c-b3b3-177cd9c9e4c5">

* Layer duplizieren und bei Symbolisierung auf "Freedom to" umstellen
<img width="623" alt="image" src="https://github.com/s92854/DTM/assets/134683810/4f0483b4-d2a2-4ce0-b537-6c379a237e0d">

### 7. Feldrechner
* neues Feld in "BIP" Attributtabelle via Feldrechner anlegen und folgenden Code eingeben:
```
CASE
WHEN "Logged GDP" > 10.2 THEN 3
WHEN "Logged GDP" <= 10.2 AND  "Logged GDP" > 9.1 THEN 2
ELSE 1
END
```

&nbsp;
Code schaut, ob BIP über 10.2 ist, wenn ja, dann wird in Gruppe 3 gepackt. Wenn kleinergleich 10.2 und größer als 9.1, dann Gruppe 2. Ansonsten Gruppe 1

&nbsp;
<img width="635" alt="image" src="https://github.com/s92854/DTM/assets/134683810/8f544379-eb34-4bee-a185-07d86c5e10f4">

* selbes Verfahren für den anderen Layer, aber mit folgendem Code:

```
CASE
WHEN "Freedom to" > 0.852 THEN 'C'
WHEN "Freedom to" <= 0.852 AND "Freedom to" > 0.76 THEN 'B'
ELSE 'A'
END
```

<img width="636" alt="image" src="https://github.com/s92854/DTM/assets/134683810/c5028dbb-be72-4e25-ad0f-42f6487492ee">

&nbsp;

### 8. Verknüpfung von "BIP_rec" und "F_rec":

```
"BIP_rec" || "F_rec"
```
<img width="635" alt="image" src="https://github.com/s92854/DTM/assets/134683810/047b50d5-f208-459e-b31a-32e0a37b084e">

&nbsp;


### 8. Anhand der Farbbeispiele eins heraussuchen und html-Farbcodes kopieren
[Farbbeispiele](https://github.com/s92854/DTM/assets/134683810/a0cef31c-90fc-43c6-aca2-44b1bc737d2b)

<img width="622" alt="image" src="https://github.com/s92854/DTM/assets/134683810/7cf1e80a-9167-4d8e-9ef7-16ebe021fd9f">

&nbsp;
