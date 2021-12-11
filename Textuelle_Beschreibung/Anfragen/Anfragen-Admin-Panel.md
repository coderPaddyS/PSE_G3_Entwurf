# Definitionen
Kartenobjektname: Eindeutiger Bezeichner für ein Kartenobjekt in menschen-lesbarer Form z.B. Gebäudenummer/Gebäude+Raumnummer

# Anfragen Admin-Panel Server

## Alias-Vorschläge anzeigen
### Admin-Panel sendet
- min. Anzahl positive Bewertungen
- min. Anzahl negative Bewertungen
### Server sendet
- Liste
    - Alias-Vorschlag (Name)
    - MapId
    - Kartenobjektbezeichner (Gebäudenummer, Raumnummer)
    - Anzahl positive Bewertungen
    - Anzahl negative Bewertungen

## Alias-Vorschlag annehmen
### Admin-Panel sendet
- MapId
- Alias-Vorschlag (Name)
### Server antwortet
Erfolg

## Alias-Vorschlag ablehnen
### Admin-Panel sendet
- MapId
- Alias-Vorschlag (Name)
### Server antwortet
Erfolg

## Blacklist einsehen
### Admin-Panel sendet
Anfrage
### Server antwortet
- Liste von: Blacklist-Einträgen

## Name auf Blacklist setzen
### Admin-Panel sendet
- Name
### Server antwortet
Erfolg

## Blacklist-Eintrag entfernen
### Admin-Panel sendet
- Blacklist-Eintrag
### Server antwortet
Erfolg

## Aliasse anzeigen
### Admin-Panel sendet
- MapId
### Server sendet
- Liste: Alias (Name) [ggf MapId]

## Anfrage Kartenobjektname
### Admin-Panel sendet
- MapId
### Server sendet
- Kartenobjektname

## Anfrage MapId zu Kartenobjektname
### Admin-Panel sendet
- Kartenobjektname
### Server sendet
- MapId

## Anfrage alle MapIDs
### Admin-Panel sendet
Anfrage
### Server sendet
- Liste: MapIds

## Alias entfernen
### Admin-Panel sendet
- MapId
- Alias (Name)
### Server antwortet
Erfolg


## TODO: Anmelden