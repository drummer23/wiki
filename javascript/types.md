#Types

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

##Scalar Types

- Strings
  - use ‘ or “ or a combination to embed strings in string
  - use \ to escape
  - use + to concatenate
- Numbers
  - Math Operations outside bounds or division by 0 returns infinity or nun 
- Bools
- Undefined/Null
 - not initialised variables or non-existent properties return undefined (aka typeof undefined)

##Objects

[Chapter Objects](objects.md)

##Typeof

Use `typeof` to check for type

```js
if (‘string’ !== typeof paramString)
```

##False

The Following 7 values are the only one converted to false in Javasript

- false
- undefined
- null
- 0
- -0
- NaN
- "" // Der leere String