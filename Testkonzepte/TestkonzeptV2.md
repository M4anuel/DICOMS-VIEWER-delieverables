# Testkonzept V2

## Unit Tests

Unit Tests werden durchgeführt. Die Software wird sich aus den folgenden Komponenten zusammensetzen:

**App/DICOM Viewer**

- ImageViewerContainer
  - ImageViewerContainer.js
  - ImageViewerContainer.test.js
  - PaintWidget
    - PaintWidget.js
    - PaintWidget.test.js
    - index.js
  - MeasureWidget
    - MeasureWidget.js
    - MeasureWidget.test.js
    - index.js
  - Toolbar
    - Toolbar.js
    - Toolbar.test.js
    - index.js

Wir definieren in unserem System eine Unit als eine Methode. Methoden, also Units, werden einzeln und unabhängig von anderen Methoden getestet mit erwartetem Output und tatsächlichem Output. Dabei testen wir nicht jede Methode der oben genannten Komponennten, sondern wir fokussieren uns auf Methoden, welche eine gewisse Komplexität haben. Methoden welche nur einen einzelnen Testfall darstellen, werden weggelassen. Für alle anderen Units werden mindestens drei Testfälle geschrieben.

Konkreter Vorschlag für Unittest der Measure Methode:
  - Mehrere Paare von Koordinaten mit bekannter Distanz werden zuerst definiert. Die bekannte Distanz kann anschliessend mit der vom Programm berechneten und im Webbrowser angezeigten Distanz verglichen werden. Die Differenz sollte unter einem bestimmten kleinen Toleranzwert liegen. 

Die automatisierten Unit- und Integrationstests für die React Komponenten werden mit dem JavaScript framework **Jest** und der **React Testing Library (RTL)** geschrieben. Eine grobe Anleitung dazu befindet sich in folgendem Dokument unter "Instruction": https://docs.google.com/document/d/1n-SOJRLCr3bpJybRZD7EiFwNpCR-hVYf_OhLXEaf_Hk/edit?usp=sharing

## Integrationstest

Die folgenden Use Cases existieren und werden getestet. In jedem Usecase werden die einzelnen Units getestet, dazu kommen noch folgende Integrationstests:

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

Konkrete Vorschläge und Bemerkungen zu einzelnen Tests:

- Für das Testen der Zoom- und Scroll-Funktionen kann die Verwendung der Maus simuliert und die Position der Kamera vorher und nachher überprüft werden.

- Das Painting kann getestet werden, indem nach einem Befehl zum Einfärben die gewählten Pixel überüprüft werden. Falls mehrere Farben möglich sind, würde jede Farbe einzeln getestet.

- Image Renderer muss in der Lage sein, eine DICOM Datei zu öffnen und bei ungültigem Dateiformat eine Fehlermeldung auszugeben. Dies kann ebenfalls automatisiert erfolgen.


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

Das User Interface wird manuell getestet, es sei denn, eine Funktion wurde bereits als Teil eines anderen Tests automatisch getestet.
Das Programm soll auf verschiedenen Bildschirmgrössen und Auflösungen getestet werden.

## Stress-Test

Die einzige potentiell hohe Belastung, der die Software standhalten muss, ist
das Laden und Darstellen einer grossen, fein aufgelösten DICOM Datei. Dabei haben wir keine Anforderungen an Performance. Das Programm darf lediglich nicht abstürzen.

Dies kann automatisiert getestet werden, indem eine sehr grosse Datei automatisch
erzeugt wird (falls noch nicht vorhanden) und dem Datenset hinzugefügt wird. Die
Software müsste diese Datei noch laden und darstellen können.

Problem: kann auch Hardware-abhängig sein.

## Usability-Test

Die voraussichtlichen Anwender der Software werden Ärzte sein. Es können keine relevanten Vorkenntnisse vorausgesetzt oder angenommen werden.

Die Software kann auf Bedienbarkeit getestet werden, indem jedes Mitglied des Teams eine Person ohne Vorkentnisse auswählt, diese die Software benutzen lässt und Rückmeldungen festhält. 
