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