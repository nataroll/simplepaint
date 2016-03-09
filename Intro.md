# Introduction #

Paint app is a simple program that could be the framework for a
feature rich paint application.  The current version simply allows the
user to draw red lines on a blank panel in the form.


# Details #

1. The application draws on a simple custom panel control that was
created to be double buffered.  The code for this control is in the
file BufferedPanel.cs.  Double buffering reduces the filickering
effect that sometimes occurs when redrawing a complex image.


2. A bitmap called "snapshot" is created to retain the drawn image.


3. In the panel's MouseDown event, the starting coordinates are saved
and a temporary bitmap called "tempDraw" is cloned from the "snapshot"
image".


4. When the mouse is moved (and the mouse is down), the current
coordinates are captured and the panel is "invalidated" causing it to
be painted..


5. In the paint routine, a graphics object 'g' is created from the
tempDraw image and a line is drawn on it.  In effect, a line is added
to the tempDraw bitmap.  Then the new tempDraw image is transferred to
the graphics object 'e' of the panel.


6. When the MouseUp event occurs, the drawing is determined to be over
and the tempDraw image is transferred to our snapshot bitmap --- ready
for the next line to be drawn.


The reason for all of these bit maps is so that we retain the lines
that are drawn between each drawing operation and we want to be able
to show the new drawn line as it is being placed without freezing it
into place until the mouse is released.

From this basic program, it should be easy to add functions to change:
  * the line color and width,
  * erase all or part of the image,
  * draw filled and unfilled rectangles and ovals.

One could also add things like
  * the paint bucket,
  * the pencil,
  * the eraser,
  * image save and load.