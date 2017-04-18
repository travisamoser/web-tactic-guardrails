# Sass
Sass should generally follow [Sass Guidelines](https://sass-guidelin.es). I've outlined general guidelines and exceptions here. See the [Sass Guidelines](https://sass-guidelin.es) for more details.

## Syntax and formatting
Roughly, we want:
- tabs, not spaces;
- ideally, 80-characters wide lines;
- properly written multi-line CSS rules;
- meaningful use of whitespace.

```
// Yep
.foo {
	display: block;
	overflow: hidden;
	padding: 0 1em;
}

// Nope
.foo {
		display: block; overflow: hidden;

		padding: 0 1em;
}
```

## CSS Ruleset
At this point, this is mostly revising what everybody knows, but here is how a CSS ruleset should be written (at least, according to most guidelines, including CSS Guidelines):

- related selectors on the same line; unrelated selectors on new lines;
- the opening brace ({) spaced from the last selector by a single space;
- each declaration on its own new line;
- a space after the colon (:);
- a trailing semi-colon (;) at the end of all declarations;
- the closing brace (}) on its own new line;
- a new line after the closing brace }.

Illustration:
```
// Yep
.foo, .foo-bar,
.baz {
	display: block;
	overflow: hidden;
	margin: 0 auto;
}

// Nope
.foo,
.foo-bar, .baz {
		display: block;
		overflow: hidden;
		margin: 0 auto }
```

Adding to those CSS-related guidelines, we want to pay attention to:

- local variables being declared before any declarations, then spaced from declarations by a new line;
- mixin calls with no @content coming before any declaration;
- nested selectors always coming after a new line;
- mixin calls with @content coming after any nested selector;
- no new line before a closing brace (}).

Illustration:
```
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

## Declaration Sorting
Concretely, there are two factions here:

- sticking to the alphabetical order;
- ordering declarations by type (position, display, colors, font, miscellaneous…).

Order declarations based on type, not alphabetically. Alphabetal ordering separates properties that are logically linked (height and width, margins and padding, etc...)

Here's an example of ordering by type:
```
.selector {
	/* Display & Positioning */
	display: block;
	float: none;
	clear: none;
	position: absolute;
	z-index: 10;
	top: 0;
	right: 0;
	opacity: 1;

	/* Box model should be ordered OUTSIDE-IN. */
	/* So first margin, then border, then padding, and finally dimensions */
	box-sizing: border-box;
	margin: 10px;
	border: 10px solid #333;
	padding: 10px;
	width: 100px;
	height: 100px;
	overflow: hidden;
	background: #000;

	/* Color & Text */
	color: #fff;
	font-family: sans-serif;
	font-size: 16px;
	line-height: 1.4;
	text-align: right;

	/* Other */
	cursor: pointer;
}
```

## Selector Nesting
Avoid selector nesting as much as possible. The [@at-root](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#at-root) directive can be used to reduce nesting while still keeping rules in logical order.
