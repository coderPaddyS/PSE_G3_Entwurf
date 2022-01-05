# How to create a floor map
1. Draw the map
2. Add room data
3. Add position data
4. Parse and extract map and room data

---
## Draw the map
The first step is to draw the map in an SVG editor. [Inkscape](https://inkscape.org/) is recommended.\
Allowed drawing elements:
- polygons (ONLY for background)
- lines (and polylines) (just straight lines, no curves)

You can draw the map in any orientation you like. The rotation and size do not matter. The map may not be mirrored!\
Useful tips:
- Consider using a polygon for the background.
- Make wall openings for doors.
- If available, use an image of the map you want to create as a (temporary) background layer to make drawing easier. Remove the image afterwards.
- Color and line width are irrelevant. 
- Keep in mind that after the parsing, the map will effectively have only two layers: The background layer where all polygons are and the foreground layer where all lines are. Within one of these layers, no drawing order is guaranteed!
- Fewer and therefore longer polylines are slightly better for performance.

### Important
Save the svg as `Plain SVG`/`Normal SVG`.

---
## Adding Room data
For every room that should be visible and clickable in the app, you have to provide data.\
The data is provided through one text per room. The font and font size are irrelevant. The text must be one line.\
The text must have the following format: `<room number>/<type tag>`.\
Use this type tag table:
| Type tag   |      Meaning      |
|----------|:-------------:|
| N | Not specified |
| LH | Lecture hall |
| O | Office |
| S | Seminar room |
| LR | Learning room |

### IMPORTANT
Place the text in such a way that the bottom left corner of the text is right in the middle of the room/building. It does not matter whether the text goes over walls etc. Only the bottom left corner counts!\
This is the position where the center of the clickable marker will be.

---
## Adding position data
In order to orient, position and scale the map automatically, you have to provide position data.
1. Pick two points on your created map. These points should be easily and precisely selectable on a map with only outlines of the buildings. Corners of buildings are recommended as points.
2. On your map, place an ellipse on each of the points. The center of the ellipse should be exactly at the point you chose. You can make the ellipse very small to not interfere with the map visually. The size of the ellipse does not matter.\\
Make one of the ellipses `RED (#FF0000)` and the other one `BLUE (#0000FF)`. These exact color values are important.
3. Get the exact coordinates of these two points on a world map. Note the positions of the red and the blue point.\
You can use [uMap](https://umap.openstreetmap.de/de/map/new/#15/49.0141/8.4183) for this step. Find the points on the uMap map and place a marker at this point. You can get the exact coordinates of the marker under coordinates.

---
## Parse the data
