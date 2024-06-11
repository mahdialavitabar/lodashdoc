# Lodash

Lodash is a JavaScript utility library that provides a plethora of functions to simplify and enhance the development process. It follows certain rules and principles:

Immutability: Lodash methods do not mutate the data they receive.

Pure Functions: Lodash provides utility functions that do not have side effects. Given the same input, they will always produce the same output.

Higher-Order Functions: Lodash provides functions like _.map, _.filter, and _.reduce that take a function as an argument and/or return a function.

Method Chaining: Lodash supports method chaining, allowing you to perform a sequence of operations on a collection in a more concise and readable way.

Memoization: Lodash provides memoization to cache the results of expensive function calls and return the cached result when the same inputs occur again.

However, there are also some potential weaknesses to using Lodash:

Code Size: Using Lodash can increase the size of your codebase, which may impact load times and performance.

Performance Overhead: Some Lodash functions may have performance overhead compared to native JavaScript methods.

Learning Curve: While Lodash provides a lot of utility, it also has a lot of functions to learn.

Potential for Overuse: Because Lodash provides so many utility functions, there’s a risk of overusing it when native JavaScript would suffice.

Increased Dependencies: Adding Lodash as a dependency increases the number of third-party dependencies your project has, which could increase the risk of vulnerabilities.

Strengths of Lodash include:

Simplicity: Lodash simplifies common programming tasks and boosts productivity.

Consistency: Lodash offers a consistent and functional programming style, making code more readable and maintainable.

Utility: Lodash provides a rich set of functions that streamline working with arrays, objects, and other data types.

Extensibility: Lodash is extensible and works well with other libraries.

Reliability: Lodash is well-maintained and has a large community, making it a reliable choice for projects.


## Categories

### Array
Array methods in Lodash are used for manipulating and working with arrays. They include functions like `_.chunk`, `_.compact`, `_.concat`, and many more.

### _.chunk(array, [size=1])
Creates an array of elements split into groups the length of `size`. If `array` can't be split evenly, the final chunk will be the remaining elements.
```javascript
_.chunk(['a', 'b', 'c', 'd'], 2); // => [['a', 'b'], ['c', 'd']]
```

### _.compact(array)
Creates an array with all falsey values removed. The values false, null, 0, "", undefined, and NaN are falsey.

```javascript
_.compact([0, 1, false, 2, '', 3]); // => [1, 2, 3]
```
### _.concat(array, [values])
Creates a new array concatenating array with any additional arrays and/or values.
```javascript
var array = [1];
var other = _.concat(array, 2, [3], [[4]]);
console.log(other); // => [1, 2, 3, [4]]
```

### _.difference(array, [values])
Creates an array of array values not included in the other given arrays using SameValueZero for equality comparisons. The order and references of result values are determined by the first array.

```javascript
_.difference([2, 1], [2, 3]); // => [1]
```
### _.differenceBy(array, [values], [iteratee=.identity])
This method is like _.difference except that it accepts iteratee which is invoked for each element of array and values to generate the criterion by which they’re compared. The order and references of result values are determined by the first array. The iteratee is invoked with one argument: (value).

```javascript
_.differenceBy([2.1, 1.2], [2.3, 3.4], Math.floor); // => [1.2]
```

### _.differenceWith(array, [values], [comparator])
This method is like _.difference except that it accepts comparator which is invoked to compare elements of array to values. The order and references of result values are determined by the first array. The comparator is invoked with two arguments: (arrVal, othVal).

```javascript
var objects = [{'x': 1, 'y': 2}, {'x': 2, 'y': 1}];
_.differenceWith(objects, [{'x': 1, 'y': 2}], _.isEqual); // => [{'x': 2, 'y': 1}]
```

### _.drop(array, [n=1])
Creates a slice of array with n elements dropped from the beginning.

```javascript
_.drop([1, 2, 3]); // => [2, 3]
```

### _.dropRight(array, [n=1])
Creates a slice of array with n elements dropped from the end.

```javascript
_.dropRight([1, 2, 3]); // => [1, 2]
```
### _.dropRightWhile(array, [predicate=.identity])
Creates a slice of array excluding elements dropped from the end. Elements are dropped until predicate returns falsey. The predicate is invoked with three arguments: (value, index, array).

```javascript
var users = [{'user': 'barney', 'active': true}, {'user': 'fred', 'active': false}, {'user': 'pebbles', 'active': false}];

_.dropRightWhile(users, function(o) { return !o.active; }); // => [{'user': 'barney', 'active': true}]
``` 
### _.dropWhile(array, [predicate=.identity])
Creates a slice of array excluding elements dropped from the beginning. Elements are dropped until predicate returns falsey. The predicate is invoked with three arguments: (value, index, array).

```javascript
var users = [{'user': 'barney', 'active': false}, {'user': 'fred', 'active': false}, {'user': 'pebbles', 'active': true}];
_.dropWhile(users, function(o) { return !o.active; }); // => [{'user': 'pebbles', 'active': true}, {'user': 'fred', 'active': false}]
```
### _.fill(array, value, [start=0], [end=array.length])
Fills elements of array with value from start up to, but not including, end.

```javascript
var array = [1, 2, 3];
_.fill(array, 'a'); // => ['a', 'a', 'a']
```

### _.findIndex(array, [predicate=.identity], [fromIndex=0])
This method is like _.find except that it returns the index of the first element predicate returns truthy for instead of the element itself.

```javascript
var users = [{'user': 'barney', 'active': false}, {'user': 'fred', 'active': false}, {'user': 'pebbles', 'active': true}];
_.findIndex(users, function(o) { return o.user == 'barney'; }); // => 0
```
### _.findLastIndex(array, [predicate=.identity], [fromIndex=array.length-1])
This method is like _.findIndex except that it iterates over elements of collection from right to left.

```javascript
var users = [{'user': 'barney', 'active': true}, {'user': 'fred', 'active': false}, {'user': 'pebbles', 'active': false}];
_.findLastIndex(users, function(o) { return o.user == 'pebbles'; }); // => 2
```

### _.first(array) -> _.head(array)
Gets the first element of array.

```javascript
_.first([1, 2, 3]); // => 1
_.head([1, 2, 3]); // => 1
```

### _.flatten(array)
Flattens `array` a single level deep.
```javascript
_.flatten([1, [2, [3, [4]], 5]]);
// => [1, 2, [3, [4]], 5]
```

### _.flattenDeep(array)
Recursively flattens `array`.
```javascript
_.flattenDeep([1, [2, [3, [4]], 5]]);
// => [1, 2, 3, 4, 5]
```

### _.flattenDepth(array, [depth=1])
Recursively flatten `array` up to `depth` times.
```javascript
var array = [1, [2, [3, [4]], 5]];
_.flattenDepth(array, 2);
// => [1, 2, 3, [4], 5]
```

### _.fromPairs(pairs)
The opposite of `_.toPairs`; this method returns an object composed from key-value `pairs`.
```javascript
_.fromPairs([['a', 1], ['b', 2]]);
// => { 'a': 1, 'b': 2 }
```

### _.head(array)
Gets the first element of `array`.
```javascript
_.head([1, 2, 3]);
// => 1
```

### _.indexOf(array, value, [fromIndex=0])
Gets the index at which the first occurrence of `value` is found in `array` using [`SameValueZero`](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) for equality comparisons. If `fromIndex` is negative, it's used as the offset from the end of `array`.
```javascript
_.indexOf([1, 2, 1, 2], 2);
// => 1
```

### _.initial(array)
Gets all but the last element of `array`.
```javascript
_.initial([1, 2, 3]);
// => [1, 2]
```

### _.intersection([arrays])
Creates an array of unique values that are included in all given arrays using [`SameValueZero`](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) for equality comparisons. The order and references of result values are determined by the first array.
```javascript
_.intersection([2, 1], [2, 3]);
// => [2]
```

### _.intersectionBy([arrays], [iteratee=_.identity])
This method is like `_.intersection` except that it accepts `iteratee` which is invoked for each element of each `arrays` to generate the criterion by which they're compared. The order and references of result values are determined by the first array. The iteratee is invoked with one argument: (value).
```javascript
_.intersectionBy([2.1, 1.2], [2.3, 3.4], Math.floor);
// => [2.1]
```

### _.intersectionWith([arrays], [comparator])
This method is like `_.intersection` except that it accepts `comparator` which is invoked to compare elements of `arrays`. The order and references of result values are determined by the first array. The comparator is invoked with two arguments: (arrVal, othVal).
```javascript
var objects = [{'x': 1, 'y': 2}, {'x': 2, 'y': 1}];
_.intersectionWith(objects, [{'x': 1, 'y': 2}], _.isEqual);
// => [{'x': 1, 'y': 2}]
```

### _.join(array, [separator=','])
Converts all elements in `array` into a string separated by `separator`.
```javascript
_.join(['a', 'b', 'c'], '~');
// => 'a~b~c'
```

### _.last(array)
Gets the last element of `array`.
```javascript
_.last([1, 2, 3]);
// => 3
```

### _.lastIndexOf(array, value, [fromIndex=array.length-1])
This method is like `_.indexOf` except that it iterates over elements of `array` from right to left.
```javascript
_.lastIndexOf([1, 2, 1, 2], 2);
// => 3
```

### _.nth(array, [n=0])
Gets the element at index `n` of `array`. If `n` is negative, the nth element from the end is returned.
```javascript
var array = ['a', 'b', 'c', 'd'];
_.nth(array, 1);
// => 'b'
_.nth(array, -2);
// => 'c'
```

### _.pull(array, [values])
Removes all given values from `array` using [`SameValueZero`](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) for equality comparisons.
```javascript
var array = ['a', 'b', 'c', 'a', 'b', 'c'];
_.pull(array, 'a', 'c');
// => ['b', 'b']
```

### _.pullAll(array, values)
This method is like `_.pull` except that it accepts an array of values to remove.
```javascript
var array = ['a', 'b', 'c', 'a', 'b', 'c'];
_.pullAll(array, ['a', 'c']);
// => ['b', 'b']
```

### _.pullAllBy(array, values, [iteratee=_.identity])
This method is like `_.pullAll` except that it accepts `iteratee` which is invoked for each element of `array` and `values` to generate the criterion by which they're compared. The iteratee is invoked with one argument: (value).
```javascript
var array = [{'x': 1}, {'x': 2}, {'x': 3}, {'x': 1}];
_.pullAllBy(array, [{'x': 1}, {'x': 3}], 'x');
// => [{'x': 2}]
```

### _.pullAllWith(array, values, [comparator])
This method is like `_.pullAll` except that it accepts `comparator` which is invoked to compare elements of `array` to `values`. The comparator is invoked with two arguments: (arrVal, othVal).
```javascript
var array = [{'x': 1, 'y': 2}, {'x': 3, 'y': 4}, {'x': 5, 'y': 6}];
_.pullAllWith(array, [{'x': 3, 'y': 4}], _.isEqual);
// => [{'x': 1, 'y': 2}, {'x': 5, 'y': 6}]
```

### _.pullAt(array, [indexes])
Removes elements from `array` corresponding to `indexes` and returns an array of removed elements.
```javascript
var array = ['a', 'b', 'c', 'd'];
var pulled = _.pullAt(array, [1, 3]);
// array => ['a', 'c']
// pulled => ['b', 'd']
```

### _.remove(array, [predicate=_.identity])
Removes all elements from `array` that `predicate` returns truthy for and returns an array of the removed elements. The predicate is invoked with three arguments: (value, index, array).
```javascript
var array = [1, 2, 3, 4];
var evens = _.remove(array, function(n) {
  return n % 2 == 0;
});
// array => [1, 3]
// evens => [2, 4]
```

### _.reverse(array)
Reverses `array` so that the first element becomes the last, the second element becomes the second to last, and so on.
```javascript
_.reverse([1, 2, 3]);
// => [3, 2, 1]
```

### _.slice(array, [start=0], [end=array.length])
Creates a slice of `array` from `start` up to, but not including, `end`.
```javascript
_.slice([1, 2, 3, 4, 5], 1, 4);
// => [2, 3, 4]
```

### _.sortedIndex(array, value)
Uses a binary search to determine the lowest index at which `value` should be inserted into `array` in order to maintain its sort order.
```javascript
_.sortedIndex([30, 50], 40);
// => 1
```

### _.sortedIndexBy(array, value, [iteratee=_.identity])
This method is like `_.sortedIndex` except that it accepts `iteratee` which is invoked for `value` and each element of `array` to compute their sort ranking. The iteratee is invoked with one argument: (value).
```javascript
var objects = [{'x': 4}, {'x': 5}];
_.sortedIndexBy(objects, {'x': 4}, function(o) { return o.x; });
// => 0
```

### _.sortedIndexOf(array, value, [fromIndex=0])
This method is like `_.indexOf` except that it performs a binary search on a sorted `array`.
```javascript
_.sortedIndexOf([4, 5, 5, 5, 6], 5);
// => 1
```

### _.sortedLastIndex(array, value)
This method is like `_.sortedIndex` except that it returns the highest index at which `value` should be inserted into `array` in order to maintain its sort order.
```javascript
_.sortedLastIndex([4, 5, 5, 5, 6], 5);
// => 4
```

