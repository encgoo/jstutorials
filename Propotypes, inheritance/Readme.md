# Prototype inheritance
```js

    // super class
    let animal = {
        eats: true,
        walk() {
            console.log('Walking');
        }
    };

    let rabbit = {
        // additional member variable
        jumps: true,
        // super class like this?
        __proto__: animal
    }
```

# F.prototype
This is an alternative of __proto__ above.

# Native prototype
Default prototype of an object?