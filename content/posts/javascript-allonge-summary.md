---
title: "Reading JavaScript Allongé"
date: 2019-04-20T19:58:49+01:00
draft: false
---

I am currently reading this amazing book called "JavaScript Allongé" and I would
like to use my blog as a notebook to summarize the parts I found the most
interesting.
<span id="index">
### Table of content
As a general [rule](https://codurance.com/videos/2018-10-28-nature-of-learning) for effective learning when reading, it is recommended that you
read the table of contents and get an idea of what the book contains and how it
is structured.

This book's table of content is a bit messy and some
titles are not very descriptive, after separating the wheat from the chaff one could
say the content can be split into the following modules:

* [Module 1: The JavaScript functions, their context and wonders.](./#module1)
* [Module 2: Rebinding and references](./#module2).
* Module 3: Objects, mutation and state.
* Module 4: Instances and classes.
* Module 5: Sequence.
* Module 6: New ideas.

--

> *"The Strength of JavaScript is that you can do anything. The weakness is that you will"*

--

<br id="module1">
### Module1: The JavaScript functions, their context and wonders
---


A function in JavaScript is of **reference** type.
```
(function () {}) === (function () {})
//=> false
```
An **ouroborian array** is an array that contains itself.
```
var ouroboros=[];
ouroboros[0]=ouroboros;
//=> [ [Circular] ]
```
**void** is an operator that takes any value and evaluates to `undefined`, **always**.
If you want to return `undefined` you may return **void 0**:
```
return void 0;
//=>undefined
```
Any value after `void` will work, but by convention you better use `void 0;`

------------

**Free variable**: a variable in a function that is not bound to the function's context. If the variable is not *free*, then it is called a *bound* variable.
```
function(y){
  return x; // x is a free variable
}
```
If a function does not contain any *free* variable, it is called a **pure function**.

If a function contains one or more *free* variables, it is called a **closure**.

```
// A pure function can contain a closure:
function(x){
  return function(y){
    return x;
  }
}
```
```
// A closure can contain a pure function:
function(){
  var x = y; // <- 'y' is free
   return function(a){ // <- pure function
     return a;
   }
}
```

------------

This is a **named function**:
```
function feedSquirrel() {
  //...
}
```
This is **NOT** a named function:
```
var feedSquirrel = function() {
  //..
}
```

A **named function** is a function that is given a name when declaring it. If
the function has no name, then it is **anonymous**.

🌟Named function names are visible in the JavaScript stack trace, meanwhile anonymous functions
will always stay anonymous, even if they were bound to a name.

Named function declarations are automatically moved to the **top** by the JavaScript
interpreter. That's why you can do things like this and it works:

```
var feedSquirrel = function(){
  return grabPeanut;
  function grabPeanut(){
    // ...
  }
}()

// === Equivalent to: ===
var feedSquirrel = function(){
  var grabPeanut = function grabPeanut(){
    // ...
  }
  return grabPeanut;
}()
```

Variable name declarations are automatically moved to the top. If you have
```
function(){
  return myVar;
  var myVar = function(){

  }
}();
//=> undefined
```
JavaScript behaves as if you’d written:

```
function(){
  var myVar;
  return myVar;
  myVar = function(){

  }
}();
```

------------

A **higher order function** is a function that takes another function as argument
or returns a function (or both)

A **combinator** is a higher order function that is *pure* and returns another
function and takes only functions. [S,K,I](https://en.wikipedia.org/wiki/SKI_combinator_calculus) are
the most basic combinators and the book ["To Mock a mockingbird"](https://www.amazon.co.uk/Mock-Mockingbird-Other-Logic-Puzzles/dp/0192801422)
is a humorous introduction to combinatory logic and the associated metamathematics, built on an elaborate ornithological metaphor.

**Use** combinators when you want to emphasize what you're **doing** and **how** it fits together vs. emphasize what you're **working with**.

A **decorator** is a higher order function that takes one function as an argument, returns another function, and the returned function is a variation of the argument function. Examples of decorators are:

* `Once`: ensures that a function can only be called once.
* `MapWith`: takes a function as an argument, and applies it to each of the elements of the array, then returns the results in another array.
* `Maybe`: ensures that a function does nothing if it's given nothing (like null or undefined)

Decorators can be **composed**

```
// Composing decorators:
var invokeTransfer = once(maybe(actuallyTransfer(...)));

```
-------------

#### Function's magic arguments

JavaScript binds two additional names in addition to any you put in the argument list. These are:
##### 1. `arguments`
```
function args(a, b){
  console.log(arguments);
}
args(2,3) //=>{'0':2,'1':3, 'length': 2}
```
As one can see, `arguments` is an **object** that binds values to names that look like
integers starting with '0'.

##### 2. `this`
It's bound to the function's *context* and will be explained in more detail in [Module 3: Objects, mutation and state](../javascript-allonge-module-three.md)

#### Function's magic methods

###### `apply` and `call`
```
function plus(a, b){
  return a+b;
}
plus(2, 3) //=> 5;
plus.call(this, 2, 3) // => 5;
plus.apply(this, [2, 3]) // => 5;
```

###### `length`
```
plus.length //=> 2 (number of arguments the function takes)
```
--------------
`let` will create a SyntaxError when you try to declare it again. While `var` will not.
Also `let` has **block** scope while `var` has **function** scope.

##### Array methods

###### `slice`
```
[1, 2, 3, 4, 5].slice(1, 4) //=> [2, 3, 4]
[1,2,3].slice(0)            //=> [1, 2, 3]
[1,2,3].slice(1)            //=> [2, 3]
[1,2,3].slice(2)            //=> [3]
```
For simplicity and speed improvement, slice is usually bound to a local variable.
```
var __slice = Array.prototype.slice;
```


###### `concat`
```
[1, 2, 3].concat([2, 1])
```

#### Recipes with basic functions

`callLast` and `callFirst` partially apply a given value to a function.
The first one applying the value to the latest function argument; the second one
to the first function argument.
Implementation and playground:
<iframe height="400px" width="100%" src="https://repl.it/repls/TotalBelatedCommand?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>


The `variadic` function allows applying a same function to each value of an array
```
variadic(double)([1, 2, 3]); //=> [4, 5, 6]
```
`unary` takes any function and turns it into a function taking exactly one argument.

`tap` takes a value and returns a function that always returns the value, but if you pass it a function, it executes the function for side-effects

<br id="module2">
<a href="./#index"> 🔝 Table of Content</a>
### Module 2: Rebinding and references
---
In JavaScript, arrays and objects mutate: we can reassign parts of their structure and their identity stays the same.
Object property names that are not alphanumeric, must be enclosed in quotes.

##### How to shoot yourself in the foot with `var`

1. Loose use:

