# C++ R-Tree with runtime Dimensionality 
The project is forked from another github project
https://github.com/nushoin/RTree, which itself is a further development of this R-Tree implementation: http://superliminal.com/sources/sources.htm.

The aim of this project is to allow the dimension to be specified at runtime and not as a template parameter at compile time.

I tried to adapt the source code so that the interfaces remain the same and the query performance corresponds as far as possible to the templated implementation.

According to my measurements at the time of writing, the queries of this version are ~12% slower compared to the implementation with templated dimension and I do not believe it can be made faster.
This performance price is to be paid for the dynamic dimension. The resulting version (query time) is still significantly faster than boost:geometry::index::rtree.

The mentioned slight loss of performance prevents this forked version from being played back into the original implementation. If the dimension is known in advance, I would still recommend the implementation https://github.com/nushoin/RTree.

## Usage

```cpp
#include <RTree.h>

// ...

DynDimRTree::RTree<Foo*, double> tree(3);
double min[3] = {0., 0., 0.};
double max[3] = {1., 1., 1.};
Foo* bar = new Foo();
tree.Insert(min, max, bar);
```

Provides search in and iteration over the 3d rtree. For examples see
[Test.cpp](https://github.com/Sergey-Grosman/DynDimRTree/blob/master/Test.cpp)

## Build
Use your favorite IDE or the following commands
```shell script
mkdir bin
cd bin
cmake ../
cmake --build .
```
Afterwards you can run `test0`, `test1` and `test2`.<br>
The RTree itself is
a single header file and can be included without compiling.

## Authors

- 1983 Original algorithm and test code by Antonin Guttman and Michael Stonebraker, UC Berkely
- 1994 ANCI C ported from original test code by Melinda Green - melinda@superliminal.com
- 1995 Sphere volume fix for degeneracy problem submitted by Paul Brook
- 2004 Templated C++ port by Greg Douglas
- 2011 Modified the container to support more data types, by Yariv Barkan
- 2017 Modified Search to take C++11 function to allow lambdas and added const qualifier, by Gero Mueller
- 2020 Provided the possibility to set the dimension at run time, by Sergey Grosman

## License

Original code was taken from https://github.com/nushoin/RTree 
and is stored as git revision 0. This revision is entirely free for all
uses. Enjoy!

We are also happy to inherit the license settings.
    
In jurisdictions where public domain property is recognized, the user of
this software may choose to accept it either 1) as public domain, 2) under
the conditions of the BSD, MIT or GPL or 3) any combination of public
domain and one or more of these licenses.
