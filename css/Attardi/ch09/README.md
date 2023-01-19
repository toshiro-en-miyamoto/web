# Transitions and Animations

- CSS transitions provide an animated transition from a start state to an end state.
- CSS animations provide animated transitions between any arbitrary number of states.
- An easing function determines the timing of the animation progress.
- Try to avoid animating layout properties, as these can negatively affect performance.
- Use the `prefers-reduced-motion` media query to improve the accessibility of your site.

## Transitions

```css
button.fancy-button {
  background: blue;
  transition: 500ms;
}
button.fancy-button:hover {
  background: red;
  transform: scale(1.1);
}
```

When the user hovers the mouse over a fancy button, the element will gradually *transition* to the new color and scale over a period of 500 milliseconds. You can think of these two states (blue background/scale 1, red background/scale 1.1) as *keyframes* in an animation.

The color will gradually change from blue to shades of purple to the final color of red. At the same time, the size will animate from `scale(1)` to `scale(1.1)`, making the element appear to grow over the course of the 500 milliseconds.

The CSS Transsitions specification is [here](https://www.w3.org/TR/css-transitions-1/).


```css
button.fancy-button {
  background: blue;
  transition: background-color 500ms,
              transform 500ms 500ms;
}
button.fancy-button:hover {
  background: red;
  transform: scale(1.1);
}
```

When specifying a transition in this way,
- the first argument is the name of the property,
- the second argument is the duration, and
- the third argument is the delay.

### The `transition-*` properties

The `transition` property is a shorthand property:

```css
button.fancy-button {
  background: blue;
  transition-property: background-color, transform;
  transition-duration: 500ms, 500ms;
  transition-delay: 0ms, 500ms;
}
button.fancy-button:hover {
  background: red;
  transform: scale(1.1);
}
```

### Easing functions

By defaut, the transition does not happen at a linear rate. That is, it appears to start out slow, speed up in the middle, then slow down again at the end. This is the default transition timing function, which is called `ease`.

Formally, these are specified as easing functions.

```css
something {
  transition-timing-function: cubic-bezier(.17, .67, .9, .6);
}
```

There are several built-in easing functions which you can specify by name instead of a `cubic-bezier` function.

| name          | `cubic-bezier`
|---------------|-----------------
| linear        | (0.00, 0.0, 1.00, 1.0)
| ease          | (0.25, 0.1, 0.25, 1.0)
| ease-in       | (0.42, 0.0, 1.00, 1.0)
| ease-out      | (0.00, 0.0, 0.58, 1.0)
| ease-in-out   | (0.42, 0.0, 0.58, 1.0)

Visit [Ceaser](https://matthewlein.com/tools/ceaser) to check how these names work.

### Step functions

Easing functions can also be specified as *step functions*. A step function divides the transition into equally sized steps in a given direction. Instead of a smooth transition like with a Bezier curve, they jump from step to step, skipping the intermediate states.

The `jump-` keywords are not supported in Internet Explorer 11. Also, at the time of writing, they are not supported in Safari.

## Animations

Animations are specified in special at-rules: `@keyframes`. The `@keyframes` rule defines the various CSS properties to be applied at given steps during the animation, and the browser will automatically animate between these states.

Each block is labeled with a percentage representing a fraction of the total animation duration.

```html
<style>
  @keyframes colors {
    0% {
      background: red;
    }
    50% {
      background: blue;
    }
    100% {
      background: green;
    }
  }
  .box {
    animation: colors 2s;
    width: 10rem;
    height: 10rem;
  }
</style>
<div class="box"></div>
```

Here, we are defining a `@keyframes` rule named `colors`.
- The initial state of an element using this animation will have a background color of red.
- At the halfway point of the animation, it will have a color of blue.
- Finally, at the end state, it will have a color of green.

Like with transitions, the browser will automatically calculate all the intermediate colors for the animation.

The `animation` property can take many forms, as it is a shorthand for several animation-related properties. Here are some examples:

```css
animation: color 2s ease-in-out 2s both
animation: pulse 2s linear infinite
```

### Animation properties

| property                      | description
|-------------------------------|-------------
| `animation-name`              | the identifier of the rule
| `animation-duration`          | the total duration of the animation
| `animation-timing-function`   | the easing function to use
| `animation-delay`             | default is 0s
| `animation-fill-mode`         | the style before and after animation
| `animation-iteration-count`   | default is only once
| `animation-direction`         | forward or backward
| `animation-play-state`        | `running` or `paused`

### Multiple animations

An element can have multiple animations applied to it. The animation shorthand property, as well as all the other animation properties, supports a comma-separated list of multiple values.

```html
<style>
  @keyframes color {
    from {
      background-color: red;
    }
    to {
      background-color: blue;
    }
  }
  @keyframes spin {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  .animate {
    width: 10rem;
    height: 10rem;
    animation: color 5s alternate infinite,
               spin 1s linear infinite;
  }
</style>
<div class="animate"></div>
```

## Property types

There are a few different categories we can put CSS properties into:

- *Layout*: such as `width`, `height`, `padding`, and `margin`; generally the most expensive to animate
- *Paint*: such as `color` or `background-image`; if overused, they can still cause performance issues
- *Composite*: such as `transform` and `opacity`; much cheaper than the other property types

## Accessibility

You can, and should, detect this scenario by using the `prefers-reduced-motion` *media query* and adjusting (or disabling) your animations accordingly.

```html
<style>
  @keyframes spin {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(360deg);
    }
  }
  .loader {
    width: 10rem;
    height: 10rem;
    background: skyblue;
    animation: spin 500ms linear infinite;
  }
  @media (prefers-reduced-motion: reduce) {
    .loader {
      animation: none;
    }
  }
</style>
<div class="loader"></div>
```

Without `@media (prefers-reduced-motion: reduce)`, the `.loader` element results in a square that spins very quickly, making one full rotation every 500ms. This could trigger seizures or other issues, as it moves very fast.

The `prefers-reduced-motion` media query is not supported in Internet Explorer.
