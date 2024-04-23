# Protokoll: [Wochenmeeting | Feedback Deliverables]

| [23.04/15:15 - 18:00]                                                   | Ort: [Engehalde Raum 005]  |
| ----------------------------------------------------------------------- | -------------------------- |
| Teilnehmer:<br />Laura,<br />Michael,<br />Roger,<br />Manuel,<br />Leo | Entschuldigt:<br />        |
| Protokollführung: Roger                                                 | Sitzungsleitung: Michael   |

## Traktandenliste:

1. Deliverables
2. Rückblick Iteration 3
3. Planung Iteration 4
   - User stories und Tasks definieren
   - Tasks verteilen
4. Usability Tests
   - Erstellung Ablauf/Konzept eines Usability Tests
5. Vorbereitung Vortrag "Qualitätssicherung Testing Usability"?
6. Leitung nächstes internes Meeting

## Beschlüsse

* Bei Problemen eher ein Emergency Meeting halten, um Massnahmen zu bestimmen
* Leitung nächstes Meeting: **Leo**
  * Vortrag
  * Kundenmeeting planen
* **Iteration 4 Tasks:**
  * Metainformationen sichtbar
    * Divs positionieren als Overlay
      * Schnell in Main pushen für Waldo
    * Daten in Divs abfüllen
    * **Verantwortlich:** Manuel, Michael
      * Tooltips für Usability
    * Deadline Statusupdate: Freitag, 26.04
  * Pixel Koordinaten von Mauszeiger
    * Mouse Event Listener einrichten/hat VTK.js solche Funktionalität?
    * Koordinaten von Renderer displayen
    * Koordinaten von Punkt im 3D-Raum displayen/holen
    * Tatsächlich gewollte Koordinaten herausfinden
    * Gewollte Koordinaten Displayen, falls es andere sind als Punkt im 3D-Raum
    * **Verantwortlich:** Leo, Laura, Roger
    * Deadline Statusupdate: Sonntag, 28.04
  * Optional: Orthogonale Kamera (nur panning)
    * Modell positionieren
    * Kamera neu ausrichten
    * Kamera ersetzen durch orthogonale Kamera statt perspective Kamera
    * Optional: Zooming implementieren
    * Optional: Interactor limitieren
    * **Verantwortlich:** Je nach zeit
  * Usability Test
    * Verantwortlich: Alle
    * Deadline: Freitag, 26.04
    * Auswertung: Roger

## Usability Test

* Szenario:
  * Arzt hat gerade einen Gehirnscan gemacht und will diesen Untersuchen
  * Arzt hat gerade einen Oberkörperscan nach einem Autounfall gemacht und will diesen Untersuchen
* Aufgaben:
  * Szenario 1:
    * Gehe zum Gehirnscan
    * Overlay ablesen - Namen überprüfen
    * Zoome an eine bestimmte Stelle im Gehirn
    * Panne an eine bestimmte andere Stelle im Gehirn
  * Szenario 2:
    * Gehe zum Oberkörperscan
    * Durch Slices durchbewegen - überprüfe, ob die Wirbelsäule in Ordnung ist
* Metriken:
  * Zeit pro Szenario
  * Einfachheit pro Szenario: Einfach - 1 bis 5 - Schwer
  * Design: Mieses Interface - 1 bis 5 - Schönes Interface
  * Allgemeines Feedback in Worten
* Pilottest: Manuel

## Feedback Deliverables

* Gut
* Dokumentation für Ende PSE: benötigen Installationsguide, damit Assistenten unsere Software zum laufen bekommen können!
