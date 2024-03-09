# Testkonzept V1

## Unit Tests

Unit Tests werden gemacht. Es ist zurzeit noch unklar, welche Units existieren 
werden, aber voraussichtlich die folgenden (womöglich mit kleineren sub-Units):
* Image Renderer
* Zooming
* Scrolling
* Measuring
* Painting

Davon können Image Renderer, Measuring, und Painting mittels Unit Tests getestet 
werden. Je nach Implementation können auch Zooming und Scrolling zumindest 
teilweise gestestet werden. D.h. bestimmte sub-Units könnten testbar sein.

Measuring könnte nur Stichprobenartig getestet werden: es würden mehrere Paare 
von Koordinaten definiert mit bekannter Distanz. Die bekannte Distanz würde mit
der vom Programm berechneten Distanz verglichen und müsste in einem kleinen 
Fehlerbereich übereinstimmen.

Painting kann getestet werden, indem nach einem Befehl zum Einfärben die gewählten
Pixel überüprüft werden. Falls mehrere Farben möglich sind, würde jede Farbe einzeln
getestet.

Image Renderer muss in der Lage sein, eine DICOM Datei zu öffnen und bei ungültigem
Dateiformat eine Fehlermeldung auszugeben.

## Integrationstest

Die folgenden Use Cases existieren und werden getestet:
* Starten des Programms/Startseite
  * wird manuell getestet.
* DICOM Datei auswählen/laden
  * wird automatisiert als Teil der Unit Tests getestet.
  * zusätzliche manuelle Tests für korrekte Darstellung.
* Neue Datei wählen
  * wird automatisiert als Teil der Unit Tests getestet.
  * zusätzliche manuelle Tests für korrekte Darstellung.
* Zooming
  * wird zumindest Teilweise manuell getestet, je nach
    Implementation vollständig manuell.
* Scrolling
  * wird zumindest Teilweise manuell getestet, je nach
    Implementation vollständig manuell.
* Painting
  * wird automatisiert als Teil der Unit Tests getestet.
  * zusätzliche manuelle Tests für korrekte Darstellung.
* Measuring
  * wird automatisiert als Teil der Unit Tests getestet.
  * zusätzliche manuelle Tests für korrekte Darstellung.
* Schliessen des Programms
  * wird manuell getestet.

Folgende Grenz- und Spezialfälle können auftreten und müssen getestet werden:
* Ungültiges Dateiformat
  * kann automatisch getestet werden als Teil der Unit Tests.
* Ausschalten des Computers während das Programm läuft
  * wird manuell getestet, falls Fehlerhaftes Verhalten auftreten kann.

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
