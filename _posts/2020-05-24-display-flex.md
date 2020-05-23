---
layout: post
title: "display: flex"
---

Just a quick refresh on css properties related to flex, since the names are often not very descriptive and are easy to forget.

### Flex container

A container, as the name suggest, is a base for other things to be aligned / ordered. When you set something with `display: flex`, this thing becomes a flex container, and elements inside it behave according the flexbox rules. By default, elements inside it line up line-by-line, then row-by-row, like normal characters in a paragraph. This can be controlled with `flex-direction`, `flex-wrap` and `flex-flow`.

### Align

But usually, we don't put enough elements to fill the entire flexbox, hence we need to specify how to align the elements inside. For the container, we can use `justify-content` to it how to align elements horizontally, and `align-items` to align elements vertically. This graphic by `css-tricks` is very clear:
<p style="text-align: center;"><i>justify-content</i></p>

![justify-content](https://css-tricks.com/wp-content/uploads/2018/10/justify-content.svg)

<p style="text-align: center;"><i>align-items</i></p>

![align-items](https://css-tricks.com/wp-content/uploads/2018/10/align-items.svg)

These are calculated for each line in the flexbox. Then `align-content` would tell the container how to place the lines relative to the whole container. For elements inside the container, we can also use `align-self` to override the alignment for that item.
