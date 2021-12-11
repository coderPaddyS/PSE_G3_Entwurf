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
- Die App schickt einen Http-Request mit dem erhaltenen ID-Token an den Server
- Der Server validiert den ID-Token mittels des Keys
- Der Server überprüft die Signatur des Tokens 
- Der Server entnimmt dem Token einen eindeutigen Identifizierer (uuovn)
- Der Server speichert diesen in der Liste der Nutzer ab falls noch nicht vorhanden(evtl wollen wir das u-Kürzel vlt noch hashen aber das sind eher Implementierungsdetails)
- Der Server generiert einen Access-Token mittels eines Algorithmus und eines Keys (Algorithmus aus Library wählbar, Key beliebig), dem er den key, der issuer, die Berechtigungen, den usernamen und ein Ablaufdatum hinzufügt. Außerdem wird noch ein Refresh-Token generiert mit deutlich längerer Lebenszeit und ohne die Berechtigungen (ansonsten gleich). Dies geschieht aus Sicherheitsgründen, da ein Access-Token in falschen Händen nicht ewig gelten sollte. Um dem Nutzer zu häufiges Anmelden zu ersparen daher aber der Refresh-Token, mit dem ein neuer Access-Token erhalten werden kann.
- Der Server schickt dem Nutzer Acces- und Refresh-Token zu. 
- Bei allen folgenden Request wird der Access-Token mitgeschickt um die Authorisierung überprüfen zu können. Ist das Token abgelaufen, wird eine spezielle Meldung vom Server zurückgeschickt und die App
schickt eine neue Anfrage mit dem Refresh-Token. Der Server generiert daraus einen neuen Access-Token und schickt diesen zurück. Die App schickt die vorherige Anfrage von selber erneut, sodass der Nutzer davon gar nichts mitbekommt.

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