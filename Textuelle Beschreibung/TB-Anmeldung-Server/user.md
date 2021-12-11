# Ausgangssituation
Der Server hat einen HTTP-Post-Request bekommen.
Dieser enthält einen User-Access-Token und einen ID-Token.

# Ablauf
1. Zunächst wird der übergebenen User-Access-Token auf Gültigkeit überprüft. Dabei wird überprüft:
    1. Die Gültigkeit der Lebensdauer des Zertifikates
    2. Die Übereinstimmung der Zertifizierungsstelle
    3. ... (mehr bei mehr Informationen zu Open ID bzw. Shibboleth)
2. Anschließend wird eine persistente ID generiert/geholt.
3. Das UAT-Field der Datenbank des entsprechenden Nutzers wird geupdated.
   ```sql
   UPDATE Users
   SET UAT = UAT_Neu
   WHERE ID = ID_NEU;
   ```
4. Bei Erfolg wird eine Erfolgsnachricht zurückgesendet.