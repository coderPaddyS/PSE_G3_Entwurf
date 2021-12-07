# Kartenobjekt-Informationen
## Ziel
Alle Informationen zu Kartenobjekt anzeigen. Bearbeitung von gewissen Daten davon (Aliasse).

## Zugehörige Funktionale Anforderungen
/FA10/,/FA20/ (Etagen-)Karten, /FA70/ Alias hinzufügen, /FA80/ lokale Aliasverwaltung, /FA90/ Alias-Vorschläge bewerten
## Beschreibung
1. Basisinformationen
    - Zu Gebäude wird Nummer, Adresse angezeigt
    - Zu Raum wird Nummer, ggf. zugehörige Person angezeigt
2. Erweiterte Informationen
    - zugehörige lokale Aliasse
        - ein Alias kann ausgewählt und gelöscht werden
            - z.B. lang auf lokalen Alias klicken
            - Popup öffnet sich, ob man lokalen Alias löschen will Ja/Abbrechen
            - Ja -> lokaler Alias wird gelöscht
    - zugehörige globale Aliasse
    - Ein Alias kann hinzugefügt und vorgeschlagen werden
        - Button bei Aliassen "Alias hinzufügen"
        - Klick -> Eingabefeld wird angezeigt, Tastatur geht auf
        - Eingabe, Auswahl, ob lokal, oder auch global vorschlagen
        - App prüft, ob Alias bereits existiert (dafür könnte man evtl. die Funktionalität Suchfunktion nutzen)
        - Existiert schon -> Fehlermeldung
        - Existiert nicht -> lokal speichern
            - wenn global: Prüfen, ob angemeldet, wenn nicht Meldung anzeigen, ggf. Anmeldung öffnen
            - Vorschlag an Server senden. Es wird nur "Vorschlag an Server gesendet" angezeigt
    - Alias-Vorschläge werden angezeigt. Bewertung ist möglich
        - --> siehe separates Dokument (Tamira)

### UI-Idee:
- Wird ein Kartenobjekt auf der Karte ausgewählt erschienen zuerst nur (mindestens) die Basis-Infos. Damit kann die Karte weiterhin angezeigt werden
- Durch "Nach-oben-ziehen" wird die Anzeigefläche größer --> ganzer Bildschirm
- Hier werden nun auch die erweiterten Infos angezeigt.
## Bereitgestellte Methoden
- bei Start wird Kartenobjekt mitgegeben
## Verarbeitete Daten
- Nummer, Adresse, des Kartenobjekts
- Raumnummer, Person (zu Büro)
- lokale und globale Aliasse zu Kartenobjekt
- Alias-Vorschläge
## Verwendete Methoden
- lokalen Alias speichern
- lokalen Alias löschen
- Alias-Vorschlag einreichen
- Feedback zu Alias-Vorschlag senden
## Sonstiges
Gewisse Funktionen stehen nur angemeldeten Benutzern zur Verfügung
