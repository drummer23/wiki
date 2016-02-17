#General

##Methods

There are two Kind of jQuery Methods:

- `$()` jQuery object methods ($.fn namespace). Automatically receive and return the selection as **this**

- `$` jQuery core methods. Not act on a selection (jQuery namespace)

##Document Ready

`$()` is the shorthand for `$(document).ready()`

##Selector

jQuery **always returns an jQuery object**, even if the selector doesn’t match anything. The object is wrapping any element(s) that match.

Test whether selection contains elements:
```js
if ( $("div.foo").length)
```

Save selections for performance issues:
```js
var divs = $("div");
```

Chaining:
```js
$("#content").find("h3).eq(2).html("hello");
```

Refine Selections:
```js
$("div.foo).has("p") //div.foo elements that contain <p> tags
$("h1").not(.bar) //h1 that don’t have class bar
$("ul li").filter(".current") //unordered list item with class current
```
more filtering: `.first()`, `.eq()` …

##Getters & Setters

```js
$("h1").html ( "hello world"); //setter
$("h1).html(); //getter
```
