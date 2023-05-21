# Introduction to browser events

An event is a signal that somethign has happened. Common events including the followings.

## Various events

### Mouse events
* click
* contextmenu
* mousever/mouseout
* mousedown/mouseup
* mousemove

### Keyboard events
* keydown
* keyup

### Form element events
* submit
* focus

### Document events
* DOMContentLoaded

### CSS events:
* transitionend

## Event handlers
To react to an event, assign a hanlder. 

### HTML-attribute
The onclick attribute of an HTML element. Example:
```html
    <input value="Click me" onclick="alert('Click!')" type="button">
```

### DOM property
Assign the onclick handler of an element. 

### "this" in handler
"this" in handler is the caller element.

### addEveltListener

### event object
The event handler can take the event as input argument.

### event handler as an object
The handleEvent method of this object will be called.

# Bubbling and capturing
The event of a child can be bubbled up to parent. 

## Bubbling principle
When an event happens, it first runs its handlers, then its parent's handler, then all the ancestors.

Some of the events don't make sense to bubble, for example, focus. 

## Event.target

Within a handler, this is the parent element of the handler. event.target is the _initial_ element that triggers the event.

## Stopping bubbling
At any stage to fthe bubbling, an event handler can stop further bubbling, by calling event.stopPropogation().

Normally it is _not_ a good idea to stop bubbling unless there is a very good reason.

## Capturing
[TBD]

# Event delegation
Since an event bubbles up, if elements share a same even handler, a single handler can be added to the common ancestor of all the elements. 

[Example](src/event_delegate.html). One drawback is that if a table cell has a child, then the click might be initiated from the child, not the cell. Then the above hanlder won't work. There is a way to fix it. 

## Delegation example: actions in markup
If we have a menu of several buttons, we can have one handler for each button. Or we can have one a single handler for all the buttons. See this [example](./src/buttons.html).

## The "behavior" pattern
It is similar to the example above. Use a specific attribute the label an element or elements. Then use a global handler at the document level to handle the event of it or them.

### Behavior: Counter
For [example](./src/counter.html), buttons behaves as counters.

### Behavior: Toggler
Need a flag. The hidden can be used as the flag to toggle on/off. See this [example](src/toggler.html).

# Browser default actions
Browser has some default actions:
* A click on a link
* a click on a form submit button
* pressing a mouse button over a text and moving it - selects the text.

## Preventing browser acions
Two ways:
* Use the event object. Call event.preventDefault()
* Returning false in the handler
```html
    <a href="/" onclick="return false">Click here</a>
    <a href="/" onclick="event.preventDefault()">here</a>
```
An [example](src/hrefBtn.html) of using "a href" as buttons. Need to prevent the default clicking handler from the browser.

## The "passive" handler option
Mobile feature. Tell the browser that it doens't need to wait to wait for the handler function to finish before knowing whether default handler will be prevented or not.

## event.defaultPrevented
[TBD}]

# Dispatching custom events
This is about generating custom events from JS.

## Event constructor
```js
    let event = new Event("click", {bubble: true});
```
An event is dispatched from an element. _NOTE_ an event can only be handled by the dispatcher itself, or if bubbles by its ancestors.

## MouseEvent, KeyboadEvent and others

Dispatch an MouseEvent.
```js
    let event = new MouseEvent("click", {
    bubbles: true,
    cancelable: true,
    clientX: 100,
    clientY: 100
    });
```
It has clientX/clientY for coordinates in the _constructor_. These two are _not_ in the constructor of Event, and need to be set outside of the constructor for workaround.

## CustomEvent

## event.proeventDefault()
