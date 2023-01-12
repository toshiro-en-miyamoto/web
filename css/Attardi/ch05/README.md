# Backgrounds and Gradients

- An element’s background can be a solid color, an image, a gradient, or a combination of the three.
- The display of a background image can be customized with properties:
  - `background-repeat`,
  - `background-position`,
  - `background-size`, and
  - `background-clip`.
- Gradients can be linear or radial.

## Backgrounds

### The `background-color` property

```
.background {
    background-color: #999999;
}
```

### The `background-image` property

```
.background {
    background-color: #999999;
    background-image: url('tiles.jpg');
    /* repeated by default */
}
```

### The `background-repeat` property

```
.background {
    background-color: #999999;
    background-image: url('tiles.jpg');
    background-repeat: no-repeat;   /* a single instance */
}
```

or

```
.background {
    background-color: #999999;
    background-image: url('tiles.jpg');
    background-repeat: repeat-y;    /* repeated vertically */
}
```

### The `background-position` property

```
.background {
    background-color: #999999;
    background-image: url('tiles.jpg');
    background-repeat: no-repeat;
    background-position: center;
}
```

A single value can be given such as `top`, `bottom`, `left`, `right`, or `center`, a length such as `50px`, or a percentage. Two values can also be given. In this case,
- the first value is the position along the X-axis, and
- the second is the position along the Y-axis.

```
.background {
    background-color: #999999;
    background-image: url('tiles.jpg');
    background-repeat: no-repeat;
    background-position: 50px center;
}
```

### The `background-size` property

By default, the background image will have its original size. Setting the `background-size: cover` will resize the background image to make sure that the element is fully covered.

```
.header-image {
    background-image: url('mountains.jpg');
    background-size: cover;
}
```

If the aspect ratio of the image doesn’t match that of the element, the image will be cropped. Most of the image may be cut off. To fix this, we can combine the `background-position` property with `background-size`:

```
.header-image {
    background-image: url('mountains.jpg');
    background-size: cover;
    background-position: center;
}
```

You can make the entire image fit within the element with `background-size: contain`:

```
.header-image {
    background-image: url('mountains.jpg');
    background-size: contain;
}
```

### The `background-clip` property

The background will extend all the way to the border (default).

```
.header-image {
    background-image: url('mountains.jpg');
    background-size: cover;
    background-position: center;
    background-clip: border-box;    /* default */
}
```

Other values are available:
- `padding-box` extends the image to the padding area, and
- `content-box` to the content area

### The `background` property

The shorthand property lets you set several of these properties in a single value.

| property              | values
|-----------------------|--------
| `background-color`    | a color value
| `background-image`    | a URL
| `background-repeat`   | `no-repeat`, `repeat-x`, `repeat-y`
| `background-position` | `top left`, `center`, etc.
| `background-size`     | `cover`, `contain`, `100px 300px`
| `background-clip`     | `border-box`, `padding-box`, `content-box`

```
.header-image {
    background: url('mountains.jpg') center / cover;
    height: 15rem;
    border: 3px solid #000000;
}
```

The values can be given in any order, with a few exceptions:
- The `background-size` must come directly after `background-position`, separated by a slash.
- The `background-color` must come last.
