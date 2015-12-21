#Promises

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
https://github.com/kriskowal/q

A Promise represents an operation that hasn't completed yet, but is expected in the future.

If a function cannot return a value or throw an exception without blocking, it can return a promise instead. **A promise is an object** that represent the return value or the thrown exception that the function may eventually provide.

It allows you to associate **handlers** to the asynchronous action's eventual success value or failure reason

## Declaration

The Promise Constructor takes a Function object with two arguments resolve and reject. The first argument fulfills the promise, the second argument rejects it. We can call these functions once our operation is completed.

```js
new Promise(executor);
new Promise(function(resolve, reject) { /* blocking operation */ });
```

##State

A Promise is in one of these states:

- pending: initial state, not fulfilled or rejected.
- fulfilled: meaning that the operation completed successfully.
- rejected: meaning that the operation failed.

##Handling

Promises have a `then` method, which you can use to get the eventual return value (fulfillment) or thrown expextion (recection).

```js
promiseMeSomething()
.then(function (value) {
}, function (reason) {
});
```

If `promiseMeSomething` returns a promise that gets fulfilled later with a return value, the first function (the fulfillment handler) will be called with the value. However, if the `promiseMeSomething` function gets rejected later by a thrown exception, the second function (the rejection handler) will be called with the exception.

##Example

```js
// i'll do something and than either call fulfillment or rejection handler
var promiseMeSomething = new Promise(function(fulfillmentHandler, rejectionHandler) {
    /* some blocking code ...
       therefore wrapped in a promise */

    //defines if function worked
    var worked = false;

    if (worked) {
        fulfillmentHandler('7');
    } else {
        rejectionHandler('error 213');
    }
});

// alright - do it, when your finished call one of those functions i give you
promiseMeSomething.then(callbackFulfill, callbackReject);

//fulfillmentHandler
function callbackFulfill(value) {
    console.log('Value is ' + value);
}

//rejectionHandler
function callbackReject (reason) {
    console.log('Reason is ' + reason);
}
```