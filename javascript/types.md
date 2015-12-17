#Types

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