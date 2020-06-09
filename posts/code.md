---
title: Code
description: How to lazily execute code when an element enters the viewport on your website
date: 2020-06-09
tags:
  - code
layout: layouts/post.njk
---

Say you want to execute some code when some elements enter the viewport.

Take this element.

```html
<div class="fadeIn">
  I will fade in after I entered the viewport.
</div>
```

You might want it to fade-in when it enters the viewport.

```html
<div class="fadeIn" data-lazy-function="fadeIn">
  I will fade in after I entered the viewport.
</div>
```

Using CSS, make the `div` initially transparent, using a property value that will transition to any other value during 500 milliseconds.

```css
.fadeIn {
  opacity: 0;
  transition: opacity 500ms;
}
```

Define the function(s) you want to execute lazily in a specific namespace, like `lazyFunctions`:

```js
window.lazyFunctions = {
  fadeIn: function (element) {
    element.style.opacity = 1;
  },
};
```

Add [vanilla-lazyload](https://github.com/verlok/vanilla-lazyload) via a `script` tag, if you don't have it already.

```html
<script src="https://cdn.jsdelivr.net/npm/vanilla-lazyload@16.1.0/dist/lazyload.min.js"></script>
```

Create a callback to be passed to the LazyLoad object...

```js
function executeLazyFunction(element) {
  var lazyFunctionName = element.getAttribute(
    "data-lazy-function"
  );
  var lazyFunction = window.lazyFunctions[lazyFunctionName];
  if (!lazyFunction) return;
  lazyFunction(element);
}
```

... and initialize it with the `new` keyword, like this.

```js
var ll = new LazyLoad({
  elements_selector: "[data-lazy-function]",
  unobserve_entered: true,
  callback_enter: executeLazyFunction
});
```

The `unobserve_entered` option will avoid lazyload executing that function multiple times (everytime the element enters the viewport).

For more custom settings to pass to the `LazyLoad` object, see [vanilla-lazyload documentation](https://github.com/verlok/vanilla-lazyload).
