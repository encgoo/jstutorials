# Class basic syntax

## The class syntx

```js
    class MyClass{
        constructor(){}
        method(){}
    }

    let a = new MyClass();
```

# Class inheritance

```js
    class Animal{
        eat(){

        }
    }

    class rabit extends Animal {
        eat(){
            // do something special
            console.log('Special steps first');
            // call super
            super.eat();
        }
    }

```

# static properties and methods
```js
    class MyClass(){
        static mVariable = 'This is static';
        static staticMethod(){

        }
    }
```

# Private and protected
New features not commonly used yet?

# Extending built-in classes
```js

    class PowerArray extends Array{

    }
```

# instanceof operator

# Multiple inheritance
Class exension in JS only supports single inheritance. To get multiple inheritace, we can mix extends and assign prototype. 
```js
class SuperA{
    methoda(){}
}
let SuperB{
    methodB() {},
    methodC() {}
};

class MyClass entends SuperA {

}

Object.assign(MyClass.prototype, SuperB)
```