# Mouse events
Mouse events include UI events from smart phones as well.

## Mouse event types

### mouseup/mousedown

### mouseover/mouseout

### mousemove

### click

### dbclick

### contextmenu

## Events order

## Mouse button
Click-related events always have the button property.

## Modifiers: shift, alt, ctrl and meta

```js
    function handleClickRelated(event){
        if (event.altKey && event.shiftKey){
            // both alt key and shift key are pressed when mouse button clicked
        }
    }
```

## Coordinates: clientX/Y, pageX/Y
pageX/Y is counted from the document left-upper corner, and it doesn't change when scroll. ClientX/Y is screen coordinates, affected by scrolling.

## Preventing selection on mousedown

Double click on a text has the selection default behavior. Mouse down->mouseMove also has the default selection behavior. This can be prevented if unwanted.

# Moving the mouse: mouseover/out, mouseenter/leave

## Events mouseover/nouseout, relatedTarget

## skip elements


# DragNDrop with mouse events
DND is a great interface solution.

## Algorithn
* On mousedown, prepare the element for moving
* on mousemove, move it by chaing left/top with position:absolute
* on mouseup perform all actions

Here is an [example](src/moveBall.html).

# Pointer events
For mouse/pen/stylus/touchscreen.

# Keyboard: keydown and keyup

# Scrolling
