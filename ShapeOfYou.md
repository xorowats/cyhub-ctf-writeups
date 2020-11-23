# Shape Of You

I downloaded the file and the extension is .blend, which is a project file for Blender which is a 3D modeling program. So let's download blender and open the file.

![Banner](images/3ds1.PNG?raw=true "3ds1")

I thought the flag might be somehow hidden in the file or somewhere in the project, but didn't find anything. I looked at the points of the object and noticed that the coordinates of the points were looking like ascii charecters, like 72, 80, 65. And there were. 

![Banner](images/3ds2.PNG?raw=true "3ds2")

The thing is the order of the charecters, there's a lot of them. So I used the python console inside blender to investigate. I got some code to get the coordinates of a vertex of an object, and every vertex hax an index 0,1,2,3,...

```python
import bpy
object = bpy.data.objects['Obroglatron']
v_local = object.data.vertices[0].co
print(v_local[0])
```
![Banner](images/3ds3.PNG?raw=true "3ds3")

With a couple of loops we can print all the coords and convert them to charecters.

![Banner](images/3ds4.PNG?raw=true "3ds4")

And we get the flag.
