# Basic Styling

- A border has a style, width, and color.
- Rounded corners with the `border-radius` property.
- Elements with an inner and/or outer box shadow.
- The transparency of an element with the `opacity` property.
- An element can be hidden in three ways:
  - `display: none;`
  - `visibility: hidden;`
  - `opacity: 0;`

## Shorthand and multiple values

| spec  | values    | T | R | B | L | formula
|-------|-----------|--:|--:|--:|--:|---------
| T     | 1         | 1 | 1 | 1 | 1 | R, B, L ⇐ T
| TR    | 1 2       | 1 | 2 | 1 | 2 | B ⇐ T, L ⇐ R
| TRB   | 1 2 3     | 1 | 2 | 3 | 2 | L ⇐ R
| TRBL  | 1 2 3 4   | 1 | 2 | 3 | 4 |

## Borders

Styles:
- `solid`, `duble`
- `dotted`, `dashed`
- `groove`, `ridge`
- `inset`, `outset`

The `border-collapse` for `table` elements:
- `separate`: (default) borders are not combined
- `collapse`: borders adjacent to another collapsed into one

The `border-radius` property:
- circular corners, e.g. `border-radius: 10px;`
- elliptical corners, e.g. `border-radius: 20px / 10px;`
- each corner can be specified with:
  - `border-top-right-radius`
  - `border-bottom-right-radius`
  - `border-bottom-left-radius`
  - `border-top-left-radius`

## Box shadows

The `box-shadow` property has:
- X and Y offsets
- blur radius (optional: default to 0)
- spread radius (optional: default to 0)
- color
- `inset` (optional)

You can apply multiple shadows to an element to apply both an inner and outer shadow.

```
.shadow {
    box-shadow: 0 0 10px 0 black, 0 0 25px red inset;
    ...
}
```

## Opacity

By default, most elements start out with a transparent background. When a background color or image is assigned, that element becomes opaque. You cannot see through the element to what's behind it. Borders and text are also opaque.

You can change this behavior with the `opacity` property.

```
<style>
  .outer {
    background: red;
    height: 10rem;
    width: 10rem;
  }
  .inner {
    background: blue;
    color: white;
    height: 8rem;
    width: 8rem;
    opacity: 0.5;
  }
</style>
<div class="outer">
  <div class="inner">
    Hello World!
  </div>
</div>
```

The `opacity` property takes a number between 0 and 1 or a percentage from 0% to 100%. Opacity applies to the entire element – background, border, text, images, and any other content within that element or its children.

## Hiding elements

- `display: none;` removes the element from the flow of the document as if it was never there, and the other blocks move to the left to fill the empty space.
- `visibility: hidden;` does not affect the flow of the document, meaning that no elements will move to fill the empty space left by the hidden element.
- `opacity: 0;` has the same net effect as `visibility: hidden` – the element is effectively hidden, but the layout is unchanged. To show the element again, just set opacity back to 1.

One reason you may want to use `opacity: 0` instead of `visibility: hidden` is while the visibility property will show or hide the element immediately, the opacity property can be transitioned gradually with a CSS transition. This can be used to create a subtle fade-in/fade-out effect.
