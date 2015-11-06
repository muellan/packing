# AM Packing Benchmarks

This repository contains my personal (putative/quasi-optimum) solutions for some selected packing problem benchmark instances.

Some of the solutions are also listed on Eckard Specht's excellent website www.packomania.com. He has nice pictures, shortest tours of the items and a contact anlysis for each packing. Note that he uses a different file format and normalizes most of the container sizes to 1.

You should also have a look on http://www2.stetson.edu/~efriedma/packing.html.


#### Conventions
 * items : objects to be packed
 * container : object(s) enclosing the items
 * n : number of items
 * i : item index in range [1,n]
 * i = 0 : container index
 * Containers are centered at the global origin and aligned to the coordinate system axes.
 * Symbols referring to container properties start with an uppercase letter.


#### Scenario / Folder Names
 * find smallest container for set of items:
   "min-ContainerType(ItemType)"
 * find legal arrangement of items in rigid container:
   "ContainerType(ItemType)"


## Inventory


### 2D Benchmark Instances

* min-Disk(Disk): circles in smallest enclosing circle
  * r(i) = 1, n=1-600
  * r(i) = i ("Al Zimmermann's contest set"), n=1-200
  * r(i) = i ^ (+1/2), n=5-100
  * r(i) = i ^ (-1/2), n=5-100
  * r(i) = i ^ (-2/3), n=5-100
  * r(i) = i ^ (-1/5), n=5-100

* min-Square(Disk): circles in smallest enclosing square
  * r(i) = 1, n=1-100
  * r(i) = i, n=1-100
  * r(i) = i ^ (+1/2), n=5-100
  * r(i) = i ^ (-1/2), n=5-100

* min-Rectangle(Disk): circles in smallest enclosing rectangle
  * r(i) = 1, n=1-100
  * r(i) = i, n=1-100

* min-Square(Square): squares in smallest enclosing square
  * h(i) = 1, n=1-100
  * h(i) = i, n=1-100

* min-Rectangle(RectangleAA): axis-oriented rectangles in smallest enclosing rectangle
  * hx(i)=i, hy(i)=0.750*i, n=1-100
  * hx(i)=i, hy(i)=0.500*i, n=1-100
  * hx(i)=i, hy(i)=0.250*i, n=1-100
  * hx(i)=i, hy(i)=0.125*i, n=1-100



### 3D Benchmark Instances
  
* min-Sphere(Sphere): spheres in smallest enclosing sphere
  * r(i) = 1, n=1-100
  * r(i) = i, n=1-100

* min-Cube(Sphere): spheres in smallest enclosing cube
  * r(i) = 1, n=1-100
  * r(i) = i, n=1-100

* min-Cuboid(Sphere): spheres in smallest enclosing cuboid
  * r(i) = 1, n=1-100
  * r(i) = i, n=1-100


### 4D & 5D Benchmark Instances

* min-Sphere4d(Sphere4d): 4d hyperspheres in smallest enclosing 4d hypersphere
  * r(i) = i, n=10,20,30,40,50,100

* min-Sphere5d(Sphere5d): 5d hyperspheres in smallest enclosing 5d hypersphere
  * r(i) = i, n=10,20,30,40,50,100



## File Format
* the encoding is ASCII, multibyte characters must not be used
* line endings are expected to be LF only
* whitespace apart from LF does not have any semantic meaning other than separating numbers or identifier texts


### Packing File Format (.pac)
```
#PACKING
#CONTAINER
  <entity-type>
  1
  <container entity-specification>
#CONTENT
   <entity-type>
   <number of items n>
   <item 1 entity-specification>
   <item 2 entity-specification>
   ...
   <item n entity-specification>
```


### Packing Input File Format (.shp)
```
<entity-type>
<number of entities n>
<entity-specification 1>
<entity-specification 2>
...
<entity-specification n>
```

#### Entity Specification
* ```entity-specification``` : ```shape-specification``` ```placing```
* ```placing``` : ```position``` ```orientation``` ```scaling```
* ```position``` : ```center coordinates x, y, z, a, b, ...```
* ```orientation``` : ```angle between local and global x-axis``` or ```unit quaternion```
* ```scaling``` : ```scaling factors sx, sy, sz, sa, sb, ...```


