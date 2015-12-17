#Functions

##Declaration

- A function is declared with the `function` keyword
- A function always **returns** a value. It can be set with the `return` keyword. Otherwise its undefined.

```js
function myFunc(a, b) {
	return a + b;
}

myFunc(2,6); //returns 6
```


##Function Expression

A function Expression defines a Java-Script Function, and the Value of that Expression is this function, which can be assigned to a variable and also returned by other functions.

defines a function and assign it to square (aka defines a function named square)

```js
var fn = function square(x) { return x * x; }
fn(3); //returns 9

var fn2 = function getFn() { return fn; }
fn2()(3) // returns 9
```

##Anonymous Functions

A function can be defined without naming it

```js
var fn = function() {};
``