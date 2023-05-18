# The HTML5 input types

The previous article covers the original values of the type attribute available since the early days of HTML. Now we'll look at the functionality of newer form controls in detail, including some new input types, which were added in HTML5.

## Email address field

The value `email` for the `type` attribute:

```html
<input type="email" id="email" name="email" multiple />
```

When the type `email` is used, the user is required to type a valid email address into the field. Any other content causes the browser to display an error when the form is submitted.

You can also use the `multiple` attribute in combination with the email input type to allow several email addresses to be entered in the same input (separated by commas).

On some devices — notably, touch devices with dynamic keyboards like smartphones — a different virtual keypad might be presented that is more suitable for entering email addresses, including the `@` key.

This is another good reason for using these newer input types, improving the user experience for users of these devices.

## Search field

Search fields are intended to be used to create search boxes on pages and apps.

```html
<input type="search" id="search" name="search" />
```

The main difference between a `text` field and a `search` field is how the browser styles its appearance. Often, `search` fields are rendered with rounded corners; they also sometimes display an ⊗, which clears the field of any value when clicked. Additionally, on devices with dynamic keyboards, the keyboard's enter key may read "*search*", or display a magnifying glass icon.

## Phone number field

A special field for filling in phone numbers can be created using `tel` as the value of the type attribute:

```html
<input type="tel" id="tel" name="tel" />
```

When accessed via a touch device with a dynamic keyboard, most devices will display a numeric keypad when `type="tel"` is encountered, meaning this type is useful whenever a numeric keypad is useful, and doesn't just have to be used for telephone numbers.

Due to the wide variety of phone number formats around the world, this type of field does not enforce any constraints on the value entered by a user (this means it may include letters, etc.).

As we mentioned earlier, the `pattern` attribute can be used to enforce constraints.

## URL field

A special type of field for entering URLs can be created using the value `url` for the `type` attribute:

```html
<input type="url" id="url" name="url" />
```

It adds special validation constraints to the field. The browser will report an error if no protocol (such as `http:`) is entered, or if the URL is otherwise malformed.

On devices with dynamic keyboards, the default keyboard will often display some or all of the colon, period, and forward slash as default keys.

## Numeric field

Controls for entering numbers can be created with an `<input>` type of `number`.

- This control looks like a text field but allows only floating-point numbers, and
- usually provides buttons in the form of a spinner to increase and decrease the value of the control.
- On devices with dynamic keyboards, the numeric keyboard is generally displayed.

With the `number` input type, you can constrain the minimum and maximum values allowed by setting the `min` and `max` attributes.

```html
<input type="number" name="age" id="age" min="1" max="10" step="2" />
<input type="number" name="change" id="pennies" min="0" max="1" step="0.01" />
```

You can also use the step attribute to set the increment increase and decrease caused by pressing the spinner buttons.

- By default, the number input type only validates if the number is an integer.
- To allow float numbers, specify `step="any"`.
- If omitted, the `step` value defaults to 1, meaning only whole numbers are valid.

The `number` input type makes sense when the range of valid values is limited, for example a person's age or height.

- If the range is too large for incremental increases to make sense (such as USA ZIP codes, which range from `00001` to `99999`), the `tel` type might be a better option; it provides the numeric keypad while forgoing the number's spinner UI feature.

## Slider controls

![Slider](./slider.png)

```html
<form>
  <h2>Slider control</h2>
  <label for="price">House price: </label>
  <input type="range" name="price" id="price"
        min="50000" max="500000" step="100" value="250000" />
  <output class="price-output" for="price"></output>
</form>
<script>
  const price = document.querySelector("#price");
  const output = document.querySelector(".price-output");
  output.textContent = price.value;
  price.addEventListener("input", () => {
    output.textContent = price.value;
  });
</script>
```

One problem with sliders is that they don't offer any kind of visual feedback as to what the current value is. This is why we've included an `<output>` element to contain the current value.

## Date and time pickers

Let's look at the different available types in brief.

- `<input type="datetime-local">` to pick a date with time with no specific time zone information.
- `<input type="month">` to pick a month with a year.
- `<input type="time">` to pick a time value.
- `<input type="week">` to pick a week number and its year.
