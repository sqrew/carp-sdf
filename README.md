# carp-sdf
A high-performance Signed Distance Field (SDF) module for the Carp programming language.

## Features
- **CPU + GPU Logic**: Provides pure Carp functions for distance queries and WGSL snippets for GPU shaders.
- **Primitives**: Sphere, Box, Torus.
- **Operations**: Union, Subtraction, Intersection, and the legendary **Smooth Union** (Gooey Merge).
- **Zero Dependencies**: Includes its own minimal math types for maximum portability.

## Installation
```clojure
(load "https://github.com/sqrew/carp-sdf@master")
```

## Usage (CPU)
```clojure
(use Sdf)
(use Vec3)

(let [p (Vec3.new 0.0 5.0 0.0)
      d (Sdf.sphere &p 1.0)]
  (println* "Distance to sphere: " (str d)))
```

## Usage (GPU)
```clojure
(use Sdf)

(def my-shader 
  (str* Sdf.Wgsl.sphere 
        Sdf.Wgsl.smooth-union
        "// Your raymarching code here..."))
```

## License
MIT
