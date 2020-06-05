---
title: Images
description: How to lazy load images on your website
date: 2020-06-03
tags:
  - images
layout: layouts/post.njk
---

This is a regular image:

```html
<img class="lazy"
  src="lazy.jpg"
  alt="A lazy image" />
```

Make it lazy by changing `src` to `data-src`:

```html
<img class="lazy"
  data-src="lazy.jpg"
  alt="A lazy image" />
```

Add vanilla-lazyload via a `script` tag, if you didn't already.

```html
<script
  src="https://cdn.jsdelivr.net/npm/vanilla-lazyload@16.1.0/dist/lazyload.min.js">
</script>
```

And initialize it with the `new` keyword, eventyally passing some options:

```js
var lazyLoadInstance = new LazyLoad({
  elements_selector: ".lazy",
  // ... more custom settings?
});
```

