---
title: iFrames
description: How to lazy load iframes on your website
date: 2020-06-03
tags:
  - iframes
  - lazyload
layout: layouts/post.njk
---

This is a regular iframe:

```html
<iframe src="lazyFrame.html"></iframe>
```

Make it lazy by changing `src` to `data-src` and also adding a `lazy` class to it. Like this:

```html
<iframe class="lazy" data-src="lazyFrame.html"></iframe>
```

Add vanilla-lazyload via a `script` tag, if you don't have it already.

```html
<script src="https://cdn.jsdelivr.net/npm/vanilla-lazyload@16.1.0/dist/lazyload.min.js"></script>
```

And initialize it with the `new` keyword, eventually passing some options:

```js
var lazyLoadInstance = new LazyLoad({
  elements_selector: ".lazy",
});
```

For more custom settings to pass to the `LazyLoad` object, see [vanilla-lazyload documentation](https://github.com/verlok/vanilla-lazyload).
