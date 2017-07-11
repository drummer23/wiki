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

*When an element is added to an array without key, PHP assigns a numeric one that is plus one to the greatest numeric existing key

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

```array_walk``` can be used to perform an iteration of an array in which a user defined function is called (callback function)

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
