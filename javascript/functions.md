#Functions

##Declaration

- A function is declared with the `function` keyword
- A function always **returns** a value. It can be set with the `return` keyword. Otherwise its undefined.

```js
function myFunc(a, b) {
	return a + b;
}

myFunc(2,6); //returns 8
```

##Function Parameters

To check with which parameters a functions has been called, use `arguments` inside any function

https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/arguments

##Function Expression

A function Expression defines a Java-Script Function, and the Value of that Expression is this function, which can be assigned to a variable and also returned by other functions.

defines a function and assign it to square (aka defines a function named square)

```js
var fn = function square(x) { return x * x; }
fn(3); //returns 9

var fn2 = function getFn() { return fn; }
fn2()(3) // returns 9
/* this function call needs two sets of parenthesis - first executes fn2, second       executes fn. without the parenthesis the functions would not be executed */
```

##Anonymous Functions

A function can be defined without naming it

```js
var fn = function() {};
```

##IIFE

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
