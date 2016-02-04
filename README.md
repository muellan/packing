# AM Packing Benchmarks

This repository contains my personal (putative/quasi-optimum) solutions for many packing problem benchmark instances.

Some of the solutions are also listed on Eckard Specht's excellent website www.packomania.com. He has nice pictures, shortest tours of the items and a contact analysis for each packing. Note that he uses a different file format and normalizes most of the container sizes to 1.

You should also have a look at http://www2.stetson.edu/~efriedma/packing.html.

See below for a list of all benchmarks, tables of all the symbols used, etc.


#### Repository Structure
```
container_type 
    scenario_type
        {overview images}
        {benchmark result lists}
        item_shape_distribution
            {result packing files}
```

#### Conventions
 * items : objects to be packed
 * container : object(s) enclosing the items
 * n : number of items
 * i : item index in range [1,n]
 * i = 0 : container index
 * Containers are centered at the global origin and aligned to the coordinate system axes.
 * Symbols referring to container properties start with an uppercase letter.


#### Scenario / Folder Names
 * find smallest container for a set of items:
   "min-ContainerType(ItemType)"
 * find legal arrangement of items in a rigid container:
   "ContainerType(ItemType)"



## Inventory

| Scenario                         | Description                                                 |
| -------------------------------- | ----------------------------------------------------------- |
| min-Circle(Circle)               | circles in smallest enclosing circle                        |
| min-Circle(ConvexRegularPolygon) | convex regular polygon in smallest enclosing circle         |
| min-Square(Circle)               | circles in smallest enclosing square                        |
| min-Square(Square)               | freely rotatable squares in smallest enclosing square       |
| min-Square(ConvexRegularPolygon) | convex regular polygon in smallest enclosing square         |
| min-Rectangle(Circle)            | circles in smallest enclosing rectangle                     |
| min-Rectangle(RectangleAA)       | axis-oriented rectangles in smallest enclosing rectangle    |
| min-Rectangle(Rectangle)         | freely rotatable rectangles in smallest enclosing rectangle |
| min-Sphere(Sphere)               | spheres in smallest enclosing sphere                        |
| min-Cube(Sphere)                 | spheres in smallest enclosing cube                          |
| min-Cuboid(Sphere)               | spheres in smallest enclosing cuboid                        |
| min-Cube(Cube)                   | cubes in smallest enclosing cube                            |
| min-Cube(CubeAA)                 | axis-aligned cubes in smallest enclosing cube               |
| min-Cuboid(Cuboid)               | cuboids in smallest cuboid                                  |
| min-Sphere4d(Sphere4d)           | 4d hyperspheres in smallest enclosing 4d hypersphere        |
| min-Sphere5d(Sphere5d)           | 5d hyperspheres in smallest enclosing 5d hypersphere        |


### 2D Benchmark Instances

