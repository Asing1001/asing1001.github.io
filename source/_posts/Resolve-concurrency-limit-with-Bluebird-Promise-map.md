---
title: Resolve concurrency limit with Bluebird-Promise.map
date: 2018-05-10 22:26:48
tags: [Bluebird, Promise, ECONNRESET]
---

## ECONNRESET when making thousands requests

In situation doing thousands of http requests, it is easy to get error `ECONNRESET`, for example :

```javascript
require('isomorphic-fetch');

const promises = []
for(var i=0; i<10000; i++){
    promises.push(fetch('http://example.com/'+i));
}

const results = await Promise.all(promises)
```

<!--more-->
After few seconds, error `ECONNRESET` show up like this, due to too many request processing at a time :

```terminal
(node:836) UnhandledPromiseRejectionWarning: FetchError: request to http://example.com/315 failed, reason: read ECONNRESET
warning.js:18
    at ClientRequest.<anonymous> (e:\Coding\00.Project\appCrack\node_modules\node-fetch\index.js:133:11)
    at emitOne (events.js:116:13)
    at ClientRequest.emit (events.js:211:7)
    at Socket.socketErrorListener (_http_client.js:387:9)
    at emitOne (events.js:116:13)
    at Socket.emit (events.js:211:7)
    at emitErrorNT (internal/streams/destroy.js:64:8)
    at _combinedTickCallback (internal/process/next_tick.js:138:11)
    at process._tickCallback (internal/process/next_tick.js:180:9)
```

## Set concurrency with Bluebird Promise.map

[Bluebird Promise.map](http://bluebirdjs.com/docs/api/promise.map.html) has a `concurrency` option to deal with this issue, here is syntax from Blubird documentation :

```javascript
Promise.map(
    Iterable<any>|Promise<Iterable<any>> input,
    function(any item, int index, int length) mapper,
    [Object {concurrency: int=Infinity} options]
) -> Promise
```

To use it, pass your `Iterable item` in first parameter, `Callback function receive item return promise` as second parameter, `concurrency` as third parameter, for example :

```javascript
require('isomorphic-fetch');
const Promise = require("bluebird");

const numbers = []
for (var i = 0; i < 10000; i++) {
    numbers.push(i);
}

const results = await Promise.map(numbers,
    number => fetch('http://example.com/' + number),
    { concurrency: 30 }
)

// no error occur !!
```

## Alternatives

You could also use [es6-promise-pool](https://github.com/timdp/es6-promise-pool), [promise-limit](https://github.com/featurist/promise-limit) or [async/queue](http://caolan.github.io/async/docs.html#queue) to deal with large amount of http requests.

## Reference

http://bluebirdjs.com/docs/api/promise.map.html
https://github.com/timdp/es6-promise-pool