#Promises

https://github.com/kriskowal/q

If a function cannot return a value or throw an exception without blocking, it can return a promise instead. **A promise is an object** that represent the return value or the thrown exception that the function may eventually provide.

Promises have a `then` method, which you can use to get the eventual return value (fulfillment) or thrown expextion (recection).

```js
promiseMeSomething()
.then(function (value) {
}, function (reason) {
});
```

If `promiseMeSomething` returns a promise that gets fulfilled later with a return value, the first function (the fulfillment handler) will be called with the value. However, if the `promiseMeSomething` function gets rejected later by a thrown exception, the second function (the rejection handler) will be called with the exception.