# Software Analytics Katas
Kleine Übungen, welche das Denken und den Umgang mit datengetriebenen Softwareanalysen schulen sollen.

## Tests sind auch nur Code

### Problembeschreibung
Die EntwicklerInnen der integrierten Entwicklungsumgebung "IntelliJ" haben festgestellt, dass sie Versionsstände auschecken, Änderungen vornehmen und diese aber erst Tage später in einem großen Commit in das Repo zurück committen.
Meistens wird hier auch noch der Test-Code vergessen einzuchecken (oder existiert überhaupt nicht, was dann später beim Code-Review erst entdeckt wird).

### Verbesserungsmaßnahme

Zur Verbesserung des Entwicklungsvorgehens haben sich die EntwicklerInnen auf folgende Maßnahme geeinigt:

-	Alle Commits müssen nun weniger als 500 Zeilen Code enthalten.
-	Das Verhältnis von Test-Code zu Quellcode muss am Tagesende mindestens 0,7:1 betragen.

### Zusätzliche Informationen
-	Nur Quellcode, der in Java oder Kotlin geschrieben ist, ist von der Maßnahme betroffen.
-	IntelliJ verwendet für Test-Code das Postfix „Test“ als Kennung.

### Zusätzlicher Kontext
-	Das Softwareprojekt verwendet einen Continuous Integration Server.
-	Der Quellcode wird mit dem Versionskontrollsystem Git verwaltet.	

### Startpunkte
-	Repository: https://github.com/JetBrains/intellij-community


## Unter der Haube

### Problembeschreibung
Die in Java geschriebene Software PartyHardy nutzt für den Zugriff auf eine Datenbank eine proprietäre Schnittstelle namens BYODBA (Build Your Own Database Access).
Leider hatte der Datenbankhersteller die Unterstützung für diese Schnittstelle und der gleichnamigen 3rd-Party-Bibliothek abgekündigt.
Das Entwicklungsteam musste daher auf das neuere Verfahren JDBC umgestellt werden. 
Es mussten viele Codestellen angepasst werden.
Die Arbeiten ziehen sich jetzt schon lange hin.
Das Vertrauen auf der Produktseite scheint zu schwinden.

### Verbesserungsmaßnahme

Das Entwicklungsteam möchte den Fortschritt der Bibliotheksablösung transparent gestalten. Sie möchten folgendes versuchen:

- Visualisierung der jeweiligen Codemengen für die alte und neue Bibliothek über die Zeit hinweg.

### Zusätzliche Informationen

- Das Team hat den Code für die beiden Bibliotheken in jeweils unterschiedlichen Verzeichnisstrukturen abgelegt.

### Zusätzlicher Kontext
-	Das Softwareprojekt verwendet einen Continuous Integration Server.
-	Der Quellcode wird mit dem Versionskontrollsystem Git verwaltet.	

### Startpunkte
- CSV-Datei mit einem Git-Log-Numstat-Output, welche die Änderungen pro Datei inkl. geänderten Codezeilen festhält.
