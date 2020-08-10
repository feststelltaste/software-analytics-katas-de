# Software Analytics Katas
Kleine Übungen, welche das Denken und den Umgang mit datengetriebenen Softwareanalysen schulen sollen.

## Katas

### Tests sind auch nur Code

#### Problembeschreibung
Die EntwicklerInnen der integrierten Entwicklungsumgebung "IntelliJ" haben festgestellt, dass sie Versionsstände auschecken, Änderungen vornehmen und diese aber erst Tage später in einem großen Commit in das Repo zurück committen.
Meistens wird hier auch noch der Test-Code vergessen einzuchecken (oder existiert überhaupt nicht, was dann später beim Code-Review erst entdeckt wird).

#### Verbesserungsmaßnahme

Zur Verbesserung des Entwicklungsvorgehens haben sich die EntwicklerInnen auf folgende Maßnahme geeinigt:

-	Alle Commits müssen nun weniger als 500 Zeilen Code enthalten.
-	Das Verhältnis von Test-Code zu Quellcode muss am Tagesende mindestens 0,7:1 betragen.

#### Zusätzliche Informationen
-	Nur Quellcode, der in Java oder Kotlin geschrieben ist, ist von der Maßnahme betroffen.
-	IntelliJ verwendet für Test-Code das Postfix „Test“ als Kennung.

#### Zusätzlicher Kontext
-	Das Softwareprojekt verwendet einen Continuous Integration Server.
-	Der Quellcode wird mit dem Versionskontrollsystem Git verwaltet.	

#### Startpunkte
-	Repository: https://github.com/JetBrains/intellij-community
