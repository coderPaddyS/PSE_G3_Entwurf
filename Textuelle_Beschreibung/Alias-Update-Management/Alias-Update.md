# Alias-Update-Funktionalität
## Ziel
Administratoren aktualisieren die globale Alias-Datenbank (Alias hinzufügen/entfernen). Die App aktualisiert ihre lokale Kopie der globalen Alias-Datenbank.
## Zugehörige Funktionale Anforderungen
~ /FA100/ globale Alias-Verwaltung
## Beschreibung
### Allgemeiner Vorgang
- Wenn die App gestartet wird, wird das Aktualisieren der lokalen Kopie der globalen Alias-DB veranlasst
- Das Aktualisieren wird im Hintergrund ausgeführt, der Benutzer kann die App ganz normal benutzen und bekommt nichts davon mit.
- Es wird weder Erfolgs- noch Misserfolgs- (z.B. wenn offline) angezeigt.
### Funktionsweise
Die globale Alias-DB hat (mind.) 2 Tabellen
1. eine für alle aktuell hinzugefügten Aliasse
2. eine mit allen Alias-Löschungen
### Alias-Tabelle
- jeder Eintrag besteht aus Alias, Kartenobjekt, und einer Versionsnummer (diese ist einfach eine Zahl)
- wird ein Alias hinzugefügt, wird er in diese Tabelle geschrieben. Die Versionsnummer ist einfach die nächste mögliche Versionsnummer.
### Löschungs-Tabelle
Jeder Eintrag besteht aus 
- Versionsnummer des Löschungs-Eintrags. Diese ist fortlaufend mit der der Alias-Tabelle (also wenn Alias-Tabelle bei Versionsnummer 20 ist und ein neuer Eintrag zur Löschungs-Tabelle kommt, bekommt der 21. Wird danach ein neuer Alias hinzugefügt bekommt er in der Alias-Tabelle 22...)
- gelöschter Alias
- ursprüngliche Versionsnummer des gelöschten Alias in der Alias-Tabelle
- Kartenobjekt des Alias
### Hinzufügen-Vorgang
Alias A soll hinzugefügt werden. Neuer Eintrag für Alias-Tabelle:
- Alias A
- Kartenobjekt zu A
- Versionsnummer: nächste freie Versionsnummer
### Löschungs-Vorgang
Alias A soll gelöscht werden
- Versionsnummer VA von A und Kartenobjekt K zu A herausfinden (Alias-Tabelle)
- Neuer Eintrag in Löschungs-Tabelle anlegen:
    - Versionsnummer: nächste Nummer
    - Alias: A
    - ursprüngliche Versionsnummer: VA
    - Kartenobjekt: K
- Eintrag von A aus Alias-Tabelle löschen
### Aktualisierungs-Vorgang
- App hat immer die Versionsnummer V der aktuellen Kopie der DB gespeichert
- App sendet Anfrage mit aktueller Versionsnummer an Server
- Server erstellt Antwort:
    1. Hinzufüge-Teil H:
        - Für alle Einträge aus Alias-Tabelle mit Versionsnummer > V: Alias, Kartenobjekt
    2. Löschungs-Teil L:
        - Für alle Einträge aus Löschungs-Tabelle mit Versionsnummer > V und ursprünglicher Versionsnummer <= V: Alias, Kartenobjekt
    3. aktuelle Versionsnummer AV der Datenbank
    - Hinweis1: durch diese Bedingungen wird sichergestellt, dass keine Informationen gesendet werden, die von der App nicht benötigt werden
- Server sendet Antwort an App
- App empfängt und verarbeitet Antwort
    - L: Lösche alle Aliasse, Kartenobjekt-Paare aus L aus der lokalen DB-Kopie
    - H: Füge alle Aliasse, Kartenobjekt-Paare aus H zur lokalen DB-Kopie hinzu
    - Setze Versionsnummer V auf AV
- Fertig
### Anmerkungen
- In der lokalen DB-Kopie liegen keine Versionsnummern für die Einträge vor (?) da diese nicht benötigt werden (?)

## Bereitgestellte Methoden
- aktualisieren
## Verarbeitete Daten
- Daten von globaler Alias-DB (von Server)
## Verwendete Methoden
- in lokale Kopie der globalen Alias-DB schreiben
## Sonstiges
Zu Hinweis1 sollten wir im Entwurf eine Ausführliche Begründung/Diagramme machen
