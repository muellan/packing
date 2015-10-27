# AM Packing Benchmarks

This repository contains my personal (putative/quasi-optimum) solutions for some selected packing problem benchmark instances.



## 2D Benchmark Instances


### Spherical Items
* min-Disk(Disk): circle in smallest enclosing circle
  * r(i) = i ("Al Zimmermann's contest set")
  * r(i) = i ^ (+1/2)
  * r(i) = i ^ (-1/2)
  * r(i) = i ^ (-2/3)
  * r(i) = i ^ (-1/5)
  * Huang et al. set

* min-Square(Disk): circles in smallest enclosing square
  * r(i) = 1
  * r(i) = i 
  * r(i) = i ^ (+1/2)
  * r(i) = i ^ (-1/2)


## 3D Benchmark Instances

min-Sphere(Sphere): spheres in smallest enclosing sphere



## Conventions


### Terms, Symbols, etc.

 * items = objects to be packed
 * container = object(s) enclosing the items
 * n = number of items
 * N = number of containers
 * i = item index in range [1,n]


### File Format

#### Simple Packing File Format (.pac)

```
#CONTAINER
  <entity-type>
  <number of containers N>
  <container 1 entity-specification>
  <container 2 entity-specification>
  ...
  <container n entity-specification>
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
* entity-specification: shape-specification placing
* shape-specification: 
* placing: position orientation scaling
* position: x y z
* orientation: 2d: angle with x-axis (ccw), 3d: unit quaternion

| type class | specification |
|---|---|
| spherical | radius center |
| cuboidal (axis-aligned) | half-lengths center |
| cuboidal | half-lengths center orientation |


## See Also
Some of the solutions are also listed on Eckard Specht's excellent site www.packomania.com. Note that he uses a different file format.
