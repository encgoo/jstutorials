# Form propertieds and methods
Forms and control elements have special properties and eventrs.

## Navigation: form and elements

Document forms are members of the special collections: `document.forms`.

```js
document.forms[0]; // the first form in the document
document.forms.my; /// the form with name="my"
```

## Form elements

## References

# Focusong: focus/blur
An elemenht receives the focus when the user either clicks on it or uses the Tab key. 

## Events focus/blur

## Methods focus/blur
Elements have these two `elem.focus()` and `elem.blur()`

## Allow focusing on any element: tabindex
Use `tabIndex='-1'` to allow only focusing by programing.

## Delegation: focusin/focusout

# Events: change, input, cut, copy, paste
Events assicated with data updates.

## Event:change
```html
<input type="text" onchange="alert(this.value)">
```

## Event: input
```html
<input type="text" oninput="console.log(this.value)">
```
Event input can't be prevented by preventDefault.

## Events: cut, copy paste
Copy and paste can be prevented. See this [exampe](./src/dataUpdate.html).

# Forms: event and methods submit

## Event: submit
See this [example](src/formSubmit.html).

## Method: submit


