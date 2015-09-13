# Sass propTypes

Inspired by React's [PropTypes validation](https://facebook.github.io/react/docs/reusable-components.html#prop-validation), Sass PropTypes helps you validate required arguments for your Sass mixins. For example, imagine you've written a mixin that compiles buttons. The mixin accepts one of several `$style` arguments:

```
@mixin button($style: default) {
  @if $style == 'default' {
    // Default button styles
  }

  @if $style == 'primary' {
    // Primary button styles
  }

  @if $style == 'negative' {
    // Negative button styles
  }

  @if $style == 'positive' {
    // Positive button styles
  }
}
```

The mixin works well so long as you pass in a valid `$style` argument (one of `default`, `primary`, `negative`, or `positive`). But what happens if you accidentally pass in a invalid argument, like `brand` or even a misspelling like `positve`? Well, nothing. You'll just lose some time debugging your compiled CSS.

This where Sass propTypes steps in. If you make a mistake and pass in a invalid argument, PropTypes will throw a warning in the console.

## How to use

Simply include the propTypes mixin in the mixin you wish to validate. For the example above:

```
@mixin button($style: default) {
  $propTypes: default, primary, negaive, positive;
  @include propTypes($style, $propTypes);

  ...
}
```

The `propTypes` mixin accepts two arguments:

* `$prop` the mixin argument you wish to validate.
* `$propType` a list of valid arguments.

If you were to pass in an invalid argument, the console will provide a helpful warning, with a stack trace that tells you exactly where to look:

```
WARNING: prmary must be one of default, primary, positive, negative
	on line 5 of src/stylesheets/library/_proptypes.scss
	from line 43 of src/stylesheets/library/_buttons.scss
	from line 40 of src/stylesheets/buttons/_base.scss
```

## Get to work

Sass propTypes is available on Bower...

```
$ bower install sass-proptypes
```

...and NPM...

```
$ npm install sass-proptypes
```

## Improvements

Got an idea to make this better? PRs welcome.
