# Generators

Regular functions return one single value (or nothing).

## Generator functions
A generator function can return more than once, using yield.
```js
    funciton* getValues(){
        yield 1;
        yield 2;
        yield 3;
    }
    let generator = getValues();
    for (let val in generator){
        console.log(val);
    }
```
See this [example](./src/generator.html). In some sense, instead of returning an array, just yield the values one by one.

```js
    function* getRange(start, end){
        for (let i = start; i <= end; ++i){
            yield i;
        }
    }
```
The difference here is the execution sequence. When a function contains yields, it is _not_ excuted when it is called. It is executed only when the (returned) generator is iterated. 

## yield is a two-way street
Caller of the generator can pass argument back to the yield generator.
```js
    function* genRange(start, end){
        for (let i = start; i <= end; ++i){
            let ret = yield i;
            console.log(ret);
        }
    }
    let gen = genRange(1, 100);
    // passing a value to yield generator
    let val = gen.next(1);
```

## generator.return
Caller can stop the yield sequence prematurally, by calling generator.return.

# Async iteration and generators

## iteratables

See [how to overload the iterator operator of a Symbol](./src/gen_overload.html). First, it needs to be an Object. 

## Async iterables

Overload Symbol.asycIterator.

## Using generator
This is simpler. 

## Async generator
If each yield is async, then we need to overload the asyncIterator. Then we need async iteration/for-loop.
```js
    for await (let i of asyncIterable){

    }
```