# Definitionen
- MapID: ID für alle in der App definierten anzeigbaren Objekte (Gebäude, Räume)
# Anfragen App-Server

## Alias-Update
Aktualisierung der Kopie der Alias-DB
### App sendet
- Aktuelle VersionsID
### Server sendet
- Hinzufügen: Liste aus Paaren: Alias, MapID
- Löschen: Liste aus Paaren: Alias, MapID
- Neue Versionsnummer

## Alias vorschlagen
### App sendet
- Access-Token (von Vorschlagendem)
- Alias (Name)
- MapId

## Alias-Vorschläge anzeigen
### App sendet
- MapId
- Anzahl (wie viele Vorschläge maximal angefordert)
- Access-Token (da Vorschläge, die bewertet/vorgeschlagen wurden nicht angezeigt werden)
### Server sendet
- Liste aus Aliasse (Name)

## Alias-Vorschlag bewerten
### App sendet
- Access-Token
- MapId
- Alias (Name)

## 


## Anmeldung/Registrierung
Überprüfung der Validität des ID-Tokens und Aufnahme des Nutzers in die Datenbank als normaler Nutzer
### App sendet
- ID-Token
### Server sendet
Erfolg