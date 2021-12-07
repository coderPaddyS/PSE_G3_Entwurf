# Text-/Dokumentenanzeige
## Ziel
Es wird ein formatierter, längerer Text in einer eigenen Ansicht angezeigt.
## Zugehörige Funktionale Anforderungen
/FA50/ Einstellungen, /FA60/ Anmeldung
## Beschreibung
Ein längerer Text in einfachem Format (muss mind. Überschriften, Links unterstützen) wird in einer eigenen Ansicht angezeigt (ganzer Bildschirm).

#### Format Vorschlag: 
Warum nehmen wir nicht einfach Markdown. 
- Markdown ist einfach zu schreiben, zu speichern und hat alle Format
- Es gibt einige Markdown-libaries, die wir benutzen können, damit ist der Aufwand dann auch sehr gering.

#### Funktionen
- Texte, die angezeigt werden können:
    - Datenschutzerklärung
    - Impressum
    - Hilfeseite
    - evtl. Lizenzen (für verwendete Libaries)
- Es gibt einen Zurück-Button. Mit ihm oder durch die Zurück-Funktion des Endgeräts wird die Textanzeige wieder geschlossen. Die App kehrt zur vorherigen Ansicht zurück

Dieses Modul ist zwar sehr schlank, jedoch ergibt die Kapselung Sinn, da z.B. die Datenschutzerklärung sowohl aus den Einstellungen, als auch aus der Anmeldefunktion aufrufbar ist.
## Bereitgestellte Methoden
- Beim Start wird ein Schlüssel (z.B. enum) für den anzuzeigenden Text mitgegeben
## Verarbeitete Daten
- Entsprechende Texte
## Verwendete Methoden

## Sonstiges
Benutzt Markdown-Libary