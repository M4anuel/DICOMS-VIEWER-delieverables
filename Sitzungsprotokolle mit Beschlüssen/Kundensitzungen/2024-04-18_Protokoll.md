# Protokoll: 

| 18.04.2024, 9:00-10:00                                                      | Ort: Insel |
| ----------------------------------------------------------------------- | ------------------------------ |
| Teilnehmer:<br />Michael,<br />Roger,<br />Leo,<br />Manuel | Entschuldigt:<br />Laura,                  |
| Protokollführung: Roger                                                 | Sitzungsleitung:  Manuel       |

## Traktandenliste:

- [ ] Presentation of second Iteration (Michael)
- [ ] Feedback to third Iteration (Roger, Leo)
- [ ] Data display discussion & Horos
- [ ] Planning for Iteration 4
  - [ ] Requirements
  - [ ] Doability
  - [ ] Final Decision
- [ ] Look Ahead to Iteration 5 (cleanup & finetuning)
  - [ ] Meeting for Planning Iteration 5
- [ ] Else

## Feedback
* Happy with resizing
* Orthogonal Camera without rotation for 2D display; perspective camera for 3D display
  * But it's fine for now
* To do synchronization of VTK with diff, get aspect ratio of diff and use that to reset the camera to that aspect ratio
  * change the viewport size to be the same as the diff (should be done automatically, but can also pass parameters during runtime)
  * minor thing
* Data Overlay: four diffs with fixed position in container; more important to write a text in VTK -> important for measuring
  * Waldo will send us some tricks if he finds some
  * Put another picture in front of the already present picture with transparent color

## Requirements
* Data Display
  * Coordinates in reference to image (there is a function in VTK (viewTo3DWorld ? ))
  * Pixel should be the same coordinates when zooming
    * Ray to image to get pixel location
    * Little tricky, but would be great
    * Key to drawing in 3D space
* That is:
  * Do the 4 diffs over the image with text
    * Once we have that, put it in main so Waldo can take a look
  * Get and display the pixel location of the mouse (includes correct display of image in plane: compute the normal, then place camera accordingly)
    * In 3D space -> hitting the image with a ray from the camera
* Nice to have (look ahead to iteration 5): how to render text in 3D space (text actor in VTK)
  * discourse.vtk.org/t/text-in-vtk-js

## Other things
* To move between slices, put volume in one part and display in another, then when scrolling through, copy the wanted slice into the display and remove the earlier
  * alternatively, change the slice to transparent
  * Don't use 3D rendering
* Waldo will try to help next week by sending some helpful stuff
* **Next Meeting: 02.05.24, 10:00**
