# Sass
Sass should generally follow [Sass Guidelines](https://sass-guidelin.es). I've outlined general guidelines and exceptions here. See the [Sass Guidelines](https://sass-guidelin.es) for more details.

These guidelines can be enforced by adding [SCSS-Lint](https://github.com/brigade/scss-lint) to the build process. *Insert config file modeled after [the one in Sass Guidelines](https://sass-guidelin.es/#scss-lint).

## Syntax and formatting
Adding to the CSS guidelines, we want to pay attention to:

- local variables being declared before any declarations, then spaced from declarations by a new line;
- mixin calls with no @content coming before any declaration;
- nested selectors always coming after a new line;
- mixin calls with @content coming after any nested selector;
- no new line before a closing brace (}).

Illustration:
```css
.foo, .foo-bar,
.baz {
	$length: 42em;

	@include ellipsis;
	@include size($length);
	display: block;
	overflow: hidden;
	margin: 0 auto;

	&:hover {
		color: red;
	}

	@include respond-to('small') {
		overflow: visible;
	}
}
```

### Selector Nesting
Avoid selector nesting as much as possible. The [@at-root](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#at-root) directive can be used to reduce nesting while still keeping rules in logical placement.

## Architecture
One of the main benefits of using a CSS preprocessor is having the ability to split the codebase over several files without impacting performance (like the `@import` CSS directive would do). Thanks to Sass’s overload of the `@import` directive, it is perfectly safe (and actually recommended) to use as many files as necessary in development, all compiled into a single stylesheet when going to production.

On top of that, I cannot stress enough the need for folders, even on small scale projects. At home, you don’t drop every sheet of paper into the same box. You use folders; one for the house/flat, one for the bank, one for bills, and so on. There is no reason to do otherwise when structuring a CSS project. Split the codebase into meaningful separated folders so it is easy to find stuff later when you have to come back to the code.

### Components
Components can be anything, as long as they:

- do one thing and one thing only;
- are re-usable and re-used across the project;
- are independent.

For instance, a search form should be treated as a component. It should be reusable, at different positions, on different pages, in various situations. It should not depend on its position in the DOM (footer, sidebar, main content…).

### Component Structure
Ideally, components should exist in their own Sass partial (within the `components/` folder), such as `components/_button.scss`. The styles described in each component file should only be concerned with:

- the style of the component itself;
- the style of the component’s variants, modifiers, and/or states;
- the styles of the component’s descendents (i.e. children), if necessary.

A component partial can include component-specific variables, placeholders, and even mixins and functions. Keep in mind, though, that you should avoid referencing (i.e. `@import`-ing) component files from other component files, as this can make your project’s dependency graph an unmaintainable tangled mess.

Here is an example of a button component partial:
```css
// Button-specific variables
$button-color: $secondary-color;

// … include any button-specific:
// - mixins
// - placeholders
// - functions

/**
 * Buttons
 */
.button {
	@include vertical-rhythm;
	display: block;
	padding: 1rem;
	color: $button-color;
	// … etc.

	/**
	 * Inlined buttons on large screens
	 */
	@include respond-to('medium') {
		display: inline-block;
	}
}

/**
 * Icons within buttons
 */
.button > svg {
	fill: currentcolor;
	// … etc.
}

/**
 * Inline button
 */
.button--inline {
	display: inline-block;
}
```

### The 7-1 Pattern
I usually go with what I call the 7-1 pattern: 7 folders, 1 file. Basically, you have all your partials stuffed into 7 different folders, and a single file at the root level (usually named `main.scss`) which imports them all to be compiled into a CSS stylesheet.

- `base/`
- `components/`
- `layout/`
- `pages/`
- `themes/`
- `abstracts/`
- `vendors/`

And of course:

- `main.scss`

See [The 7-1 Pattern Section of Sass Guidelines](https://sass-guidelin.es/#the-7-1-pattern) for more details. Also a there is a ready [boilerplate](https://github.com/HugoGiraudel/sass-boilerplate) on Github.

## Responsive Web Design and breakpoints
Breakpoints should not be named after devices but something more general.

```css
// Yep
$breakpoints: (
	'medium': (min-width: 800px),
	'large': (min-width: 1000px),
	'huge': (min-width: 1200px),
);

// Nope
$breakpoints: (
	'tablet': (min-width: 800px),
	'computer': (min-width: 1000px),
	'tv': (min-width: 1200px),
);
```

See [The 100% Correct Way to do CSS Breakpoints](https://medium.freecodecamp.com/the-100-correct-way-to-do-css-breakpoints-88d6a5ba1862) for why our breakpoints aren't based on specific device sizes (320px, 768px, 1024px, etc..).

Additionally, if using a combination of `min-width` and `max-width` media queries, beware of the edge case where the browser's current zoom state could cause it to be in-between the breakpoints.

```css
// Yep
$breakpoints: (
	'small': (max-width: 799.99px),
	'medium': (min-width: 800px),
	'large': (min-width: 1000px),
);

// Nope
$breakpoints: (
	'small': (max-width: 799px),
	// zoomed browser could potentially fall in this 1px gap
	'medium': (min-width: 800px),
	'large': (min-width: 1000px),
);
```

Or even better, your media queries should be mobile-first and avoid mixing `min-width` and `max-width`.

## Sass's media query duplication problem
Consider structuring your components to use mixins to [solve Sass's media query duplication problem and enhance your workflow](https://medium.com/front-end-developers/the-solution-to-media-queries-in-sass-5493ebe16844)

## Extend
In short, don't use the `@extend` directive. A more nuanced opinion is that you can use it as long as you fully understand the side effects of it's usage (bloat being the major one) and mitigate it accordingly.

Use `@extend` only for maintaining relationships within selectors. If two selectors are characteristically similar, that is the perfect use-case for `@extend`. If they are unrelated but share some rules, a `@mixin` might suit you better. More on how to choose between the two in [this write-up](http://csswizardry.com/2014/11/when-to-use-extend-when-to-use-a-mixin/).
