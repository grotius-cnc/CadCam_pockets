# CadCam_pockets
This is a upload of the current status of the CadCam program. Not finished, only for info to other parties.

The Cad Cam program has a opengl interface. This upload is specific for testing pocket offsets, CavalierContours https://github.com/jbuckmccready/CavalierContours

The program has no QT dependencies. It's important to use the std library and leave the QT libraries untouched. 
In this way the program can be ported to other platforms in minutes. 

The program can load dxf files from : 
-librecad, use only the spline trough points. 
-freecad.
-inkscape, used for trace bitmap, objects to path.

The program has a contour recognize button (process) to reorganize the dxf drawing into closed contour path's. 
- Red is a cw path. 
- Yellow is a ccw path.
- Grey is open path.
The contour recognize class is a powerfull one that can handle huge ammounts of dxf data. More then sheetcam or dxf2gcode.
The offset parameter is - for inside and + for outside offset.

The order of contours is done by the depth sequence. Depth 0 is the contour without inner objects. Depth 1 is a inside contour of Depth 0, and so on.
There is no limit to the depth sequence. The cnc cut sequence is perfect ordered in this way.

The gcode output is done for the orginal cad contour. Later it can be expanded to process specific cad layers, contours, depth's, etc.  
Think about adding post processor files etc.

Another great 15 minute invention is the true spline primitive. 
This is a natural cubic spline algoritme that has a unique property. The spline has no difference if drawed
from left to right or visa versa. Therefore it's great to implement in cnc machinery, stock market prediction, robot backwards interpolation etc.
The spline can be swapped wihout noticing any changes in output. 

Used spline algoritme : https://mathworld.wolfram.com/CubicSpline.html
Expanded with : difference function

CadCam program output example wihout islands, see cam_offset.h :
![alt text](https://raw.githubusercontent.com/grotius-cnc/CadCam_pockets/master/example/printed_circuit_contour_offset.png)
Example with islands, the islands are added in a loop, deactivate the comments cam_offset.h :
![alt text](https://raw.githubusercontent.com/grotius-cnc/CadCam_pockets/master/example/evolution_pocket.png)
