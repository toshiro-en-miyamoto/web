# Layout and Positioning

- Spacing with padding and margin
  - paddings create extra space *within* an element
  - margins create extra space *around* an element
- the `position` property
  - values: `static`, `relative`, `absolute`, `fixed`, or `sticky`
- the `z-index` property
- the `float` property

## Paddings

- By default, most elements have zero padding.
- An element’s padding is not inherited by its children.
- The `%` unit is defined as a percentage of the element’s width.
- A `background-color` extends underneath the content and padding box of the element.

## Margins

- By default, most elements have no margin.
- The size of the margin as a percentage, relative to the inline size (width in a horizontal language) of the containing block.

When the horizontal margin is set to `auto`,

- the element takes up the specified width, and
- the margin is *automatically* distributed evenly between the left and right margins; therefore
- the element is centered horizontally within its containing element.

## Margin collapse

Vertical margins collapse:

- When two elements with a vertical margin meet vertically, the two margins are *collapsed* into a single margin.
  - If they are the same size, then the collapsed margin will be the same size as the common margin.
  - If they are different sizes, the collapsed margin will take the size of the larger margin.
- When there is no border, padding, or other content between a parent and its child, the top and bottom margins of the inner element are collapsed (removed).
  - If the outer element has, say, a padding, we can see the margins of the inner element.

## Positioning elements

The CSS `position` property determines how an element is positioned, including *static*, *relative*, *absolute*, *fixed*, or *sticky*.

### `static`

A statically positioned element is positioned in the normal flow of the document. `static` is the default value of the `position` property. The `top`, `right`, `bottom`, and `left` properties have no effect.

A statically-positioned block element will, by default, take up the full width of its container.

### `relative`

A relatively positioned element is positioned relative to where it would normally appear in the flow of the document. The `top`, `right`, `bottom`, and `left` properties determine the offset.

The other elements in the document flow are not affected; they remain at their original positions in the document flow.

A relatively-positioned block element will, by default, take up the full width of its container.

### `absolute`

An absolutely positioned element is removed from the document flow and *floats* above it. The layout of other elements will be adjusted as if the absolutely positioned element is not there.

The `top`, `right`, `bottom`, and `left` offsets are relative to the *closest ancestor positioned element*. This is not necessarily the element’s direct parent.

An absolutely-positioned block element will only be as wide as it needs to be to fit its content. Add a `width: 100%` to the element if the full width behavior is still desired.

### `fixed`

A fixed element is removed from the document flow.

The `top`, `right`, `bottom`, and `left` offsets are relative to the viewport. Even if the page is scrolled, a fixed element will remain in the same position, useful for a fixed header or navigation bar.

An fixed block element will only be as wide as it needs to be to fit its content. Add a `width: 100%` to the element if the full width behavior is still desired.

### `sticky`

It is not supported in Internet Explorer.

A sticky element acts as a relatively positioned element, scrolling with the document. When the element reaches a point specified via a `top`, `right`, `bottom`, or `left` value, then it turns into a fixed element.

