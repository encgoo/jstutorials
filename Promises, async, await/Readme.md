# Introduction: callbacks
The `setTimeout` function discussed before is an async function. It must be running in a backgroudn thread. The main thread keeps track of the time used, and terminate the background thread if times out. 

# other async events
A new script can be set to the html document. _Once_ it is set, the script will be run by the browser. This is async. See the [example](./src/asyncSource.html). If we need to call from the newly added script, we need to wait for the loading. onload is an async event handler.
onerror can be used with async.

# Promise
A promise is a special JS object that works like a message/subscription list. 
The above example can be [re-rewritten using promise](./src/promise.html).

Basically create a Promise object.
```js
    let promise = new Promise(function(goodFunc, badFunc){
        // do whatever we need.
        // There will be some async events as the result of the above steps.

        // For a normal async event, call good goodFunc
        // for example documentElement.onload = () => {goodFunc(something)};

        // For an error event, call badFunc
        // for example documentElement.onerror = () => {badFunc(new Error('Failed');};

    })
```
The promise created above can be used in .then
```js
    promise.then(
        // first is a funcion for normal return. This is basically the goodFunc above
        // It takes one input argument
        (something) => {
            // promise is done successfully. We can use whatever promised.
        },
        // second argument is a function for bad return. This is basically the badFunc above
        (error) => {
            // something bad, we didn't get whatever promised.
            console.log(error);
        }
    )
```

# Promise chain
One example is the fetch(url) call. One fetch after another fetch is a promise chain.

# Error handling with promise
```js
    ftech('https://someweb.com').then((response) =>{
        // do something if we get a response successfully
    }).catch((err) => {
        // do something if we get an error.
    })
```

# Promise API
## Promise.all
We want many promises to excute in parallel and wait until _all_ of them are ready. It goes like this:
```js
    let promise1 = new Promise(function(resolve) {

    });
    let promise2 = new Promise(function(resolve){

    })

    let promisAll = Promise.all([promise1, promise2]);

    promiseAll.then((something) => {

    });
```
One example is to handle multiple fetch.
```js
Promise.all([
    fetch(url1),
    fetch(url2),
    fetch(url3)]);
```
Note that if promises are grouped like this into Promise.all, a failure in _any_ promise will fail the whole thing.

## Promise.allSettled (recent addition of JS)
Promise.all means "all or nothing". Promise.allSettled just waits for all to be done, failure or success.
See [example](https://javascript.info/promise-api).

## Promise.race
Wait for the first to settle.

## Promise.any
First successful.

## Promise.resolve/reject
Not commonly used. See async/wait

# Promisification
Async events can be handled by callbacks. As in section 2 above, the onload event is an async event, and we can provide a callback function to handle that event.

Here is a good [refernece](https://www.freecodecamp.org/news/write-your-own-promisify-function-from-scratch/).

As a practice, here it is shown [how to promisify by wrapping callback](./src/promisification.html).

# Microtasks
Promise handlers .then/.catch/.finally are async.

To manage the async task, a FIFO queue is used

## Microtasks queue

The hanlders from a promise are inserted into the microtasks queue. The JS engine finish the current code block first, and then starts to execute the tasks in the queue.

## Unhandled rejection

# async/await

This is supposed to help Promise to become easier for users.

## aync keyword
A function can be declared as async
```js
    async function foo(){

    }
```
An async function returns a Promise.

## await keyword
Inside an async function, we can await for a promise to settle. Check async with and without await in [this](./src/async_await.html).

 * async is good to hanlde other async functions. 
 * await or not, once async with promise, there is always a background thread running. 
    * await essentially just moves the then handler into the async function. 
    * the good thing is that it flatten the async function in some sense. Imagine an async function that calls several other async funcitons, and it needs to do them sequentially. Without the await keyword, nested of .then handlers are needed. With await, we can just await for each promise. Then no then handler is needed. 
    * this is also the reason why await can only be inside an async function. After the _first_ await, the execution already returns back to the caller (main thread). Whatever left in the async function will be done in a background thread. In a sync function, this can be done. 

## time-slicing
Even though the above sounds like multi-threaded/parallel/concurrent, it is more like time-slicing. WHen promises are used, all the .then handlers are pushed into the Microtask queue. The caller (sync) function foo will be finished first, without getting into the .then handlers. Then the .then handlers in the microtasks queue will be executed one by one. This explains why the caller code 'after' the .then handler is _always_ executed first before the .then handler code, even if the promise takes no time to finish. The order here is deterministic, not like a real multi-threaded env. 
```js
function foo(){
    const url = 'https://cnn.com';
    let prmse = fetch(url);
    prmse.then(
        (resp) => {
            console.log(resp);
        }
    )
    console.log('This will be executed first before the .then handler above');
}
```
JS in a browser env is event driven. Async means it is waiting for another event. So in some sense, a sync function is also an event handler. It might be in the Microtasks queue as well. The difference between sync/async functions is that the former one tells the caller that it handles everything, nothing else to worry about. The latter one says there are .then/.catch events to handle later on. 




