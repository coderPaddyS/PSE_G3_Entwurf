# Gebäudekarte Parsing
## Ziel
Der Admins können erstelle Gebäudekarten in das benötigte Format umwandeln.
## Plattform
Admin Panel
## Eingabe
- Eine normale GEOJSON-Datei mit:
    - Polygonen
    - Punkten mit Namen
## Ausgabe
- KML-Datei (Karte)
- Datei mit Extrahierten Daten (!Format noch nicht fest!)

## Beschreibung allgemein
- Extrahiere Daten: siehe unten.
- Erstelle Kartendatei (KML): siehe unten.
- Gebe beides zum Download aus.

## Beschreibung der Datenextraktion
Erstelle aus den Punkten mit Namen die Gebäudedaten.\
DAS AUSGABEFORMAT MUSS NOCH GEKLÄRT WERDEN!\
Fest steht:
- mapId : int des Gebäudes (muss generiert werden)
- pos : (breitengrad:double, längengrad:double) aus Position des Punktes lesen
- name : String Name des Punktes
- KLÄREN: Default Stockwerkdaten
- KLÄREN: Woher bekommen wir die Adresse des Gebäudes?/Wann wird sie hinzugefügt?


## Erstellung Kartendatei
- Entferne alle Punkte aus der GEOJSON Datei.
- Wandle sie in eine KML-Datei um. Dafür gibt es Libraries wie z.B. https://github.com/mapbox/tokml.