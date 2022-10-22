
[![Arduino CI](https://github.com/RobTillaart/moduloMap/workflows/Arduino%20CI/badge.svg)](https://github.com/marketplace/actions/arduino_ci)
[![Arduino-lint](https://github.com/RobTillaart/moduloMap/actions/workflows/arduino-lint.yml/badge.svg)](https://github.com/RobTillaart/moduloMap/actions/workflows/arduino-lint.yml)
[![JSON check](https://github.com/RobTillaart/moduloMap/actions/workflows/jsoncheck.yml/badge.svg)](https://github.com/RobTillaart/moduloMap/actions/workflows/jsoncheck.yml)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/RobTillaart/moduloMap/blob/master/LICENSE)
[![GitHub release](https://img.shields.io/github/release/RobTillaart/moduloMap.svg?maxAge=3600)](https://github.com/RobTillaart/moduloMap/releases)


# moduloMap

Arduino library for the moduloMap class.


## Description

The moduloMap is an experimental library that optimizes modular mapping.

How do I define modular mapping?

Imagine the mapping of all real numbers on a subset in a modular way.
Imagine the real number line rolled around a defined circle. 
After one rotation numbers start over again.

E.g. map all the real numbers to  \[7; 13>  that is module 6, 
with numbers 7..13 do not change as they are already in the range.
6 is mapped on 12, 5 on 11, 4 on 10, .. 1 on 7, 0 on 12 -1 on 11 etc.

Other name might be circular mapping, although it might be any shape.
(for now circles is complex enough)

### Applications 

- modular mapping of rotations to angles.
This can be on 0-360 degrees or 0-2PI radians or -180-180 degrees
or even -90..270 degrees.
- hoist math
Imagine a hoist, that needs to roll up / roll off a long rope around a cylinder.
- wire cutter
Determine the length of a wire for a wire cutter by moving it between two
wheels with known circumference.
- math fun


## Interface

- **moduloMap()** constructor.
- **bool begin(float minimum, float maximum)** define the range the numbers should be mapped to.
Returns true if minimum < maximum, false otherwise.
- **float map(float value)** actual mapping of a value to a number within the range.
- **float rotations(float value)** how many ranges (maximum - minimum) fit in a given length.
Think of it as how many rotations must a hoist must make to free a rope of given length.
Or how many rotations a hoist has to make to roll up a rope of given length.
This includes the minimum that already has rolled off / should stay rolled off.

Get internal parameters (debug)
- **float getMinimum()** idem.
- **float getMaximum()** idem.
- **float getRange()** idem.


## Performance

Tested with moduloMap_performance.ino on AVR.

|  version  |  1000 x map  |
|:---------:|:------------:|
|  0.1.0    |  44120 us    |
|  0.1.1    |  36340 us    |


## Operation

The examples show the basic working of the functions.


## Future
- elaborate documentation
- optimize performance
- add examples
- move code to .cpp file
- are there other than circular modulos
  - triangular, fractal?
- add link to related libraries
  - angles + fastmap?
- add **begin(float radius)**
  - assumes circle from 0..max