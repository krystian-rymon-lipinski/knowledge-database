Grafika wektorowa.
Źródło: https://www.w3.org/TR/SVG/paths.html
 Example:
 ```
 M100,100 L300,100 L200,300 z  
//or  
M 100 100 L 300 100 L 200 300 z  
//or  
M1100,100L300,100L200,300z
 ```
 The alphabet can be upper or lowercase. **Uppercase means absolute position, lowercase means relative position**.

## Commands

**M** or **m (X,Y)+  
moveto**: Move cursor to position, uppercase is absolute, lowercase is relative  
moveto commands are followed by X,Y coordinates. There can be more than one set of coordinates following an M command, these are treated as implicit lineto commands.

**Z** or **z  
closepath**: Draws a line from the current position of the cursor to the start position of the path. Does not have any parameters.

**L** or **l** **(X,Y)+**  
**lineto**: Draws a line from the current position to the position specified by X,Y. Uppercase means absolute coordinates, lowercase means relative coordinates. You can have more than one set of coordinates following a lineto command. If you want specify more than one set of coordinates, it means that you’re creating a polyline (shape consisting of multiple string lines).

**H** or **h (X)+  
Horizontal lineto** draws a horizontal line from the current cursor position to the position specified by X. If there are multiple X coordinates following the command, this is treated as a polyline. The Y coordinate remains unchanged. Uppercase **H** is absolute coordinates, lowercase **h** is relative coordinates.

**V** or **v (Y)+  
Vertical lineto** draws a vertical line from the current cursor position to the position specified by Y. If there are multiple Y coordinates following the command, this is treated as a polyline. The X coordinate remains unchanged. Uppercase **V** is absolute coordinates, lowercase **v** is relative coordinates.


**Arcs:**
The elliptical arc command draws a section of an ellipse which must meet the following constraints:

-   the arc starts at the current point
-   the arc ends at point (**x**, **y**)
-   the ellipse has the two radii (**rx**, **ry**)
-   the x-axis of the ellipse is rotated by **x-axis-rotation** degrees relative to the x-axis of the current coordinate system.

```xml
<path d="M300,200 h-150 a150,150 0 1,0 150,-150 z"
        fill="red" stroke="blue" stroke-width="5" />
```

https://www.w3.org/TR/SVG/paths.html#PathDataEllipticalArcCommands