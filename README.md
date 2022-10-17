# NoSleep.js

Prevent display sleep and enable wake lock in all Android and iOS web browsers.

## Installation

This library is available on [Bower](http://bower.io/) as **nosleep**.

`bower install nosleep`

This package is published to npm as **nosleep.js** and can be installed with:

`npm install nosleep.js`

## Build from source

Install all development dependencies with:

`npm install`

To build this library run:

`npm run build`

A new build of [NoSleep.js](https://github.com/richtr/NoSleep.js/blob/master/dist/NoSleep.js) and [NoSleep.min.js](https://github.com/richtr/NoSleep.js/blob/master/dist/NoSleep.min.js) will now be available in the `/dist` directory.

## Usage
Import ES6 module:

```javascript
import NoSleep from 'nosleep.js';
```

Create a new NoSleep object and then enable or disable it when needed.

To create a new NoSleep object:

```javascript
var noSleep = new NoSleep();
```

To enable wake lock:

**NOTE: This function call must be wrapped in a user input event handler e.g. a mouse or touch handler**

```javascript
// Enable wake lock.
// (must be wrapped in a user input event handler e.g. a mouse or touch handler)
document.addEventListener('click', function enableNoSleep() {
  document.removeEventListener('click', enableNoSleep, false);
  noSleep.enable();
}, false);
```

To disable wake lock:

```javascript
// Disable wake lock at some point in the future.
// (does not need to be wrapped in any user input event handler)
noSleep.disable();
```


## Example
```html
<!DOCTYPE html>
<html>
  <head>
    <title>NoSleep.js - Simple Test Page</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
  </head>
  <body>
    <h1>NoSleep Test Page</h1>
    <script src="../dist/NoSleep.min.js"></script>

    <input type="button" id="toggle" value="Wake Lock is disabled" />

    <script>
      var noSleep = new NoSleep();

      var wakeLockEnabled = false;
      var toggleEl = document.querySelector("#toggle");
      toggleEl.addEventListener('click', function() {
        if (!wakeLockEnabled) {
          noSleep.enable(); // keep the screen on!
          wakeLockEnabled = true;
          toggleEl.value = "Wake Lock is enabled";
          document.body.style.backgroundColor = "green";
        } else {
          noSleep.disable(); // let the screen turn off.
          wakeLockEnabled = false;
          toggleEl.value = "Wake Lock is disabled";
          document.body.style.backgroundColor = "";
        }
      }, false);
    </script>

    <!-- Github Ribbon -->
    <a href="https://github.com/richtr/NoSleep.js"><img style="position: absolute; top: 0; right: 0; border: 0;" src="https://camo.githubusercontent.com/365986a132ccd6a44c23a9169022c0b5c890c387/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f7265645f6161303030302e706e67" alt="Fork me on GitHub" data-canonical-src="https://s3.amazonaws.com/github/ribbons/forkme_right_red_aa0000.png"></a>
  </body>
</html>
```

## License

MIT. Copyright (c)
