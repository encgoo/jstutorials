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

# Event delegation

# Browser default actions

# Despatching custom events
