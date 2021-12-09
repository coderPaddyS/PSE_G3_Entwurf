# Anmeldefunktion
## Ziel
Verarbeiten, durchführen und darstellen der Anmeldung.
## Zugehörige Funktionale Anforderungen
/FA60/ Anmeldefunktion
## Beschreibung
Dieses Modul verarbeitet die Eingabe der Anmeldung und führt die Anmeldung durch.
- nur nicht angemeldete Benutzer können sich anmelden
- verwendet OpenID

#### Ablauf:
Es ist zu beachten, dass der Benutzer die Anmeldung bei jedem Schritt abbrechen kann -> überall Abbruchbutton anzeigen
- Benutzer kann sich den Datenschutz anzeigen lassen
- Der Benutzer muss den Datenschutz akzeptieren
- Der Benutzer wählt eine der unterstützen Anmeldeplattformen
- Benutzer gibt seine Daten ein (diese könnten evtl. je nach Anmeldeplattform ein unterschiedliches Format haben). Bestätigt Eingabe
- Anmeldung wird durchgeführt -> OpenId
    - Erfolg: 
        - Speichere:
            - Benutzer ist angemeldeter Benutzer
            - ID
            - ID Server mitteilen ?
        - Zeige Erfolgsmeldung an, schließe Anmeldung
    - Misserfolg: 
        - Zeige Misserfolgsmeldung an

#### Modul-Design:
- Das Modul muss so gestaltet werden, dass es möglich ist, die Anmeldeplattform (z.B. Shibboleth) gegen eine andere (z.B. Google) auszutauschen.
- Das Modul muss so gestaltet sein, dass es mehrere Anmeldeplattformen geben kann, von denen der Nutzer eine wählen kann
## Bereitgestellte Methoden
- Starten der Anmeldung. Wird dann aufgerufen, wenn der Benutzer versucht eine Aktion durchzuführen, für die man angemeldet sein muss.
## Verarbeitete Daten
- Wert, ob Benutzer schon angemeldet ist
- Daten zu unterstützten Anmeldeplattformen und ggf welche Eingabeparameter dafür benötigt werden
## Verwendete Methoden
- Textanzeige kann aufgerufen werden, um Datenschutz anzuzeigen
- Wert, ob Benutzer angemeldet ist festlegen
- ID festlegen bez. speichern (auch serverseitig (?))
## Sonstiges
- Benutzt OpenID
- Benutzt Standard-Tastatur

Notice: ich hatte leider noch nicht die Zeit mich in OpenID, Anmeldungs-Libraries einzulesen. Gerne um genaueres ergänzen