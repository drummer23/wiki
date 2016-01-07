# Async Programming

Asynchronous programming means that code can be inactive until some trigger event reactivates execution. Execution then continues in a callback.

In principle it's the same as in the browser.

```js
// addEventListener requires a callback as 2nd argument
document.querySelector('button').addEventListener('click', onClick);

function onClick(event) {
  // callback function, only called WHEN there is an event
}
```

This DOM example shows a function that is only **invoked** when the user clicks a button. The click is a form of *input* that triggers an **event**. The `onClick` function is immediately registered as an *event handler*, but only executed **asynchronously**. An event handler is a form of a callback.

The same can be written using anonymous callbacks.

```js
$('button').on('click', function(ev) {
	// callback function, only called WHEN there is an event
});
```

Here's another example of Node.js:

```js
// 2-examples-node/01-server-1b.js
var http = require('http');
http.createServer(function(req, res) {
	res.writeHead(200);
	res.end('You requested ' + req.url);
}).listen(3000);
```

Writing many sequential async tasks using only a pattern of inline anonymous callbacks can quickly lead to problems ("Callback Hell"). It's a good idea to work with named functions, that are kept small.

There are additional approaches to solving problems with async programming including usage of async helper libraries like Async.js and Q (Promises).

Here's the http server written with a more descriptive syntax, without an inline callback.

```js
// 2-examples-node/01-server-2.js
var http = require('http');
var server = http.createServer();

var onRequest = function handleRequest(req,res) {
	res.writeHead(200);
	res.end('You requested '+ req.url);
};

server
	.listen(3000)
	.on('request', onRequest)
;
```

Again `onRequest` is a callback that is only invoked once a request is received.
