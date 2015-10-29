# AM Packing Benchmarks

This repository contains my personal (putative/quasi-optimum) solutions for some selected packing problem benchmark instances.

Some of the solutions are also listed on Eckard Specht's excellent website www.packomania.com. He has nice pictures, shortest tours of the items and a contact anlysis for each packing. Note that he uses a different file format and normalizes most of the container sizes to 1.


## Inventory


### 2D Benchmark Instances

* min-Disk(Disk): circles in smallest enclosing circle
  * r(i) = i ("Al Zimmermann's contest set"), n=1-200
  * r(i) = i ^ (+1/2), n=1-100
  * r(i) = i ^ (-1/2), n=1-100
  * r(i) = i ^ (-2/3), n=1-100
  * r(i) = i ^ (-1/5), n=1-100

* min-Square(Disk): circles in smallest enclosing square
  * r(i) = 1, n=1-100
  * r(i) = i, n=1-100
  * r(i) = i ^ (+1/2), n=1-100
  * r(i) = i ^ (-1/2), n=1-100


### 3D Benchmark Instances

min-Sphere(Sphere): spheres in smallest enclosing sphere
  * r(i) = 1, n=1-100
  * r(i) = i, n=1-100



## Conventions


### Terms, Symbols, etc.

 * items : objects to be packed
 * container : object(s) enclosing the items
 * n : number of items
 * i : item index in range [1,n]
 * i = 0 : container index


### File Format
* the encoding is ASCII, multibyte characters must not be used
* line endings are expected to be LF only
* whitespace apart from LF does not have any semantic meaning


#### Simple Packing File Format (.pac)
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


#### Simple Packing Input File Format (.shp)
```
<entity-type>
<number of entities n>
<entity-specification 1>
<entity-specification 2>
...
<entity-specification n>
```

#### Entity Specifications
* ```entity-specification```: ```shape-specification``` ```placing```
* ```placing```:              ```position``` ```orientation``` ```scaling```
* ```position```:             ```center``` ```coordinates x, y, z, a, b, ...```
* ```orientation```:          ```angle between local and global x-axis``` or ```unit quaternion```
* ```shape-specification```:
  | symbol            | description                                                          |
  | ---               | ---                                                                  |
  | ```r          ``` | radius                                                               |
  | ```h          ``` | half length                                                          |
  | ```l          ``` | full length                                                          |
  | ```hx         ``` | half length on axis x                                                |
  | ```lx         ``` | full length on axis x                                                |
  | ```p          ``` | angle between local and global x-axis (counter-clockwise) in degrees |
  | ```qw qx qy qz``` | orientation quaternion (qw: scalar part)                             |


#### Simple 2D Entity Types
| type            | description                      | specification       |
| --------------- | ----------------------------     | ---------------     |
| Disk            | circle                           | ```r      x y   ``` |
| SquareAA        | axis-aligned square              | ```h      x y   ``` |
| Square          | freely rotatable square          | ```h      x y  p``` |
| Rectangle       | axis-aligned rectangle           | ```hx hy  x y   ``` |
| RectangleAA     | freely rotatable rectangle       | ```hx hy  x y  p``` |
| RegularPolygon  | regular n-gon                    | ```r      x y   ``` |
| Capsule2d       | rectangle with hemicircular caps | ```r h    x y   ``` |

#### Simple 3D Entity Types
| type               | description                      | specification                      |
| ---------------    | ----------------------------     | ---------------                    |
| Sphere             | sphere                           | ```r         x y z             ``` |
| CubeAA             | axis-aligned cube                | ```h         x y z             ``` |
| Cube               | freely rotatable cube            | ```h         x y z  qw qx qy qz``` |
| CuboidAA           | axis-aligned cuboid              | ```hx hy hz  x y z             ``` |
| Cuboid             | freely rotatable cuboid          | ```hx hy hz  x y z  qw qx qy qz``` |
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

#### Special Entity Types
| type              | description                          | specification                   |
| ------------      | ----------------------------         | ---------------                 |
| $file             | name of .shp file                    | ```filename```                  |
| $file // $placing | name of .shp file and transformation | ```filename``` // ```placing``` |


#### Examples
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

