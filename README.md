# Software Analytics Katas
Kleine Übungen, welche das analytische Denken und den Umgang mit datengetriebenen Softwareanalysen schulen sollen.

_Wenn Du sofort mit Python & pandas loslegen möchtest, kannst Du durch einen Klick auf diesen Button sofort tun!_ [![Binder](http://mybinder.org/badge.svg)](http://mybinder.org/repo/feststelltaste/software-analytics-katas-de)

## Herzklopfen
Kategorie: klassisch  
Datenquelle: Logdateien  
Schwierigkeitsgrad: mittel  

### Problemkontext
Die Steuerungssoftware für die Geisterbahnattraktion "DependencyHell" wurde als Microservices-Architektur implementiert.
Da es immer wieder zu unerklärlichen Ausfällen in unheimlichen Fällen kam, wurde eine Ping-API für alle Services eingeführt.
Damit können Services andere Services aufrufen, um zu sehen, ob diese derzeit erreichbar sind.
Für die API wurde eine Konvention eingeführt, wonach jeder funktionierende Service einen Aufruf von `/healthy` mit dem HTTP-Statuscode 200 quittieren soll.
Es gibt jedoch immer noch sporadische Ausfallerscheinungen.

### Analyseauftrag

Das Entwicklungsteam möchte näher eingrenzen, wann und warum die sporadischen Fehler auftauchen.

- Eine Analyse der Logdateien über die Ausfallsituationen bei den Microservices soll Klarheit schaffen.

### Zusatzinformationen
-	Es liegt eine aggregierte Logdatei vor, welche die Ping-Aufrufe über mehrere Tage protokolliert.
- Das Logdatei-Format ist bei allen Services gleich
- Die Betriebssoftware läuft im eigenen Rechenzentrum des Austellerbetriebs.
- Der Schaustellerbetrieb läuft meist ab 13 Uhr und geht auch einmal tief in die Nacht hinein.

### Startpunkte
- Logdatei (~7 MB) mit der mitgeschnittenen Kommunikation zwischen den Services von einer Woche mit folgenden Informationen:
  - `timestamp`: Zeitstempel des Protokolleintrags
  - `status`: Zurückgelieferter HTTP-Statuscode einer Anfrage
  - `method`: Genutzte HTTP-Anfragemethode
  - `url`: Aufgerufene Serivce-URL
  - `ms`: Antwortzeit des aufgerufenen Service-Calls
- Dataset-URL: [`datasets/scarylog.csv`](https://raw.githubusercontent.com/feststelltaste/software-analytics-katas-de/master/datasets/scarylog.csv)
  - Möglicher Header-String: `"timestamp", "status", "method", "url", "ms"`

## Motivationsproblem
Kategorie: klassisch  
Datenquelle: Stack Overflow  
Schwierigkeitsgrad: einfach  

### Problemkontext
EntwicklerInnen in einem Softwareunternehmen verwenden ein Versionskontrollsystem (kurz "VCS") namens CVS (Concurrent Versions System).
Nun haben EntwicklerInnen die Idee, auf SVN (Subversion) zu migrieren.
Du glaubst jedoch, dass "Git" mittlerweile zum Standard in der Softwareentwicklungs-Community geworden ist.
Also schlägst Du Git als Alternative für das Team vor.

### Analyseauftrag
- Finde datengestütze Fakten, die zeigen, dass die Softwareentwicklungs-Community hauptsächlich das Versionskontrollsystem Git verwendet!

### Zusatzinformationen
- Du weißt, dass Stack Overflow eine Plattform ist, die Antworten auf Fragen bzgl. bestimmter Technologien bereitstellt.

### Startpunkt
- Datei (~ 4 MB) mit einer Statistik über die gestellten Fragen auf Stack Overflow über Versionskontrollsysteme über mehrere Jahre hinweg.
  - `CreationDate`: Der Zeitstempel des Erstellungsdatums eines Stack Overflow Posts (= Frage)
  - `TagName`: Der Tag-Name für eine Technologie (in unserem Fall für nur 4 VCSes: "cvs", "svn", "git" und "mercurial")
  - `ViewCount`: Die Anzahl der Ansichten eines Beitrags
- Dataset-URL: [`datasets/stackoverflow_vcs_data_subset.csv`](https://raw.githubusercontent.com/feststelltaste/software-analytics-katas-de/master/datasets/stackoverflow_vcs_data_subset.csv)

## Tests sind auch nur Code
Kategorie: klassisch  
Datenquelle: Versionskontrollsystem  
Schwierigkeitsgrad: mittel  

### Problemkontext
Die EntwicklerInnen der integrierten Entwicklungsumgebung "IntelliJ IDEA" haben festgestellt, dass sie Versionsstände auschecken, Änderungen vornehmen und diese aber erst Tage später in einem großen Commit in das Repo zurück committen.
Meistens wird hier auch noch der Test-Code vergessen einzuchecken (oder existiert überhaupt nicht, was dann später beim Code-Review erst entdeckt wird).

Zur Verbesserung des Entwicklungsvorgehens haben sich die EntwicklerInnen auf folgende Maßnahme geeinigt:

-	Alle Commits müssen nun weniger als 500 Zeilen Code enthalten.
-	Das Verhältnis von Test-Code zu Quellcode muss am Tagesende mindestens 0,7:1 betragen.

### Analyseauftrag
Zeige, dass die Entwickler jetzt so arbeiten, wie sie es vereinbart haben!
Verfolge dazu die Commit-Aktivitäten und finde heraus, ob die EntwicklerInnen jetzt zum Code auch Tests dazuschreiben, so wie sie es sollten.

### Zusatzinformationen
-	Nur Quellcode, der in Java oder Kotlin geschrieben ist, ist von der Maßnahme betroffen.
-	IntelliJ IDEA verwendet für Test-Code das Postfix „Test“ als Kennung.
-	Der Quellcode wird mit dem Versionskontrollsystem Git verwaltet.
-	Das Softwareprojekt verwendet einen Continuous Integration Server.

### Startpunkte
- Eine (vorverarbeitete) Git Log Numstat Datei über einen Zeitraum von sechs Monaten. Jeder Zeile enspricht einer Änderung an einer Quellcode-Datei und enthält folgenden Inhalt:
  - `ts_in_s`: Der Commit-Zeitstempel in Sekunden
  - `path`: Der Dateipfad der Quellcode-Datei
  - `add`: Anzahl der hinzugefügten Zeilen ("additions")
  - `del`: Anzehl der gelöschten Zeilen ("deletions)
- Dataset-URL: [`datasets/intellij_testing.csv`](https://raw.githubusercontent.com/feststelltaste/software-analytics-katas-de/master/datasets/intellij_testing.csv)

## Unter der Haube
Kategorie: klassisch  
Datenquelle: Versionskontrollsystem  
Schwierigkeitsgrad: mittel  

### Problemkontext
Ein in Java geschriebenes Kundenmanagementsystem für Tierarztpraxen namens PetClinic nutzt für den Zugriff auf eine Datenbank die Schnittstelle JDBC (Java Database Connectivity).
Die Enterprise-Architekten haben nun jedoch festgelegt, das zukünftig alle Datenbankzugriffe über ein objektrelationales Mapping mittels der Schnittelle von JPA (Java Persistence API) erfolgen soll.
Das Entwicklungsteam muss daher auch ihren Zugriff auf JPA neben der normalen Feature-Entwicklung umstellen. 
Hierfür mussten und müssen immer noch viele Codestellen angepasst werden.
Die Arbeiten ziehen sich jetzt schon lange hin.
Das Vertrauen seitens des Produktmanagements scheint jedoch langsam zu schwinden.

### Analyseauftrag
Das Entwicklungsteam möchte den Fortschritt der Technologieablösung transparent gestalten. Sie möchten folgendes versuchen:

- Visualisierung der jeweiligen Codemengen für die alte und neue Bibliothek über die Zeit hinweg, um den Fortschritt zu zeigen.

### Zusatzinformationen

- Das Team hat den Code für die beiden Schnittstellen (JDBC bzw. JPA) in jeweils unterschiedlichen Java-Packages (= Verzeichnissen) mit dem jeweiligen Namen der Schnittstelle abgelegt.
-	Der Quellcode wird mit dem Versionskontrollsystem Git verwaltet.	
-	Das Softwareprojekt verwendet einen Continuous Integration Server.

### Startpunkte
- Eine (vorverarbeitete) Git Log Numstat CSV-Datei (~3 MB) mit einem Git-Log-Numstat-Output, welche pro Zeile die Änderungen pro Datei inkl. geänderten Anzahl an Codezeilen festhält.
- Dataset-URL: [`datasets/db_api_refactoring.csv`](https://raw.githubusercontent.com/feststelltaste/software-analytics-katas-de/master/datasets/db_api_refactoring.csv)

## Zugang verweigert
Kategorie: klassisch  
Datenquelle: statisch, dynamisch  
Schwierigkeit: anspruchsvoll  

### Problemkontext
Im internen Versicherungsanwendungssystem InsurHappy ist eine Web-Anwendung, welche starken Gebrauch von Mainframe-Kommunikation vornimmt.
Bei der Verwendung kommt es hier jedoch sporadisch zu Berechtigungsfehlern in der Anwendung.
Es wird vermutet, dass einzelne Rechte von einzelnen Benutzern für die Ausführung von COBOL-Routinen nicht vorhanden sind.
Die Mainframe-Verantwortlichen sind gleichzeitig sehr besorgt, dass Benutzer nicht zu viele Rechte erhalten. 

### Analyseauftrag
Es wird eine Liste mit fehlenden Benutzerberechtigungen benötigt, die zeigt, welcher Benutzer mit welcher Benutzer-ID welche Routinen benötigt, um mit InsurHappy reibungslos arbeiten zu können.

### Startpunkte
- Die COBOL-Routinen werden von CICS-Transaktionen umklammert. Diese sind in der Datei ([`datasets/access/TRANSACT.DEF`](https://raw.githubusercontent.com/feststelltaste/software-analytics-katas-de/master/datasets/access/TRANSACT.DEF) definiert und mit `EBCDIC 500` encodiert.
- Die CICS-Transaktionen wiederum werden über ein Mapping-Datei mit den SOAP-Servicemethoden verdrahtet. Die Definitionen liegen in [`datasets/access/webservice_definition_v0.1.xml`](https://raw.githubusercontent.com/feststelltaste/software-analytics-katas-de/master/datasets/access/webservice_definition_v0.1.xml) (für eine einfachere Variante, siehe [`datasets/access/webservice_definition_v0.1.json`](https://raw.githubusercontent.com/feststelltaste/software-analytics-katas-de/master/datasets/access/webservice_definition_v0.1.json)). Diese SOAP-Service-Methoden werden von InsurHappy zur Kommunikation mit dem Mainframe aufgerufen.
- Es liegt eine Log-Datei namens [`datasets/access/calls.log`](https://raw.githubusercontent.com/feststelltaste/software-analytics-katas-de/master/datasets/access/calls.log) von InsurHappy vor, welche einen Überblick über die in der vergangenen Woche aufgerufenen Services bietet.
- Weiterhin existiert eine sog. "Access-Matrix" ([`datasets/access/access_matrix.xlsx`](https://raw.githubusercontent.com/feststelltaste/software-analytics-katas-de/master/datasets/access/access_matrix.xlsx)) die angibt, welche Benutzer welche COBOL-Routinen aufrufen dürfen.
- Zudem ist Liste der echten Namen der Benutzer vorhanden ([`datasets/access/user_list.csv`](https://raw.githubusercontent.com/feststelltaste/software-analytics-katas-de/master/datasets/access/user_list.csv), um User-IDs aufzuschlüsseln.