### _.sortedLastIndexBy(array, value, [iteratee=_.identity])
This method is like `_.sortedLastIndex` except that it accepts `iteratee` which is invoked for `value` and each element of `array` to compute their sort ranking. The iteratee is invoked with one argument: (value).
```javascript
var objects = [{'x': 4}, {'x': 5}];
_.sortedLastIndexBy(objects, {'x': 4}, function(o) { return o.x; });
// => 1
```

### _.sortedLastIndexOf(array, value, [fromIndex=array.length-1])
This method is like `_.lastIndexOf` except that it performs a binary search on a sorted `array`.
```javascript
_.sortedLastIndexOf([4, 5, 5, 5, 6], 5);
// => 3
```

### _.sortedUniq(array)
This method is like `_.uniq` except that it's designed and optimized for sorted arrays.
```javascript
_.sortedUniq([1, 1, 2]);
// => [1, 2]
```

### _.sortedUniqBy(array, [iteratee])
This method is like `_.uniqBy` except that it's designed and optimized for sorted arrays.
```javascript
_.sortedUniqBy([1.1, 1.2, 2.3, 2.4], Math.floor);
// => [1.1, 2.3]
```

### _.tail(array)
Gets all but the first element of `array`.
```javascript
_.tail([1, 2, 3]);
// => [2, 3]
```

### _.take(array, [n=1])
Creates a slice of `array` with `n` elements taken from the beginning.
```javascript
_.take([1, 2, 3], 2);
// => [1, 2]
```

### _.takeRight(array, [n=1])
Creates a slice of `array` with `n` elements taken from the end.
```javascript
_.takeRight([1, 2, 3], 2);
// => [2, 3]
```

### _.takeRightWhile(array, [predicate=_.identity])
Creates a slice of `array` with elements taken from the end. Elements are taken until `predicate` returns falsey. The predicate is invoked with three arguments: (value, index, array).
```javascript
var users = [{'user': 'barney', 'active': true}, {'user': 'fred', 'active': false}, {'user': 'pebbles', 'active': false}];
_.takeRightWhile(users, function(o) { return !o.active; });
// => [{'user': 'fred', 'active': false}, {'user': 'pebbles', 'active': false}]
```

### _.takeWhile(array, [predicate=_.identity])
Creates a slice of `array` with elements taken from the beginning. Elements are taken until `predicate` returns falsey. The predicate is invoked with three arguments: (value, index, array).
```javascript
var users = [{'user': 'barney', 'active': false}, {'user': 'fred', 'active': false}, {'user': 'pebbles', 'active': true}];
_.takeWhile(users, function(o) { return !o.active; });
// => [{'user': 'barney', 'active': false}, {'user': 'fred', 'active': false}]
```

### _.union([arrays])
Creates an array of unique values, in order, from all given arrays using [`SameValueZero`](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) for equality comparisons.
```javascript
_.union([2], [1, 2]);
// => [2, 1]
```

### _.unionBy([arrays], [iteratee=_.identity])
This method is like `_.union` except that it accepts `iteratee` which is invoked for each element of each `arrays` to generate the criterion by which uniqueness is computed. The iteratee is invoked with one argument: (value).
```javascript
_.unionBy([2.1], [1.2, 2.3], Math.floor);
// => [2.1, 1.2]
```

### _.unionWith([arrays], [comparator])
This method is like `_.union` except that it accepts `comparator` which is invoked to compare elements of `arrays`. The comparator is invoked with two arguments: (arrVal, othVal).
```javascript
var objects = [{'x': 1, 'y': 2}, {'x': 2, 'y': 1}];
_.unionWith(objects, [{'x': 1, 'y': 1}], _.isEqual);
// => [{'x': 1, 'y': 2}, {'x': 2, 'y': 1}]
```

### _.uniq(array)
Creates a duplicate-free version of an array, in which only the first occurrence of each element is kept. The order of result values is determined by the order they occur in the array.
```javascript
_.uniq([2, 1, 2]);
// => [2, 1]
```

### _.uniqBy(array, [iteratee=_.identity])
This method is like `_.uniq` except that it accepts `iteratee` which is invoked for each element in `array` to generate the criterion by which uniqueness is computed. The order of result values is determined by the order they occur in the array. The iteratee is invoked with one argument: (value).
```javascript
_.uniqBy([2.1, 1.2, 2.3], Math.floor);
// => [2.1, 1.2]
```

### _.uniqWith(array, [comparator])
This method is like `_.uniq` except that it accepts `comparator` which is invoked to compare elements of `array`. The order of result values is determined by the order they occur in the array. The comparator is invoked with two arguments: (arrVal, othVal).
```javascript
var objects = [{'x': 1, 'y': 2}, {'x': 2, 'y': 1}, {'x': 1, 'y': 2}];
_.uniqWith(objects, _.isEqual);
// => [{'x': 1, 'y': 2}, {'x': 2, 'y': 1}]
```

### _.unzip(array)
This method is like `_.zip` except that it accepts an array of grouped elements and creates an array regrouping the elements to their pre-zip configuration.
```javascript
_.unzip([['a', 1, true], ['b', 2, false]]);
// => [['a', 'b'], [1, 2], [true, false]]
```

### _.unzipWith(array, [iteratee=_.identity])
This method is like `_.unzip` except that it accepts `iteratee` to specify how regrouped values should be combined. The iteratee is invoked with the elements of each group: (...group).
```javascript
var zipped = _.zip([1, 2], [10, 20], [100, 200]);
_.unzipWith(zipped, _.add);
// => [111, 222]
```

### _.without(array, [values])
Creates an array excluding all given values using [`SameValueZero`](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) for equality comparisons.
```javascript
_.without([2, 1, 2, 3], 1, 2);
// => [3]
```

