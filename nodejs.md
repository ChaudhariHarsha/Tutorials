### 1 what is Dispatcher 
It facilitates interaction between objects in Node. A Dispatcher is a service object that is used to ensure that the Event is passed to all relevant Listeners


### 3 How to Use Buffers in Node.js

#### Why Buffers?
Pure JavaScript, while great with unicode-encoded strings, does not handle straight binary data very well. This is fine on the browser, where most data is in the form of strings. However, Node.js servers have to also deal with TCP streams and reading and writing to the filesystem, both of which make it necessary to deal with purely binary streams of data.

#### What Are Buffers?
The Buffer class in Node.js is designed to handle raw binary data. Each buffer corresponds to some raw memory allocated outside V8. Buffers act somewhat like arrays of integers, but aren't resizable and have a whole bunch of methods specifically for binary data


##### Where You See Buffers:
In the wild, buffers are usually seen in the context of binary data coming from streams, such as fs.createReadStream.


### 4 what is event emiter 

EventEmitter class, which we'll use to handle our events
You initialize that using
```
const EventEmitter = require('events');

const eventEmitter = new EventEmitter();
```

This object exposes, among many others, the on and emit methods.

emit is used to trigger an event
on is used to add a callback function that's going to be executed when the event is triggered

```
eventEmitter.on('start', () => {
  console.log('started');
});
```
```
eventEmitter.emit('start');
```

### 4 how to create node js server without express 
```
var http = require('http'); // 1 - Import Node.js core module

var server = http.createServer(function (req, res) {   // 2 - creating server

    //handle incomming requests here..

});

server.listen(5000); 
```

##### with express 
```
const express  = require('express');
const app = express();
app.listen(port,()=>{
    console.log(`server Running on http://localhost:${port}`);
});

```


#### turio 
Turio™ system management server


### what is cluster  in nodejs 

Clusters of Node.js processes can be used to run multiple instances of Node.js that can distribute workloads among their application threads. When process isolation is not needed, use the worker_threads module instead, which allows running multiple application threads within a single Node.js instance.

The cluster module allows easy creation of child processes that all share server ports.


###  waht is worker_threads 

worker_threads module instead, which allows running multiple application threads within a single Node.js instance.
The node:worker_threads module enables the use of threads that execute JavaScript in parallel. To access it:


```
const worker = require('node:worker_threads');

```
#### What is Node.js Event Loop?

 Due to the fact that JavaScript is single-threaded i.e. it performs only a single process at a time, so it is the Event Loop that allows Node.js to perform non-blocking I/O operations. 

#### Working of Event Loop?

 At the start of a JavaScript program, an event loop is initialized. There are several operations that execute in an event loop. Below is the sequence in which different they are executed in a single iteration of the event loop. These operations are processed in a queue.

```
timers–>pending callbacks–>idle,prepare–>incoming connections(poll,data,etc)–>check–>close callbacks
```

##### setImmediate() vs setTimeout()
setImmediate() and setTimeout() are similar, but behave in different ways depending on when they are called.

setImmediate() is designed to execute a script once the current poll phase completes( on check Phase it invoked) .
setTimeout() schedules a script to be run after a minimum threshold in ms has elapsed.

##### setImmediate() 
On a check event cycle setImmediate() callbacks are invoked 

##### process.nextTick() 
process.nextTick() fires immediately on the same phase

```
function apiCall(arg, callback) {
  if (typeof arg !== 'string')
    return process.nextTick(
      callback,
      new TypeError('argument should be string')
    );
}
```

##### process.nextTick() vs setImmediate()
We have two calls that are similar as far as users are concerned, but their names are confusing.

process.nextTick() fires immediately on the same phase
setImmediate() fires on the following iteration or 'tick' of the event loop

In essence, the names should be swapped. process.nextTick() fires more immediately than setImmediate(),


```
setImmediate(function A() {
    console.log("1st immediate");
});
 
setImmediate(function B() {
    console.log("2nd immediate");
});
 
process.nextTick(function C() {
    console.log("1st process");
});
 
process.nextTick(function D() {
    console.log("2nd process");
});
 
// First event queue ends here
console.log("program started");
```

The output will be 

```
program started
1st process
2nd process
1st immediate
2nd immediate

```

