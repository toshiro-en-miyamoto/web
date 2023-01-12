# Basic CSS Concepts

- All elements are represented by a rectangular box with content, padding, border, and margin.
- There are three main types of elements: `block`, `inline`, and `inline-block`.
- There are many different units for CSS values:
  - `px` should be avoided except when setting the document’s base font size.
  - `em` is relative to the element’s font size.
  - `rem` is relative to the document’s base font size.
  - `vw`, `vh`, `vmin`, and `vmax` are relative to the viewport size.
- The `calc` function is used to compute CSS values by performing calculations with multiple values, potentially with different units.
- Colors can be defined in several ways.
  - Named colors: `red`, `blue`, and `orangered`
  - Hexadecimal RGB: `#FF0000`
  - RGB function: `rgb(255, 0, 0)`
  - HSL function: `hsl(90, 50%, 25%)`
- If an element’s content cannot fit inside of it, the content will overflow.
- Overflow handling can be changed with the `overflow`, `overflow-x`, and `overflow-y` properties.

## The box model

Every element in CSS is treated like a rectanglar box that is made up of four parts, starting from the outside: `margin`, `border`, `padding`, and content.

The margin is the space between an element`s border and its surrounding elements.

## Box sizing

With the `content-box`:

```
.box1 {
    box-sizing: content-box;    /* default */
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 2px solid red;
}
```

| width of  | pixels    | because
|-----------|----------:|---------
| `.box1`   | 144       | `= width + 2* padding + 2* border`
| content   | 100       | `= width`

With the `border-box`:

```
.box2 {
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 2px solid red;
}
```

| width of  | pixels    | because
|-----------|----------:|---------
| `.box2`   | 120       | `= width`
| content   |  76       | `= width - 2* border - 2* padding`;

## Block and inline elements

There are three types of HTML elements: `block`, `inline`, and `inline-block`. An element's type can be changed by setting the `display` property.

A `block` element always apears on its own line, and
- it, by default, takes up only enough space to fit its content;
- the `width`, `height`, `padding` and `margin` properties are respected.

An `inline` element is rendered inside the normal flow of text, and
- the `width` and `height` properties are ignored only to take up enough width and height to fit its content;
- the vertical values of the `padding` and `margin` properties are ignored;
- the horizontal values of the `padding` and `margin` properties are respected to take up extra hirizontal space.

An `inline-block` element flows with the text like an `inline` element, but
- the `width`, `height`, `padding` and `margin` properties are respected.

## Units

| unit  | description
|-------|-------------
| `px`  | not recommended to use, except for the `font-size` property
| `em`  | relative to the *inherited* font size of the element
| `rem` | stands for *root em*, relative to the page's base font size
| `vw`  | `1vw` is 1% of the *viewport width*
| `vh`  | `1vh` is 1% of the *viewport height*
| `%`   | relative to another value

The `rem` unit is a good choice, especially for layout properties, since the size of `1rem` remains constant throughtout the document (unlike the `em` unit). If the browser is zoomed, everything resizes nicely because it's all proportional to the base font size.

The *viewport* is the area of the page that is currently visible in your web browser. f the viewport is resized, then any elements using `vw` units will have their sizes adjusted accordingly. Because `vw` and `vh` are relative to the viewport size, they are a good chice when using responsive design techniques.

## Colors

[A list of *named color*](https://developer.mozilla.org/en-US/docs/Web/CSS/named-color) is available to the MDN Web Docs.

The `transparent` keyword can be used anywhere a color is expected. This will apply no color. This can be useful when an element is positioned on top of another element, and you want the element underneath to show through. The background color of most elements defaults to `transparent`.

| notation                  | description
|---------------------------|-------------
| `rgb(255, 0, 0)`          | pure red with 100% opacity
| `rgba(255, 0, 0, 0.5)`    | pure red with 50% opacity

The HSL color model can be used with the `hsl()` or `hsla()` functions.

## Handling overflow

The content inside a block element, by default, will wrap to a new line when it doesn’t fit horizontally. What happens when an explicit height is set and the content does not fit inside the element's dimensions? This is a condition known as *vertical overflow*.

```
<style>
  .container {
    height: 2rem;
    width: 10rem;
  }
</style>
<div class="container">
  This is some really long text that will overflow the container.
</div>
```

We can change this behavior with the `white-space` property. If we set this property to `nowrap`, this will also cause *horizontal overflow*.

| if a container has    | then, it may cause
|-----------------------|-------------
| an explicit width     | horizontal overflow
| an explicit height    | vertical overflow

We have some control over how overflow is handled with the `overflow` property.

| `overflow:`   | behavior
|---------------|----------
| `visible`     | (default)
| `hidden`      | the overflowing content is clipped
| `scroll`      | the scrollbars are provided always
| `auto`        | the scrollbars are provided if it overflows

## CSS variables

Note that CSS variables, officially called *CSS custom properties*, are not supported in Internet Explorer.

CSS variables are declared with two dashes followed by the variable name, such as `--heading-color: blue;`.

```
<style>
  .container {
    --heading-color: blue;
    font-family: Arial, sans-serif;
  }
  .container h1 {
    color: var(--heading-color);
  }
</style>
<div class="container">
  <h1>Welcome</h1>
</div>
```
