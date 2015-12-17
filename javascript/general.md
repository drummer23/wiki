#General

JavaScript is CaseSensitive.

Comments:
```js
// comment
/* comment */
```

##Scopes

Javascript has 2 scopes:

- Global
- Function

##Strict Mode

```js
‘use strict’;
```

## The Global Object

When the Script Interpreter starts (Web browser), it creates a Global Object

- Global Properties and Functions (e.g. undefined or parteInt())
- Constructor Functions like Date(), Array()
- Global Objects like Math and JSON
- Your own global Variables.

use `window` or `this` if on top layer to access the global object.

## Expressions

An Expression is simply an statement, which the Interpreter can evaluate to an value.

```js
"hello", 1,23, i
```

##Variables

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