| Container Type    | Item Type       | Item Shape Distribution   | n       |                               |
| ----------------- | --------------- | ------------------------- | ------- | ----------------------------- |
| min-Circle        | Circle          | r(i) = 1                  | 1 - 600 |                               |
| min-Circle        | Circle          | r(i) = i                  | 1 - 200 | "Al Zimmermann's contest set" |
| min-Circle        | Circle          | r(i) = i ^ (+1/2)         | 5 - 100 |                               |
| min-Circle        | Circle          | r(i) = i ^ (-1/2)         | 5 - 100 |                               |
| min-Circle        | Circle          | r(i) = i ^ (-2/3)         | 5 - 100 |                               |
| min-Circle        | Circle          | r(i) = i ^ (-1/5)         | 5 - 100 |                               |
| min-Circle        | RegularTriangle | r(i) = 1                  | 2 - 100 |                               |
| min-Circle        | RegularTriangle | r(i) = i                  | 2 - 100 |                               |
| min-Circle        | RegularPentagon | r(i) = 1                  | 2 - 100 |                               |
| min-Circle        | RegularPentagon | r(i) = i                  | 2 - 100 |                               |
| min-Circle        | RegularHexagon  | r(i) = 1                  | 2 - 100 |                               |
| min-Circle        | RegularHexagon  | r(i) = i                  | 2 - 100 |                               |
| min-Circle        | RegularOctagon  | r(i) = 1                  | 2 - 100 |                               |
| min-Circle        | RegularOctagon  | r(i) = i                  | 2 - 100 |                               |
| min-Square        | Circle          | r(i) = 1                  | 1 - 100 |                               |
| min-Square        | Circle          | r(i) = i                  | 1 - 100 |                               |
| min-Square        | Circle          | r(i) = i ^ (+1/2)         | 5 - 100 |                               |
| min-Square        | Circle          | r(i) = i ^ (-1/2)         | 5 - 100 |                               |
| min-Square        | Square          | h(i) = 1                  | 1 - 100 |                               |
| min-Square        | Square          | h(i) = i                  | 1 - 100 |                               |
| min-Square        | RegularTriangle | r(i) = 1                  | 2 - 100 |                               |
| min-Square        | RegularTriangle | r(i) = i                  | 2 - 100 |                               |
| min-Square        | RegularPentagon | r(i) = 1                  | 2 - 100 |                               |
| min-Square        | RegularPentagon | r(i) = i                  | 2 - 100 |                               |
| min-Square        | RegularHexagon  | r(i) = 1                  | 2 - 100 |                               |
| min-Square        | RegularHexagon  | r(i) = i                  | 2 - 100 |                               |
| min-Square        | RegularOctagon  | r(i) = 1                  | 2 - 100 |                               |
| min-Square        | RegularOctagon  | r(i) = i                  | 2 - 100 |                               |
| min-Rectangle     | Circle          | r(i) = 1                  | 1 - 100 |                               |
| min-Rectangle     | Circle          | r(i) = i                  | 1 - 100 |                               |
| min-Rectangle     | RetangleAA      | hx(i)=i, hy(i)=0.750·i    | 1 - 100 |                               |
| min-Rectangle     | RetangleAA      | hx(i)=i, hy(i)=0.500·i    | 1 - 100 |                               |
| min-Rectangle     | RetangleAA      | hx(i)=i, hy(i)=0.250·i    | 1 - 100 |                               |
| min-Rectangle     | RetangleAA      | hx(i)=i, hy(i)=0.125·i    | 1 - 100 |                               |
| min-Rectangle     | Rectangle       | hx(i)=i, hy(i)=0.750·i    | 1 - 100 |                               |
| min-Rectangle     | Rectangle       | hx(i)=i, hy(i)=0.500·i    | 1 - 100 |                               |
| min-Rectangle     | Rectangle       | hx(i)=i, hy(i)=0.250·i    | 1 - 100 |                               |
| min-Rectangle     | Rectangle       | hx(i)=i, hy(i)=0.125·i    | 1 - 100 |                               |


### 3D Benchmark Instances
  
| Container Type | Item Type  | Item Shape Distribution                | n       |                     |
| -------------- | ---------- | -------------------------------------- | ------- | ------------------- |
| min-Sphere     | Sphere     | r(i) = 1                               | 1 - 100 |                     |
| min-Sphere     | Sphere     | r(i) = i                               | 1 - 100 |                     |
| min-Cube       | Sphere     | r(i) = 1                               | 1 - 100 |                     |
| min-Cube       | Sphere     | r(i) = i                               | 1 - 100 |                     |
| min-Cube       | Cube       | h(i) = 1                               | 1 - 100 |                     |
| min-Cube       | Cube       | h(i) = i                               | 1 - 100 |                     |
| min-Cube       | CubeAA     | h(i) = 1                               | 1 - 100 |                     |
| min-Cube       | CubeAA     | h(i) = i                               | 1 - 100 |                     |
| min-Cuboid     | Sphere     | r(i) = 1                               | 1 - 100 |                     |
| min-Cuboid     | Sphere     | r(i) = i                               | 1 - 100 |                     |
| min-Cuboid     | Cuboid     | hx(i)=i, hy(i)=0.75·i,  hz(i)=0.5·i    | 2 - 100 | "boxes"   4 x 3 x 2 |
| min-Cuboid     | Cuboid     | hx(i)=i, hy(i)=0.5·i,   hz(i)=0.25·i   | 2 - 100 | "bricks"  4 x 2 x 1 |
| min-Cuboid     | Cuboid     | hx(i)=i, hy(i)=0.5·i,   hz(i)=0.1·i    | 2 - 100 | "plates" 10 x 5 x 1 |
| min-Cuboid     | Cuboid     | hx(i)=i, hy(i)=0.125·i, hz(i)=0.125·i  | 2 - 100 | "poles"   8 x 1 x 1 |
| min-Cuboid     | Cuboid     | AM cuboid set 1                        | 2 - 100 |                     |


