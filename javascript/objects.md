# Arrays

In JS Arrays are actually objects too
```js
var cars = [‘vw’,’audi’,’bmw’];
car.push(‘opel);   //adds element
```

# Objects

Objects are **collections of properties as keys and values**. A property can reference another object or a primitive

they are just like arrays, but every value is named

```js
var car = {
	//key  : value
	brand  : 'audi',
    engine : '1.8',
    upgrade : function() {
    	this.engine = '2.0';
    }
};

car.wheels = 4; //add property after creation
```

nested:

```js
var square = { upperLeft: { x:2, y:2 },
			   lowerRight: {x: 4, y: 5} };
```

read properties (both are equal)

```js
car.brand;
car[“brand"];
```

## Prototypes

Every JavaScript object also has a special additional attribute: a pointer to another object. This is called the object’s prototype. If you create an object using **literals**, JavaScript automaticly adds `Object` as prototype to it.

New objects automaticly inherit from `Object`. Therefore all the the objects have properties [we never assigned to them](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype#Properties).

```js
// primitive
var string = 'blue';
// object
var object = {};

console.log(typeof object.toString); // => function
console.log(typeof object.valueOf); // => function
console.log(typeof string.length); // => number (when accessing a primitive like an object, it is converted to object to get a result)
```


To create an object and set prototype exlicit, use `Object.create()`
```js
var fruit = Object.create(null);
var apple = Object.create(fruit);
```

Use `getPrototypeOf` to access the Prototype. In this example we have to use `Object.getPropertyOf` because `fruit` haven't been created from `Object`
```js
Object.getPrototypeOf(apple)
```
*There is a difference between the property `prototype` and `__proto__`. The property can be set to anything whereas the later is fail safe (draft - evaluate this)*

## Inheritance

https://github.com/MarcDiethelm/fe-lectures/blob/master/3-js-advanced/2-prototype.md

If you try to look up a key on an object and it is not found, JavaScript will look for it in the prototype. And if not found there it will look in the prototypes prototype and so on. It will follow the **“prototype chain”** until the prototype is null instead of an object. In that case, it returns undefined.

**A property on a Child will have its Parents value until explicit set on the Child. A property set on a child will not be set on its Parent**

Use `hasOwnProperty` to check if property is defined on this very Object

## Constructor

todo
