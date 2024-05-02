# Protokoll:

| 02.05.2024, 10:00-11:00                                                  | Ort: Insel              |
| ------------------------------------------------------------------------ | ----------------------- |
| Teilnehmer:<br />Laura, <br />Michael,<br />Roger,<br />Leo,<br />Manuel | Entschuldigt:<br />     |
| Protokollführung: Roger                                                  | Sitzungsleitung: Manuel |

## Traktandenliste:

- [ ] Presentation of the fourth iteration (Manuel)
- [ ] Feedback (Roger)
- [ ] Presentation of the "me_testing" branch (Waldo)
  - [ ] What should be included in the main branch?
- [ ] Question: Is cloning Horos UI still a desired task?
- [ ] Planning for the **last** iteration
  - [ ] Requirements
  - [ ] What is needed for project handover (documentation,...)?
  - [ ] Doability
  - [ ] Final Decision
- [ ] Arrange final meeting to present work of last iteration and project handover
- [ ] Else

## Feedback

* Pixel Coordinates: not in floats; not negative
  * Zero Pixel is at the origin
* Camera rotation: pass the other two vectors for the orientation of the image to the camera as well
* Otherwise looks good!
* Function styleManipulator (?): change what the mouse does on right click, left click, scrolling, etc.
  * Code in Waldo's branch
* Waldo was able to use our code and is happy as our client

## Requirements

* Draw a line and measure the distance, display the distance by the line
  * Need the x,y,z in image space (from ray caster)
  * Drag and drop mouse will measure a distance in 3D space
  * Values will already be in millimeters with using 3D coordinates
  * Already have some examples of this
    * setupSVG in TestViewer.js for the text
* Alignment/rotation of the camera be the same as the picture
* Zoom - interaction with the camera (may use Waldo's code or find something ourselves)
* Optional, if other 3 are done: scrolling through slices, but Waldo can do that by himself

## Other things

* Important code: FourViewers folder (not FourViewersFull)
* Zoom: get interactor, get all the interaction from the mouse (interactor.onMouseMove, onRightButtonRelease, etc.)
* interactorStyle = vtkInteractorStyleImage (in: FourViewers/components/ViewerImage/components/initRenderWindow.js)
  * Does not allow for 3D interaction
  * Has a reset button
* Reset zoom: camera.zoom(1)

- **Next Meeting: 16.05, 10:00**
