# total-serialism

`total-serialism` is a set of methods for the generation and transformation of number sequences mainly designed for algorithmic composition of music.

!!! Work-In-Progress !!!

# Install

```
$ npm install total-serialism
```

# Usage

The entire library

```js
const Serialism = require('total-serialism');
```
Or an individual section

```js
const Gen  = require('total-serialism').Generativ;
const Algo = require('total-serialism').Algorithmic;
const Mod  = require('total-serialism').Transform;
const Rand = require('total-serialism').Stochastic;
const Util = require('total-serialism').Utility;
```

# Examples

Generative Methods

```js
const Gen = require('total-serialism').Generative;

// generate an array of 7 ints between range 0-7
Gen.spread(7); //=> [0, 1, 2, 3, 4, 5, 6]

// generate an array of 5 ints between range 7-19
Gen.spread(5, 7, 19); //=> [7, 9, 11, 14, 16]

// generate an array of 9 floats between -1 - 1 (inclusive)
Gen.spreadInclusiveFloat(9, -1, 1); //=> [-1, -0.75, -0.5, -0.25, 0, 0.25, 0.5, 0.75, 1]

// fill an array with duplicates of a value
Gen.fill(10, 2, 15, 3, 20, 4); //=> [10, 10, 15, 15, 15, 20, 20, 20, 20]
```

Stochastic Methods
```js
const Rand = require('total-serialism').Stochastic;

// set the random number generator seed
Rand.seed(19374);

// generate an array of random floats in range -1 to 1
Rand.randomFloat(3, -1, 1); //=>  [0.6291111850577886, 0.15153786227276944, 0.32814801081039646]

// generate an array of random integers in range
Rand.random(5, 0, 12); //=>  [3, 3, 7, 1, 0]

// generate an array of coin tosses
Rand.coin(10); //=> [0, 1, 0, 1, 0, 1, 0, 0, 1, 0]

// generate an array of dice rolls
Rand.dice(4); //=>  [4, 4, 2, 3] 
```

Transformative Methods

```js
const Trs = require('total-serialism').Transform;

// duplicate an array with an offset added to every value
Trs.clone([0, 5, 7], 0, 12, -12); //=>  [0, 5, 7, 12, 17, 19, -12, -7, -5] 

// combine multiple numbers/arrays into one
Trs.combine([0, 5], 12, [7, 3]); //=>  [0, 5, 12, 7, 3] 

// duplicate an array certain amount of times
Trs.duplicate([0, 5, 7], 3); //=> [0, 5, 7, 0, 5, 7, 0, 5, 7]

// invert an array around a center point
Trs.invert([0, 2, 5, 10, 13], 5); //=>  [10, 8, 5, 0, -3]

// interleave multiple arrays into one
Trs.lace([0, 5, 9], [3, 3], [7, 12, 11, -1]); //=>  [0, 3, 7, 5, 3, 12, 9, 11, -1]

// merge arrays into a 2D-array
Trs.merge([0, 3, 7], [3, 12], [12, -1, 19, 5]); //=>  [[0, 3, 12], [3, 12, -1], [7, 19], [5]]

// generate a palindrome of an array
Trs.palindrome([0, 3, 5, 7]); //=> [0, 3, 5, 7, 7, 5, 3, 0]

// rotate an array in positive or negative direction
Trs.rotate([0, 5, 7, 12], -1); //=>  [5, 7, 12, 0] 

// reverse an array
Trs.reverse([0, 5, 7, 12]); //=>  [12, 7, 5, 0]

// shuffle the items in an array (Fisher-Yates shuffle algorithm)
Trs.shuffle([0, 5, 7, 12]); //=>  [7, 5, 0, 12] 

// remove duplicates from an array, leave order of appearance intact
Trs.unique([5, 7, 5, 0, 12, 7, 5]); //=>  [5, 7, 0, 12] 

```

# License

The MIT License
