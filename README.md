# Loading .obj file in OpenGL
## Introduction
In this project, we will only deal with OBJ files with 1 UV coordinate and 1 normal per vertex.

OBJ (or .OBJ) is a geometry definition file format first developed by Wavefront Technologies for its Advanced Visualizer animation package. The file format is open and has been adopted by other 3D graphics application vendors.

The OBJ file format is a simple data-format that represents 3D geometry alone — namely, the position of each vertex, the UV position of each texture coordinate vertex, vertex normals, and the faces that make each polygon defined as a list of vertices, and texture vertices. Vertices are stored in a counter-clockwise order by default, making explicit declaration of face normals unnecessary. OBJ coordinates have no units, but OBJ files can contain scale information in a human readable comment line.

## Example OBJ file
### 1 UV coordinate and 1 normal per vertex
An OBJ file looks more or less like this :    
```
# Blender3D v249 OBJ File: untitled.blend
# www.blender3d.org
mtllib cube.mtl
# List of geometric vertices, with (x, y, z [,w]) coordinates, w is optional and defaults to 1.0.
# Example: v 0.123 0.234 0.345 1.0
v 1.000000 -1.000000 -1.000000
v 1.000000 -1.000000 1.000000
v -1.000000 -1.000000 1.000000
v -1.000000 -1.000000 -1.000000
v 1.000000 1.000000 -1.000000
v 0.999999 1.000000 1.000001
v -1.000000 1.000000 1.000000
v -1.000000 1.000000 -1.000000
# List of texture coordinates, in (u, [,v ,w]) coordinates, these will vary between 0 and 1. v, w are optional and default to 0.
# Example: vt 0.500 1 [0]
vt 0.748573 0.750412
vt 0.749279 0.501284
vt 0.999110 0.501077
vt 0.999455 0.750380
vt 0.250471 0.500702
vt 0.249682 0.749677
vt 0.001085 0.750380
vt 0.001517 0.499994
vt 0.499422 0.500239
vt 0.500149 0.750166
vt 0.748355 0.998230
vt 0.500193 0.998728
vt 0.498993 0.250415
vt 0.748953 0.250920
# List of vertex normals in (x,y,z) form; normals might not be unit vectors.
# Example: vn 0.707 0.000 0.707
vn 0.000000 0.000000 -1.000000
vn -1.000000 -0.000000 -0.000000
vn -0.000000 -0.000000 1.000000
vn -0.000001 0.000000 1.000000
vn 1.000000 -0.000000 0.000000
vn 1.000000 0.000000 0.000001
vn 0.000000 1.000000 -0.000000
vn -0.000000 -1.000000 0.000000
# Parameter space vertices in ( u [,v] [,w] ) form; free form geometry statement ( see below )
# Example: vp 0.310000 3.210000 2.100000
usemtl Material_ray.png
s off
# Polygonal face element
f 5/1/1 1/2/1 4/3/1
f 5/1/1 4/3/1 8/4/1
f 3/5/2 7/6/2 8/7/2
f 3/5/2 8/7/2 4/8/2
f 2/9/3 6/10/3 3/5/3
f 6/10/4 7/6/4 3/5/4
f 1/2/5 5/1/5 2/9/5
f 5/1/6 6/10/6 2/9/6
f 5/1/7 8/11/7 6/10/7
f 8/11/7 7/12/7 6/10/7
f 1/2/8 2/9/8 3/13/8
f 1/2/8 3/13/8 4/14/8
# Line element (see below)
# l 5 8 1 2 4 9
```
So :   

***#*** is a comment, just like **//** in C++   
***usemtl*** and ***mtllib*** describe the look of the model.   
***v*** is a vertex   
***vt*** is the texture coordinate of one vertex   
***vn*** is the normal of one vertex   
***f*** is a face  

v, vt and vn are simple to understand. f is more tricky. So, for f 8/11/7 7/12/7 6/10/7 :   

***8/11/7*** describes the first vertex of the triangle   
***7/12/7*** describes the second vertex of the triangle   
***6/10/7*** describes the third vertex of the triangle (duh)   

For the first vertex,   
***8*** says which vertex to use. So in this case, -1.000000 1.000000 -1.000000 (index start to 1, not to 0 like in C++)  
***11*** says which texture coordinate to use. So in this case, 0.748355 0.998230  
***7*** says which normal to use. So in this case, 0.000000 1.000000 -0.000000  


## Reference
[Tutorial 7 : Model loading](http://www.opengl-tutorial.org/beginners-tutorials/tutorial-7-model-loading/#loading-the-obj)    
[Wavefront .obj file Wikipedia](https://en.wikipedia.org/wiki/Wavefront_.obj_file)     

