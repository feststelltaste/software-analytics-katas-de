# Software Analytics Katas
Kleine Übungen, welche das Denken und den Umgang mit datengetriebenen Softwareanalysen schulen sollen.

## Herzklopfen
Kategorie: klassisch  
Datenquelle: Logdateien  
Schwierigkeitsgrad: einfach  

### Problemkontext
Die Betriebssoftware der Geisterbahnattraktion namens DependencyHell wurde als Microservices implementiert.
Da es immer wieder zu unerklärlichen Ausfällen in unheimlichen Fällen kam, wurde eine Ping-API für alle Services eingeführt.
Damit können Services andere Services aufrufen, um zu sehen, ob diese derzeit erreichbar sind.
Für die API wurde eine Konvention eingeführt, wonach jeder funktionierende Service einen Aufruf von `/healty` mit dem HTTP-Statuscode 200 quittieren soll.
Es gibt jedoch immer noch sporadische Ausfallerscheinungen.

### Analyseauftrag

Das Entwicklungsteam möchte näher eingrenzen, wann und warum die sporadischen Fehler auftauchen.

- Eine Analyse der Logdateien über die Ausfallsituationen bei den Microservices soll Klarheit schaffen.

### Zusatzinformationen
-	Es liegt eine aggregierte Logdatei vor, welche die Ping-Aufrufe über mehrere Tage protokolliert.
- Das Logdatei-Format ist bei allen Services gleich
- Die Betriebssoftware läuft im eigenen Rechenzentrum des Austellerbetriebs.

### Startpunkte
- Logdatei mit Ping-Anfragen aller Services

## Tests sind auch nur Code
Kategorie: klassisch  
Datenquelle: Versionskontrollsystem  
Schwierigkeitsgrad: mittel  

### Problemkontext
Die EntwicklerInnen der integrierten Entwicklungsumgebung "IntelliJ" haben festgestellt, dass sie Versionsstände auschecken, Änderungen vornehmen und diese aber erst Tage später in einem großen Commit in das Repo zurück committen.
Meistens wird hier auch noch der Test-Code vergessen einzuchecken (oder existiert überhaupt nicht, was dann später beim Code-Review erst entdeckt wird).

### Analyseauftrag
Zur Verbesserung des Entwicklungsvorgehens haben sich die EntwicklerInnen auf folgende Maßnahme geeinigt:

-	Alle Commits müssen nun weniger als 500 Zeilen Code enthalten.
-	Das Verhältnis von Test-Code zu Quellcode muss am Tagesende mindestens 0,7:1 betragen.

### Zusatzinformationen
-	Nur Quellcode, der in Java oder Kotlin geschrieben ist, ist von der Maßnahme betroffen.
-	IntelliJ verwendet für Test-Code das Postfix „Test“ als Kennung.
-	Der Quellcode wird mit dem Versionskontrollsystem Git verwaltet.
-	Das Softwareprojekt verwendet einen Continuous Integration Server.

### Startpunkte
-	Repository: https://github.com/JetBrains/intellij-community


## Unter der Haube
Kategorie: klassisch  
Datenquelle: Versionskontrollsystem  
Schwierigkeitsgrad: einfach  

### Problemkontext
Die in Java geschriebene Software PartyHardy nutzt für den Zugriff auf eine Datenbank eine proprietäre Schnittstelle namens BYODBA (Build Your Own Database Access).
Leider hatte der Datenbankhersteller die Unterstützung für diese Schnittstelle und der gleichnamigen 3rd-Party-Bibliothek abgekündigt.
Das Entwicklungsteam musste daher auf das neuere Verfahren JDBC umgestellt werden. 
Es mussten viele Codestellen angepasst werden.
Die Arbeiten ziehen sich jetzt schon lange hin.
Das Vertrauen auf der Produktseite scheint zu schwinden.

### Analyseauftrag
Das Entwicklungsteam möchte den Fortschritt der Bibliotheksablösung transparent gestalten. Sie möchten folgendes versuchen:

- Visualisierung der jeweiligen Codemengen für die alte und neue Bibliothek über die Zeit hinweg.

### Zusatzinformationen

- Das Team hat den Code für die beiden Bibliotheken in jeweils unterschiedlichen Verzeichnisstrukturen abgelegt.
-	Der Quellcode wird mit dem Versionskontrollsystem Git verwaltet.	
-	Das Softwareprojekt verwendet einen Continuous Integration Server.

### Startpunkte
- CSV-Datei mit einem Git-Log-Numstat-Output, welche die Änderungen pro Datei inkl. geänderten Codezeilen festhält.
