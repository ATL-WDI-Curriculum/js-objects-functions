# Objects and Functions

[![Build Status](https://travis-ci.org/ga-wdi-lessons/js-objects-functions.svg?branch=master)](https://travis-ci.org/ga-wdi-lessons/js-objects-functions)

## Learning Objectives

### Functions
- Describe what a JavaScript function is.
- Recognize the parts of a function.
- Write a function in JavaScript using a declaration and an expression.
- State the difference between a function's output and side effects.
- Differentiate between referencing and invoking a function.
- Define hoisting.

### Objects
- Explain how objects are defined as data structures
- Create objects using object literal syntax.
- Practice interacting with properties of literal objects.
- Explain nested data structures.
- Explain the difference between object properties and methods.
- Write an object method.

### Framing
**What have you learned so far in Javascript?**

* Data Types
* Conditionals
* Data Collections

## Functions

**What’s a function?**

* Fundamental component of Javascript.
* A reusable block of Javascript code.
* Simply put, a function is a block of code that takes an input, processes that input and then produces an output.
* Analogy: Quizno's Oven

**Q. Think back to what we have covered so far, when have you used functions before?**

### Why do we use functions?

> Say we wanted the product of two numbers? How would we do that with a function?

Benefits of functions
* Reusability.
* DRYness.
* Naming convention (describes intent).

### Recognize the parts

**What are the components of a function?**

#### Function Container

```js
function multiply(){

}
```

#### Input ("Arguments" or "Parameters")

```js
function multiply( num1, num2 ){

}
```

#### Output and Side Effects

```js
function multiply( num1, num2 ){
  console.log( num1 * num2 );
  return num1 * num2;
}
```
* Output: return value.
* Side Effects: e.g., print statements.

**Q**. Does a function need an input, output and/or side effects to work?
---

> A. Short answer. No.  Note: There is always an output (undefined). Discuss.

#### Calling and Referencing a Function

We've defined a function. Now we need to call it...

**Q. Now we that we have stored that function in memory, how to do we use it?**

```js
// Call the multiply function.
multiply( 2, 5 );

// What happens if we reference the function without parentheses?
multiply;
```

### Function Declarations and Expressions (10 / 30)

There are two ways to define or declare a function...

#### Declaration

``` javascript
function multiply( num1, num2 ) {
  return num1 * num2;
}
```

#### Expression

``` javascript
var multiply = function ( num1, num2 ) {
  return num1 * num2;
}
```

#### Declarations vs. Expressions

Both do the same thing and run the same chunk of code. But they are different.

- **Q. What differences do you notice?**

**Function declarations** define functions without assigning them to variables.

**Function expressions** save anonymous functions to variables.

While we call/reference functions defined through declarations and expressions the same way, they do have a subtle but important difference...

> **Note**: Declarations are processed before any code is executed, meaning you can call functions before they are declared. This behavior is known as **hoisting**.


### Hoisting

What do you think will happen when we run the below code...
```js
multiply( 3, 5 );
var multiply = function( num1, num2 ){           // NOTE: This is a function expression
  return num1 * num2;
}
```

Surely the same thing will happen when we run the below code...

```js
multiply( 3, 5 );
function multiply( num1, num2 ) {               // NOTE: This is a function declaration
  return num1 * num2;
}
```
> We can successfully call the multiply function before declaring it. When our script file loads, it essentially processes all function declarations first, and then runs the rest of our Javascript from top to bottom.

Knowing this, what will happen each time we call `express` and `declare` in the below example?

```js
express();        // What happens when we run this function at this point in the code?

var express = function() {
    console.log('Function expression called.');
};
```

What changes when we run?

```js
var express = function() {
    console.log('Function expression called.');
};

declare();        // ???
express();        // ???

function declare() {
    console.log('Function declaration called.');
}
```

**Q. This is a neat feature, but can you think of a potential pitfall of "hoisting" too often?**

* Code organization and readability.

> You could argue that Function Declarations are forgiving – if you try to use a function before it is declared, hoisting fixes the order and the function gets called without mishap. But that kind of forgiveness does not encourage tight coding and in the long run is probably more likely to promote surprises than prevent them. After all, programmers arrange their statements in a particular sequence for a reason.

## What's a Return Statement?

The ***return*** statement ends the execution of the function and (optionally) returns a value to the caller.

### Example

```javascript
// return the first object in the array that has the specified id.
function findById(arr, id) {
  for (var i = 0; i < arr.length; i++) {
    if (arr[i].id === id) {
      return arr[i];
    }
  }
  return null;      // why do we need this?
}
```

### Example

```javascript
// calculate income tax
function getTax(income) {
  if (income < 50000) {
    return income * 0.15;
  }
  else if (income < 100000) {
    return income * 0.20;
  }
  else {
    return income * 0.25;
  }
}

// calling the function
console.log("Tax on 40000 = " + getTax(40000));
console.log("Tax on 80000 = " + getTax(80000));
console.log("Tax on 120000 = " + getTax(120000));
```

## When There Is No Return Statement

Not all functions have a return value.

### Example

```javascript
line(10, 20, 60, 100); // draws a line
console.log(str);      // outputs str to console
```

Since a function is called to perform some task, the function must either (a) ***return*** a value; or (b) ***change**** the environment in some way; or (c) ***both***.

### Pure Functions

Functions that do *not* change the environment (and thus only return a value) are called ***pure*** functions.

Pure functions are generally easier to reason about and test because they are ***deterministic*** (i.e. predictable).

Pure functions also provide for easier ***composition***.

![alt tag](https://raw.githubusercontent.com/ATL-WDI-Curriculum/js-functions/master/images/composite-function.png)

One of the primary characteristics of ***Functional Programming*** is that most or all of the functions are ***pure*** functions.

### Functions in Variables

JavaScript can store anything in variables.

> Including functions!

### More Function Declarations

```javascript
// simple function declaration 
function square(x) {
  return x * x;
}

// function assigned to a variable
 var square = function(x) {
  return x * x;
};

// functions as properties of an Object 
var mathHelpers = { 
  square: function(x) {
    return x * x;
  },
  average: function(x, y) { 
    return (x + y) / 2; 
  }
 };

// invoking a "method"
var y = mathHelpers.square(3);
```

## Functions as 1st Class Citizens

In computer science, a programming language is said to have ***first-class*** functions if it treats functions as first-class citizens.

Specifically, this means that the language supports:

* Assigning functions to variables
* Storing functions within data structures
* Passing functions as arguments to other functions
* Returning functions as the value from other functions


## Anonymous Functions

```javascript
function foo() {
  // This is a named function...
}

function() {
  // This is an anonymous function...
}
```

Common uses of anonymous functions:

* store it as an object key’s value
* store it in a variable inside an object
* pass it as an argument to a function or method
  - use it as a callback or handler

## Functions & Scope

In modern programming languages, variables have a ***scope***, i.e. the part of the program where a variable is bound to a memory location. You can think of the ***scope*** as the lifetime of the variable (where in the program the variable is born and where it dies or is discarded).

***Global*** variables have ***global*** scope; they are alive for the entire duration of the program execution.

***Local*** variables have ***local*** scope; they are alive during a part of the execution of the program.

> For JavaScript (before JavaScript 2015), local variables are scoped by their enclosing ```function```.  JavaScript 2015 is introducing ***lexical*** scope for variables declared with the `let` keyword.

### Example

```javascript
var president = "Everyone knows me. Globally!";

function town() {
  var mayor = "I'm unknown outside of my township.";

  function house() {
    var homebody = "No one knows me. " +
      "I don't leave home. " +
      "but I know the mayor and the president.";
  }

  evilDictator = "I am evil! Want to know why?";
}
```

> If you forget the `var` keyword when declaring / introducing a new variable, JavaScript will ***punish*** you by making the variable ***global***. Many JavaScript **linters** (static code analyzers) will detect and report this mistake.


## Exercise: Fun with Functions Quiz

What is alerted in each case? Write down your answer before running the code.

1.
```js
function foo(){
  function bar() {
      return 3;
  }
  return bar();
  function bar() {
      return 8;
  }
}
alert(foo());
```
2.
```js
function foo(){
  var bar = function() {
      return 3;
  };
  return bar();
  var bar = function() {
      return 8;
  };
}
alert(foo());
```

3.
```js
function foo(){
  return bar();
  var bar = function() {
      return 3;
  };
  var bar = function() {
      return 8;
  };
}
alert(foo());
```


##YOU DO
1. Check out the function exercises [here](https://github.com/ATL-WDI-Curriculum/js-objects-functions/blob/master/js-functions-exercises.md).

2. Check out this [JS Calculator Exercise](https://github.com/ATL-WDI-Exercises/js-calculator).

3. Try implementing [fizzBuzz](https://github.com/ATL-WDI-Exercises/fizzBuzz_redux) in the console with Functions! 



## Break

## Intro to Objects

In JavaScript, Objects are arbitrary collections of properties; we can add or remove these properties as we please. One way to create an object is by using a curly brace notation.

```js
var car = {
  make: "Honda",
  model: "Civic",
  year: 1997
}
```

Objects are a complex data type - usually referred to as an *unordered* list (or dictionary/hash/map).
* They are a collection of key-value pairs called properties.
* The keys which we explicitly state when defining a property are analogous to our array indexes. They are how we access the associated value (more below).

### Turn and Jot: Model WDI Student

You're goal is to pseudo-code an object literal:

* In pairs, spend 2 minutes thinking about what attributes a WDI student should have (think of at least 5!).
* Take 3 minutes to construct your object literal with appropriate key value pairs by drawing it on the table
* **Bonus - One key value pair contains an array**

### You DO: Interacting with Objects

**Read through the below, and then complete the exercise with your partner**

#### Create

We already saved a sample object to a `car` variable. We did this using **object literal notation**.

```js
var car = {
  make: "Honda",
  model: "Civic",
  year: 1997,

  // NOTE: Keys with a "-" in their name must be surrounded by quotation marks.
  "tire-type": "Goodyear"
}
```

#### Read

To access object properties, we use either dot (`.property`) or bracket (`["property"]`) notation.

```js
console.log( car.make );
console.log( car["make"] );

// What happens when we try to access a property yet to be defined?
console.log( car.owner )

// NOTE: When accessing properties whose keys have a "-" in them, you must use bracket notation.
console.log( car["tire-type"] );
```

#### Update

To update an object property, we place it on the left side of an assignment statement.

```js
car.year = 2003
```

We can also create brand new properties for an object after it's initialized using this method.

```js
// Now our car has a smell property equal to "Leathery Boot". We did not initially declare this property.
car.smell = "Leathery Boot"
```

#### Delete

If you want to delete an object property entirely, use the `delete` keyword.
* This deletes the whole key-value pair, not just the value.
* You won't do this often.

```js
delete car.smell
```

#### Iterating through an Object

Like arrays, you can use a loop to iterate through an object. Say we want to print out all of an object's keys...

```js
// Iterate through object keys
for (attribute in car) {
  console.log( attribute );
}
```
> Knowing this, how could we go about getting all the values in an object?

Javascript objects also have native methods that take care of this for us...
```js
// .keys()
Object.keys( car );
```

### Exercise

Create a variable named `wdiStudent` and assign it to an object literal.

1. Give your student at least three properties.
2. One must have a key that contains a hyphen.
3. One must contain an array or object.
4. Update two properties, one of which is the hyphenated.
5. Give your student a new property using dot or bracket notation.
6. Delete one attribute.
7. Iterate through and print out all of the student's key-value pairs.

**Bonus:** Write a function that returns your `wdiStudent` object

> [Solution](https://gist.github.com/nolds9/efdb0a320e7143f42e96)

### Nested Collections

Object properties aren't limited to simple data types. We can also nest collections inside of collections.

```js
var car = {
  make: "Honda",
  model: "Civic",
  year: 1997,

  // An array within an object.
  gears: ["Reverse", "Neutral", "1", "2", "3", "4"],

  // An object within an object.
  engine: {
    horsepower: "6 horses",
    pistons: 12,
    fast: true,
    furious: false
  }
}
```

**Q** In the above examples, how do we access...
* "Neutral" (i.e., array value within an object)?
* "6 horses" (i.e., object value within an object)?

### Break

### You Do: Big Ol' Twitter Object

As this course continues you will encounter plenty of Javascript objects in the wild. Spend **10 minutes** on the following...
* Follow the link below and answer the questions in bold.
* Along with each answer, write down how we would access the property in question.
* Let's do the first one together...

[Twitter JSON Exercise](https://github.com/ga-dc/big_ole_twitter_object)

## Methods

Methods are functions that are attached to some object.

```js
// Our car now has a drive method...
var car = {
  make: "Honda",
  model: "Civic",
  color: "red",
  drive: function(){
    console.log("vroom vroom");
  },

  // Methods can take arguments
  gps: function( location ){
    console.log( "Beep boop, driving to " + location );
  },
  paint: function( newColor ){
    console.log( "Your car has been painted " + newColor );
    car.color = newColor;
  }
}

// We can run the car's two methods like so...
car.drive();
car.paint( "blue" );
console.log( "Car color is: " + car.color );
```

With methods as part of our Javascript toolbox, we now have a cool interface with which we can interact with our objects.
* Why would custom methods be a preferred way to modify object properties vs. using object literal notation?

We've only scratched the surface for objects. We're going to dive much deeper into them later on in the course.

> If you're looking for a sneak peak into the power of objects and functions, we recommend reading [The Secret Life of JS Objects](http://eloquentjavascript.net/06_object.html) chapter in Eloquent JS

## Closing, Q&A, Review LO's

1. Does a function need an input, output, and side-effect to work?
2. What's difference between calling and referencing a function?
3. What's difference between function expressions and declarations?
4. How are objects like dictionaries?
5. What's difference between a property and a method?

## Homework: Calculator

[Javascript Calculator](https://github.com/ga-dc/js-calculator)

## Further Reading / Resources

* [Javascript Scoping and Hoisting](http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html)
* [The Secret Life of JS Objects](http://eloquentjavascript.net/06_object.html)
* [Secrets of the Javascript Ninja](http://webandbeer.com.ar/wp-content/uploads/2014/11/SecretsOfTheJavaScriptNinja.pdf)
* [JS for Cats](http://jsforcats.com/)
* [CoderByte Challenges](https://coderbyte.com/challenges/)
