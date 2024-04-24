# Protokoll: 

| 28.03.2024, 10:00-11:00                                                      | Ort: Insel |
| ----------------------------------------------------------------------- | ------------------------------ |
| Teilnehmer:<br />Laura,<br />Michael,<br />Roger,<br />Leo,<br />Manuel | Entschuldigt:                  |
| Protokollführung: Roger                                                 | Sitzungsleitung: Michael       |

## Traktandenliste:

- [ ] Presentation of second Iteration (Manuel)
- [ ] Feedback to second Iteration (Roger, Leo)
  - [ ] UI within or outside the Viewer?
- [ ] Presenting Tests, Require Assistance/Resources (Laura)
- [ ] Planning for Iteration 3
  - [ ] Requirements
  - [ ] Doability
  - [ ] Final Decision
- [ ] Look Ahead to Iteration 4
  - [ ] Meeting for Planning Iteration 4 (April 25?)
- [ ] Else

## Feedback
* Good, except have a dynamic height of viewer
* Also, 
* Information from the image rendered with VTK inside viewer
* **Tests:**
  * Viewer may be too complicated to test, no time for that
  * Test the buttons and the things we implement outside of VTK.js
  * Interaction between React and VTK -> e.g. check if the information was sent and received by the (mocked) library
    * Cannot interact directly inside the library

## Requirements
* Change background color to see the actual size of the picture -> make sure aspect ratio of picture doesn't change
* Load full Volume
  * Look at the VTK.js examples, should be in there
* Graphical Information in VTK
  * Put Text and information from the DICOM in the viewer
* Zoom, Contrast, Panning
  * Buttons, after click on each button the mouse reacts only with the specific function
  * Buttons OUTSIDE of viewer
  * Zoom and Panning minimum (just functions to be found in VTK), Contrast an Option
* **Iteration 4:**
  * **Meeting:** April 18, 10:00-11:00

## Other things
* Design: look up HOROS; open source browser, shows how the viewer in the web should look
* Normally preload the full volume -> tell VTK the total dimensions
  * Shows a progress bar, showing which slices are already ready
    * Users will wait until progress bar is full -> don't care where we start, middle slice or slice 0
  * vtkSlice function to get perpendicular slice -> display to see the volume being loaded
