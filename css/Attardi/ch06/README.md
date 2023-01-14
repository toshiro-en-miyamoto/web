# Text Styling

## Fonts

- `font-family:`
  - `monospace`, `serif`, `sans-serif`
- `font-size:`
  - absolute keywords: `xx-small`, `x-small`, `small`, `medium`, `large`, `x-large`, `xx-large`, `xxx-large`
  - relative keywords: `larger`, `smaller`
  - units for a value: `em`, `rem`, `%`, etc.
- `color:`
  - The `color` property controls the element's text color (and text decorations such as underlines). It also sets the *current color*. This is a special value called `currentColor` that resolves to the text color, which can be referenced from other properties.
  - values: named colors, RGB and HSL values, `currentColor`
- `font-weight:`
  - numeric values:
    - keywords: `100`, `200`, ..., `900`
    - 1 ≤ value ≤ 1000 since CSS Fonts Level 4
  - absolute keywords: `normal`, `bold`
    - `normal` is 400, and `bold` is 700
  - relative keywords: `lighter`, `bolder`
- `font-style:`
  - keywords: `normal`, `italic`, `oblique`
- `text-decoration:` (a shorthand for)
  - `text-decoration-line:`
    - keywords: `none`, `underline`, `overline`, `line-through`, `blibk`
  - `text-decoration-color:`
    - values: named colors, RGB and HSL values, `currentColor`
  - `text-decoration-style:`
    - keywords: `solid`, `double`, `dotted`, `dashed`, `wavy`
  - `text-decoration-thickness:`
    - keywords: `auto`, `from-font`
    - units for a value: `em`, `rem`, `%`, etc.
- `text-transform:`
  - keywords: `none`, `capitalize`, `uppercase`, `lowercase`
- `letter-spacing:`
  - keywords: `normal`
  - units for a value: `em`, `rem`, `%`, etc.
- `font-variant:` (a shorthand for)
  - `font-variant-alternates:`
  - `font-variant-caps:`
  - `font-variant-east-asian:`
  - `font-variant-emoji:`
  - `font-variant-ligatures:`
  - `font-variant-numeric:`
  - `font-variant-position:`

## Text layout

- `text-indent:`
  - units for a value: `em`, `rem`, `%`, etc.
- `white-space:`
  - keywords: `normal`, `nowrap`, `pre`, `pre-wrap`, `pre-line`, `break-spaces`
- `text-overflow:`
  - keywords: `clip`, `ellipsis`
- `text-align:`
  - keywords: `left`, `right`, `center`, `justify`
- `vertical-align:`
  - keywords: `baseline`, `sub`, `super`, `text-top`, `text-bottom`, `middle`, `top`, `bottom`
  - units for a value: `em`, `rem`, `%`, etc.
- `text-shadow:`
  - four values: X and Y offsets, blur radius, color

## Web fonts

There are several different supported web font formats:

- Web Open Font Format version 1 or 2 (WOFF/WOFF2)
- Embedded Open Type (EOT)
- TrueType Font (TTF)
- Scalable Vector Graphics (SVG)

A `@font-face` rule declares a new font. The desired name of the font is given with the `font-family` property, and one or more source URLs are given with the `src` property.

```
@font-face {
  font-family: 'SomeWebFont';
  src:
    url('/some-font.woff2') format('woff2'),
    url('/some-font.woff') format('woff');
}
body {
  font-family: SomeWebFont, Arial, sans-serif;
}
```

Usually, a given web font file is only a single weight or style version of the font. This means there is one font file for the normal version and another for the bold version. They both must be registered in a separate `@font-face` rule under the same `font-family`.

```
@font-face {
  font-family: 'SomeWebFont';
  src: url('/some-font.woff2') format('woff2');
  font-weight: 400;
}
@font-face {
  font-family: 'SomeWebFont';
  src: url('/some-font-bold.woff2') format('woff2');
  font-weight: 700;
}
```

The browser must download the web font files before they can be used. If this is not done quickly, the browser may render the site in a fallback font while the web font is still loading. Once the font is loaded, the text is re-rendered in the new font. This results in unstyled text briefly appearing before being replaced by the correctly styled text:

- the *flash of unstyled text*
- the *flash of invisible text*
