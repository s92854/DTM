## Value By Alpha Maps in QGIS

### Datenquelle (Wahlgeometrien & Wahlergebnisse)
[Bundestagswahlen 2021](https://www.bundeswahlleiterin.de/bundestagswahlen/2021/ergebnisse.html)

Tabelle (kerg1.csv) mit Wahlergebissen bereinigen
<img width="755" alt="image" src="https://github.com/s92854/DTM/assets/134683810/b3b1a9d9-e483-41d1-862e-cf08e7638fc8">

## In QGIS
&nbsp;
1.) Vergleich SPD mit CDU.. Stimmenstärke Partei regelbasiert darstellen

Regel "Olaf"
```
"SPD" > "CDU"
```
<img width="628" alt="image" src="https://github.com/s92854/DTM/assets/134683810/ee8affb1-5a3b-4c6e-ad37-eb97cf82d8f9">

&nbsp;

Regel "Armin"
```
"SPD" < "CDU"
```
<img width="627" alt="image" src="https://github.com/s92854/DTM/assets/134683810/911f66e4-c197-423b-b369-a6c30e70baf2">

&nbsp;

2.) Ebene "Alpha" ergänzen und auf Symbolebene 1 setzen
<img width="627" alt="image" src="https://github.com/s92854/DTM/assets/134683810/fdde0098-586b-4d8c-8a45-bebc2fa8f98c">
<img width="624" alt="image" src="https://github.com/s92854/DTM/assets/134683810/9220920e-120d-4860-b97c-20cc366945cb">

&nbsp;

3.) Für die Ebene "Alpha": Über "Einfache Füllung" unter "Füllfarbe" > "Datendefinierte Übersteuerung" > "Bearbeiten":
```
set_color_part(
'black',
'alpha',
126
)
```

<img width="634" alt="image" src="https://github.com/s92854/DTM/assets/134683810/5cca73d3-9d9e-4978-960b-003199ce6283">

&nbsp;

4.) Ersetzen des festen Alphawertes der obigen Formel durch Funktion, die den Alphakanal der Wahlkreise nach ... kategorisiert.

```
set_color_part(
'black',
'alpha',
scale_linear(
"G",
100000, 200000,
225,0
)
)
```

