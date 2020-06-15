---
title: Responsive images
description: How to lazy load responsive images on your website
date: 2020-06-15
tags:
  - images
  - responsive images
layout: layouts/post.njk
---

This is a regular responsive image:

```html
<img
  alt="A responsive image"
  src="220x280.jpg"
  srcset="
    220x280.jpg 220w,
    440x560.jpg 440w,
    660x840.jpg 660w
  "
  sizes="75vw"
/>
```

Make it lazy by changing `src` to `data-src`, `srcset` to `data-src`, `sizes` to `data-sizez`, and also adding a `lazy` class to it. Like this:

```html
<img
  class="lazy"
  alt="A lazy responsive image"
  data-src="220x280.jpg"
  data-srcset="
    220x280.jpg 220w,
    440x560.jpg 440w,
    660x840.jpg 660w
  "
  data-sizes="75vw"
/>
```

Add [vanilla-lazyload](https://github.com/verlok/vanilla-lazyload) via a `script` tag, if you don't have it already.

```html
<script
  src="https://cdn.jsdelivr.net/npm/vanilla-lazyload@16.1.0/dist/lazyload.min.js">
</script>
```

And initialize it with the `new` keyword, eventually passing some options:

```js
var myLL = new LazyLoad({
  elements_selector: ".lazy"
});
```

For more custom settings to pass to the `LazyLoad` object, see [vanilla-lazyload documentation](https://github.com/verlok/vanilla-lazyload).

## Pictures too!

You can do the same with a `picture` tag. A regular one, like this:

```html
<picture>
  <source
    media="(orientation: landscape)"
    srcset="
      280x220.jpg 1x,
      560x440.jpg 2x"
    >
  <img
    alt="A responsive picture"
    src="220x280.jpg"
    srcset="
      220x280.jpg 1x,
      440x560.jpg 2x
    "
  />
</picture>
```

Can become a lazy picture, like this:

```html
<picture>
  <source
    media="(orientation: landscape)"
    data-srcset="
      280x220.jpg 1x,
      560x440.jpg 2x"
    >
  <img
    alt="A responsive picture"
    data-src="220x280.jpg"
    data-srcset="
      220x280.jpg 1x,
      440x560.jpg 2x
    "
  />
</picture>
```

## A complete guide

Read the complete guide on [Lazy loading responsive images in 2020](https://www.andreaverlicchi.eu/lazy-load-responsive-images-in-2020-srcset-sizes-picture-webp/).
