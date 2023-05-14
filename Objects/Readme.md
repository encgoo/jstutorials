# Objects

A object in js is a collection of data

```js
    let user = {}; // or let user = Object();
```
Initialize an object
```js
    let user = {
        name: 'John',
        age: 30
    };
    // add more
    user.isAdmin = true;
    // delete an added one
    delete user.age;
```
An object is in some sense a dict in python

Use variable as key. 

```js
    let fruit = prompt('Which fruit to by', 'apple');
    let bag = {
        [fruits]: 5
    };
```

## iterate an object
We can iterate the key like this
```js
    let codes = {
        "1": "USA",
        "41": "Switzerland"
    };

    for (let code in codes){
        alert(code); // 1, 41
    }
```

## Object references and copying
Object assignment is reference assignment. 
```js
    let a = {
        name: "John"
    };
    let b = a;
    a.name = 'Smith',
    console.log(b.name); // this is Smith as well, since a and b both refer to the same object
```

## clone and _merge_
```js
    let a = {
        name: "John"
    };


    let b = {
        age: 30
    };

    Object.assign(c, a, b); // merge all from and b to c. What happen if there is conflict in a and b?

```
Object.assign is only one level clone. Deep clone needs structureClone.
```js
    let a = {
        name: 'Jone',
        sizes: {
            height: 182,
            width: 50
        }
    };

    let b = structClone(a);

```
# Garbage collection
It is a separated thread for garbage collection, and it depends on the reachability of an object.

# Object methods

Objects can have methods
```js
    let user = {
        name: "John"
    };

    user.getName = () => {
        return this.name;
    };
```
Or it can be more like a class.
```js
    let user = {
        name: "John",
        sayHi() {
            return "Hi, " + this.name;
        }
    };
```
The "this" in js is run-time evaluted, and not statically bound. So different objects can share the same method.

```js
    let student = {
        name: 'Johe'
    };
    let teacher = {
        name: 'Smith'
    };

    function sayHi(){
        // "this" is not defined in statically here. It will be figured out during run-time
        alert('Hi, ' + this.name);
    }

    student.sayHi = sayHi;
    teacher.sayHi = sayHi;

    student.sayHi(); // now this is student
    teacher.sayHi(); // this is teacher
```

Arrow function doesn't have its own "this", it is taken from the outer function.

## Optional chain '?.'
```js
    // in case user or user.address is not defined
    alert('user?.address?.street');
```

