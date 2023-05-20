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


# Browser default actions

# Despatching custom events
