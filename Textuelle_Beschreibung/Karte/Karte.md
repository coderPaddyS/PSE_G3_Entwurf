# Kartenfunktionalität
## Ziel
Anzeigen der Karte, Etagenkarte, Standort und Interaktion damit
## Zugehörige Funktionale Anforderungen
FA10 Karte, FA20 Etagenkarte, FA30 Ortungsfunktion
## Beschreibung
Dieses Modul ist sehr UI-lastig. Für den Großteil der Funktionen wird eine Karten-Library verwendet. Diese kann i.d.R. mindestens: Karte anzeigen, Koordinaten (Standort) parsen und anzeigen
- Karte anzeigen
- Karteninteraktionen: Zoomen, verschieben, anklicken
- Etagen anzeigen, wechseln
- Ortungsfunktion: Standort parsen (kann i.d.R. Karten Library) und anzeigen. Beachten: Standortzugriff kann verweigert werden -> Fehlermeldung anzeigen
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
