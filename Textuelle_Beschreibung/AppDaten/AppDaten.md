### Disclaimer: 
- Dies ist eine Zusammenfassung der in der App gespeicherten Daten aus allen Textuellen Beschreibungen und mündlich besprochenen
- Dies hier ist noch KEINE Modellierung der (Basis)Klassen
- Dies ist v.a. für die Speicherung im Model
- Der Schwerpunkt liegt hier auf den Informationen, die gespeichert werden (es könnte bei machen Daten, die hier zusammenstehen, sein, dass verschiedene Teile in verschiedenen Kontexten so verwendet werden, dass man letztendlich immer nur disjunkte Teilmengen davon benutzt)

# Basisobjekte
## Kartenobjekte
### Gebäude
- MapId
- Name (Standardname, der kein Alias ist)
- TODO: Geocoding (Ort, Etage, evtl. Labelname)
- Weitere Informationen (muss hier erweiterbar sein):
    - Adresse
### Raum
- MapId
- Name (Standardname, der kein Alias ist)
- TODO: Geocoding (Ort, Etage, evtl. Labelname)
- Weitere Informationen (muss hier erweiterbar sein)
    - TODO: evtl. Gebäude (diese Information wäre nur für den Benutzer zum Anzeigen, evtl. Suche?; Die Karte braucht diese Information NICHT (steckt eigentlich schon in Geocoding), könnte man wenn Geocoding feststeht ggf. als Methode machen?)

## Aliasse
- MapId
- Name

## Person
- Name
- Raum

## Textdokumente
Z.B. Datenschutz, Impressum, etc.\
In Implementierung evtl. als normale sprachspezifische Strings \
Im Markdownformat; Format sollte aber austauschbar sein
- ID (identifiziert die verschiedenen Textdokumente)
- Text

## Sprache
\[String-Ressourcen],
- Anzeigename (z.B. "Deutsch")

## Theme
- ID
- Name (Anzeigename): BEACHTEN: Das ist hier die ID für den Anzeigenamen (nötig da mehrsprachige String-Ressource)
- TODO: Theme-Modellierung (Farben etc., beachte Compose-Themes)

## TODO: Suchverlauf/Suchverlauf-Einträge

## TODO: Karte

## TODO: Etagenkarten


# Daten, die App lokal gespeichert hat:

## Aliasse
Hinweis: Die Trennung in lokale und globale Aliastabelle ist hier (im Entwurf) sinnvoll, da es andere Schreibberechtigungen (User fügt hinzu/löscht BEZ. Aktualisierung mit Server) gibt
### Globale Aliastabelle (lokale Kopie)
- Versionsnummer der lokalen Kopie der globalen Alias-Tabelle
- Liste von Aliassen
### Lokale Aliastabelle
- Liste von Aliassen

## Anmeldung
- Wert ist Nutzer angemeldet (in Implementierung ggf. aus anderen Daten ableitbar)
- Access-Token
- Refresh-Token

## Textdokumente
- Textdokumente

## Allgemeine Einstellungen
- Liste aller verfügbaren Sprachen
- gewählte Sprache
- Liste von Themes
- aktuell ausgewähltes Theme (Referenz)

## Suche
- Suchverlauf speichern/nicht speichern
- TODO Suchverlauf



## NICHT (dauerhaft in der App) gespeichert werden:
- Alias-Vorschläge (sowohl eingereichte, als auch zur Bewertung heruntergeladene)
