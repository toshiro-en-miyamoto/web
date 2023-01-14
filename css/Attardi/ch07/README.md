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

The CSS `position` property determines how an element is positioned.

- A *statically positioned* element is positioned in the normal flow of the document.
- A *relatively positioned* element is positioned relative to where it would normally appear in the flow of the document.

The relatively positioned is offset

- 10px below the top of its original position and
- 10px to the right of its original position.

```
<style>
    .block {
        position: relative;
        top: 10px;
        left: 10px;
    }
</style>
```

When a vertical or horizontal offset is given, the element is moved in the opposite direction. That is, `top` moves the element down, `left` moves the element to the right, `right` moves the element to the left, and `bottom` moves the element up.

- Generally, if both top and bottom are specified, the top value is used, and the bottom value is ignored.
- Similarly, if both left and right are specified, left wins if the text direction is left to right and right wins if the text direction is right to left.