#### Shape Specification
| symbol   | description           |
| -------- | --------------------- |
| ```r```  | radius                |
| ```h```  | half length           |
| ```l```  | full length           |
| ```hx``` | half length on axis x |
| ```lx``` | full length on axis x |


#### Shape Placing
| symbol                            | description                              |
| -----------------                 | ---------------------------------------- |
| ```x```, ```y```, ```z```, ...    | x,y,z...-coordinate of the local origin  |
| ```p```                           | angle (local x, global x) in radians     |
| ```qw qx qy qz```                 | orientation quaternion (qw: scalar part) |
| ```sx```, ```sy```, ```sz```, ... | scaling along x,y,z...-axis              |


#### Simple 2D Entity Types
| type                  | description                      | specification       |
| ---------------       | ----------------------------     | ---------------     |
| Disk / Circle         | circle                           | ```r      x y   ``` |
| SquareAA              | axis-aligned square              | ```h      x y   ``` |
| Square                | freely rotatable square          | ```h      x y  p``` |
| RectangleAA / Box2dAA | axis-aligned rectangle           | ```hx hy  x y   ``` |
| Rectangle / Box2d     | freely rotatable rectangle       | ```hx hy  x y  p``` |
| RegularPolygon        | regular n-gon                    | ```r      x y   ``` |
| Capsule2d             | rectangle with hemicircular caps | ```r h    x y   ``` |

#### Simple 3D Entity Types
| type               | description                      | specification                      |
| ---------------    | ----------------------------     | ---------------                    |
| Sphere             | sphere                           | ```r         x y z             ``` |
| CubeAA             | axis-aligned cube                | ```h         x y z             ``` |
| Cube               | freely rotatable cube            | ```h         x y z  qw qx qy qz``` |
| CuboidAA / Box3dAA | axis-aligned cuboid              | ```hx hy hz  x y z             ``` |
| Cuboid / Box3d     | freely rotatable cuboid          | ```hx hy hz  x y z  qw qx qy qz``` |
| RegularTetrahedron | regular tetrahedron              | ```r         x y z             ``` |
| Capsule            | cylinder with hemispherical caps | ```r h       x y z             ``` |

#### Simple Entity Types (more than 3 dimensions)
| type            | description                  | specification      |
| --------------- | ---------------------------- | ---------------    |
| HyperSphere4d   | 4-dimensional sphere         | ```r  x y z a  ``` |
| HyperSphere5d   | 5-dimensional sphere         | ```r  x y z a b``` |


#### Complex Entity Types
* Polygon: planar, closed and possibly non-convex polygon with m points and m edges (orientation: ccw) 
  ```
  <number of points m>
  <point 1>
  <point 2>
  ...
  <point m>
  x y  p
  ```

* TriangleCompound: collection of triangles "triangle soup"
  ```
  <number of triangles m>
  <point 1-a> <point 1-b> <point 1-c>
  <point 2-a> <point 2-b> <point 2-c>
  ...
  <point m-a> <point m-b> <point m-c>
  x y z  qw qx qy qz
  ```


#### Special Entity Types
| type              | description                          | specification                   |
| ------------      | ----------------------------         | ---------------                 |
| $file             | name of .shp file                    | ```filename```                  |
| $file // $placing | name of .shp file and transformation | ```filename``` // ```placing``` |
  

### Examples
* A packing solution file for the min-Disk(Disk) problem:
  ```
  #PACKING
  #CONTAINER
  Disk
  1
  5  0 0
  #CONTENT
  Disk
  3
  1  1 3
  2  3 0
  3  -2 0
  ```

* A packing file that references 3 .shp files containing some polygons:
  ```
  #PACKING
  #CONTAINER
  RectangleAA
  1
  100 200 0 0
  #CONTENT
  $file // $placing
  3
  singlePolygon1.shp // -10.5 6.7  12.34
  singlePolygon2.shp // 0.0 0.0    10
  manyPolygons.shp   // 12.4 -23   270
  ```

* A .shp file specifying two 4-sided polygons:
  ```
  Polygon
  2
  4
  0.0 0.0
  5.0 0.0
  5.0 4.0
  6.0 0.0
    1.023 -0.34
  4
  0.0 0.0
  5.0 0.0
  5.0 5.0
  5.0 0.0
    -12.2 4.5
  ```

