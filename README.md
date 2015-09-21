# domhelpers

DOMhelpers is a (very) small collection of some handy utility functions which
help you query the DOM.


## Usage

At the moment, the only way to install DOMhelpers is through npm, which means
you'll have to use a tool like [browserify][browserify] in order to include it
in your code.

```bash
$ npm install --save domhelpers
```

Then you can include the individual methods with

```js
var getParent = require('domhelpers/getParent');
```

Or include all methods with

```js
var domhelpers = require('domhelpers');
domhelpers.getParent(element, selector);
```

Full docs for the individual methods can be found in the next section

[browserify]: http://browserify.org/


## Methods

### getClosest(element, selector)

Get the closest parent from `element` which matches `selector` or `element`
itself if it matches the selector.

```html
<div class="el1">
  <div class="el2"></div>
</div>
```

```js
var el2 = document.querySelector('.el2');
console.log(getClosest(el2, '.el1')); // div.el1
console.log(getClosest(el2, '.el2')); // div.el2
```


### getParent(element, selector)

Get the closest element from `element` which matches `selector`. This does NOT
include the `element` itself, instead it searches from the `element`'s parentNode.

```html
<div class="el1">
  <div class="el2"></div>
</div>
```

```js
var el2 = document.querySelector('.el2');
console.log(getClosest(el2, '.el1')); // div.el1
console.log(getClosest(el2, '.el2')); // undefined
```


### getParents(element, selector)

Get all parents from `element` which match `selector`. This function always
returns an array.

```html
<div class="el1">
  <div class="el1">
    <div class="el2"></div>
  </div>
</div>
```

```js
var el2 = document.querySelector('.el2');
console.log(getClosest(el2, '.el1')); // [div.el1, div.el1]
console.log(getClosest(el2, '.el2')); // []
```
