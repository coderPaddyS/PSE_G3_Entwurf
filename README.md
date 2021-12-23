# Repository
Dieses Repository ist Teil eines PSE-Projekt der KIT Universität, Institut KASTEL und unter der GPL3.0-or-later Lizenz veröffentlicht und somit zur Nutzung freigegeben.

# PSE
Dieses Repository beinhaltet den Quellcode zum Pflichtenheft nach dem Wasserfallmodell mit Rückkoppelung.
Zur Compilierung wird eine installierte LaTeX Umgebung mit `latexmk` und `shell-escape` benötigt.

# Kompilierungsmindestanforderungen
Um den Sourcecode zu kompilieren werden diverse Systemvoraussetzungen benötigt. Zum einen natürlich eine lokale LaTeX-Umgebung, die in der Lage ist `latexmk` mit `shell-escape` auszuführen.

# Module
Das gesamte Pflichtenheft ist unterteilt in einzelne Kapitel und Unterkapitel bzw. Module und Submodule. Diese können ausgehend von der Hauptdatei `./main.tex` per `\inpmod` eingebunden werden, so bindet `\inpmod{Kriterien}` das Kapitel Kriterien ein. Um in einem Modul ein relatives Submodul einzubinden, kann hierfür `\inprelmod` gleichermaßen verwendet werden.
Um andere, zur momentan bearbeiteten Datei, relative Dateien einzubinden, kann `\relfile` genutzt werden, um zur Compilezeit den richtigen, absoluten Pfad zu bekommen.
Bilddateien im direkten Subordner `images` können über `\inprelimg` eingebunden werden. Bsp: Um `images/bild01.png` mit `10cm` Breite einzubinden, kann `\inprelimg[width=10cm]{bild01.png}` verwendet werden. Die Optionen sind die selben wie für `\includegraphics`.

## Aufbau eines Moduls
Ein Modul besteht mindestes aus einer `main.tex` Datei, welche den Inhalt des Moduls bestimmt. Sollte das Modul aus Submodulen bestehen, so soll die `main.tex` dieses Moduls nur als Einbindungsdatei für die Submodule dienen, um die Struktur dieses Repos einzuhalten.
Andernfalls kann die `main.tex` beliebigen Inhalt beschreiben, jedoch sollte dieser thematisch natürlich zum Modul passen.
