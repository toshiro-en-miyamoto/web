# Basic CSS Concepts

## Selectors

| selector              | matches
|-----------------------|----------------
| `a`                   | all `a` elements
| `#header`             | `<any id="header">`
| `.nav-link`           | `<any class="nav-link">`
| attributes            |
| `[name]`              | `<any name="?????">`; with `name` of any value
| `[name="value"]`      | `<any name="value">`; the value `value`
| `[name~="v1"]`        | `<any name="v1 v2">`; the word `v1`
| `[name*="alu"]`       | `<any name="value">`; the substring `alu`
| `[name^="val"]`       | `<any name="value">`; begins with `val`
| `[name$="lue"]`       | `<any name="value">`; ends with `lue`
| combinations          |
| `div, a`              | all `div` and `a` elements
| `nav a`               | all `a` inside any `nav` element
| `nav > a`             | all `a`, one level deep in any `nav`
| `.header ~ div`       | general sibling
| `.header + div`       | adjacent sibling
| pseudo-classes        |
| `:active`             | mouse depressed but not yet released
| `:checked`            | checked or selected
| `:focus`              | currently has the focus
| `:valid`              | valid form elements
| `:invalid`            | invalid form elements
| `:visited`            | visited links
| `:first-child`        | the first child of its parent
| `:last-child`         | the last child of its parent
| `:nth-child()`        | `:nth-child(4n)`, `:nth-child(even)`
| `:nth-of-type()`      | `a:nth-of-type(1)`
| pseudo-elements       |
| `::first-line`        | the first line of a block element
| `::first-letter`      | the first letter of the first line of an element
| `::before`            | creates a new element as the first child
| `::after`             | creates a new element as the last child

## Specificity rankings

The specificity rankings of CSS rules from most specific to least specific:

1. Inline styles
2. ID selectors
3. Class selectors, attribute selectors, and pseudo-classes
4. Element selectors, and pseudo-elements

Consider an example `ul#prim-nav li.active`: the specificity value is `112`.

| fragment      | rank  | type
|---------------|-------|------
| `ul`          | 0001  | element selector
| `#prim-nav`   | 0100  | ID selector
| `li`          | 0001  | element selector
| `.active`     | 0010  | class selector
|               | 0112  | sum

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

The `rem` unit is a good choice, especially for layout properties, since the size of `1rem` remains constant throughtout the document (unlike the `em` unit). If the browser is zoomed, everything resizes nicely because it's all proportional to the base font size.

The *viewport* is the area of the page that is currently visible in your web browser. f the viewport is resized, then any elements using `vw` units will have their sizes adjusted accordingly. Because `vw` and `vh` are relative to the viewport size, they are a good chice when using responsive design techniques.


