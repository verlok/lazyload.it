---
title: Images
description: How to lazy load images on your website
date: 2020-06-03
tags:
  - images
  - lazyload
layout: layouts/post.njk
---

This is a regular image:

```html
<img
  src="lazy.jpg"
  alt="An image" />
```

Make it lazy by changing `src` to `data-src` and also adding a `lazy` class to it. Like this:

```html
<img class="lazy"
  data-src="lazy.jpg"
  alt="A lazy image" />
```

Add [vanilla-lazyload](https://github.com/verlok/vanilla-lazyload) via a `script` tag, if you don't have it already.

```html
<script
  src="https://cdn.jsdelivr.net/npm/vanilla-lazyload@16.1.0/dist/lazyload.min.js">
</script>
```

And initialize it with the `new` keyword, eventually passing some options:

```js
var lazyLoadInstance = new LazyLoad({
  elements_selector: ".lazy"
});
```

For more custom settings to pass to the `LazyLoad` object, see [vanilla-lazyload documentation](https://github.com/verlok/vanilla-lazyload).
