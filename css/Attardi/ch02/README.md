# CSS Selectors

- The most commonly used selectors are element, ID, class, and attribute selectors.
- Combinators can be used to create even more specific selectors.
- Multiple selectors can match an element.
- Conflicts are resolved by using the rule that is more specific.

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
| compound selectors    |
| `div.one`             | all `div` with a class of `one`
| `div.one.two`         | all `div` with a class of both `one` and `two`
| `div.one[name="val"]` | all `div` and `one` with `name` attrib `val`
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
| `:root`               | usually the `html` element
| `:not()`              | e.g., `div:not(.fancy)`
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
