- [ General ](#general) 
- [ Types ] (#types)
- [ Operators ] (#operators)
- [ Functions ] (#functions)
- [ Arrays ] (#arrays)
- [ String ] (#strings)
- [ Classes ] (#classes)
- [ Errors ] (#error)

<a name="general"></a>
# General

## Scopes

PHP has 3 scopes:
- global
- function
- class

There is **no block scope**. Variables defined in a Loop for example are accessible outside/after the loop.

To access global variables, use keyword global or superglobal `$GLOBALS` array

## Language Constructs

also called Keywords. Some of them look like functions, but there not!
- echo
- break
- while
- continue
- return
- die()*
- ………

*The output of die is returned to the process that called the script*

## Control Structures

`if` `else` `? :` `switch` `while`  `do while` `for`
`break` `continue`

### Foreach
```php
foreach (array_expression as $key => $value)
    statement
```

## Variables & Constants
- are both case sensitive
- use `isset` to check for variable
- constant can only hold scalar types


<a name="types"></a>
# Types

## Scalars

Data Types with as single value. In PHP these are

- boolean
- int
- float
- string

Numeric types sometimes behave unexpected when it comes to Calculation. Use Extension BCMath for arbitrary precise functions


<a name="operators"></a>
# Operators

most are binary (2 operands where operator sits in the middle)

## Assignment Operators

`=` `+=` `-=` `.=`

## Arithmetic Operators

`+` `-` `*` `/` `%` `++` `-`

## String Operators

`.`

## Comparison Operators

`==` `!=` `===` `!==`
`>` `>=` `<` `<=`

- **Equal** Operators `==` TRUE if equal after type juggling
- **Identical** Operators `===`TRUE if equal and same type

for type safe comparison use `===` and `!==`

```php
0 == null // evalutates to true!!
0 === null // evaluates to false
```

## Logical Operators

Logical Operators check from **left to right**, and only go further if necessary. `!`  is an unary operator

`!` `&&` `||` `XOR`


<a name="functions"></a>
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

<a name="arrays"></a>
# Array

Array Consist of ```key => value```

## Create

```php
$fruits = array();
$fruits = array('a' => 'apple', 'b'=> 'banana')

// as of PHP 5.4
$fruits = [];
$fruits = ['b' => 'banana'];
```

## Add

```php
$fruits['a'] = 'apple',
$fruits[] = 'orange'; *
```

*When an element is added to an array without key, PHP assigns a numeric one that is plus one to the greatest numeric existing key*

**Add Element in the middle** of use ```splice```. Use ```array_values``` to generate a new array with fresh, continues Keys.

## Print

Print an array using var_dump or print_r

## Array Functions

Arrays are the most powerfull data management tool in PHP. Knowing when to use built-in function and when to write your own array manipulation is very important: because array are sometimes get large, **built-in functions provide significant performance over user written code**

```php
count()             // size of an array
is_array()          // variable contains an array
array_key_exists()  // does an key exist
in_array()          // does an value exist
unset(key)          // remove element from array
array_reverse()     // invert the order of array elements
array_values()      // returns just values
array_keys()        // returns just keys

```

### Passive Iteration

`array_walk` can be used to perform an iteration of an array in which a user defined function is called (callback function)

### Sorting

```php
sort()/asort        // sort array / keep keys
natsort()           // adv sorting for values like 10t,1t
ksort()             // sort by keys
usort()/uasort()	// sort by user defined function
shuffle()           // anti-sort

```

### Stacks and Queues

Stack: Last In/First Out   - use ```array_push``` and ```array_pop```
Queue: First In, First Out - use ```array_unshift``` and ```array_shift```

push does the the same as $array[] = $value, but the later is much faster since no function is called. Is should be used unless you need to add more than one value

### Compare

```php
array_diff          //show diffs
array_diff_assoc
array_diff_keys

array_diff_uassoc   //call user-defined callbacks
array_diff_ukey

array_intersect     //show intersections (schnittmenge)
array_intersect_key
```

<a name="strings"></a>
# Strings

## Control Characters / Escaping

```php
echo "\x2a";  //hex for asterix
echo "\n";    //newline
```

## Variable Interpolation

Variables can be embedded directly inside double quotes. Use **braces** for more complex statements

```php
$who = 'world';
$names = ['simon','sven']

echo "Hello $who\n";
echo "User: {$names[0]}[1977]"; //name and year
```

## Basic Functions

```php
strlen()       // determine length
strtr()        // transform characters or replace substring
someString[3]  // access individual characters like members of array
```

## Comparing, Searching and Replacing

`strpos` finds position of substring. in this example its important to use **identity operator**, to distinguish betwen found at positin zero (0) vs not found (false)

```php
if (strpos ($haystack, $needle) !== false) {
	echo 'found;
}
```

`strstr()` work similar to strpos, but returns a string instead of a position. Both are case-sensitive, for case-**i**nsesitive use `stripos` and `stristr`


<a name="classes"></a>
# Classes

## Definiton

```php

class car
{
    const MYCONSTANT = “some value”;
    private $color;

    public function __construct($color = null) {
    	$this->color = $color;
	}

    public function getColor() {
    	return $this->color;
    }

    public function printConstant() {
    	echo self::MYCONSTANT;
    }
}
```

## Instiation

```php
$golf = new car(‘red’);
```

## Instance of
```php
if ($variable instanceof car)
```

<a name="error"></a>
# Error Handling

## Error Types

- Compile-time errors 1
- Fatal Errors 1
- Recoverable errors
- Warnings
- Notices

*1 cannot be trapped*

## Configuration

globaly in php.ini or dynamically within script

```
error_repporting=E_ALL & ~E_NOTICE
display_errors=on
log_errors=on
```
Use set_error_handler to set custom error handler

## Stack Traces

are presented inside->out
first entry is where the exception happened. last entry is where the code finaly abortet

## Handling

```php

try {
	throw new Exception('Something happene');
} catch (Exception $e) {
	echo 'Caught Exception' : ’ . $e->getMessage();
}

```