### 4D & 5D Benchmark Instances

| Container Type | Item Type  | Item Shape Distribution  | n                       | 
| -------------- | ---------- | ------------------------ | ----------------------- | 
| min-Sphere4d   | Sphere4d   | r(i) = i                 | 10, 20, 30, 40, 50, 100 | 
| min-Sphere5d   | Sphere5d   | r(i) = i                 | 10, 20, 30, 40, 50, 100 | 



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
| symbol                            | description                                            |
| -----------------                 | ----------------------------------------               |
| ```x```, ```y```, ```z```, ...    | x,y,z...-coordinate of the local origin                |
| ```p```                           | angle(local x, global x), counter-clockwise in radians |
| ```qw qx qy qz```                 | orientation unit quaternion (qw: scalar part)          |
| ```sx```, ```sy```, ```sz```, ... | scaling along x,y,z...-axis                            |


#### Simple 2D Entity Types
| type            | description                       | specification                  |
| --------------- | ----------------------------      | ---------------                |
| Circle          | circle                            | ```r```      ```x y```         |
| SquareAA        | axis-aligned square               | ```h```      ```x y```         |
| Square          | freely rotatable square           | ```h```      ```x y``` ```p``` |
| RectangleAA     | axis-aligned rectangle            | ```hx hy```  ```x y```         |
| Rectangle       | freely rotatable rectangle        | ```hx hy```  ```x y``` ```p``` |
| RegularTriangle | freely rotatable regular triangle | ```r```      ```x y``` ```p``` |
| RegularPentagon | freely rotatable regular pentagon | ```r```      ```x y``` ```p``` |
| RegularHexagon  | freely rotatable regular hexagon  | ```r```      ```x y``` ```p``` |
| RegularOctagon  | freely rotatable regular octagon  | ```r```      ```x y``` ```p``` |
| Capsule2d       | rectangle with semicircular caps  | ```r h```    ```x y``` ```p``` |

#### Simple 3D Entity Types
| type               | description                      | specification                                |
| ---------------    | ----------------------------     | ---------------                              |
| Sphere             | sphere                           | ```r```        ```x y z```                   |
| CubeAA             | axis-aligned cube                | ```h```        ```x y z```                   |
| Cube               | freely rotatable cube            | ```h```        ```x y z``` ```qw qx qy qz``` |
| CuboidAA           | axis-aligned cuboid              | ```hx hy hz``` ```x y z```                   |
| Cuboid             | freely rotatable cuboid          | ```hx hy hz``` ```x y z``` ```qw qx qy qz``` |
| RegularTetrahedron | regular tetrahedron              | ```r```        ```x y z``` ```qw qx qy qz``` |
| Capsule            | cylinder with hemispherical caps | ```r h```      ```x y z``` ```qw qx qy qz``` |

#### Simple Entity Types (more than 3 dimensions)
| type            | description                  | specification           |
| --------------- | ---------------------------- | ---------------         |
| HyperSphere4d   | 4-dimensional sphere         | ```r``` ```x y z a  ``` |
| HyperSphere5d   | 5-dimensional sphere         | ```r``` ```x y z a b``` |


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
* A packing solution file for the min-Circle(Circle) problem:
  ```
  #PACKING
  #CONTAINER
  Circle
  1
  5  0 0
  #CONTENT
  Circle
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

