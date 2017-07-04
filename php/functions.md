# Functions

All functions in PHP return a value. If you don't return a value, PHP will return null.

## Variable Scope

PHP has 3 scopes: global, function and class.

If you declare a vaiable outside of a function or class, that varibable is in the global scope. Every time you enter a function, PHP creates a new, clean scope..

## Arguments

You can pass any number of arguments regardless of how many specified in function declaration. **Optional Arguments** can have default Values an must be right-most to make sense

```php
function hello($who = "World")
```

To pass by reference use the by-reference operator &

## Type Hinting

Type Hints can force **Parameters of Functions** to be a certain type. Otherwise it raises a catchable error.

Works for Objects, Array but not for Scalar Types
```php
function ForceArray (array $a)
```
