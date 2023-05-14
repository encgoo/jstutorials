# Recursion and stack
Recursive functions.

# Rest parameters and spread syntax
Gather all input arguments.
```js
function sumAll(...args){
    // this function can take any number of inputs
}
// It is different from this
function sumArray(arr){
    // this function takes only one input as an array
}
```

# Variable scope, closure

# The old var
Var is different from let:
* var has no scope
* var can be redeclared

# Global object

# Function object, NFE
A function object has these properties
```js
    function foo(in1, in2){

    }
    console.log(foo.name);
    colsole.log(foo.length); // # of inputs
```
## cunstom properties as static variable
```js
    function foo(){
        console.log('called');
        // special ? custom property that can be accessed from outside
        foo.counter ++;
    }

    foo();
    foo();
    console.log(foo.counter);
```

# New function
Create a new function using a string.
```js
    let func = new Function([in1, in2], 'return in1 + in2');
```

# Scheduling: setTimeout and setTiemInterval
Set timeout for a function.
```js
    function foo(in1, in2){

    }
    setTimeout(foo, 1000, in1, in2);
```

# Decorators and forwarding, call/apple

# Arrow function revisit
Compare these two approaches to see why arrow function is good using "this" from outer context.

```js
    let group = {
        title: "Our group",
        students: ["John", "Smith", "Cruise"],
        showListBad() {
            // this.students is ok since showListBad still has context of "this"
            // using normal callback function
            this.students.forEach(function(student){
                // a normal function has no "this"
                // the following will result in failure
                // even though student is accessible.
                // a normal function like this can have information only about
                // student, the input argument. It has not context
                console.log(this.title + ":" + student);
            })
        }
        showListGood() {
            this.students.forEach(student => {
                // this is ok. Arrow function can have context of "this". It comes from
                // the outer context.
                consel.log(this.title + ":" + student);
            })
        }
    }
    


```