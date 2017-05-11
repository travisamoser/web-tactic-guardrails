# JavaScript

## Syntax and formatting
Roughly, we want:
- tabs, not spaces;
- consistent indentation
- ideally, 80-characters wide lines;
- meaningful use of whitespace;
- no commented-out code;
- no dead code (unused code).

## Linting
JavaScript files should be linted with [ESLint](https://www.npmjs.com/package/eslint) as an integrated part of the site build process. See the Handlebars POC for configuration.

## Version
For multi-page sites utilizing the Gulp + Handlebars build process, use ES6 syntax with Babel for pre-compilation.

For single-page sites, use ES5 syntax.

## Style
For multi-page sites using ES6, follow the [AirBNB ES6 Styleguide](https://github.com/airbnb/javascript)

For single-page sites using ES5, follow the [AirBNB ES5 Styleguide](https://github.com/airbnb/javascript/tree/es5-deprecated/es5)
