# Testkonzept V1

## Unit Tests

Unit Tests werden durchgeführt. Es ist zurzeit noch unklar, welche Units existieren
werden. Eventuell werden sie sich aus den folgenden Klassen und (deren Funktionen) zusammensetzen:

| App/DICOM Viewer |               |
| ---------------- | ------------- |
| Image Renderer   | Layer Manager |
| Zoom Renderer    | Image Layer   |
| Scroll Renderer  | Paint Layer   |
| Measure Renderer | Measure Layer |
| Paint Renderer   | Control Panel |
| Render Window    |               |

Wir werden versuchen möglichst viele Units automatisiert und isoliert voneinender zu testen und den Fokus auf das korrekte Rendern und das korrekte Ausführen der User Interaction in den Zoom-, Scroll-, Measure- und Paint Klassen legen.

Konkrete Vorschläge und Bemerkungen zu einzelnen Tests:

- Die Measure-Funktion könnte Stichprobenartig getestet werden:
  Dazu könnten zuerst mehrere Paare von Koordinaten mit bekannter Distanz definiert werden. Die bekannte Distanz würde anschliessend mit der vom Programm berechneten und im Webbrowser angezeigten Distanz verglichen werden. Die Differenz sollte unter einem bestimmten kleinen Toleranzwert liegen.

- Das Testen der Zoom- und Scroll-Funktionen könnte sich als schwierig erweisen, da wir dazu unteranderem den "Grad" des Zoomens, beziehungsweise des Cursers bestimmen müssten. Dennoch werden wir versuchen zumindest einzelne Sub-Units zu testen und den Rest manuel mittels Augenmass testen.

- Das Painting kann getestet werden, indem nach einem Befehl zum Einfärben die gewählten Pixel überüprüft werden. Falls mehrere Farben möglich sind, würde jede Farbe einzeln getestet.

- Image Renderer muss in der Lage sein, eine DICOM Datei zu öffnen und bei ungültigem Dateiformat eine Fehlermeldung auszugeben.

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
- Ausschalten des Computers während das Programm läuft
  - wird manuell getestet, falls Fehlerhaftes Verhalten auftreten kann.

## GUI Test

Das User Interface wird manuell getestet, es sei denn, eine Funktion wurde
bereits als Teil eines anderen Tests automatisch getestet.

## Stress-Test

Die einzige potentiell hohe Belastung, der die Software standhalten muss, ist
das Laden und Darstellen einer grossen, fein aufgelösten DICOM Datei.

Dies kann automatisiert getestet werden, indem eine sehr grosse Datei automatisch
erzeugt wird (falls noch nicht vorhanden) und dem Datenset hinzugefügt wird. Die
Software müsste diese Datei noch laden und darstellen können.

Problem: kann auch Hardware-abhängig sein.

## Usability-Test

Die voraussichtlichen Anwender der Software werden Ärzte sein. Es können keine
relevanten Vorkenntnisse vorausgesetzt oder angenommen werden.

Die Software kann auf Bedienbarkeit getestet werden, indem jedes Mitglied des Teams
eine Person ohne Vorkentnisse auswählt, diese die Software benutzen lässt und
Rückmeldungen festhält.
