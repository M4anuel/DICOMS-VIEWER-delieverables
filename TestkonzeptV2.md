# Testkonzept V2

## Unit Tests

Unit Tests werden durchgeführt. Die Software wird sich aus den folgenden Komponenten zusammensetzen:

**App/DICOM Viewer**

- ImageViewerContainer
  - ImageViewerContainer.js
  - ImageViewerContainerTest.js
  - PaintWidget
    - PaintWidget.js
    - PaintWidgetTest.js
    - index.js
  - MeasureWidget
    - MeasureWidget.js
    - MeasureWidgetTest.js
    - index.js
  - Toolbar
    - Toolbar.js
    - ToolbarTest.js
    - index.js

Wir werden versuchen möglichst viele Units automatisiert und isoliert voneinender zu testen und den Fokus auf das korrekte Rendern und das korrekte Ausführen der User Interaction in den Zoom-, Scroll-, Measure- und Paint Klassen legen.

Konkrete Vorschläge und Bemerkungen zu einzelnen Tests:

- Die Measure-Funktion kann Stichprobenartig getestet werden:
  Dazu werden zuerst mehrere Paare von Koordinaten mit bekannter Distanz definiert. Die bekannte Distanz kann anschliessend mit der vom Programm berechneten und im Webbrowser angezeigten Distanz verglichen werden. Die Differenz sollte unter einem bestimmten kleinen Toleranzwert liegen.

- Für das Testen der Zoom- und Scroll-Funktionen kann die Verwendung der Maus simuliert und die Position der Kamera vorher und nachher überprüft werden.

- Das Painting kann getestet werden, indem nach einem Befehl zum Einfärben die gewählten Pixel überüprüft werden. Falls mehrere Farben möglich sind, würde jede Farbe einzeln getestet.

- Image Renderer muss in der Lage sein, eine DICOM Datei zu öffnen und bei ungültigem Dateiformat eine Fehlermeldung auszugeben. Dies kann ebenfalls automatisiert erfolgen.

Die automatisierten Unit- und Integrationstests für die React Komponenten werden mit dem JavaScript framework **Jest** und der **React Testing Library (RTL)** geschrieben. Eine grobe Anleitung dazu befindet sich in folgendem Dokument unter "Instruction": https://docs.google.com/document/d/1n-SOJRLCr3bpJybRZD7EiFwNpCR-hVYf_OhLXEaf_Hk/edit?usp=sharing

## Integrationstest

Die folgenden Use Cases existieren und werden getestet:

- Starten des Programms/Startseite
  - wird manuell getestet.
- DICOM Datei auswählen/laden
  - wird automatisiert als Teil der Unit Tests getestet.
  - zusätzliche manuelle Tests für korrekte Darstellung.
- Neue Datei wählen
  - wird automatisiert als Teil der Unit Tests getestet.
  - zusätzliche manuelle Tests für korrekte Darstellung.
- Zooming
  - wird zumindest Teilweise manuell getestet, je nach
    Implementation vollständig manuell.
- Scrolling
  - wird zumindest Teilweise manuell getestet, je nach
    Implementation vollständig manuell.
- Painting
  - wird automatisiert als Teil der Unit Tests getestet.
  - zusätzliche manuelle Tests für korrekte Darstellung.
- Measuring
  - wird automatisiert als Teil der Unit Tests getestet.
  - zusätzliche manuelle Tests für korrekte Darstellung.
- Schliessen des Programms
  - wird manuell getestet.

Folgende Grenz- und Spezialfälle können auftreten und müssen getestet werden:

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
das Laden und Darstellen einer grossen, fein aufgelösten DICOM Datei.

Dies kann automatisiert getestet werden, indem eine sehr grosse Datei automatisch
erzeugt wird (falls noch nicht vorhanden) und dem Datenset hinzugefügt wird. Die
Software müsste diese Datei noch laden und darstellen können.

Problem: kann auch Hardware-abhängig sein.

## Usability-Test

Die voraussichtlichen Anwender der Software werden Ärzte sein. Es können keine relevanten Vorkenntnisse vorausgesetzt oder angenommen werden.

Die Software kann auf Bedienbarkeit getestet werden, indem jedes Mitglied des Teams eine Person ohne Vorkentnisse auswählt, diese die Software benutzen lässt und Rückmeldungen festhält.
