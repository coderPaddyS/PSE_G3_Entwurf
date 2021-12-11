# Kartenfunktionalität
## Ziel
Anzeigen der Karte, Etagenkarte, Standort und Interaktion damit
## Zugehörige Funktionale Anforderungen
FA10 Karte, FA20 Etagenkarte, FA30 Ortungsfunktion
## Beschreibung
Dieses Modul ist sehr UI-lastig. Für den Großteil der Funktionen wird eine Karten-Library verwendet. Diese kann i.d.R. mindestens: Karte anzeigen, Koordinaten (Standort) parsen und anzeigen
- Karte anzeigen
- Karteninteraktionen: Zoomen, verschieben, anklicken
- Etagen anzeigen
    - Etagenkarten sind letztendlich nur eine weitere Layer über der Karte
    - Hierbei darf aber trotzdem immer nur die Etagenkarte eines Gebäudes und Stockwerks geladen werden. Das heißt, alle Etagen liegen als extra Datum vor  und werden zur Laufzeit entsprechend ausgewählt und als eigene Layer über der Karte angezeigt.
- Etagen wechseln
    - hierfür muss eine eigene Schaltfläche angezeigt werden
    - Diese Schaltfläche muss mit der Etagenkartenansicht aus- und eingeblendet werden
- Ortungsfunktion: Standort parsen (kann i.d.R. Karten Library) und anzeigen. Beachten: Standortzugriff kann verweigert werden -> Fehlermeldung anzeigen

### Mögliche Library: Mapsforge
Die Library Mapsforge sieht ganz gut aus.
- Eine Beschreibung von OSM darüber:
https://wiki.openstreetmap.org/wiki/Mapsforge
- Github: https://github.com/mapsforge/mapsforge

Funktionen:
- Anzeigen von Karten (inkl. OpenStreetMap Karten, auch ein paar andere Anbieter) (offline, Kartendaten liegen auf Endgerät vor)
- Anzeigen von Kartenoverlay (Layers, Labels, etc).
- Standort anzeigen (mit 10 loc möglich)
- Einige Touch-Funktionen z.B. Zoomen etc.
## Bereitgestellte Methoden
- Fokussieren eines gegebenen Kartenobjekts (= mittig auf Bildschirm anzeigen und heranzoomen) [wird von Suche benötigt]
## Verarbeitete Daten
- Straßen- und Etagenkarte
- Letzter Standort, bevor App beendet wurde
## Verwendete Methoden
- Informationen zu Kartenobjekt anzeigen (nachdem es angeklickt wurde) -> extra Dokument
## Sonstiges
- Benutzt Karten-Library
- Benutzt Standortzugriff (wenn erlaubt)
