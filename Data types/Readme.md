# Number

Use _ in a number
```js
    let a = 1_000_000;
```

## to string
```js
    let a = 3.14;
    let b = a.toString();
```
## round

```js
    let a = 3.1415926;
    let b = a.toFixed(2); // "3.14"
```

# String
# Arrays
## array methods
### splice
Deleting array elements. 
```js
    let a = ['apple', 'banana', 'cantaloupe', 'durian' ];
    a.splice(3,3); /// gets rid of durian
```

### slice
Copy a section of an array.

### filter
```js
    let users = [
        {id: 1, name: "John"},
        {id: 2, name: "Smith"},
        {id: 3, name: "Tom"},
    ];

    let someUsers = users.filter(item => item.id < 3);
}
```
### map
```js
    let users = [
        {id: 1, name: "John"},
        {id: 2, name: "Smith"},
        {id: 3, name: "Tom"},
    ];
    let nameLenghts = users.map(item => item.name.length);
```

### sort with compare callback
```js

```
### reduce
Google map and reduce?

### split and join
Very similar to python

# Iterables
# Map and Set
## Map methods
* new Map() constructor
* map.set(key, value)
* map.get(key)
* map.has(key)
* map.delte(key)
* iterator `(let key of map.keys)`
* map.forEach((key, value, map) =>{})

## Set methods
* new Set() constructor
* set.add(item)
* iterator `(let e of set)`
* set.forEach((value, valueAgain, set) => {})

# WeakMap and WeakSet
Weakly linked to stored values, and allows garbage collection to clear unused members.

#  Object.key, values, entries
Object in somesense is like a map. What are the differences? So like maps, objects can have 
* keys
* values

# Destructuring assignment
## split string into array

# Date and time
Date is a built-in object.
```js
    let now = new Date();
    console.log(new);
```

# serialization/deserialization/json
* JSON.stringify
* JSON.parse
