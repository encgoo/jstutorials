# Modules, introduction
## historical packages

* AMD
* CommonJS
* UMD

## What is a module
A Module is a file with scripts. Modules can load each other and use import/export to exchange functionality.
* export keyword means variables/functions can be accessed from other modules
* import means importing from other modules

_One important thing_, import/export only works through http(s). Opening a page locally (using file://) won't work. Need to run a HTTP server and access a page from it. A simple way is to use python http server.

`python3 -m http.server`

One module can export a function, another module can import this function and then call it. See this [example](./src/import.html).

_NOTE_: Module script needs to be loaded to a HTML page by "<script type='module' src='path/to/file.js'"

For embedded scripts, type='module' is also needed.

## Core module features

What are the diffs between modules and regular scripts?

### Always "use strict"

Modules are always running with "use strict".

### Moduleplevel scope

Each module has its _own_ scope. Unless vars/funcs are exported, the scope is private, not accessbile by others.

Use window level scope to pass global variables if necessary.

### module _init_ and share
If a module is impoorted by more than one other moduule, it is imported only once, and then shared. this become important if exported varaible is 'initialized'. It is initialized only once.

```js
    export let admin = {
        name: 'John'
    };
```
If js1 import the above, admin is first initialized to John. If now js1 changes it, and then js2 import it. When js2 imports the above, the code won't be run. So js2 will see whatever js2 changed.

### import.meta

The import.meta contains the information about the current module. 

### this in module

In a module, top-level this is undefined.

## Broswer-sepcific features

## Build tools
Browser modules are rarely used in their 'raw' form. There are build-tools to bundle them. 
Webpack is a such build-tool.

After bunlded, import/export dependecies are analyzed and resolved/removed. Eventually a single script file without import/export is generated. Then it can be loaded into a script tag without type='module'.

Webpack exercise will be done somewhere else.

# Export and Import
## Export before declaration
Examples
```js
export let name = 'John';
export const ID = '123456';
export class User {
    constructor (name) {
        this.name = name;
    }
}
```

## Export apart from declarations
```js
function logName(user) {
    console.log(user);
}
function logNum(in) {
    console.log(in);
}
export {logName, logNum}; //a list of exported
```

## import *
Import all from a module as a struct/object.
```js
import * as utils from './js/utils.js'

utils.logName('John');
```
Note that it is OK to import all, including unused stuffs. The modern build-tool like Webpack optimizes, and removes unused imports.

## import/export as

## export default
One per module. This is recommended. 

Remember use `import {} from` for named exports, and `import from ` for `export default`.

## re-export an import

# Dynamic imports

## import function?
`import(path_to_js)` returns a promise, because it takes time to import. 

# Special Note about require
Keywords require/define come from RequireJS and is used by Node.js.

## tutorial
Following [this](https://www.tutorialspoint.com/requirejs/requirejs_environment_setup.htm). 

## setup
To use require, we need the require.js. It can be [donwloaded](https://requirejs.org/docs/download.html#rjs). The downloaded js file is saved [here](./requirejs/require.js).

## load require.js
There are two ways to load require.js.

### data-domain
Use the data-domain attribute of the script tag. See sample [html](requirejs/datamain.html).
```html
    <script data-main="./main.js" src="./require.js"></script>
```
The main.js is a function. But doing the above, this function will be execuated.
```js
define(['./phonebook.js'], function(Phonebook){
    console.log('Name: ' + Phonebook.Name);
});
```
### load require.js first
See this sample [html](requirejs/separate.html). Note here two js are loaded _in order_.
```html
        <script src="./require.js"> </script>
        <script src="./main.js"></script>
```
By doing so, the funciton in main.js is NOT called automatically. Still need to explicitly call it. Also because of this, the function can't be anonymous. Give it a name so we can call it from the html file.
```js
define('log', ['./phonebook.js'], function(Phonebook){
    console.log('Name: ' + Phonebook.Name);
});
```




