# stitch-support

Adds helpers for adding prefixed properties and values for cross-browser compatability

## Mixins

### Helpers

There are a bunch of included helpers that provide some syntax sugar. These mixins take any value and will output the correct prefixed properties.

They are:

* appearance
* background-clip
* background-origin
* background-size
* border-radius
* box-shadow
* display-box
* box-orient
* box-align
* box-flex
* box-flex-group
* box-ordinal-group
* box-direction
* box-lines
* box-pack
* box-sizing
* column-count
* column-gap
* column-width
* column-rule-width
* column-rule-style
* column-rule-color
* column-rule

### `prefix`

Params: `$property, $value, $prefixes: $default-prefixes`

Prefix a property with the default prefixes.

```
@include prefix(border-radius, 5px, -webkit -moz)
```

Will render

```
-webkit-border-radius: 5px
-moz-border-radius: 5px
border-radius: 5px
```

Notice that it outputs the non-prefixed version as well.

### `prefix-value`

Params: `$property, $value, $prefixes: $default-prefixes`

Works the same as above but prefixes the value instead.

### `keyframes`

Params: `$name`

Renders the keyframes for webkit, gecko and w3c so you don't need to write them out separately

```sass
@include keyframes(my-animation)
  0%
    top: 0
  100%
    top: 100%
```

renders

```css
@-webkit-keyframes my-animation {
  0% {
    top: 0; }

  100% {
    top: 100%; } }

@-moz-keyframes my-animation {
  0% {
    top: 0; }

  100% {
    top: 100%; } }

@keyframes my-animation {
  0% {
    top: 0; }

  100% {
    top: 100%; } }
```

### Default Prefixes

You can alter the prefixes that are used by editing the `$default-prefixes` list. By default it looks like this:

```
$default-prefixes: -webkit, -moz !default
$default-prefixes-appearance: -webkit, -moz !default
$default-prefixes-background-clip: -webkit, -moz !default
$default-prefixes-background-origin: -webkit, -moz !default
$default-prefixes-background-size: -webkit, -moz, -o !default
$default-prefixes-border-radius: -webkit, -moz !default
$default-prefixes-box-shadow: -webkit, -moz !default
$default-prefixes-box: -webkit, -moz !default
$default-prefixes-box-sizing: -webkit, -moz !default
$default-prefixes-columns: -webkit, -moz !default
$default-prefixes-animation: -webkit, -moz, -o !default
$default-prefixes-transition: -webkit, -moz, -o !default
$default-prefixes-transform: -webkit, -moz, -o
```

You can alter the prefixes that are output by default for any of the helper mixins. The plain `$default-prefixes` will affect the `prefix` mixin when it is called without any prefixes.