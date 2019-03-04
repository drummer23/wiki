# Javascript

# Table of Contents

1. [General](#general)
2. [Types](#types)
3. [Arrays & Objects](#objects)
4. [Functions](#functions)
5. [Async](#async)
6. [Promises](#promises)
7. [Debugging](#debugging)

<a name="general"></a>
# General

JavaScript is CaseSensitive.

Comments:
```js
// comment
/* comment */
```

## Scopes

Javascript has 2 scopes:

- Global
- Function

## Strict Mode

```js
‘use strict’;
```

## The Global Object

When the Script Interpreter starts (Web browser), it creates a Global Object

- Global Properties and Functions (e.g. undefined or parteInt())
- Constructor Functions like Date(), Array()
- Global Objects like Math and JSON
- Your own global Variables.

use `window` in the Browser or `global` in Node.js to access the global object. On the top layer you can also use `this`

## Expressions

An Expression is simply an statement, which the Interpreter can evaluate to an value.

```js
"hello", 1,23, i
```

## Variables

- are typeless.
- type conversion works implicit likewise in php
- are either global or scoped to function
- variables are function scoped, instead of block scoped compared to other languages

Use `var` for declaration (with value undefined) :
```js
var someVariable;
```

### Hoisting

https://www.kenneth-truyers.net/2013/04/20/javascript-hoisting-explained/

In Javascript, you can have multiple var-statements in a function. All of these statements act as if they were declared at the top of the function. Hoisting is the act of moving the declarations to the top of the function.

In this example, the declaration of myvar inside the function is hoisted to the top of the function. Meaning `var myvar`is executed first and therefore has value undefined at the first alert.

```js
var myvar = "global variable";

function mymethod(){
    alert(myvar);   // expected "global variable", result: undefined
    var myvar = "local variable";
    alert(myvar); // local variable
}

mymethod();
```
**Best practice**: Always declare variables first


<a name="types"></a>
# Types

In JavaScript everything is a primitive value (aka scalar) or an object.

```js
var undVar;
console.log(typeof undVar); //-> undefined

var bolVar = true;
console.log(typeof bolVar); // -> boolean

var numVar = 7;
console.log(typeof numVar); // -> number

var strVar = 'hello';
console.log(typeof strVar); // -> string

var arrVar = ['a','b','c'];
console.log(typeof arrVar); // -> object

var objVar = {a : 'a', b: 'b'};
console.log(typeof objVar); // -> object
```

## Scalar Types

- Strings
  - use ‘ or “ or a combination to embed strings in string
  - use \ to escape
  - use + to concatenate
- Numbers
  - Math Operations outside bounds or division by 0 returns infinity or nun
- Bools
- Undefined/Null
 - not initialised variables or non-existent properties return undefined (aka typeof undefined)

## Objects

[see Chapter Objects]((#objects))

## Typeof

Use `typeof` to check for type

```js
if (‘string’ !== typeof paramString)
```

## False

The Following 7 values are the only one converted to false in Javasript

- false
- undefined
- null
- 0
- -0
- NaN
- "" // Der leere String

<a name="objects"></a>
# Arrays

In JS Arrays are actually objects too
```js
var cars = [‘vw’,’audi’,’bmw’];
car.push(‘opel);   //adds element
```

# Objects

Objects are **collections of properties as keys and values**. A property can reference another object or a primitive

they are just like arrays, but every value is named

```js
var car = {
	//key  : value
	brand  : 'audi',
    engine : '1.8',
    upgrade : function() {
    	this.engine = '2.0';
    }
};

car.wheels = 4; //add property after creation
```

nested:

```js
var square = { upperLeft: { x:2, y:2 },
			   lowerRight: {x: 4, y: 5} };
```

read properties (both are equal)

```js
car.brand;
car[“brand"];
```

## Prototypes

Every JavaScript object also has a special additional attribute: a pointer to another object. This is called the object’s prototype. If you create an object using **literals**, JavaScript automaticly adds `Object` as prototype to it.

New objects automaticly inherit from `Object`. Therefore all the the objects have properties [we never assigned to them](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype#Properties).

```js
// primitive
var string = 'blue';
// object
var object = {};

console.log(typeof object.toString); // => function
console.log(typeof object.valueOf); // => function
console.log(typeof string.length); // => number (when accessing a primitive like an object, it is converted to object to get a result)
```


To create an object and set prototype exlicit, use `Object.create()`
```js
var fruit = Object.create(null);
var apple = Object.create(fruit);
```

Use `getPrototypeOf` to access the Prototype. In this example we have to use `Object.getPropertyOf` because `fruit` haven't been created from `Object`
```js
Object.getPrototypeOf(apple)
```
*There is a difference between the property `prototype` and `__proto__`. The property can be set to anything whereas the later is fail safe (draft - evaluate this)*

## Inheritance

https://github.com/MarcDiethelm/fe-lectures/blob/master/3-js-advanced/2-prototype.md

If you try to look up a key on an object and it is not found, JavaScript will look for it in the prototype. And if not found there it will look in the prototypes prototype and so on. It will follow the **“prototype chain”** until the prototype is null instead of an object. In that case, it returns undefined.

**A property on a Child will have its Parents value until explicit set on the Child. A property set on a child will not be set on its Parent**

Use `hasOwnProperty` to check if property is defined on this very Object

## Constructor

todo

<a name="functions"></a>
# Functions

## Declaration

- A function is declared with the `function` keyword
- A function always **returns** a value. It can be set with the `return` keyword. Otherwise its undefined.

```js
function myFunc(a, b) {
	return a + b;
}

myFunc(2,6); //returns 8
```

## Function Parameters

To check with which parameters a functions has been called, use `arguments` inside any function

https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/arguments

## Function Expression

A function Expression defines a Java-Script Function, and the Value of that Expression is this function, which can be assigned to a variable and also returned by other functions.

defines a function and assign it to square (aka defines a function named square)

```js
var fn = function square(x) { return x * x; }
fn(3); //returns 9

var fn2 = function getFn() { return fn; }
fn2()(3) // returns 9
/* this function call needs two sets of parenthesis - first executes fn2, second       executes fn. without the parenthesis the functions would not be executed */
```

## Anonymous Functions

A function can be defined without naming it

```js
var fn = function() {};
```

## IIFE

IFFE is a pattern for encapslulation using function scope

How it works:
Code is encapsulated within an anonymous function, which is immediately called/invoked. The main benefit is that this Code stays out of the Global Scope

In this example, the anonymous function is defined on the first line ```(function(){})```, and invoked on the second to last line ```();```. Therefore ```privateVar``` is not defined on the Global Scope.

```js
(function() {
	var privateVar = 'private';
    console.log(typeof privateVar); // => string
})();
console.log(typeof privateVar); // => undefined
```

**Another benefit is that you can assure aliases**. For example as alot of frameworks uses ```$``` as an alias, this construct assures its an alias for jQuery inside the IIFE

```js
(function($) {
	//...
})(jQuery);
```

The IFEE Pattern is based on the Closure principe:
https://de.m.wikipedia.org/wiki/Closure_(Funktion)


## Callbacks

A callback function is a function passed as a parameter to another function. The passed function is not executed directly but when the other function **calls(-back)** it

```js

console.log(typeof console.log); // => function

function someFunction(fn, x) {
	//does something...

    //callback
    fn(x);
}

someFunction(console.log, 'hello');

```
see chapter [async](async.md) for more about callbacks


<a name="async"></a>
# Async Programming

Asynchronous programming means that code can be inactive until some trigger event reactivates execution. Execution then continues in a callback.

In principle it's the same as in the browser.

```js
// addEventListener requires a callback as 2nd argument
document.querySelector('button').addEventListener('click', onClick);

function onClick(event) {
  // callback function, only called WHEN there is an event
}
```

This DOM example shows a function that is only **invoked** when the user clicks a button. The click is a form of *input* that triggers an **event**. The `onClick` function is immediately registered as an *event handler*, but only executed **asynchronously**. An event handler is a form of a callback.

The same can be written using anonymous callbacks.

```js
$('button').on('click', function(ev) {
	// callback function, only called WHEN there is an event
});
```

Here's another example of Node.js:

```js
// 2-examples-node/01-server-1b.js
var http = require('http');
http.createServer(function(req, res) {
	res.writeHead(200);
	res.end('You requested ' + req.url);
}).listen(3000);
```

Writing many sequential async tasks using only a pattern of inline anonymous callbacks can quickly lead to problems ("Callback Hell"). It's a good idea to work with named functions, that are kept small.

There are additional approaches to solving problems with async programming including usage of async helper libraries like Async.js and Q (Promises).

Here's the http server written with a more descriptive syntax, without an inline callback.

```js
// 2-examples-node/01-server-2.js
var http = require('http');
var server = http.createServer();

var onRequest = function handleRequest(req,res) {
	res.writeHead(200);
	res.end('You requested '+ req.url);
};

server
	.listen(3000)
	.on('request', onRequest)
;
```

Again `onRequest` is a callback that is only invoked once a request is received.


<a name="promises"></a>
# Promises

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
https://github.com/kriskowal/q

A Promise represents an operation that hasn't completed yet, but is expected in the future.

If a function cannot return a value or throw an exception without blocking, it can return a promise instead. **A promise is an object** that represent the return value or the thrown exception that the function may eventually provide.

It allows you to associate **handlers** to the asynchronous action's eventual success value or failure reason

## Declaration

The Promise Constructor takes a Function object with two arguments resolve and reject. The first argument fulfills the promise, the second argument rejects it. We can call these functions once our operation is completed.

```js
new Promise(executor);
new Promise(function(resolve, reject) { /* blocking operation */ });
```

## State

A Promise is in one of these states:

- pending: initial state, not fulfilled or rejected.
- fulfilled: meaning that the operation completed successfully.
- rejected: meaning that the operation failed.

## Handling

Promises have a `then` method, which you can use to get the eventual return value (fulfillment) or thrown expextion (recection).

```js
promiseMeSomething()
.then(function (value) {
}, function (reason) {
});
```

If `promiseMeSomething` returns a promise that gets fulfilled later with a return value, the first function (the fulfillment handler) will be called with the value. However, if the `promiseMeSomething` function gets rejected later by a thrown exception, the second function (the rejection handler) will be called with the exception.

## Example

```js
// i'll do something and than either call fulfillment or rejection handler
var promiseMeSomething = new Promise(function(fulfillmentHandler, rejectionHandler) {
    /* some blocking code ...
       therefore wrapped in a promise */

    //defines if function worked
    var worked = false;

    if (worked) {
        fulfillmentHandler('7');
    } else {
        rejectionHandler('error 213');
    }
});

// alright - do it, when your finished call one of those functions i give you
promiseMeSomething.then(callbackFulfill, callbackReject);

//fulfillmentHandler
function callbackFulfill(value) {
    console.log('Value is ' + value);
}

//rejectionHandler
function callbackReject (reason) {
    console.log('Reason is ' + reason);
}
```


<a name="debugging"></a>
# Debugging

```js
console.dir; //prints an object
debugger;    //stops for debugging at this line
arguments;   //prints arguments of current function
```
