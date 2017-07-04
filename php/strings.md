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
