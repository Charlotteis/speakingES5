# Basic JavaScript

The official name for JavaScript is actually ECMAScript. The term
'JavaScript' is trademarked by Oracle, but everyone uses it anyway.

JavaScript is missing much functionality that other languages have:
e.g. Block Scoped variables, modules and support for subclassing.

_All of the above and more is coming in ES6 :tada:_

> "In other languages, you learn language features. In JavaScript, you
often learn patterns instead."

_I think this is one of the reasons why people struggle to learn JS?_

JavaScript is a mix of functional programming (map, reduce, etc.) and
object-oriented programming (objects, inheritance).

**TODO: Find a good beginners resource on functional programming**

## =, ==, ===

`=`: assigning a value to a variable
`==`: comparing two values with lenience (type coersion)
    * `15 == '15'` is True
`===`: comparing two values with strictness (no coersion)
    * `15 === '15'` is False

## Statements vs. Expressions

A statement does something. When you are running a program, you are
running a sequence of statements.

```javascript
var statement = "This is a statement!";
```

An expression produces a value.

```javascript
123 + 456 + "cheese is great!"
```

You can use an expression as a function argument, but you cannot use
a statement as a function argument.

## Values & Properties

JavaScript has the following values and more: booleans, numbers,
strings, arrays and objects. Every value has a property, like
`variable.length`, `string.toUpperCase()`.

Booleans, numbers, strings, null and undefined are termed "Primitive
Values". Every other value is an object (objects, arrays, regular
expressions). We can compare two primitives together, but every object
created (even if it has the same value) is unique and a comparison will
always be False.

```javascript
var one = 1;
var two = 1;
console.log(one === two);
// -> true
```

```javascript
var dog = {
    name: "jake"
};

var dog2 = {
    name: "jake"
};

console.log('🐶 ', dog === dog2);
// -> 🐶 false
```

Primitives are always immutable. I.E You cannot change
the length of a string (a property) by doing `string.length = 4`.
You also cannot add a property to a primitive, nor remove one.

Non-primitive values are mutable by default.
`undefined` and `null` are considered "non-values" and both denote
that information is missing. Non-values have no properties.

## Numbers

All numbers in JavaScript are floating point. `1.0 === 1`.
`NaN` = Not a Number (not my Nan, which would be cooler)👵🏼.
`Infinity` is mostly an error value, larger than any other number.

Operators: +, -, \*, \/, %, ++, --, -value, +value.

## Strings

slice(), trim(), toUpperCase(), indexOf().

## Functions

Functional expressions produce a value and can thus be used to
directly pass function as arguments to other functions.

Function declarations are hoisted (moved in their entirety to the
beginning of the scope it resides in). Meaning, you can refer to
functions at the top of a file that are declared late in the file. 

Variable declarations are also hoisted, but assignments performed
by them, are not.

## `arguments`

`arguments` is a special variable that is an array referring
to the arguments passed into a function.

If there are too many arguments, the rest will be ignored.
If there are too few, all others will be set to 'undefined'.

Optional parameters in ES5:

```javascript
function add(x, y) {
    x == x || 0;
    y == y || 0;

    return x + y;
}
```

Optional parameters in ES6:

```javascript
function add(x = 0, y = 0) {
    return a + b;
}
```

To force a specific number of parameters: `if (arguments.length != 2)`.

`arguments` is not an Array, it is just array-like. It has a length,
but you cannot push or pop elements from it. None of the inbuilt Array
methods will work on it, either.

## Exception handling

`throw new Error('Error Message')`

Or use Try and Catch.

## Strict mode

`use strict;` - enables more warnings and makes JS cleaner. Can enable
it per function, rather than the whole document, if necessary. (This is what is effectively done for Modules in ES6, IIRC).

## IIFE

If you want to prevent a variable from becoming global, you can't use
a block so you must use a function. To use a function in a block-like
manner, you can use the IIFE (Immediately Invoked Function Expression).

```javascript
(function() {
    var password = '123'; // lol, don't do this
}());
```

## Objects & Constructors

Constructors are "factories" for objects. Like classes in other 
languages. _And way more annoying, this will change with ES6_.

Can get & set object literal properties. 
`dog.name` = getting, `dog.name = 'Charlie'` = setting.
A property on an object that is a function is called a method.

`'propertyName' in object.`
`delete dog.name`

### Extracting a method from an object

```javascript
var dog = {
    name: 'Jake',
    describe: function() {
        return 'Dog named ' + this.name;
    }
}

var func = dog.describe;
func();
// -> TypeError

var func = dog.describe.bind(dog);
func();
// -> 'Dog named Jake'
```

### Constructors

JavaScript objects support the object-oriented approach of inheritance.
Functions are also constructors, creating objects if invoked by `new`.

```javascript
function Dog(name) {
    this.name = name;
}

Dog.prototype.speak = function() {
    return this.name + ' says, "Woof!"'
}

var Jeremy = new Dog('Jeremy');
Jeremy.speak();
// -> Jeremy says, "Woof!"
```

## Arrays

Iteration through `forEach`.

### `map`

Creates a new array by applying a function to a provided array.

```javascript

var array = [1, 2, 3, 4];
var timesTwo = array.map(function(item) {
    return item * 2;
});
console.log(timesTwo);
// -> [2, 4, 6, 8]
```

## Regular Expressions (RegEx)

`expression.test('string')` - determine if your string matches a RegEx
`string.replace('expression', 'thing to replace')`.
