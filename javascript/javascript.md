## General Concepts

### Reference vs. Value

(_The following is basically a short version of [this article](https://codeburst.io/explaining-value-vs-reference-in-javascript-647a975e12a0)_)

Primitives are accessed directly. Primitives are:

- `String`
- `Number`
- `Boolean`
- `null`
- `undefined`

Other data types are passed by reference (and handled as Objects in JavaScript):

- `Array`
- `Function`
- `Object`

When a primitive is assigned to a variable, its value is _copied_. For example:

```JavaScript
var x = 10
var a = x
var x = 'abc'

console.log(x) // => 'abc'
console.log(a) // => 10
```

Changes made to `x` after assigning `x` to `a` are not reflected in `a`, because its value copied and the variables have no connection whatsoever to on another.

In contrast, Objects are references to an address. If an Object is assigned to a variable, that variable contains a _reference_ to the address of the Object. Therefore, changes made to the object are reflected in all variables referencing that address.

```JavaScript
function invalidatePerson(person) {
	person.valid = false
}

var jenkins = {
	age: 25,
	valid: true
}

var invalidPerson = invalidatePerson(jenkins)

console.log(jenkins.valid) // => false
console.log(invalidPerson.valid) // => false
```

### [What is a pure function?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976#.8h1rzm6vi)

A pure function in JavaScript is a function with no side effects, everytime you call it with the same arguments it returns the exact same result. Common disqualifiers for a pure function are Methods like `Math.random()` and `Date.now()` being called. I the function has to manupilate an object, it has to manipulate a copy of it to not manipulate the external state.

## Useful things

### [`console.table`](https://developer.mozilla.org/en-US/docs/Web/API/Console/table)

Useful to print out complexer data structures. (Non Standard)

### [Template Literals](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Template_literals)

String literals that allow embedded expressiosn:

```javascript
console.log("The result is ${result * 2}");
```

### Sum of an array

There is no native `sum()` function on JavaScript arrays, so the sum has to be calculated by hand somehow.
There is the method `reduce()` on array, though.

> The reduce() method applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value.

So, to sum the values of an array, we can simply use `reduce()` in a way like this (ES6 Syntax):

```JavaScript
const array = [1, 2, 3, 4]
const arraySum = array.reduce((sum, value) => sum + value, 1)
console.log(arraySum) // -> 10
```

[Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce?v=b)

### Create a unique array

Given the array

```
const arr = [0, 0, 0, 1, 2, 3, 3, 3, 4]
```

using `Set` we can create an array with only unique values in it

```
const uniqueArr = [...new Set(arr)] // [0, 1, 2, 3, 4]
```
