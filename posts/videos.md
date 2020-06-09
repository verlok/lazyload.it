---
title: Videos
description: How to lazy load videos on your website
date: 2020-06-05
tags:
  - videos
layout: layouts/post.njk
---

This is a regular video:

```html
<video
  controls
  width="620"
  data-src="lazy.mp4"
  data-poster="lazy.jpg"
>
  <source type="video/mp4" src="lazy.mp4" />
  <source type="video/ogg" src="lazy.ogg" />
  <source type="video/avi" src="lazy.avi" />
</video>
```

Make it lazy by changing `src` to `data-src` and also adding a `lazy` class to it. Like this:

```html
<video
  class="lazy"
  controls
  width="620"
  data-src="lazy.mp4"
  data-poster="lazy.jpg"
>
  <source type="video/mp4" data-src="lazy.mp4" />
  <source type="video/ogg" data-src="lazy.ogg" />
  <source type="video/avi" data-src="lazy.avi" />
</video>
```

Add [vanilla-lazyload](https://github.com/verlok/vanilla-lazyload) via a `script` tag, if you don't have it already.

```html
<script src="https://cdn.jsdelivr.net/npm/vanilla-lazyload@16.1.0/dist/lazyload.min.js"></script>
```

And initialize it with the `new` keyword, eventually passing some options:

```js
var myLL = new LazyLoad({
  elements_selector: ".lazy",
});
```

For more custom settings to pass to the `LazyLoad` object, see [vanilla-lazyload documentation](https://github.com/verlok/vanilla-lazyload).
