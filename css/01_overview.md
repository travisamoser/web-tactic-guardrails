# CSS
Use a Sass preprocessor (SCSS syntax) to buid your CSS. See the [Sass section](sass/01_overview.md) for details on the Sass guardrails.

## Linting
CSS files should be are not linted after compilation. CSS code is linted pre-compilation by [SASS-Lint](https://www.npmjs.com/package/sass-lint).

## Syntax and formatting
Roughly, we want:
- tabs, not spaces;
- consistent indentation
- ideally, 80-characters wide lines;
- properly written multi-line CSS rules;
- meaningful use of whitespace;
- no commented-out code;
- no dead code (unused code).

```css
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

### CSS Ruleset
At this point, this is mostly revising what everybody knows, but here is how a CSS ruleset should be written (at least, according to most guidelines, including CSS Guidelines):

- related selectors on the same line; unrelated selectors on new lines;
- the opening brace ({) spaced from the last selector by a single space;
- each declaration on its own new line;
- a space after the colon (:);
- a trailing semi-colon (;) at the end of all declarations;
- the closing brace (}) on its own new line;
- a new line after the closing brace }.

Illustration:
```css
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
	display:block;
	overflow: hidden;
	margin:0 auto }
```

### Declaration Sorting
Concretely, there are two factions here:

- sticking to the alphabetical order;
- ordering declarations by type (position, display, colors, font, miscellaneous…).

Order declarations based on type, not alphabetically. Alphabetal ordering separates properties that are logically linked (height and width, margins and padding, etc...)

Here's an example of ordering by type:
```css
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

	/* Color & Text */
	color: #fff;
	font-family: sans-serif;
	font-size: 16px;
	line-height: 1.4;
	text-align: right;

	/* Background, Other */
	background: #000;
	cursor: pointer;
}
```

## Normalize your CSS, don't reset it
From [Continue Normalising Your CSS](https://csswizardry.com/2016/10/continue-normalising-your-css/):

When we talk about Normalize.css, we’re not talking about making websites look the same in every browser, we’re talking about providing a consistent and bug-free baseline. We’re talking about making a consistent baseline to make development easier. Normalize.css isn’t for our users or our clients, it’s for us as developers. We should always put the user first, but developer convenience is still a thing.

From Nicolas’ [article in which he introduces Normalize.css](http://nicolasgallagher.com/about-normalize-css/):
> Resets impose a homogeneous visual style by flattening the default styles for almost all elements. In contrast, [N]ormalize.css retains many useful default browser styles.
So please, do keep using Normalize.css. It makes your life easier, and with an absolute minimal overhead: v5.0.0 is a mere 984 bytes after gzip. For context, that represents less than 1.3% of the average CSS project.

## Box-sizing fix
Box sizing is set universally to `border-box`. See [Box Sizing](https://css-tricks.com/box-sizing/#article-header-id-6)
```css
html {
	box-sizing: border-box;
}
*, *:before, *:after {
	box-sizing: inherit;
}
```

## Inline styles
Don't use inline styles. They are difficult to maintain and make responsive design difficult.

## CSS shorthand
In general, don't use the CSS shorthand properties because it often unsets other properties that we never intended to modify. Read more in [CSS Shorthand Syntax Considered an Anti-Pattern](https://csswizardry.com/2016/12/css-shorthand-syntax-considered-an-anti-pattern/)

## Line-height is unitless
[Line-Height is Unitless](http://allthingssmitty.com/2017/01/30/nope-nope-nope-line-height-is-unitless/)
```css
/* Yep */
.selector {
	line-height: 1.2;
};

/* Nope */
.selector {
	line-height: 18px;
};
```

## A note on backgrounds images and responsive design

If you include a background image in your CSS and then override it with another background image in a media query, both background image files will be downloaded by the browser. If you need separate background images for different displays, as a best practice you should wrap each background image in a media query.
```css
/* In desktop view, browser will download both images */
body {
    background-image: src(../img/body-bg_mobile.jpg);
}
@media only screen and (min-width: 768px) {
	body {
		background-image: src(../img/body-bg_desktop.jpg);
	}
}

/* Browser will only download the appropriate image, regardless of screen size */
@media only screen and (max-width: 767.99px) {
	body {
		background-image: src(../img/body-bg_mobile.jpg);
	}
}
@media only screen and (min-width: 768px) {
	body {
		background-image: src(../img/body-bg_desktop.jpg);
	}
}
```

## Transition links and buttons on hover and focus
Transition [animatible properties](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties) of links and buttons on hover and focus. This creates a less jarring experience for the user.
```css
a {
	color: #337ab7;
	transition: color 0.2s ease-in-out;
}
a:hover {
	color: #23527c;
}
```

## Avoid transitioning `all`
Transitioning `all` properties can lead to unexpected results and may cause performance issues. It's better to be explicit about what properties should be transitioned.
```css
/* Yep */
button {
	color: #fff;
	background-color: #428bca;
	transition: 0.2s ease-in-out;
	transition-property: color, background-color;
}
button:hover {
	color: #eee;
	background-color: #3071a9;
}

/* Nope */
button {
	color: #fff;
	background-color: #428bca;
	transition: all 0.2s ease-in-out;
}
button:hover {
	color: #eee;
	background-color: #3071a9;
}
```

## Code Smells
> How can you tell if your CSS code smells? What are the signs that the code is sub-optional, or that the developer hasn’t done a good job? What do you look for in the code to determine how good or bad it is?

[Part 1:](https://csswizardry.com/2012/11/code-smells-in-css/)
- Undoing Styles
- Magic Numbers
- Qualified Selectors
- Absolute Values
- Brute Forcing
- Dangerous Selectors
- Reactive !important
- IDs
- Loose Class Names

[Part 2:](https://csswizardry.com/2017/02/code-smells-in-css-revisited/)
- @extend
- String Concatenation for Classes
- Background Shorthand
- Duplicated Key Selectors
- Classes in Wrong Components
- `@import`