### _.xor([arrays])
Creates an array of unique values that is the [symmetric difference](https://en.wikipedia.org/wiki/Symmetric_difference) of the given arrays. The order of result values is determined by the order they occur in the arrays.
```javascript
_.xor([2, 1], [2, 3]);
// => [1, 3]
```

### _.xorBy([arrays], [iteratee=_.identity])
This method is like `_.xor` except that it accepts `iteratee` which is invoked for each element of each `arrays` to generate the criterion by which by which they're compared. The order of result values is determined by the order they occur in the arrays. The iteratee is invoked with one argument: (value).
```javascript
_.xorBy([2.1, 1.2], [2.3, 3.4], Math.floor);
// => [1.2, 3.4]
```

### _.xorWith([arrays], [comparator])
This method is like `_.xor` except that it accepts `comparator` which is invoked to compare elements of `arrays`. The order of result values is determined by the order they occur in the arrays. The comparator is invoked with two arguments: (arrVal, othVal).
```javascript
var objects = [{'x': 1, 'y': 2}, {'x': 2, 'y': 1}];
_.xorWith(objects, [{'x': 1, 'y': 2}], _.isEqual);
// => [{'x': 2, 'y': 1}]
```

### _.zip([arrays])
Creates an array of grouped elements, the first of which contains the first elements of the input arrays, the second of which contains the second elements of the input arrays, and so on.
```javascript
_.zip(['a', 'b'], [1, 2], [true, false]);
// => [['a', 1, true], ['b', 2, false]]
```

### _.zipObject([props=[]], [values=[]])
This method is like `_.fromPairs` except that it accepts two arrays, one of property identifiers and one of corresponding values.
```javascript
_.zipObject(['a', 'b'], [1, 2]);
// => { 'a': 1, 'b': 2 }
```

### _.zipObjectDeep([props=[]], [values=[]])
This method is like `_.zipObject` except that it supports property paths.
```javascript
_.zipObjectDeep(['a.b[0].c', 'a.b[1].d'], [1, 2]);
// => { 'a': { 'b': [{ 'c': 1 }, { 'd': 2 }] } }
```

### _.zipWith([arrays], [iteratee=_.identity])
This method is like `_.zip` except that it accepts `iteratee` to specify how grouped values should be combined. The iteratee is invoked with the elements of each group: (...group).
```javascript
_.zipWith([1, 2], [10, 20], [100, 200], function(a, b, c) {
  return a + b + c;
});
// => [111, 222]
```

### Collection
Collection methods work on arrays, objects, and strings. They include functions like `_.countBy`, `_.each`, `_.every`, and others.

Sure, here are the descriptions and examples for the Lodash collection methods you mentioned:

### _.countBy(collection, [iteratee=_.identity])
Creates an object composed of keys generated from the results of running each element of `collection` through `iteratee`. The corresponding value of each key is the number of times the key was returned by `iteratee`.
```javascript
_.countBy([6.1, 4.2, 6.3], Math.floor);
// => { '4': 1, '6': 2 }
```

### _.each(collection, [iteratee=_.identity]) -> _.forEach(collection, [iteratee=_.identity])
Iterates over elements of `collection` and invokes `iteratee` for each element. The iteratee is invoked with three arguments: (value, index|key, collection).
```javascript
_.forEach([1, 2], function(value) {
  console.log(value);
});
// => Logs `1` then `2`.
```

### _.eachRight(collection, [iteratee=_.identity]) -> _.forEachRight(collection, [iteratee=_.identity])
This method is like `_.forEach` except that it iterates over elements of `collection` from right to left.
```javascript
_.forEachRight([1, 2], function(value) {
  console.log(value);
});
// => Logs `2` then `1`.
```

### _.every(collection, [predicate=_.identity])
Checks if `predicate` returns truthy for **all** elements of `collection`. Iteration is stopped once `predicate` returns falsey. The predicate is invoked with three arguments: (value, index|key, collection).
```javascript
_.every([true, 1, null, 'yes'], Boolean);
// => false
```

### _.filter(collection, [predicate=_.identity])
Iterates over elements of `collection`, returning an array of all elements `predicate` returns truthy for. The predicate is invoked with three arguments: (value, index|key, collection).
```javascript
var users = [
  { 'user': 'barney', 'age': 36, 'active': true },
  { 'user': 'fred',   'age': 40, 'active': false }
];
_.filter(users, function(o) { return !o.active; });
// => objects for ['fred']
```

### _.find(collection, [predicate=_.identity], [fromIndex=0])
Iterates over elements of `collection`, returning the first element `predicate` returns truthy for. The predicate is invoked with three arguments: (value, index|key, collection).
```javascript
var users = [
  { 'user': 'barney',  'age': 36, 'active': true },
  { 'user': 'fred',    'age': 40, 'active': false },
  { 'user': 'pebbles', 'age': 1,  'active': true }
];
_.find(users, function(o) { return o.age < 40; });
// => object for 'barney'
```

### _.findLast(collection, [predicate=_.identity], [fromIndex=collection.length-1])
This method is like `_.find` except that it iterates over elements of `collection` from right to left.
```javascript
_.findLast([1, 2, 3, 4], function(n) {
  return n % 2 == 1;
});
// => 3
```

### _.flatMap(collection, [iteratee=_.identity])
Creates a flattened array of values by running each element in `collection` through `iteratee` and flattening the mapped results. The iteratee is invoked with three arguments: (value, index|key, collection).
```javascript
function duplicate(n) {
  return [n, n];
}
_.flatMap([1, 2], duplicate);
// => [1, 1, 2, 2]
```

### _.flatMapDeep(collection, [iteratee=_.identity])
This method is like `_.flatMap` except that it recursively flattens the mapped results.
```javascript
function duplicate(n) {
  return [[[n, n]]];
}
_.flatMapDeep([1, 2], duplicate);
// => [1, 1, 2, 2]
```

### _.flatMapDepth(collection, [iteratee=_.identity], [depth=1])
This method is like `_.flatMap` except that it recursively flattens the mapped results up to `depth` times.
```javascript
var func = _.over(_.property('n'), _.property('m'));
_.flatMapDepth([1, 2], func, 1);
// => [1, 1, 2, 2]
```

### _.forEach(collection, [iteratee=_.identity])
Iterates over elements of `collection` and invokes `iteratee` for each element. The iteratee is invoked with three arguments: (value, index|key, collection).
```javascript
_.forEach([1, 2], function(value) {
  console.log(value);
});
// => Logs `1` then `2`.
```

### _.forEachRight(collection, [iteratee=_.identity])
This method is like `_.forEach` except that it iterates over elements of `collection` from right to left.
```javascript
_.forEachRight([1, 2], function(value) {
  console.log(value);
});
// => Logs `2` then `1`.
```

### _.groupBy(collection, [iteratee=_.identity])
Creates an object composed of keys generated from the results of running each element of `collection` through `iteratee`. The order of grouped values is determined by the order they occur in `collection`. The corresponding value of each key is an array of elements responsible for generating the key. The iteratee is invoked with one argument: (value).
```javascript
_.groupBy([6.1, 4.2, 6.3], Math.floor);
// => { '4': [4.2], '6': [6.1, 6.3] }
```

### _.includes(collection, value, [fromIndex=0])
Checks if `value` is in `collection`. If `collection` is a string, it's checked for a substring of `value`, otherwise [`SameValueZero`](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) is used for equality comparisons. If `fromIndex` is negative, it's used as the offset from the end of `collection`.
```javascript
_.includes([1, 2, 3], 1);
// => true
```

### _.invokeMap(collection, path, [args])
Invokes the method at `path` of each element in `collection`, returning an array of the results of each invoked method. Any additional arguments are provided to each invoked method. If `path` is a function, it's invoked for, and `this` bound to, each element in `collection`.
```javascript
_.invokeMap([[5, 1, 7], [3, 2, 1]], 'sort');
// => [[1, 5, 7], [1, 2, 3]]
```

### _.keyBy(collection, [iteratee=_.identity])
Creates an object composed of keys generated from the results of running each element of `collection` through `iteratee`. The corresponding value of each key is the last element responsible for generating the key. The iteratee is invoked with one argument: (value).
```javascript
var array = [
  { 'dir': 'left', 'code': 97 },
  { 'dir': 'right', 'code': 100 }
];
_.keyBy(array, function(o) {
  return String.fromCharCode(o.code);
});
// => { 'a': { 'dir': 'left', 'code': 97 }, 'd': { 'dir': 'right', 'code': 100 } }
```

### _.map(collection, [iteratee=_.identity])
Creates an array of values by running each element in `collection` through `iteratee`. The iteratee is invoked with three arguments: (value, index|key, collection).
```javascript
function square(n) {
  return n * n;
}
_.map([4, 8], square);
// => [16, 64]
```

### _.orderBy(collection, [iteratees=[_.identity]], [orders])
This method is like `_.sortBy` except that it allows specifying the sort orders of the `iteratees` to sort by. If `orders` is unspecified, all values are sorted in ascending order. Otherwise, specify an order of "desc" for descending or "asc" for ascending sort order of corresponding values.
```javascript
var users = [
  { 'user': 'fred',   'age': 48 },
  { 'user': 'barney', 'age': 36 },
  { 'user': 'fred',   'age': 40 },
  { 'user': 'barney', 'age': 34 }
];
_.orderBy(users, ['user', 'age'], ['asc', 'desc']);
// => [{'user': 'barney', 'age': 36}, {'user': 'barney', 'age': 34}, {'user': 'fred', 'age': 48}, {'user': 'fred', 'age': 40}]
```

### _.partition(collection, [predicate=_.identity])
Creates an array of elements split into two groups, the first of which contains elements `predicate` returns truthy for, the second of which contains elements `predicate` returns falsey for. The predicate is invoked with one argument: (value).
```javascript
var users = [
  { 'user': 'barney',  'age': 36, 'active': false },
  { 'user': 'fred',    'age': 40, 'active': true }
];
_.partition(users, function(o) { return o.active; });
// => [[{'user': 'fred', 'age': 40, 'active': true}], [{'user': 'barney', 'age': 36, 'active': false}]]
```

### _.reduce(collection, [iteratee=_.identity], [accumulator])
Reduces `collection` to a value which is the accumulated result of running each element in `collection` through `iteratee`, where each successive invocation is supplied the return value of the previous. If `accumulator` is not given, the first element of `collection` is used as the initial value. The iteratee is invoked with four arguments: (accumulator, value, index|key, collection).
```javascript
_.reduce([1, 2], function(sum, n) {
  return sum + n;
}, 0);
// => 3
```

### _.reduceRight(collection, [iteratee=_.identity], [accumulator])
This method is like `_.reduce` except that it iterates over elements of `collection` from right to left.
```javascript
var array = [[0, 1], [2, 3], [4, 5]];
_.reduceRight(array, function(flattened, other) {
  return flattened.concat(other);
}, []);
// => [4, 5, 2, 3, 0, 1]
```

### _.reject(collection, [predicate=_.identity])
The opposite of `_.filter`; this method returns the elements of `collection` that `predicate` does **not** return truthy for.
```javascript
var users = [
  { 'user': 'barney', 'age': 36, 'active': false },
  { 'user': 'fred',   'age': 40, 'active': true }
];
_.reject(users, function(o) { return !o.active; });
// => [{'user': 'fred', 'age': 40, 'active': true}]
```

### _.sample(collection)
Gets a random element from `collection`.
```javascript
_.sample([1, 2, 3, 4]);
// => 2
```

### _.sampleSize(collection, [n=1])
Gets `n` random elements at unique keys from `collection` up to the size of `collection`.
```javascript
_.sampleSize([1, 2, 3], 2);
// => [3, 1]
```

### _.shuffle(collection)
Creates a shuffled copy of the given array, using a version of the [Fisher-Yates shuffle](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle).
```javascript
_.shuffle([1, 2, 3, 4]);
// => [4, 1, 3, 2]
```

### _.size(collection)
Gets the size of `collection` by returning its length for array-like values or the number of own enumerable string keyed properties for objects.
```javascript
_.size([1, 2, 3]);
// => 3
```

### _.some(collection, [predicate=_.identity])
Checks if `predicate` returns truthy for **any** element of `collection`. Iteration is stopped once `predicate` returns truthy. The predicate is invoked with three arguments: (value, index|key, collection).
```javascript
_.some([null, 0, 'yes', false], Boolean);
// => true
```

### _.sortBy(collection, [iteratees=[_.identity]])
Creates an array of elements, sorted in ascending order by the results of running each element in a collection through each iteratee. This method performs a stable sort, that is, it preserves the original sort order of equal elements. The iteratees are invoked with one argument: (value).
```javascript
var users = [
  { 'user': 'fred',   'age': 48 },
  { 'user': 'barney', 'age': 36 },
  { 'user': 'fred',   'age': 40 },
  { 'user': 'barney', 'age': 34 }
];
_.sortBy(users, ['user', 'age']);
// => [{'user': 'barney', 'age': 34}, {'user': 'barney', 'age': 36}, {'user': 'fred', 'age': 40}, {'user': 'fred', 'age': 48}]
```

### Date
Lodash's Date category includes the `_.now` function which gets the timestamp of the host machine.

### _.now()
Gets the timestamp of the number of milliseconds that have elapsed since the Unix epoch (1 January 1970 00:00:00 UTC).
```javascript
_.defer(function(stamp) {
	console.log(_.now() - stamp);
}, _.now());
// => Logs the number of milliseconds it took for the deferred invocation.
```

### Function
Function methods in Lodash are used to create more complex behaviors of functions. They include functions like `_.after`, `_.ary`, `_.before`, and others[^4^][4].

### _.after(n, func)
Creates a function that invokes `func` after being called `n` times.
```javascript
var saves = ['profile', 'settings'];
var done = _.after(saves.length, function() {
  console.log('done saving!');
});
_.forEach(saves, function(type) {
  asyncSave({ 'type': type, 'complete': done });
});
// => Logs 'done saving!' after the two async saves have completed.
```

### _.ary(func, [n=func.length])
Creates a function that invokes `func`, with up to `n` arguments, ignoring any additional arguments.
```javascript
_.map(['6', '8', '10'], _.ary(parseInt, 1));
// => [6, 8, 10]
```

### _.before(n, func)
Creates a function that invokes `func`, with the `this` binding and arguments of the created function, while it's called less than `n` times. Subsequent calls to the created function return the result of the last `func` invocation.
```javascript
jQuery(element).on('click', _.before(5, addContactToList));
// => Allows adding up to 4 contacts to the list.
```

### _.bind(func, thisArg, [partials])
Creates a function that invokes `func` with the `this` binding of `thisArg` and `partials` prepended to the arguments it receives.
```javascript
function greet(greeting, punctuation) {
  return greeting + ' ' + this.user + punctuation;
}
var object = { 'user': 'fred' };
var bound = _.bind(greet, object, 'hi');
bound('!');
// => 'hi fred!'
```

### _.bindKey(object, key, [partials])
Creates a function that invokes the method at `object[key]` with `partials` prepended to the arguments it receives.
```javascript
var object = {
  'user': 'fred',
  'greet': function(greeting, punctuation) {
    return greeting + ' ' + this.user + punctuation;
  }
};
var bound = _.bindKey(object, 'greet', 'hi');
bound('!');
// => 'hi fred!'
```

### _.curry(func, [arity=func.length])
Creates a function that accepts arguments of `func` and either invokes `func` returning its result, if at least `arity` number of arguments have been provided, or returns a function that accepts the remaining `func` arguments, and so on.
```javascript
var abc = function(a, b, c) {
  return [a, b, c];
};
var curried = _.curry(abc);
curried(1)(2)(3);
// => [1, 2, 3]
```

### _.curryRight(func, [arity=func.length])
This method is like `_.curry` except that arguments are applied to `func` in the manner of `_.partialRight` instead of `_.partial`.
```javascript
var abc = function(a, b, c) {
  return [a, b, c];
};
var curried = _.curryRight(abc);
curried(3)(2)(1);
// => [1, 2, 3]
```

### _.debounce(func, [wait=0], [options={leading: false, maxWait: wait, trailing: true}])
Creates a debounced function that delays invoking `func` until after `wait` milliseconds have elapsed since the last time the debounced function was invoked.
```javascript
// Avoid costly calculations while the window size is in flux.
jQuery(window).on('resize', _.debounce(calculateLayout, 150));
```

### _.defer(func, [args])
Defers invoking the `func` until the current call stack has cleared. Any additional arguments are provided to `func` when it's invoked.
```javascript
_.defer(function(text) {
  console.log(text);
}, 'deferred');
// Logs 'deferred' after one millisecond.
```

### _.delay(func, wait, [args])
Invokes `func` after `wait` milliseconds. Any additional arguments are provided to `func` when it's invoked.
```javascript
_.delay(function(text) {
  console.log(text);
}, 1000, 'later');
// Logs 'later' after one second.
```

### _.flip(func)
Creates a function that invokes `func` with arguments reversed.
```javascript
var flipped = _.flip(function() {
  return _.toArray(arguments);
});
flipped('a', 'b', 'c', 'd');
// => ['d', 'c', 'b', 'a']
```

### _.memoize(func, [resolver])
Creates a function that memoizes the result of `func`. If `resolver` is provided, it determines the cache key for storing the result based on the arguments provided to the memoized function. By default, the first argument provided to the memoized function is used as the map cache key.
```javascript
var object = { 'a': 1, 'b': 2 };
var other = { 'c': 3, 'd': 4 };
var values = _.memoize(_.values);
values(object);
// => [1, 2]
values(other);
// => [3, 4]
```

### _.negate(predicate)
Creates a function that negates the result of the predicate `func`.
```javascript
function isEven(n) {
  return n % 2 == 0;
}
_.filter([1, 2, 3, 4, 5, 6], _.negate(isEven));
// => [1, 3, 5]
```

### _.once(func)
Creates a function that is restricted to invoking `func` once. Repeat calls to the function return the value of the first invocation.
```javascript
var initialize = _.once(createApplication);
initialize();
initialize();
// `createApplication` is invoked once
```

### _.overArgs(func, [transforms=[_.identity]])
Creates a function that invokes `func` with its arguments transformed.
```javascript
function doubled(n) {
  return n * 2;
}
function square(n) {
  return n * n;
}
var func = _.overArgs(function(x, y) {
  return [x, y];
}, [square, doubled]);
func(9, 3);
// => [81, 6]
```

### _.partial(func, [partials])
Creates a function that invokes `func` with `partials` prepended to the arguments it receives. This method is like `_.bind` except it does not alter the `this` binding.
```javascript
function greet(greeting, name) {
  return greeting + ' ' + name;
}
var sayHelloTo = _.partial(greet, 'hello');
sayHelloTo('fred');
// => 'hello fred'
```

### _.partialRight(func, [partials])
This method is like `_.partial` except that partially applied arguments are appended to the arguments it receives.
```javascript
function greet(greeting, name) {
  return greeting + ' ' + name;
}
var greetFred = _.partialRight(greet, 'fred');
greetFred('hi');
// => 'hi fred'
```

### _.rearg(func, indexes)
Creates a function that invokes `func` with arguments arranged according to the specified `indexes` where the argument value at the first index is provided as the first argument, the argument value at the second index is provided as the second argument, and so on.
```javascript
var rearged = _.rearg(function(a, b, c) {
  return [a, b, c];
}, [2, 0, 1]);
rearged('b', 'c', 'a')
// => ['a', 'b', 'c']
```

### _.rest(func, [start=func.length-1])
Creates a function that invokes `func` with the `this` binding of the created function and arguments from `start` and beyond provided as an array.
```javascript
var say = _.rest(function(what, names) {
  return what + ' ' + _.initial(names).join(', ') +
    (_.size(names) > 1 ? ', & ' : '') + _.last(names);
});
say('hello', 'fred', 'barney', 'pebbles');
// => 'hello fred, barney, & pebbles'
```

### _.spread(func, [start=0])
Creates a function that invokes `func` with the `this` binding of the create function and an array of arguments much like [`Function#apply`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply).
```javascript
var say = _.spread(function(who, what) {
  return who + ' says ' + what;
});
say(['fred', 'hello']);
// => 'fred says hello'
```

### _.throttle(func, [wait=0], [options={leading: true, trailing: true}])
Creates a throttled function that only invokes `func` at most once per every `wait` milliseconds. You may want to throttle a function to control its rate of execution.
```javascript
// Avoid excessively updating the position while scrolling.
var throttled = _.throttle(updatePosition, 100);
jQuery(window).on('scroll', throttled);
```

### _.unary(func)
Creates a function that accepts up to one argument, ignoring any additional arguments.
```javascript
_.map(['6', '8', '10'], _.unary(parseInt));
// => [6, 8, 10]
```

### _.wrap(value, [wrapper=identity])
Creates a function that provides `value` to the wrapper function as its first argument. Any additional arguments provided to the function are appended to those provided to the wrapper function. The wrapper is invoked with one argument: (value).
```javascript
var p = _.wrap(_.escape, function(func, text) {
  return '<p>' + func(text) + '</p>';
});
p('fred, barney, & pebbles');
// => '<p>fred, barney, &amp; pebbles</p>'
```

### Lang
Lang methods include various helpers for working with JavaScript types and data structures, like `_.isNaN`, `_.isNil`, `_.isNull`, and more[^5^][5].

### _.castArray(value)
Casts `value` as an array if it's not one.
```javascript
_.castArray(1);
// => [1]
```

### _.clone(value)
Creates a shallow clone of `value`.
```javascript
var objects = [{ 'a': 1 }, { 'b': 2 }];
var shallow = _.clone(objects);
console.log(shallow[0] === objects[0]);
// => true
```

### _.cloneDeep(value)
This method is like `_.clone` except that it recursively clones `value`.
```javascript
var objects = [{ 'a': 1 }, { 'b': 2 }];
var deep = _.cloneDeep(objects);
console.log(deep[0] === objects[0]);
// => false
```

### _.cloneDeepWith(value, [customizer])
This method is like `_.cloneWith` except that it recursively clones `value`.
```javascript
function customizer(value) {
  if (_.isElement(value)) {
    return value.cloneNode(true);
  }
}
var el = _.cloneDeepWith(document.body, customizer);
console.log(el === document.body);
// => false
console.log(el.nodeName);
// => 'BODY'
console.log(el.childNodes.length);
// => 20
```

### _.cloneWith(value, [customizer])
This method is like `_.clone` except that it accepts `customizer` which is invoked to produce the cloned value. If `customizer` returns `undefined`, cloning is handled by the method instead. The `customizer` is invoked with up to four arguments: (value [, index|key, object, stack]).
```javascript
function customizer(value) {
  if (_.isElement(value)) {
    return value.cloneNode(false);
  }
}
var el = _.cloneWith(document.body, customizer);
console.log(el === document.body);
// => false
console.log(el.nodeName);
// => 'BODY'
console.log(el.childNodes.length);
// => 0
```

### _.conformsTo(object, source)
Checks if `object` conforms to `source` by invoking the predicate properties of `source` with the corresponding property values of `object`.
```javascript
var object = {'a': 1, 'b': 2};
_.conformsTo(object, {'b': function(n) { return n > 1; }});
// => true
```

### _.eq(value, other)
Performs a [`SameValueZero`](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) comparison between two values to determine if they are equivalent.
```javascript
var object = {'a': 1};
var other = {'a': 1};
_.eq(object, object);
// => true
_.eq(object, other);
// => false
```

### _.gt(value, other)
Checks if `value` is greater than `other`.
```javascript
_.gt(3, 1);
// => true
_.gt(3, 3);
// => false
_.gt(1, 3);
// => false
```

### _.gte(value, other)
Checks if `value` is greater than or equal to `other`.
```javascript
_.gte(3, 1);
// => true
_.gte(3, 3);
// => true
_.gte(1, 3);
// => false
```

### _.isArguments(value)
Checks if `value` is likely an `arguments` object.
```javascript
_.isArguments(function() { return arguments; }());
// => true
_.isArguments([1, 2, 3]);
// => false
```

### _.isArray(value)
Checks if `value` is classified as an `Array` object.
```javascript
_.isArray([1, 2, 3]);
// => true
_.isArray(document.body.children);
// => false
_.isArray('abc');
// => false
_.isArray(_.noop);
// => false
```

### _.isArrayBuffer(value)
Checks if `value` is classified as an `ArrayBuffer` object.
```javascript
var typed = new Int8Array(new ArrayBuffer(8));
_.isArrayBuffer(typed.buffer);
// => true
```

### _.isArrayLike(value)
Checks if `value` is array-like. A value is considered array-like if it's not a function and has a `value.length` that's an integer greater than or equal to `0` and less than or equal to `Number.MAX_SAFE_INTEGER`.
```javascript
_.isArrayLike([1, 2, 3]);
// => true
_.isArrayLike(document.body.children);
// => true
_.isArrayLike('abc');
// => true
_.isArrayLike(_.noop);
// => false
```

### _.isArrayLikeObject(value)
This method is like `_.isArrayLike` except that it also checks if `value` is an object.
```javascript
_.isArrayLikeObject([1, 2, 3]);
// => true
_.isArrayLikeObject(document.body.children);
// => true
_.isArrayLikeObject('abc');
// => false
_.isArrayLikeObject(_.noop);
// => false
```

### _.isBoolean(value)
Checks if `value` is classified as a boolean primitive or object.
```javascript
_.isBoolean(false);
// => true
_.isBoolean(null);
// => false
```

### _.isBuffer(value)
Checks if `value` is a buffer.
```javascript
_.isBuffer(new Buffer(2));
// => true
_.isBuffer(new Uint8Array(2));
// => false
```

### _.isDate(value)
Checks if `value` is classified as a `Date` object.
```javascript
_.isDate(new Date);
// => true
_.isDate('Mon April 23 2012');
// => false
```

### _.isElement(value)
Checks if `value` is likely a DOM element.
```javascript
_.isElement(document.body);
// => true
_.isElement('<body>');
// => false
```

### _.isEmpty(value)
Checks if `value` is an empty object, collection, map, or set. Objects are considered empty if they have no own enumerable string keyed properties.
```javascript
_.isEmpty(null);
// => true
_.isEmpty(true);
// => true
_.isEmpty(1);
// => true
_.isEmpty([1, 2, 3]);
// => false
_.isEmpty({ 'a': 1 });
// => false
```

### _.isEqual(value, other)
Performs a deep comparison between two values to determine if they are equivalent.
```javascript
var object = {'a': 1};
var other = {'a': 1};
_.isEqual(object, other);
// => true
```

### _.isEqualWith(value, other, [customizer])
This method is like `_.isEqual` except that it accepts `customizer` which is invoked to compare values. If `customizer` returns `undefined`, comparisons are handled by the method instead. The `customizer` is invoked with up to six arguments: (objValue, othValue [, index|key, object, other, stack]).
```javascript
function isGreeting(value) {
  return /^h(?:i|ello)$/.test(value);
}
function customizer(objValue, othValue) {
  if (isGreeting(objValue) && isGreeting(othValue)) {
    return true;
  }
}
var array = ['hello', 'goodbye'];
var other = ['hi', 'goodbye'];
_.isEqualWith(array, other, customizer);
// => true
```

### _.isError(value)
Checks if `value` is an `Error`, `EvalError`, `RangeError`, `ReferenceError`, `SyntaxError`, `TypeError`, or `URIError` object.
```javascript
_.isError(new Error);
// => true
_.isError(Error);
// => false
```

### _.isFinite(value)
Checks if `value` is a finite primitive number.
```javascript
_.isFinite(3);
// => true
_.isFinite(Number.MIN_VALUE);
// => true
_.isFinite(Infinity);
// => false
_.isFinite('3');
// => false
```

### _.isFunction(value)
Checks if `value` is classified as a `Function` object.
```javascript
_.isFunction(_);
// => true
_.isFunction(/abc/);
// => false
```

### _.isInteger(value)
Checks if `value` is an integer.
```javascript
_.isInteger(3);
// => true
_.isInteger(Number.MIN_VALUE);
// => false
_.isInteger(Infinity);
// => false
_.isInteger('3');
// => false
```

### _.isLength(value)
Checks if `value` is a valid array-like length.
```javascript
_.isLength(3);
// => true
_.isLength(Number.MIN_VALUE);
// => false
_.isLength(Infinity);
// => false
_.isLength('3');
// => false
```

### _.isMap(value)
Checks if `value` is classified as a `Map` object.
```javascript
_.isMap(new Map);
// => true
_.isMap(new WeakMap);
// => false
```

### _.isMatch(object, source)
Performs a partial deep comparison between `object` and `source` to determine if `object` contains equivalent property values.
```javascript
var object = {'a': 1, 'b': 2};
_.isMatch(object, {'b': 2});
// => true
```

### _.isMatchWith(object, source, [customizer])
This method is like `_.isMatch` except that it accepts `customizer` which is invoked to compare values. If `customizer` returns `undefined`, comparisons are handled by the method instead. The `customizer` is invoked with five arguments: (objValue, srcValue, index|key, object, source).
```javascript
function isGreeting(value) {
  return /^h(?:i|ello)$/.test(value);
}
function customizer(objValue, srcValue) {
  if (isGreeting(objValue) && isGreeting(srcValue)) {
    return true;
  }
}
var object = {'greeting': 'hello'};
var source = {'greeting': 'hi'};
_.isMatchWith(object, source, customizer);
// => true
```

### _.isNaN(value)
Checks if `value` is `NaN`.
```javascript
_.isNaN(NaN);
// => true
_.isNaN(new Number(NaN));
// => true
isNaN(undefined);
// => true
_.isNaN(undefined);
// => false
```

### _.isNative(value)
Checks if `value` is a pristine native function.
```javascript
_.isNative(Array.prototype.push);
// => true
_.isNative(_);
// => false
```

### _.isNil(value)
Checks if `value` is `null` or `undefined`.
```javascript
_.isNil(null);
// => true
_.isNil(void 0);
// => true
```

### _.isNull(value)
Checks if `value` is `null`.
```javascript
_.isNull(null);
// => true
_.isNull(void 0);
// => false
```

### _.isNumber(value)
Checks if `value` is classified as a `Number` primitive or object.
```javascript
_.isNumber(3);
// => true
_.isNumber(Number.MIN_VALUE);
// => true
_.isNumber(Infinity);
// => true
_.isNumber('3');
// => false
```

### _.isObject(value)
Checks if `value` is the language type of `Object`. (e.g. arrays, functions, objects, regexes, `new Number(0)`, and `new String('')`)
```javascript
_.isObject({});
// => true
_.isObject([1, 2, 3]);
// => true
_.isObject(_.noop);
// => true
_.isObject(null);
// => false
```

### _.isObjectLike(value)
Checks if `value` is object-like. A value is object-like if it's not `null` and has a `typeof` result of "object".
```javascript
_.isObjectLike({});
// => true
_.isObjectLike([1, 2, 3]);
// => true
_.isObjectLike(_.noop);
// => false
_.isObjectLike(null);
// => false
```

### _.isPlainObject(value)
Checks if `value` is a plain object, that is, an object created by the `Object` constructor or one with a `[[Prototype]]` of `null`.
```javascript
function Foo() {
  this.a = 1;
}
_.isPlainObject(new Foo);
// => false
_.isPlainObject([1, 2, 3]);
// => false
_.isPlainObject({ 'x': 0, 'y': 0 });
// => true
_.isPlainObject(Object.create(null));
// => true
```

### _.isRegExp(value)
Checks if `value` is classified as a `RegExp` object.
```javascript
_.isRegExp(/abc/);
// => true
_.isRegExp('/abc/');
// => false
```

### _.isSafeInteger(value)
Checks if `value` is a safe integer. An integer is safe if it's an IEEE-754 double precision number which isn't the result of a rounded unsafe integer.
```javascript
_.isSafeInteger(3);
// => true
_.isSafeInteger(Number.MIN_VALUE);
// => false
_.isSafeInteger(Infinity);
// => false
_.isSafeInteger('3');
// => false
```

### _.isSet(value)
Checks if `value` is classified as a `Set` object.
```javascript
_.isSet(new Set);
// => true
_.isSet(new WeakSet);
// => false
```

### _.isString(value)
Checks if `value` is classified as a `String` primitive or object.
```javascript
_.isString('abc');
// => true
_.isString(1);
// => false
```

### _.isSymbol(value)
Checks if `value` is classified as a `Symbol` primitive or object.
```javascript
_.isSymbol(Symbol.iterator);
// => true
_.isSymbol('abc');
// => false
```

### _.isTypedArray(value)
Checks if `value` is classified as a typed array.
```javascript
_.isTypedArray(new Uint8Array);
// => true
_.isTypedArray([]);
// => false
```

### _.isUndefined(value)
Checks if `value` is `undefined`.
```javascript
_.isUndefined(void 0);
// => true
_.isUndefined(null);
// => false
```

### _.isWeakMap(value)
Checks if `value` is classified as a `WeakMap` object.
```javascript
_.isWeakMap(new WeakMap);
// => true
_.isWeakMap(new Map);
// => false
```

### _.isWeakSet(value)
Checks if `value` is classified as a `WeakSet` object.
```javascript
_.isWeakSet(new WeakSet);
// => true
_.isWeakSet(new Set);
// => false
```

### _.lt(value, other)
Checks if `value` is less than `other`.
```javascript
_.lt(1, 3);
// => true
_.lt(3, 3);
// => false
_.lt(3, 1);
// => false
```

### _.lte(value, other)
Checks if `value` is less than or equal to `other`.
```javascript
_.lte(1, 3);
// => true
_.lte(3, 3);
// => true
_.lte(3, 1);
// => false
```

### _.toArray(value)
Converts `value` to an array.
```javascript
_.toArray({ 'a': 1, 'b': 2 });
// => [1, 2]
_.toArray('abc');
// => ['a', 'b', 'c']
_.toArray(1);
// => []
_.toArray(null);
// => []
```

### _.toFinite(value)
Converts `value` to a finite number.
```javascript
_.toFinite(3.2);
// => 3.2
_.toFinite(Number.MIN_VALUE);
// => 5e-324
_.toFinite(Infinity);
// => 1.7976931348623157e+308
_.toFinite('3.2');
// => 3.2
```

### _.toInteger(value)
Converts `value` to an integer.
```javascript
_.toInteger(3.2);
// => 3
_.toInteger(Number.MIN_VALUE);
// => 0
_.toInteger(Infinity);
// => 1.7976931348623157e+308
_.toInteger('3.2');
// => 3
```

### _.toLength(value)
Converts `value` to an integer suitable for use as the length of an array-like object.
```javascript
_.toLength(3.2);
// => 3
_.toLength(Number.MIN_VALUE);
// => 0
_.toLength(Infinity);
// => 4294967295
_.toLength('3.2');
// => 3
```

### _.toNumber(value)
Converts `value` to a number.
```javascript
_.toNumber(3.2);
// => 3.2
_.toNumber(Number.MIN_VALUE);
// => 5e-324
_.toNumber(Infinity);
// => Infinity
_.toNumber('3.2');
// => 3.2
```

### _.toPlainObject(value)
Converts `value` to a plain object flattening inherited enumerable string keyed properties of `value` to own properties of the plain object.
```javascript
function Foo() {
  this.b = 2;
}
Foo.prototype.c = 3;
_.toPlainObject(new Foo);
// => { 'b': 2, 'c': 3 }
```

### _.toSafeInteger(value)
Converts `value` to a safe integer. A safe integer can be compared and represented correctly.
```javascript
_.toSafeInteger(3.2);
// => 3
_.toSafeInteger(Number.MIN_VALUE);
// => 0
_.toSafeInteger(Infinity);
// => 9007199254740991
_.toSafeInteger('3.2');
// => 3
```

### _.toString(value)
Converts `value` to a string. An empty string is returned for `null` and `undefined` values. The sign of `-0` is preserved.
```javascript
_.toString(null);
// => ''
_.toString(-0);
// => '-0'
_.toString([1, 2, 3]);
// => '1,2,3'
```

### Math
Math methods include mathematical operations like `_.add`, `_.ceil`, `_.divide`, and others.

### _.add(augend, addend)
Adds two numbers.
```javascript
_.add(6, 4);
// => 10
```

### _.ceil(number, [precision=0])
Computes `number` rounded up to `precision`.
```javascript
_.ceil(4.006);
// => 5
_.ceil(6.004, 2);
// => 6.01
_.ceil(6040, -2);
// => 6100
```

### _.divide(dividend, divisor)
Divides two numbers.
```javascript
_.divide(6, 4);
// => 1.5
```

### _.floor(number, [precision=0])
Computes `number` rounded down to `precision`.
```javascript
_.floor(4.006);
// => 4
_.floor(0.046, 2);
// => 0.04
_.floor(4060, -2);
// => 4000
```

### _.max(array)
Computes the maximum value of `array`. If `array` is empty or falsey, `undefined` is returned.
```javascript
_.max([4, 2, 8, 6]);
// => 8
```

### _.maxBy(array, [iteratee=_.identity])
This method is like `_.max` except that it accepts `iteratee` which is invoked for each element in `array` to generate the criterion by which the value is ranked. The iteratee is invoked with one argument: (value).
```javascript
var objects = [{'n': 1}, {'n': 2}];
_.maxBy(objects, function(o) { return o.n; });
// => {'n': 2}
```

### _.mean(array)
Computes the mean of the values in `array`.
```javascript
_.mean([4, 2, 8, 6]);
// => 5
```

### _.meanBy(array, [iteratee=_.identity])
This method is like `_.mean` except that it accepts `iteratee` which is invoked for each element in `array` to generate the value to be averaged. The iteratee is invoked with one argument: (value).
```javascript
var objects = [{'n': 4}, {'n': 2}, {'n': 8}, {'n': 6}];
_.meanBy(objects, function(o) { return o.n; });
// => 5
```

### _.min(array)
Computes the minimum value of `array`. If `array` is empty or falsey, `undefined` is returned.
```javascript
_.min([4, 2, 8, 6]);
// => 2
```

### _.minBy(array, [iteratee=_.identity])
This method is like `_.min` except that it accepts `iteratee` which is invoked for each element in `array` to generate the criterion by which the value is ranked. The iteratee is invoked with one argument: (value).
```javascript
var objects = [{'n': 1}, {'n': 2}];
_.minBy(objects, function(o) { return o.n; });
// => {'n': 1}
```

### _.multiply(multiplier, multiplicand)
Multiplies two numbers.
```javascript
_.multiply(6, 4);
// => 24
```

### _.round(number, [precision=0])
Computes `number` rounded to `precision`.
```javascript
_.round(4.006);
// => 4
_.round(4.006, 2);
// => 4.01
_.round(4060, -2);
// => 4100
```

### _.subtract(minuend, subtrahend)
Subtracts two numbers.
```javascript
_.subtract(6, 4);
// => 2
```

### _.sum(array)
Computes the sum of the values in `array`.
```javascript
_.sum([4, 2, 8, 6]);
// => 20
```

### _.sumBy(array, [iteratee=_.identity])
This method is like `_.sum` except that it accepts `iteratee` which is invoked for each element in `array` to generate the value to be summed. The iteratee is invoked with one argument: (value).
```javascript
var objects = [{'n': 4}, {'n': 2}, {'n': 8}, {'n': 6}];
_.sumBy(objects, function(o) { return o.n; });
// => 20
```

### Number
Number methods include functions like `_.clamp`, `_.inRange`, `_.random`, and more.

### _.clamp(number, [lower], upper)
Clamps `number` within the inclusive `lower` and `upper` bounds.
```javascript
_.clamp(-10, -5, 5);
// => -5
_.clamp(10, -5, 5);
// => 5
```

### _.inRange(number, [start=0], end)
Checks if `number` is between `start` and up to, but not including, `end`. If `end` is not specified, it's set to `start` with `start` then set to `0`. If `start` is greater than `end` the params are swapped to support negative ranges.
```javascript
_.inRange(3, 2, 4);
// => true
_.inRange(4, 8);
// => true
_.inRange(4, 2);
// => false
_.inRange(2, 2);
// => false
_.inRange(1.2, 2);
// => true
_.inRange(5.2, 4);
// => false
_.inRange(-3, -2, -6);
// => true
```

### _.random([lower=0], [upper=1], [floating])
Produces a random number between the inclusive `lower` and `upper` bounds. If only one argument is provided a number between `0` and the given number is returned. If `floating` is `true`, or either `lower` or `upper` are floats, a floating-point number is returned instead of an integer.
```javascript
_.random(0, 5);
// => an integer between 0 and 5
_.random(5);
// => also an integer between 0 and 5
_.random(5, true);
// => a floating-point number between 0 and 5
_.random(1.2, 5.2);
// => a floating-point number between 1.2 and 5.2
```

### Object
Object methods include functions for working with objects and arrays. They include functions like `_.assign`, `_.at`, `_.defaults`, and others.

### _.assign(object, [sources])
Assigns own enumerable string keyed properties of source objects to the destination object. Source objects are applied from left to right. Subsequent sources overwrite property assignments of previous sources.
```javascript
function Foo() {
  this.a = 1;
}
function Bar() {
  this.c = 3;
}
_.assign({ 'a': 0 }, new Foo, new Bar);
// => { 'a': 1, 'c': 3 }
```

### _.assignIn(object, [sources]) -> _.extend(object, [sources])
This method is like `_.assign` except that it iterates over own and inherited source properties.
```javascript
function Foo() {
  this.a = 1;
}
function Bar() {
  this.c = 3;
}
Bar.prototype.b = 2;
_.assignIn({ 'a': 0 }, new Foo, new Bar);
// => { 'a': 1, 'b': 2, 'c': 3 }
```

### _.assignInWith(object, sources, [customizer]) -> _.extendWith(object, sources, [customizer])
This method is like `_.assignIn` except that it accepts `customizer` which is invoked to produce the assigned values. If `customizer` returns `undefined`, assignment is handled by the method instead. The `customizer` is invoked with five arguments: (objValue, srcValue, key, object, source).
```javascript
function customizer(objValue, srcValue) {
  return _.isUndefined(objValue) ? srcValue : objValue;
}
var defaults = _.partialRight(_.assignInWith, customizer);
defaults({ 'a': 1 }, { 'b': 2 }, { 'a': 3 });
// => { 'a': 1, 'b': 2 }
```

### _.assignWith(object, sources, [customizer])
This method is like `_.assign` except that it accepts `customizer` which is invoked to produce the assigned values. If `customizer` returns `undefined`, assignment is handled by the method instead. The `customizer` is invoked with five arguments: (objValue, srcValue, key, object, source).
```javascript
function customizer(objValue, srcValue) {
  return _.isUndefined(objValue) ? srcValue : objValue;
}
var defaults = _.partialRight(_.assignWith, customizer);
defaults({ 'a': 1 }, { 'b': 2 }, { 'a': 3 });
// => { 'a': 1, 'b': 2 }
```

### _.at(object, [paths])
Creates an array of values corresponding to `paths` of `object`.
```javascript
var object = { 'a': [{ 'b': { 'c': 3 } }, 4] };
_.at(object, ['a[0].b.c', 'a[1]']);
// => [3, 4]
```

### _.create(prototype, [properties])
Creates an object that inherits from the `prototype` object. If a `properties` object is given its own enumerable string keyed properties are assigned to the created object.
```javascript
function Shape() {
  this.x = 0;
  this.y = 0;
}
function Circle() {
  Shape.call(this);
}
Circle.prototype = _.create(Shape.prototype, {
  'constructor': Circle
});
var circle = new Circle;
circle instanceof Circle;
// => true
circle instanceof Shape;
// => true
```

### _.defaults(object, [sources])
Assigns own and inherited enumerable string keyed properties of source objects to the destination object for all destination properties that resolve to `undefined`. Source objects are applied from right to left. Once a property is set, additional values of the same property are ignored.
```javascript
_.defaults({ 'a': 1 }, { 'b': 2 }, { 'a': 3 });
// => { 'a': 1, 'b': 2 }
```

### _.defaultsDeep(object, [sources])
This method is like `_.defaults` except that it recursively assigns default properties.
```javascript
_.defaultsDeep({ 'a': { 'b': 2 } }, { 'a': { 'b': 1, 'c': 3 } });
// => { 'a': { 'b': 2, 'c': 3 } }
```

### _.entries(object) -> _.toPairs(object)
Creates an array of own enumerable string keyed-value pairs for `object` which can be consumed by `_.fromPairs`. If `object` is a map or set, its entries are returned.
```javascript
function Foo() {
  this.a = 1;
}
Foo.prototype.b = 2;
_.toPairs(new Foo);
// => [['a', 1]] (iteration order is not guaranteed)
```

### _.entriesIn(object) -> _.toPairsIn(object)
This method is like `_.toPairs` except that it includes inherited enumerable string keyed properties.
```javascript
function Foo() {
  this.a = 1;
}
Foo.prototype.b = 2;
_.toPairsIn(new Foo);
// => [['a', 1], ['b', 2]] (iteration order is not guaranteed)
```

### _.findKey(object, [predicate=_.identity])
This method is like `_.find` except that it returns the key of the first element `predicate` returns truthy for instead of the element itself.
```javascript
var users = {
  'barney':  { 'age': 36, 'active': true },
  'fred':    { 'age': 40, 'active': false },
  'pebbles': { 'age': 1,  'active': true }
};
_.findKey(users, function(o) { return o.age < 40; });
// => 'barney'
```

### _.findLastKey(object, [predicate=_.identity])
This method is like `_.findKey` except that it iterates over elements of a collection in the opposite order.
```javascript
var users = {
  'barney':  { 'age': 36, 'active': true },
  'fred':    { 'age': 40, 'active': false },
  'pebbles': { 'age': 1,  'active': true }
};
_.findLastKey(users, function(o) { return o.age < 40; });
// => returns 'pebbles' assuming `_.findKey` returns 'barney'
```

### _.forIn(object, [iteratee=_.identity])
Iterates over own and inherited enumerable string keyed properties of an object and invokes `iteratee` for each property. The iteratee is invoked with three arguments: (value, key, object). Iteratee functions may exit iteration early by explicitly returning `false`.
```javascript
function Foo() {
  this.a = 1;
  this.b = 2;
}
Foo.prototype.c = 3;
_.forIn(new Foo, function(value, key) {
  console.log(key);
});
// => Logs 'a', 'b', then 'c' (iteration order is not guaranteed).
```

### _.forInRight(object, [iteratee=_.identity])
This method is like `_.forIn` except that it iterates over properties of `object` in the opposite order.
```javascript
function Foo() {
  this.a = 1;
  this.b = 2;
}
Foo.prototype.c = 3;
_.forInRight(new Foo, function(value, key) {
  console.log(key);
});
// => Logs 'c', 'b', then 'a' assuming `_.forIn` logs 'a', 'b', then 'c'.
```

### _.forOwn(object, [iteratee=_.identity])
Iterates over own enumerable string keyed properties of an object and invokes `iteratee` for each property. The iteratee is invoked with three arguments: (value, key, object). Iteratee functions may exit iteration early by explicitly returning `false`.
```javascript
function Foo() {
  this.a = 1;
  this.b = 2;
}
Foo.prototype.c = 3;
_.forOwn(new Foo, function(value, key) {
  console.log(key);
});
// => Logs 'a' then 'b' (iteration order is not guaranteed).
```

### _.forOwnRight(object, [iteratee=_.identity])
This method is like `_.forOwn` except that it iterates over properties of `object` in the opposite order.
```javascript
function Foo() {
  this.a = 1;
  this.b = 2;
}
Foo.prototype.c = 3;
_.forOwnRight(new Foo, function(value, key) {
  console.log(key);
});
// => Logs 'b' then 'a' assuming `_.forOwn` logs 'a' then 'b'.
```

### _.functions(object)
Creates an array of function property names from own enumerable properties of `object`.
```javascript
function Foo() {
  this.a = _.constant('a');
  this.b = _.constant('b');
}
Foo.prototype.c = _.constant('c');
_.functions(new Foo);
// => ['a', 'b']
```

### _.functionsIn(object)
This method is like `_.functions` except that it returns the names of all function properties, including those that are not enumerable.
```javascript
function Foo() {
  this.a = _.constant('a');
  this.b = _.constant('b');
}
Foo.prototype.c = _.constant('c');
_.functionsIn(new Foo);
// => ['a', 'b', 'c']
```

### _.get(object, path, [defaultValue])
Gets the value at `path` of `object`. If the resolved value is `undefined`, the `defaultValue` is returned in its place.
```javascript
var object = { 'a': [{ 'b': { 'c': 3 } }] };
_.get(object, 'a[0].b.c');
// => 3
_.get(object, ['a', '0', 'b', 'c']);
// => 3
_.get(object, 'a.b.c', 'default');
// => 'default'
```

### _.has(object, path)
Checks if `path` is a direct property of `object`.
```javascript
var object = { 'a': { 'b': 2 } };
_.has(object, 'a');
// => true
_.has(object, 'a.b');
// => true
_.has(object, ['a', 'b']);
// => true
```

### _.hasIn(object, path)
Checks if `path` is a direct or inherited property of `object`.
```javascript
var object = _.create({ 'a': _.create({ 'b': 2 }) });
_.hasIn(object, 'a');
// => true
_.hasIn(object, 'a.b');
// => true
_.hasIn(object, ['a', 'b']);
// => true
```

### _.invert(object)
Creates an object composed of the inverted keys and values of `object`. If `object` contains duplicate values, subsequent values overwrite property assignments of previous values.
```javascript
var object = { 'a': 1, 'b': 2, 'c': 1 };
_.invert(object);
// => { '1': 'c', '2': 'b' }
```

### _.invertBy(object, [iteratee=_.identity])
This method is like `_.invert` except that the inverted object is generated from the results of running each element of `object` through `iteratee`. The corresponding inverted value of each inverted key is an array of keys responsible for generating the inverted value. The iteratee is invoked with one argument: (value).
```javascript
var object = { 'a': 1, 'b': 2, 'c': 1 };
_.invertBy(object);
// => { '1': ['a', 'c'], '2': ['b'] }
_.invertBy(object, function(value) {
  return 'group' + value;
});
// => { 'group1': ['a', 'c'], 'group2': ['b'] }
```

### _.invoke(object, path, [args])
Invokes the method at `path` of `object`. Any additional arguments are provided to the invoked method. If `path` is a function, it's invoked with the `this` binding of its parent object.
```javascript
var object = { 'a': [{ 'b': { 'c': [1, 2, 3, _.constant(5)] } }] };
_.invoke(object, 'a[0].b.c[3]');
// => 5
_.invoke(object, 'a[0].b.c.slice', 1);
// => [2, 3, 5]
```

### _.keys(object)
Creates an array of the own enumerable string keyed property names of `object`.
```javascript
function Foo() {
  this.a = 1;
  this.b = 2;
}
Foo.prototype.c = 3;
_.keys(new Foo);
// => ['a', 'b'] (iteration order is not guaranteed)
```

### _.keysIn(object)
Creates an array of the own and inherited enumerable string keyed property names of `object`.
```javascript
function Foo() {
  this.a = 1;
  this.b = 2;
}
Foo.prototype.c = 3;
_.keysIn(new Foo);
// => ['a', 'b', 'c'] (iteration order is not guaranteed)
```

### _.mapKeys(object, [iteratee=_.identity])
The opposite of `_.mapValues`; this method creates an object with the same values as `object` and keys generated by running each own enumerable string keyed property of `object` through `iteratee`. The iteratee is invoked with three arguments: (value, key, object).
```javascript
_.mapKeys({ 'a': 1, 'b': 2 }, function(value, key) {
  return key + value;
});
// => { 'a1': 1, 'b2': 2 }
```

### _.mapValues(object, [iteratee=_.identity])
Creates an object with the same keys as `object` and values generated by running each own enumerable string keyed property of `object` through `iteratee`. The iteratee is invoked with three arguments: (value, key, object).
```javascript
var users = {
  'fred':    { 'user': 'fred',    'age': 40 },
  'pebbles': { 'user': 'pebbles', 'age': 1 }
};
_.mapValues(users, function(o) { return o.age; });
// => { 'fred': 40, 'pebbles': 1 } (iteration order is not guaranteed)
```

### _.merge(object, [sources])
This method is like `_.assign` except that it recursively merges own and inherited enumerable string keyed properties of source objects into the destination object. Source properties that resolve to `undefined` are skipped if a destination value exists. Array and plain object properties are merged recursively. Other objects and value types are overridden by assignment. Source objects are applied from left to right. Subsequent sources overwrite property assignments of previous sources.
```javascript
var object = {
  'a': [{ 'b': 2 }, { 'd': 4 }]
};
var other = {
  'a': [{ 'c': 3 }, { 'e': 5 }]
};
_.merge(object, other);
// => { 'a': [{ 'b': 2, 'c': 3 }, { 'd': 4, 'e': 5 }] }
```

### _.mergeWith(object, sources, [customizer])
This method is like `_.merge` except that it accepts `customizer` which is invoked to produce the merged values of the destination and source properties. If `customizer` returns `undefined`, merging is handled by the method instead. The `customizer` is invoked with six arguments: (objValue, srcValue, key, object, source, stack).
```javascript
function customizer(objValue, srcValue) {
  if (_.isArray(objValue)) {
    return objValue.concat(srcValue);
  }
}
var object = { 'a': [1], 'b': [2] };
var other = { 'a': [3], 'b': [4] };
_.mergeWith(object, other, customizer);
// => { 'a': [1, 3], 'b': [2, 4] }
```

### _.omit(object, [paths])
The opposite of `_.pick`; this method creates an object composed of the own and inherited enumerable string keyed properties of `object` that are not omitted.
```javascript
var object = { 'a': 1, 'b': '2', 'c': 3 };
_.omit(object, ['a', 'c']);
// => { 'b': '2' }
```

### _.omitBy(object, [predicate=_.identity])
Creates an object composed of the own and inherited enumerable string keyed properties of `object` that `predicate` doesn't return truthy for. The predicate is invoked with two arguments: (value, key).
```javascript
var object = { 'a': 1, 'b': '2', 'c': 3 };
_.omitBy(object, _.isNumber);
// => { 'b': '2' }
```

### _.pick(object, [paths])
Creates an object composed of the picked `object` properties.
```javascript
var object = { 'a': 1, 'b': '2', 'c': 3 };
_.pick(object, ['a', 'c']);
// => { 'a': 1, 'c': 3 }
```

### _.pickBy(object, [predicate=_.identity])
Creates an object composed of the `object` properties `predicate` returns truthy for. The predicate is invoked with two arguments: (value, key).
```javascript
var object = { 'a': 1, 'b': '2', 'c': 3 };
_.pickBy(object, _.isNumber);
// => { 'a': 1, 'c': 3 }
```

### _.result(object, path, [defaultValue])
This method is like `_.get` except that if the resolved value is a function it's invoked with the `this` binding of its parent object and its result is returned.
```javascript
var object = { 'a': [{ 'b': { 'c1': 3, 'c2': _.constant(4) } }] };
_.result(object, 'a[0].b.c1');
// => 3
_.result(object, 'a[0].b.c2');
// => 4
_.result(object, 'a[0].b.c3', 'default');
// => 'default'
_.result(object, 'a[0].b.c3', _.constant('default'));
// => 'default'
```

### _.set(object, path, value)
Sets the value at `path` of `object`. If a portion of `path` doesn't exist, it's created. Arrays are created for missing index properties while objects are created for all other missing properties. Use `_.setWith` to customize `path` creation.
```javascript
var object = { 'a': [{ 'b': { 'c': 3 } }] };
_.set(object, 'a[0].b.c', 4);
_.set(object, ['x', '0', 'y', 'z'], 5);
console.log(object);
// => { 'a': [{ 'b': { 'c': 4 } }], 'x': [{ 'y': { 'z': 5 } }] }
```

### _.setWith(object, path, value, [customizer])
This method is like `_.set` except that it accepts `customizer` which is invoked to produce the intermediate objects of `path`. If `customizer` returns `undefined`, `path` creation is handled by the method instead. The `customizer` is invoked with three arguments: (nsValue, key, nsObject).
```javascript
var object = {};
_.setWith(object, '[0][1]', 'a', Object);
console.log(object);
// => { '0': { '1': 'a' } }
```

### _.toPairs(object)
Creates an array of own enumerable string keyed-value pairs for `object` which can be consumed by `_.fromPairs`.
```javascript
function Foo() {
  this.a = 1;
  this.b = 2;
}
_.toPairs(new Foo);
// => [['a', 1], ['b', 2]] (iteration order is not guaranteed)
```

### _.toPairsIn(object)
This method is like `_.toPairs` except that it includes inherited enumerable string keyed properties.
```javascript
function Foo() {
  this.a = 1;
  this.b = 2;
}
Foo.prototype.c = 3;
_.toPairsIn(new Foo);
// => [['a', 1], ['b', 2], ['c', 3]] (iteration order is not guaranteed)
```

### _.transform(object, [iteratee=_.identity], [accumulator])
An alternative to `_.reduce`; this method transforms `object` to a new `accumulator` object which is the result of running each of its own enumerable string keyed properties through `iteratee`, with each invocation potentially mutating `accumulator`. The iteratee is invoked with four arguments: (accumulator, value, key, object). Iteratee functions may exit iteration early by explicitly returning `false`.
```javascript
_.transform([2, 3, 4], function(result, n) {
  result.push(n *= n);
  return n % 2 == 0;
}, []);
// => [4, 9]
```

### _.unset(object, path)
Removes the property at `path` of `object`.
```javascript
var object = { 'a': [{ 'b': { 'c': 7 } }] };
_.unset(object, 'a[0].b.c');
console.log(object);
// => { 'a': [{ 'b': {} }] };
_.unset(object, ['a', '0', 'b', 'c']);
console.log(object);
// => { 'a': [{ 'b': {} }] };
```

### _.update(object, path, updater)
This method is like `_.set` except that accepts `updater` to produce the value to set. Use `_.updateWith` to customize `path` creation. The `updater` is invoked with one argument: (value).
```javascript
var object = { 'a': [{ 'b': { 'c': 3 } }] };
_.update(object, 'a[0].b.c', function(n) { return n * n; });
console.log(object);
// => { 'a': [{ 'b': { 'c': 9 } }] }
_.update(object, 'a[0].b.c', function(n) { return n ? n + 1 : 0; });
console.log(object);
// => { 'a': [{ 'b': { 'c': 10 } }] }
```

### _.updateWith(object, path, updater, [customizer])
This method is like `_.update` except that it accepts `customizer` which is invoked to produce the objects of `path`. If `customizer` returns `undefined`, `path` creation is handled by the method instead. The `customizer` is invoked with three arguments: (nsValue, key, nsObject).
```javascript
var object = {};
_.updateWith(object, '[0][1]', _.constant('a'), Object);
console.log(object);
// => { '0': { '1': 'a' } }
```

### _.values(object)
Creates an array of the own enumerable string keyed property values of `object`.
```javascript
function Foo() {
  this.a = 1;
  this.b = 2;
}
_.values(new Foo);
// => [1, 2] (iteration order is not guaranteed)
```

### _.valuesIn(object)
This method is like `_.values` except that it includes inherited enumerable string keyed properties.
```javascript
function Foo() {
  this.a = 1;
  this.b = 2;
}
Foo.prototype.c = 3;
_.valuesIn(new Foo);
// => [1, 2, 3] (iteration order is not guaranteed)
```

### Seq
Seq methods are sequence methods that, when chained, return wrapped values. They include `_.chain`, `_.tap`, `_.thru`, and others.

Sure, here are the descriptions and examples for the Lodash seq methods you mentioned:

### _(value)
Creates a lodash wrapper instance that wraps `value` with implicit method chain sequences enabled. The result of such sequences must be unwrapped with `_#value`.
```javascript
_([1, 2, 3]).map(function(n) { return n * 2; }).reverse().value();
// => [6, 4, 2]
```

### _.chain(value)
Creates a lodash wrapper instance that wraps `value` with explicit method chain sequences enabled. The result of such sequences must be unwrapped with `_#value`.
```javascript
var users = [
  { 'user': 'barney',  'age': 36 },
  { 'user': 'fred',    'age': 40 },
  { 'user': 'pebbles', 'age': 1 }
];
var youngest = _
  .chain(users)
  .sortBy('age')
  .map(function(o) {
    return o.user + ' is ' + o.age;
  })
  .head()
  .value();
// => 'pebbles is 1'
```

### _.tap(value, interceptor)
This method invokes `interceptor` and returns `value`. The interceptor is invoked with one argument: (value). The purpose of this method is to "tap into" a method chain sequence in order to modify intermediate results.
```javascript
_([1, 2, 3])
 .tap(function(array) {
   // Mutate input array.
   array.pop();
 })
 .reverse()
 .value();
// => [2, 1]
```

### _.thru(value, interceptor)
This method is like `_.tap` except that it returns the result of `interceptor`. The purpose of this method is to "pass thru" values replacing intermediate results in a method chain sequence.
```javascript
_([1, 2, 3])
 .map(function(n) {
   return n * 3;
 })
 .thru(function(array) {
   return array.reduce(function(sum, n) {
     return sum + n;
   }, 0);
 })
 .value();
// => 18
```

### _.prototype[Symbol.iterator]
This method enables the wrapper to be iterable.
```javascript
var wrapped = _([1, 2]);
wrapped[Symbol.iterator]() === wrapped;
// => true
Array.from(wrapped);
// => [1, 2]
```

### _.prototype.at(paths)
This method is like `_.at` except that it accepts multiple paths (arrays), spreading them into the method chain.
```javascript
var object = { 'a': [{ 'b': { 'c': 3, 'd': 4 } }] };
_(object).at(['a[0].b.c', 'a[0].b.d']).value();
// => [3, 4]
```

### _.prototype.chain()
Enables explicit method chain sequences for the wrapper object.
```javascript
_([1, 2, 3])
 .chain()
 .map(function(n) {
   return n * 2;
 })
 .reverse()
 .value();
// => [6, 4, 2]
```

### _.prototype.commit()
Executes the chain sequence and returns the wrapped result.
```javascript
var wrapped = _([1, 2, 3]);
wrapped.reverse().value();
// => [3, 2, 1]
wrapped.commit().reverse().value();
// => [1, 2, 3]
```

### _.prototype.next()
Gets the next wrapped value in the chain sequence. If the chain sequence has ended, `undefined` is returned.
```javascript
var wrapped = _([1, 2]);
wrapped.next();
// => { 'done': false, 'value': 1 }
wrapped.next();
// => { 'done': false, 'value': 2 }
wrapped.next();
// => { 'done': true, 'value': undefined }
```

### _.prototype.plant(value)
Replaces the wrapped value.
```javascript
var wrapped = _([1, 2]);
var other = wrapped.plant([3, 4]);
other.value();
// => [3, 4]
wrapped.value();
// => [1, 2]
```

### _.prototype.reverse()
Reverses the wrapped array so the first element becomes the last, the second element becomes the second to last, and so on.
```javascript
var array = [1, 2, 3];
_(array).reverse().value();
// => [3, 2, 1]
console.log(array);
// => [3, 2, 1]
```

### _.prototype.toJSON() -> _.prototype.value()
Executes the chain sequence to resolve the unwrapped value.
```javascript
var wrapped = _({ 'user': 'barney' });
wrapped.toJSON();
// => { 'user': 'barney' }
wrapped.value();
// => { 'user': 'barney' }
```

### _.prototype.value()
Executes the chain sequence to resolve the unwrapped value.
```javascript
_([1, 2, 3]).value();
// => [1, 2, 3]
```

### _.prototype.valueOf() -> _.prototype.value()
This method returns the result of a sequence chain sequence unwrapped.
```javascript
_([1, 2, 3]).valueOf();
// => [1, 2, 3]
```

### String
String methods include functions like `_.camelCase`, `_.capitalize`, `_.deburr`, and more.

### _.camelCase([string=''])
Converts `string` to camel case.
```javascript
_.camelCase('Foo Bar');
// => 'fooBar'
_.camelCase('--foo-bar--');
// => 'fooBar'
_.camelCase('__FOO_BAR__');
// => 'fooBar'
```

### _.capitalize([string=''])
Converts the first character of `string` to upper case and the remaining to lower case.
```javascript
_.capitalize('FRED');
// => 'Fred'
```

### _.deburr([string=''])
Deburrs `string` by converting Latin-1 Supplement and Latin Extended-A letters to basic Latin letters and removing combining diacritical marks.
```javascript
_.deburr('déjà vu');
// => 'deja vu'
```

### _.endsWith([string=''], [target], [position=string.length])
Checks if `string` ends with the given target string.
```javascript
_.endsWith('abc', 'c');
// => true
_.endsWith('abc', 'b');
// => false
_.endsWith('abc', 'b', 2);
// => true
```

### _.escape([string=''])
Converts the characters "&", "<", ">", '"', and "'" in `string` to their corresponding HTML entities.
```javascript
_.escape('fred, barney, & pebbles');
// => 'fred, barney, &amp; pebbles'
```

### _.escapeRegExp([string=''])
Escapes the RegExp special characters "^", "$", "\", ".", "*", "+", "?", "(", ")", "[", "]", "{", "}", and "|" in `string`.
```javascript
_.escapeRegExp('[lodash](https://lodash.com/)');
// => '\[lodash\]\(https://lodash\.com/\)'
```

### _.kebabCase([string=''])
Converts `string` to kebab case.
```javascript
_.kebabCase('Foo Bar');
// => 'foo-bar'
_.kebabCase('fooBar');
// => 'foo-bar'
_.kebabCase('__FOO_BAR__');
// => 'foo-bar'
```

### _.lowerCase([string=''])
Converts `string`, as space separated words, to lower case.
```javascript
_.lowerCase('--Foo-Bar--');
// => 'foo bar'
_.lowerCase('fooBar');
// => 'foo bar'
_.lowerCase('__FOO_BAR__');
// => 'foo bar'
```

### _.lowerFirst([string=''])
Converts the first character of `string` to lower case.
```javascript
_.lowerFirst('Fred');
// => 'fred'
_.lowerFirst('FRED');
// => 'fRED'
```

### _.pad([string=''], [length=0], [chars=' '])
Pads `string` on the left and right sides if it's shorter than `length`. Padding characters are truncated if they can't be evenly divided by `length`.
```javascript
_.pad('abc', 8);
// => '  abc   '
_.pad('abc', 8, '_-');
// => '_-abc_-_'
_.pad('abc', 3);
// => 'abc'
```

### _.padEnd([string=''], [length=0], [chars=' '])
Pads `string` on the right side if it's shorter than `length`. Padding characters are truncated if they exceed `length`.
```javascript
_.padEnd('abc', 6);
// => 'abc   '
_.padEnd('abc', 6, '_-');
// => 'abc_-_'
_.padEnd('abc', 3);
// => 'abc'
```

### _.padStart([string=''], [length=0], [chars=' '])
Pads `string` on the left side if it's shorter than `length`. Padding characters are truncated if they exceed `length`.
```javascript
_.padStart('abc', 6);
// => '   abc'
_.padStart('abc', 6, '_-');
// => '_-_abc'
_.padStart('abc', 3);
// => 'abc'
```

### _.parseInt(string, [radix=10])
Converts `string` to an integer of the specified radix. If `radix` is `undefined` or `0`, a `radix` of `10` is used unless `value` is a hexadecimal, in which case a `radix` of `16` is used.
```javascript
_.parseInt('08');
// => 8
```

### _.repeat([string=''], [n=1])
Repeats the given string `n` times.
```javascript
_.repeat('*', 3);
// => '***'
_.repeat('abc', 2);
// => 'abcabc'
_.repeat('abc', 0);
// => ''
```

### _.replace([string=''], pattern, replacement)
Replaces matches for `pattern` in `string` with `replacement`.
```javascript
_.replace('Hi Fred', 'Fred', 'Barney');
// => 'Hi Barney'
```

### _.snakeCase([string=''])
Converts `string` to snake case.
```javascript
_.snakeCase('Foo Bar');
// => 'foo_bar'
_.snakeCase('fooBar');
// => 'foo_bar'
_.snakeCase('--FOO-BAR--');
// => 'foo_bar'
```

### _.split([string=''], separator, [limit])
Splits `string` by `separator`.
```javascript
_.split('a-b-c', '-', 2);
// => ['a', 'b']
```

### _.startCase([string=''])
Converts `string` to start case.
```javascript
_.startCase('--foo-bar--');
// => 'Foo Bar'
_.startCase('fooBar');
// => 'Foo Bar'
_.startCase('__FOO_BAR__');
// => 'FOO BAR'
```

### _.startsWith([string=''], [target], [position=0])
Checks if `string` starts with the given target string.
```javascript
_.startsWith('abc', 'a');
// => true
_.startsWith('abc', 'b');
// => false
_.startsWith('abc', 'b', 1);
// => true
```

### _.template([string=''], [options={}])
Creates a compiled template function that can interpolate data properties in "interpolate" delimiters, HTML-escape interpolated data properties in "escape" delimiters, and execute JavaScript in "evaluate" delimiters. Data properties may be accessed as free variables in the template. If a setting object is provided, it takes precedence over `_.templateSettings` values.
```javascript
var compiled = _.template('hello <%= user %>!');
compiled({ 'user': 'pebbles' });
// => 'hello pebbles!'
```

### _.toLower([string=''])
Converts `string`, as a whole, to lower case just like `String#toLowerCase`.
```javascript
_.toLower('--Foo-Bar--');
// => '--foo-bar--'
_.toLower('fooBar');
// => 'foobar'
_.toLower('__FOO_BAR__');
// => '__foo_bar__'
```

### _.toUpper([string=''])
Converts `string`, as a whole, to upper case just like `String#toUpperCase`.
```javascript
_.toUpper('--foo-bar--');
// => '--FOO-BAR--'
_.toUpper('fooBar');
// => 'FOOBAR'
_.toUpper('__foo_bar__');
// => '__FOO_BAR__'
```

### _.trim([string=''], [chars=whitespace])
Removes leading and trailing whitespace or specified characters from `string`.
```javascript
_.trim('  abc  ');
// => 'abc'
_.trim('-_-abc-_-', '_-');
// => 'abc'
```

### _.trimEnd([string=''], [chars=whitespace])
Removes trailing whitespace or specified characters from `string`.
```javascript
_.trimEnd('  abc  ');
// => '  abc'
_.trimEnd('-_-abc-_-', '_-');
// => '-_-abc'
```

### _.trimStart([string=''], [chars=whitespace])
Removes leading whitespace or specified characters from `string`.
```javascript
_.trimStart('  abc  ');
// => 'abc  '
_.trimStart('-_-abc-_-', '_-');
// => 'abc-_-'
```

### _.truncate([string=''], [options={}])
Truncates `string` if it's longer than the given maximum string length. The last characters of the truncated string are replaced with the omission string which defaults to "...".
```javascript
_.truncate('hi-diddly-ho there, neighborino');
// => 'hi-diddly-ho there, neighbo...'
_.truncate('hi-diddly-ho there, neighborino', {
  'length': 24,
  'separator': ' '
});
// => 'hi-diddly-ho there,...'
_.truncate('hi-diddly-ho there, neighborino', {
  'length': 24,
  'separator': /,? +/
});
// => 'hi-diddly-ho there...'
_.truncate('hi-diddly-ho there, neighborino', {
  'omission': ' [...]'
});
// => 'hi-diddly-ho there, neig [...]'
```

### _.unescape([string=''])
The inverse of `_.escape`; this method converts the HTML entities `&amp;`, `&lt;`, `&gt;`, `&quot;`, and `&#39;` in `string` to their corresponding characters.
```javascript
_.unescape('fred, barney, &amp; pebbles');
// => 'fred, barney, & pebbles'
```

### _.upperCase([string=''])
Converts `string`, as space separated words, to upper case.
```javascript
_.upperCase('--foo-bar');
// => 'FOO BAR'
_.upperCase('fooBar');
// => 'FOO BAR'
_.upperCase('__foo_bar__');
// => 'FOO BAR'
```

### _.upperFirst([string=''])
Converts the first character of `string` to upper case.
```javascript
_.upperFirst('fred');
// => 'Fred'
_.upperFirst('FRED');
// => 'FRED'
```

### _.words([string=''], [pattern])
Splits `string` into an array of its words.
```javascript
_.words('fred, barney, & pebbles');
// => ['fred', 'barney', 'pebbles']
_.words('fred, barney, & pebbles', /[^, ]+/g);
// => ['fred', 'barney', '&', 'pebbles']
```

### Util
Util methods include utility functions like `_.attempt`, `_.bindAll`, `_.cond`, and others.

### _.attempt(func, [args])
The `_.attempt` method attempts to invoke the function `func`, returning either the result or the caught error object. Any additional arguments are provided to `func` when it's invoked.
```javascript
// Example
let result = _.attempt(JSON.parse, '{ "name": "John Doe" }');
console.log(result); // => { name: 'John Doe' }
```

### _.bindAll(object, methodNames)
The `_.bindAll` method binds methods of an object to the object itself, overwriting the existing method. `methodNames` are the method names to bind.
```javascript
// Example
let view = {
  'label': 'docs',
  'click': function() {
    console.log('clicked ' + this.label);
  }
};
_.bindAll(view, ['click']);
jQuery(element).on('click', view.click);
// => Logs 'clicked docs' when clicked.
```

### _.cond(pairs)
The `_.cond` method creates a function that iterates over the `pairs` and invokes the corresponding function of the first predicate to return truthy.
```javascript
// Example
let func = _.cond([
  [_.matches({ 'a': 1 }),      _.constant('matches A')],
  [_.conforms({ 'b': _.isNumber }), _.constant('matches B')],
  [_.stubTrue, _.constant('no match')]
]);
console.log(func({ 'a': 1, 'b': 2 })); // => 'matches A'
```

### _.conforms(source)
The `_.conforms` method creates a function that checks if the given object conforms to `source` by invoking the predicate properties of `source` with the corresponding property values of the given object.
```javascript
// Example
let objects = [
  { 'a': 2, 'b': 1 },
  { 'a': 1, 'b': 2 }
];
console.log(_.filter(objects, _.conforms({ 'b': function(n) { return n > 1; } }))); // => [{ 'a': 1, 'b': 2 }]
```

### _.constant(value)
The `_.constant` method creates a function that returns `value`.
```javascript
// Example
let getFive = _.constant(5);
console.log(getFive()); // => 5
```

### _.defaultTo(value, defaultValue)
The `_.defaultTo` method checks `value` to determine whether a default value should be returned in its place. The `defaultValue` is returned if `value` is `NaN`, `null`, or `undefined`.
```javascript
// Example
console.log(_.defaultTo(1, 10)); // => 1
console.log(_.defaultTo(undefined, 10)); // => 10
```

### _.flow([funcs])
The `_.flow` method creates a function that returns the result of invoking the given functions with the `this` binding of the created function, where each successive invocation is supplied the return value of the previous.
```javascript
// Example
function square(n) {
  return n * n;
}
let addSquare = _.flow([_.add, square]);
console.log(addSquare(1, 2)); // => 9
```

### _.flowRight([funcs])
The `_.flowRight` method is like `_.flow` except that it creates a function that invokes the given functions from right to left.
```javascript
// Example
function square(n) {
  return n * n;
}
let squareAdd = _.flowRight([square, _.add]);
console.log(squareAdd(1, 2)); // => 9
```

### _.identity(value)
The `_.identity` method returns the first argument it receives.
```javascript
// Example
console.log(_.identity({ 'a': 1 })); // => { 'a': 1 }
```

### _.iteratee([func=_.identity])
The `_.iteratee` method creates a function that invokes `func` with the arguments of the created function. If `func` is a property name, the created function returns the property value for a given element.
```javascript
let users = [
  { 'user': 'barney', 'age': 36, 'active': true },
  { 'user': 'fred',   'age': 40, 'active': false }
];
console.log(_.filter(users, _.iteratee({ 'user': 'barney', 'active': true }))); // => [{ 'user': 'barney', 'age': 36, 'active': true }]
```

### _.matches(source)
The `_.matches` method creates a function that performs a partial deep comparison between a given object and source, returning true if the given object has equivalent property values, else false²⁵.
```javascript
let objects = [{ 'a': 1, 'b': 2, 'c': 3 }, { 'a': 4, 'b': 5, 'c': 6 }];
let result = _.filter(objects, _.matches({ 'a': 4, 'c': 6 }));
console.log(result); // => [{ 'a': 4, 'b': 5, 'c': 6 }]
```

### _.matchesProperty(path, srcValue)
The `_.matchesProperty` method creates a function that performs a partial deep comparison between the value at the path of a given object to srcValue, returning true if the object value is equivalent, else false¹.
```javascript
let objects = [{ 'a': 1, 'b': 2, 'c': 3 }, { 'a': 4, 'b': 5, 'c': 6 }];
let result = _.find(objects, _.matchesProperty('a', 4));
console.log(result); // => { 'a': 4, 'b': 5, 'c': 6 }
```

### _.method(path, [args])
The `_.method` function creates a function that invokes the method at `path` of a given object. Any additional arguments are provided to the invoked method⁵.

### _.methodOf(object, [args])
The `_.methodOf` method creates a function that invokes the method at a given path of the object. Any additional arguments are provided to the invoked method¹⁸.
```javascript
let array = _.times(3, _.constant);
let object = { 'a': array, 'b': array, 'c': array };
console.log(_.map(['a', 'c'], _.methodOf(object))); // => [[Function], [Function]]
```

### _.mixin([object=lodash], source, [options={}])
The `_.mixin` method extends the destination object with source object properties³⁴.
```javascript
function vowels(string) {
  return _.filter(string, function(v) {
    return /[aeiou]/i.test(v);
  });
}
_.mixin({ 'vowels': vowels }, { 'chain': false });
console.log(_('Julie').vowels()); // => ['u', 'i', 'e']
```

### _.noConflict()
The `_.noConflict` method is used to avoid conflicts with other libraries that use the same `_` variable. The function restores the original value of the global `_` variable and returns a reference to the lodash library¹⁴.

### _.noop([args])
The `_.noop` method is a function that returns `undefined` irrespective of the arguments passed to it²⁹.
```javascript
console.log(_.noop('value')); // => undefined
```

### _.nthArg([n=0])
The `_.nthArg` method creates a function that gets the argument at index `n`. If `n` is negative, the nth argument from the end is returned[^10^].
```javascript
let func = _.nthArg(1);
console.log(func('a', 'b', 'c', 'd')); // => 'b'
```

### _.over(iteratees)
The `_.over` method creates a function that invokes iteratees with the arguments it receives and returns the results²².
```javascript
let func = _.over([Math.min, Math.max]);
console.log(func(2, 4, -6, 8)); // => [2, 8]
```

### _.overEvery([predicates=_.identity])
The `_.overEvery` method creates a function that checks if all predicates return truthy when invoked with the arguments it receives³⁷.
```javascript
let func = _.overEvery([Boolean, isFinite]);
console.log(func(10)); // => true
```

### _.overSome([predicates=_.identity])
The `_.overSome` method creates a function that checks if any of the predicates return truthy when invoked with the arguments it receives⁵.
```javascript
let func = _.overSome([Boolean, isFinite]);
console.log(func('1')); // => true
console.log(func(null)); // => true
console.log(func(NaN)); // => false
```

### _.property(path)
The `_.property` method returns a function that will return the specified property of any passed-in object⁹.
```javascript
let info = { Company:  'GeeksforGeeks', Address:  'Noida' };
let gfg = _.property('Company')(info);
console.log(gfg); // => 'GeeksforGeeks'
```

### _.propertyOf(object)
The `_.propertyOf` method creates a function that returns the value at a given path of object²².
```javascript
let array = [0, 2], object = {  'a': array,  'b': array };
let propInfo = _.propertyOf(object)(['a', 0]);
console.log(propInfo); // => 0
```

### _.range([start=0], end, [step=1])
The `_.range` method creates an array of numbers (positive and/or negative) progressing from start up to, but not including, end¹⁹.
```javascript
console.log(_.range(4)); // => [0, 1, 2, 3]
console.log(_.range(0, 20, 5)); // => [0, 5, 10, 15]
```

### _.rangeRight([start=0], end, [step=1])
The `_.rangeRight` method is similar to `_.range`, but it populates values in the returned array in descending order⁵.
```javascript
console.log(_.rangeRight(0, 10, 2)); // => [8, 6, 4, 2, 0]
```

### _.runInContext([context=root])
The `_.runInContext` method creates a new lodash function using the given context object²⁸.

```javascript
_.mixin({ 'foo': _.constant('foo') });

var lodash = _.runInContext();
lodash.mixin({ 'bar': lodash.constant('bar') });

_.isFunction(_.foo);
// => true
_.isFunction(_.bar);
// => false

lodash.isFunction(lodash.foo);
// => false
lodash.isFunction(lodash.bar);
// => true

// Create a suped-up `defer` in Node.js.
var defer = _.runInContext({ 'setTimeout': setImmediate }).defer;
```

### _.stubArray()
The `_.stubArray` method returns a new empty array¹².
```javascript
var arrays = _.times(2, _.stubArray);

console.log(arrays);
// => [[], []]

console.log(arrays[0] === arrays[1]);
// => false
```

### _.stubFalse()
The `_.stubFalse` method returns `false`¹⁵.
```javascript
console.log(_.times(2, _.stubFalse)); // => [false, false]
```

### _.stubObject()
The `_.stubObject` method returns a new empty object²⁴.
```javascript
console.log(_.times(2, _.stubObject)); // => [{}, {}]
```

### _.stubString()
The `_.stubString` method returns an empty string³³.
```javascript
console.log(_.times(2, _.stubString)); // => ['', '']
```

### _.stubTrue()
The `_.stubTrue` method returns `true`. It's the opposite of `_.stubFalse`.
```javascript
_.times(2, _.stubTrue);
// => [true, true]
```
### _.times(n, [iteratee=_.identity])
The `_.times` method invokes the iteratee `n` times, returning an array of the results of each invocation. The iteratee is invoked with one argument: (index).
```javascript
 _.times(3, String);
// => ['0', '1', '2']

_.times(4, _.constant(0));
// => [0, 0, 0, 0]
 ```
### _.toPath(value)
The `_.toPath` method converts `value` to a property path array.
```javascript
_.toPath('a.b.c');
// => ['a', 'b', 'c']
 
_.toPath('a[0].b.c');
// => ['a', '0', 'b', 'c']
```
### _.uniqueId([prefix=''])
The `_.uniqueId` method generates a unique ID. If `prefix` is given, the ID is appended to it.
```javascript
_.uniqueId('contact_');
// => 'contact_104'
 
_.uniqueId();
// => '105'
```


### Properties
Properties in Lodash include values like `_.VERSION`, `_.templateSettings`, `_.support`, and others.

### _.VERSION
The `_.VERSION` property returns the version number of the Lodash library being utilized².
```javascript
const _ = require('lodash');
console.log(_.VERSION); // Output: "4.17.21" (or the version of Lodash installed in your project)
```

### _.templateSettings
The `_.templateSettings` property is an object for setting the default values of `_.template` method¹¹.
```javascript
const templateSettings = _.templateSettings;
console.log(templateSettings);
// Output: { 'escape': /<%-([sS]+?)%>/g, 'evaluate': /<%([sS]+?)%>/g, 'interpolate': /<%=([sS]+?)%>/g, 'variable': '', 'imports': { '_': { 'escape': [Function: escape] } } }
```

### _.templateSettings.escape
The `_.templateSettings.escape` property is a regular expression that determines the HTML entities in the template to be escaped¹¹.
```javascript
const templateSettingsEscape = _.templateSettings.escape;
```

### _.templateSettings.evaluate
The `_.templateSettings.evaluate` property is a regular expression that determines the JavaScript code in the template to be evaluated[^10^].
```javascript
_.templateSettings = {
  evaluate: /{{([sS]+?)}}/g
};
```

### _.templateSettings.imports
The `_.templateSettings.imports` property is an object for specifying imported variables for the template¹¹.
```javascript
const templateSettingsImports = _.templateSettings.imports;
```

### _.templateSettings.interpolate
The `_.templateSettings.interpolate` property is a regular expression that determines the data properties in the template to be interpolated¹³.
```javascript
_.templateSettings = {
  interpolate: /{{(.+?)}}/g
};
```

### _.templateSettings.variable
The `_.templateSettings.variable` property is a string for specifying the data object variable name¹¹.
```javascript
const templateSettingsVariable = _.templateSettings.variable;
```


### Methods
Methods in Lodash include all the functions available through it.

### _.templateSettings.imports._
A reference to the lodash function.

## Documentation

For detailed usage and API information, see the [official Lodash documentation](https://lodash.com/docs).
