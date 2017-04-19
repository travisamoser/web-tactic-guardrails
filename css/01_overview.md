# CSS
Use Sass (SCSS) syntax. See the [Sass section](sass/01_overview.md) for details on Sass guardrails.

CSS files should be linted with [CSSLint](https://www.npmjs.com/package/csslint) as an integrated part of the site build process. See the CSSLint configuration file for recommended settings. *Add config file

## Normalize your CSS, don't reset it
From [Continue Normalising Your CSS](https://csswizardry.com/2016/10/continue-normalising-your-css/):

When we talk about Normalize.css, we’re not talking about making websites look the same in every browser, we’re talking about providing a consistent and bug-free baseline. We’re talking about making a consistent baseline to make development easier. Normalize.css isn’t for our users or our clients, it’s for us as developers. We should always put the user first, but developer convenience is still a thing.

From Nicolas’ [article in which he introduces Normalize.css](http://nicolasgallagher.com/about-normalize-css/):
> Resets impose a homogeneous visual style by flattening the default styles for almost all elements. In contrast, [N]ormalize.css retains many useful default browser styles.
So please, do keep using Normalize.css. It makes your life easier, and with an absolute minimal overhead: v5.0.0 is a mere 984 bytes after gzip. For context, that represents less than 1.3% of the average CSS project.

## Inline Styles
Don't use inline styles. They are difficult to maintain and make responsive design difficult.

## CSS Shorthand
In general, don't use the CSS shorthand properties because it often unsets other properties that we never intended to modify. Read more in [CSS Shorthand Syntax Considered an Anti-Pattern](https://csswizardry.com/2016/12/css-shorthand-syntax-considered-an-anti-pattern/)

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
- Non BEM
- @import

## Line-Height is Unitless
[Line-Height is Unitless](http://allthingssmitty.com/2017/01/30/nope-nope-nope-line-height-is-unitless/)
```
// Yep
.selector (
	line-height: 1.2;
);

// Nope
.selector (
	line-height: 18px;
);
```