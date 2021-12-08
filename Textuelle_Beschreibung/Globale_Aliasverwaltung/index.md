# Ausgangssituation

Das Admin-Panel ist geöffnet.

# Ablauf

- Das Admin-Panel ist passwortgeschützt.
    - Es ist wichtig, dass die Passwörter sicher verschlüsselt sind.
        - Eine Möglichkeit hierfür wäre, die Pakete `javax.crypto`, `java.security` und die Klasse `java.util.Base64` zu verwenden [(Quelle zum Nachlesen)](#https://www.delftstack.com/de/howto/java/java-password-encryption/)
- Das Admin-Panel zeigt eingereichte Alias-Vorschläge mit ihrer Bewertung an.
    - Hierfür muss das Admin-Panel mit dem Server kommunizieren können.
        - Die Kommunikation mit dem Server wird durch `HTTPS` ermöglicht, wobei der Server über die definierte URL https://pse.itermori.de, das Admin-Panel über die URL https://pse.itermori.de/admin erreichbar ist.
- Der Administrator kann auswählen, wie viele positive oder negative Bewertungen ein Alias-Vorschlag haben muss, damit er angezeigt wird.
    - Selbstverständlich ist es hier wichtig, diese Anzahl variabel ändern zu können.
- Der Administrator kann den Standardwert wählen, wie viele positive oder negative Bewertungen ein Alias-Vorschlag haben muss, damit er angezeigt wird. Der neue Standardwert wird gespeichert
    - Analog ist es hier wichtig, diesen Standardwert variabel verändern zu können, jedoch sollte hier eine andere Variable verwendet werden, die zum langfristigen Setzen des Standardwertes dient.
- Der Administrator kann einen Alias-Vorschlag annehmen.
    - Dabei ist der Alias-Vorschlag vom Server in die Datenbank aufzunehmen.
        - Dementsprechend könnte das Admin-Panel mit dem Server über eine Schnittstelle kommunizieren.
        - Über die bekommt der Server die Anweisung, den Alias-Vorschlag in die Datenbank aufzunehmen.
    - Der Alias-Vorschlag ist nun ein globaler Alias.
- Der Administrator kann einen Alias-Vorschlag ablehnen.
    - Der Alias-Vorschlag ist dann zu verwerfen.
        - Demzufolge könnte das Admin-Panel mit dem Server über die gleiche, oben erwähnte Schnittstelle kommunizieren. 
        - Über die bekommt der Server die Anweisung, den Alias-Vorschlag zu verwerfen.
- Der Administrator kann einen Alias-Vorschlag ablehnen und auf eine Blacklist setzen.
    - Der Server fügt den Alias-Vorschlag zur Blacklist hinzu, der Alias-Vorschlag ist zu verwerfen.
        - Weiter könnte das Admin-Panel mit dem Server über die gleiche, oben erwähnte Schnittstelle kommunizieren.
        - Über die bekommt der Server die Anweisung, den Alias-Vorschlag auf die Blacklist zu setzen, und den Alias-Vorschlag zu verwerfen.
    - Die Blacklist könnte eventuell als HashMap oder mithilfe von SQL implementiert werden.
- Der Administrator kann einen beliebigen Begriff auf die Blacklist setzen.
    - Hierfür könnte man wie oben die gleiche Schnittstelle verwenden, um dem Server die Anweisung zu erteilen, den Begriff auf die Blacklist zu setzen.
- Der Administrator kann die Blacklist einsehen.
    - Hierfür könnte man wie oben die gleiche Schnittstelle verwenden, um dem Server die Anweisung zu erteilen, die Blacklist anzuzeigen.
- Der Administrator kann einen Begriff von der Blacklist löschen.
    - Hierfür könnte man wie oben die gleiche Schnittstelle verwenden, um dem Server die Anweisung zu erteilen, den Begriff von der Blacklist zu löschen.
- Der Administrator kann einen existierenden globalen Alias entfernen.
    - Dabei löscht der Server den globalen Alias aus der Alias-Datenbank.
        - Hierfür könnte man wie oben die gleiche Schnittstelle verwenden, um dem Server die Anweisung zu erteilen, den existierenden globalen Alias zu löschen.

Wichtig ist, dass die Daten der App regelmäßig synchronisiert werden und dadurch mit den Daten auf dem Server und den Änderungen durch das Admin-Panel übereinstimmen.
