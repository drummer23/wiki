#Arrays

In JS Arrays are actually objects too
```js
var cars = [‘vw’,’audi’,’bmw’];
car.push(‘opel);   //adds element
```

#Objects

Objects are **collections of properties as keys and values**. A property can reference another object or a primitive

they are just like arrays, but every value is named

```js
var car = {
	//key  : value
	brand  : ‘audi’,
    engine : ‘1.8’
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

##Prototypes

Every JavaScript object also has a special additional attribute: a pointer to another object. This is called the object’s prototype. **If you create an objects, JavaScript automaticly adds a prototype to it.**

New Objects automaticly inherit from Object. Therefore all the the objects have properties [we never assigned to them](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype#Properties).

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

##Inheritance

https://github.com/MarcDiethelm/fe-lectures/blob/master/3-js-advanced/2-prototype.md

If you try to look up a key on an object and it is not found, JavaScript will look for it in the prototype. 


