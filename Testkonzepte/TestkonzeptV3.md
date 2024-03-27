# Testkonzept V3

## Allgemeines

Nach unserer Definition of Done soll der Code eines Tasks getestet sein, bevor der Task als beendet betrachtet werden kann.
Daher ist es das Ziel, automatisierte Tests spätestens vor Ende der jeweiligen Iteration zu schreiben, damit der Code ohne 
grössere Fehler abgegeben werden kann.

Die automatisierten Unit- und Integrationstests für die React Komponenten werden mit dem JavaScript framework **Jest** und 
der **React Testing Library (RTL)** geschrieben. Eine grobe Anleitung dazu befindet sich in folgendem Dokument unter 
"Instruction": https://docs.google.com/document/d/1n-SOJRLCr3bpJybRZD7EiFwNpCR-hVYf_OhLXEaf_Hk/edit?usp=sharing

Die automatischen Tests werden in .test.js Dateien in demselben Ordner gespeichert wie der zu testende Code. Beispielsweise
würde der Ordner Toolbar so aussehen:
- Toolbar
  - Toolbar.js
  - Toolbar.test.js
  - index.js

Diese Dateien können mit dem Befehl `npm run test` ausgeführt werden, was für neue Tests ebenfalls spätestens vor Ende der 
jeweiligen Iteration geschehen soll. Bereits geschriebene Tests, insbesondere aus früheren Iterationen, sind spätestens vor 
einem Pull Request in den `main` Branch auszuführen.

## Unit Tests

Unit Tests werden automatisch durchgeführt. 

Wir definieren in unserem System eine Unit als eine Methode. Methoden, also Units, werden einzeln und unabhängig von 
anderen Methoden getestet mit erwartetem Output und tatsächlichem Output. Dabei testen wir nicht jede Methode jedes 
Komponennten, sondern wir fokussieren uns auf Methoden, welche eine gewisse Komplexität haben. Methoden welche nur einen 
einzelnen Testfall darstellen, werden weggelassen. Für alle anderen Units sollen mindestens ein Normalfall, mögliche 
Edge-cases falls solche vorhanden sind, sowie Fehlerfälle getestet werden.

Konkreter Vorschlag für Unittest der Measure Methode:
  - Mehrere Paare von Koordinaten, sodass die jeweiligen Messungen in verschiedene Richtungen erfolgen, mit bekannter
    Distanz werden zuerst definiert. Die bekannte Distanz kann anschliessend mit der vom Programm berechneten und im
    Webbrowser angezeigten Distanz verglichen werden. Die Differenz sollte unter einem bestimmten kleinen Toleranzwert
    liegen.

## Integrationstest

Die folgenden Use Cases existieren und werden getestet. In jedem Usecase werden die einzelnen Units getestet, dazu kommen 
noch folgende Integrationstests:

- Starten des Programms/Startseite
- DICOM Datei auswählen/laden
  - für korrekte Darstellung und Zusammenarbeit vom Backend und Renderer.
- Neue Datei wählen
  - für korrekte Zusammenarbeit vom Verwerfen der alten Datei und Laden der neuen.
- Zooming
  - für korrekte Zusammenarbeit vom Renderer und User-Interaction.
- Scrolling
  - für korrekte Zusammenarbeit vom Backend, Cache, Renderer und User-Interaction.
- Painting
  - für korrekte Zusammenarbeit vom Cache, Renderer und User-Interaction. 
- Measuring
  - für korrekte Zusammenarbeit vom Measure-Widget, Renderer und User-Interaction.
- Paarweise Kombination von Zooming, Scrolling, Painting und Measuring
  - die korrekte Zusammenarbeit der Funktionen wird paarweise manuell getestet.
- Schliessen des Programms

Konkrete Vorschläge und Bemerkungen zu einzelnen, automatisierten Tests:

- Für das Testen der Zoom- und Scroll-Funktionen kann die Verwendung der Maus simuliert und die Position der Kamera vorher
  und nachher überprüft werden.

- Das Painting kann getestet werden, indem nach einem Befehl zum Einfärben die gewählten Pixel überüprüft werden. Falls
  mehrere Farben möglich sind, würde jede Farbe einzeln getestet.

- Image Renderer muss in der Lage sein, eine DICOM Datei zu öffnen und bei ungültigem Dateiformat eine Fehlermeldung
  auszugeben.

## Tests für Grenz- und Spezialfälle

- Ungültiges Dateiformat
  - kann automatisch getestet werden als Teil der Unit Tests.
- Internet-Unterbruch während der Datenübertragung vom Server zum Client
  - wird manuell getestet (Der Viewer muss den Fehlerfall erkennen und dem Benutzer eine entsprechende Meldung anzeigen)
- Ausschalten des Computers während das Programm läuft
  - wird manuell getestet, falls fehlerhaftes Verhalten auftreten kann.
- Messen und Einfärben ausserhalb von Bild
  - wird automatisiert getestet (Verhalten muss noch definiert werden)

## GUI Test

Das User Interface wird manuell getestet, es sei denn, eine Funktion wurde bereits als Teil eines anderen Tests 
automatisch getestet.

Das Programm soll auf verschiedenen Bildschirmgrössen und Auflösungen getestet werden. Dies geschieht insofern, dass
alle Teammitglieder das Programm auf ihren jeweiligen Geräten während des Programmierens ausführen sollen und 
Unstimmigkeiten melden.

## Stress-Test

Die einzige potentiell hohe Belastung, der die Software standhalten muss, ist das Laden und Darstellen einer grossen, 
fein aufgelösten DICOM Datei. Dabei haben wir keine Anforderungen an Performance, das Programm darf lediglich nicht 
abstürzen.

Dies kann automatisiert getestet werden, indem eine sehr grosse Datei automatisch erzeugt wird (falls noch nicht 
vorhanden) und dem Datenset hinzugefügt wird. Die Software müsste diese Datei noch laden und darstellen können.

Dieser Stress-Test sollte vor dem 1. Mai stattfinden, um in der Präsentation Qualitätssicherung und Testing die 
Resultate präsentieren zu können.

Problem: kann auch Hardware-abhängig sein.

## Usability-Test

Die voraussichtlichen Anwender der Software werden Ärzte sein. Es können keine relevanten Vorkenntnisse vorausgesetzt 
oder angenommen werden.

Die Software kann auf Bedienbarkeit getestet werden, indem jedes Mitglied des Teams eine Person ohne Vorkentnisse 
auswählt, diese die Software benutzen lässt und Rückmeldungen festhält. 

Dieser Usability-Test sollte vor dem 1. Mai stattfinden, um in der Präsentation Qualitätssicherung und Testing die 
Resultate präsentieren zu können.
