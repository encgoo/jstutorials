# Try...catch
```js
    try{
        
    } catch(err){

    }
```

# custom error
The Error class is built-in, and it can be extended
```js

    class NewError extends Error {

    }

    function foo(){
        throw new NewError('Error image');
    }
```