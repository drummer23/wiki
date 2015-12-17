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

##Variables

- are typeless.
- type conversion works implicit likewise in php
- are either global or scoped to function
- variables are function scoped, instead of block scoped compared to other languages

Use `var` for declaration (with value undefined) :
```js
var someVariable;
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
``
