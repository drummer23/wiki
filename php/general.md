#General

##Scopes

PHP has 3 scopes:
- global
- function
- class

There is **no block scope**. Variables defined in a Loop for example are accessible outside/after the loop.

To access global variables, use keyword global or superglobal `$GLOBALS` array

##Language Constructs

also called Keywords. Some of them look like functions, but there not!
- echo
- break
- while
- continue
- return
- die()*
- ………

*The output of die is returned to the process that called the script

##Control Structures

`if` `else` `? :` `switch` `while`  `do while` `for`
`break` `continue`

###Foreach
```php
foreach (array_expression as $key => $value)
    statement
```

##Variables & Constants
- are both case sensitive
- use `isset` to check for variable
- constant can only hold scalar types