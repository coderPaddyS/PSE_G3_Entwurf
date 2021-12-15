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
- Der Benutzer wird auf die Anmeldeseite der ausgewählten Anmeldeplattform im systemeigenen Browser weitergeleitet
- Benutzer gibt seine Daten ein (diese könnten evtl. je nach Anmeldeplattform ein unterschiedliches Format haben). Bestätigt Eingabe
- Anmeldung wird durchgeführt -> OpenId
    - Erfolg: 
        - Nutzer wird zur App zurückgeleitet
        - Empfange den Authorization Code der Anmeldeplattform
        - Tausche Authorization Code gegen Access-, ID- und Refreshtoken
        - Übermittle ID-Token dem Server als User-Mutation
            - Misserfolg Empfang, Austausch, Übermittlung:
                - Nutzer informieren
                - Anmeldevorgang abbrechen
        - Speichere:
            - Benutzer ist angemeldeter Benutzer
            - Accesstoken, Refreshtoken
        - Zeige Erfolgsmeldung an
        - Beende 
    - Misserfolg: 
        - Der Nutzer hat zwei Möglichkeiten:
            - Eingaben korrigieren
            - Anmeldevorgang abbrechen und als nicht angemeldeter Nutzer fortführen

#### Modul-Design:
- Das Modul muss so gestaltet werden, dass es möglich ist, die Anmeldeplattform (z.B. Shibboleth) gegen eine andere (z.B. Google) auszutauschen.
- Das Modul muss so gestaltet sein, dass es mehrere Anmeldeplattformen geben kann, von denen der Nutzer eine wählen kann
## Bereitgestellte Methoden
- Starten der Anmeldung. Wird dann aufgerufen, wenn der Benutzer versucht eine Aktion durchzuführen, für die man angemeldet sein muss.
## Verarbeitete Daten
- Wert, ob Benutzer schon angemeldet ist
- Nutzeridentifizierende Informationen wie, ID- und Accesstoken
- Daten zu unterstützten Anmeldeplattformen und ggf welche Eingabeparameter dafür benötigt werden
## Verwendete Methoden
- Textanzeige kann aufgerufen werden, um Datenschutz anzuzeigen
- Wert, ob Benutzer angemeldet ist festlegen
- Speicherung der Access- und Refreshtoken
- Übermittlung einer User-Mutation mit ID-Token
## Sonstiges
- Benutzt OpenID
- Benutzt Standard-Tastatur
- Benutzt Standard-Browser
- Benutzt Internet

Notice: ich hatte leider noch nicht die Zeit mich in OpenID, Anmeldungs-Libraries einzulesen. Gerne um genaueres ergänzen