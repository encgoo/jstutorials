# Page: DOMContentLoaded, load, beforeunload, unload
Three important events of a HTML page
* DOMContentLoaded. HTML content fully loaded, but external images and stylesheets may not yet have loaded
    * DOM is ready, can lookup DOM nodes.
* load External resources also loaded
    * image size is known at this point
* beforeunload/unload: User is leaving the page
    * check if user saved changes and ask if not

See this [example](src/events.html).

## readyState


# Scripts: async, defer
Several important concepts here. When the browser loads HTML, and comes across a script tag, it _can't_ continue building the DOM. It needs to execute the script first.
* The script when is being execute, can see only the DOM element above them, not those below them
* If the script takes time to execute, this will "block the page", causing an "not responding, do you want to stop the script?" message.

One way is to put the script to the bottom. Not a perfect solution, because the DOM takes time to build.

For this, the script tag has two attributes: defer and async

## defer
The defer attribute tells the browser don't wait for the script to finish. The browser will continue to build the DOM. The script loads "in the background" and then runs when the DOM is fully built.
```html
    <script defer src='https://.....'>
```
If there are more than one defer, then the relative order still keeps, even though the later one finishes download first.
## async
The async means:
* script is completely independent. So the browser won't wait either.
* other scripts don't wait for async scripts either, even other async won't wait
* DOMcontentLoaded and async don't wait for each other.
So async scripts load in the background, and run whenever ready. This can be used for change analysis, and rollup status.

## dynamic script
Script tag can be dynamically added to the DOM programmatically after the DOM is built. Dynamic scripts are by default async. 


# Resource loading: onload and onerror

