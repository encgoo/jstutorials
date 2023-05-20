# Browser environment, specs
JS runs on a platform. A proatform can be a broswer, a web-server, or even a smart coffee machine. A platform is also called a host environment.

A host env provides its own objects and functions in addition to the core JS. 

## Broswer env
There is a root object called window. 

### DOM (Document Object Model)

[DOM](https://dom.spec.whatwg.org) represents all page content as objects that can be modified. The `document` object is the main entery point to the page.

CSS has [CSSOM](https://www.w3.org/TR/cssom-1/) (CSS Object Model).

### BOM (Browser Object Model)

BOM represents additional objects provided by the browser (a host env) for working with everything else except the document.

Some examples:
* navigator object 
    * navigator.userAgent
    * nagivator.platform
* location
    * location.href: current URL. Set this one to redirect
* alert/confirm/prompt functions

# DOM Tree

The backbone of an HTML/XML document is tags. _Every HTML tag is an object_. Nested tags are "children" of the enclosing one. 

Each object has
* style
    * background
* innerHTML
* offsetWidth
* ...

# Walking the DOM

[TBD]

# Searching: getElement*, querySelector*

DOM searching provides random access to the DOM tree.

## document.getElementById or just id

If an element has the id attribute, then this can be used. Note that HTML allows more then one element with the same id. In that case, getElementById returns the first or a random one. See this [example](./src/getElementById.html).

## querySelectorAll
It is a method of an element inside the HTML DOM. It query using the given CSS selector.

## querySelector

## matches

## closest(css)

## getElementsBy*
* getelementsByTagName('div'): It returns a collection.

## Live collections

# Node properties: type, tag and contents




