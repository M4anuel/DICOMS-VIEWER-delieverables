# Protokoll:

| 15.05.2024, 10:00-10:35                                                  | Ort: Insel             |
| ------------------------------------------------------------------------ | ---------------------- |
| Teilnehmer:<br />Laura, <br />Michael,<br />Roger,<br />Leo,<br />Manuel | Entschuldigt:<br />    |
| Protokollführung: Roger                                                  | Sitzungsleitung: Laura |

## Traktandenliste:

- [ ] Presentation of fifth iteration
  * Aligning the camera
  * Change interactor style, implement zooming
  * LineWidget and distance display
     
- [ ] Feedback

- [ ] Planning for the final week(s)
  - [ ] Presenting existing backlog:
    * Complete line widget implementation
    * Contrast
    * UI: Clone Horos UI, adjusting buttons
    * Clean up code

- [ ] Planning of project handover
- [ ] Arrange final meeting?

- [ ] Else

## Feedback

* Good: no rotation in 3D
* Calculation for line widget: gl-matrix
  * See in frontend/node_modules/@kitware/rendering/camera.js for examples
  * Re-render after updateDistance()!

## Final Weeks

* Just the line, that's it!
* If we have more time (not so important, Waldo can also do this):
  * display value/color intensity of the pixel in the Overlay;
  * only one slice - vtkImageActor for single slice
    * Supply slice to the mapper, then pass that data to the actor so the actor doesn't change
* Replace the white background with black
* Final Meeting: Up to us, send Waldo an email
* Handover: Push to main by 30.05.2024
