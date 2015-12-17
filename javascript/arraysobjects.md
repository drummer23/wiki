#Arrays

```js
var cars = [‘vw’,’audi’,’bmw’];
car.push(‘opel);   //adds element
```

#Objects

like array, but every value is named

```js
var car = {brand: ‘audi’, engine: ‘1.8T’};
car.wheels = 4; //set additional property
````

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