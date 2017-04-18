# web-tactic-guardrails

Instructions for the feeding and care of your web tactic project.

## General formatting
Use tabs instead of spaces. Tabs have a few advantages.
- They result in lower file size (one bit instead of 2 or 4)
- Their apparent width can be adjusted based on user preferences (they can appear to be the equivalent of 2 or 4 spaces)
- They require less key presses to navigate around a file (one hit of the arrow key instead of 2 or 4).

Each project should include a workplace settings config file that the developer can use install in their code editor of choice to keep the project formatting consistent.
[insert links to config files for VSCode and Atom]

## HTML
See the [HTML Overview document](html/01_overview.md)

## CSS
See the [CSS Overview document](css/01_overview.md)

## Sass
See the [Sass Overview document](sass/01_overview.md)

### Syntax and Formatting

Sass files should be broken out logically into components and imported into one main.scss file.

## JS

## Images
Don't use unnecessarry images.

Handle design elements with CSS. Many icons can be generated with unicode characters. Menu hamburger icons can be created with pseudo elements and have the advantage of being animatable. Arrows and carets can be created with borders.

If you have to use an image, use an SVG when possible. Optimize your SVGs in your build process or by using [SVG OMG](https://jakearchibald.github.io/svgomg/)

If you have to use an image and it can't be SVG, optimize it in your build process, manually with command line tools or with an app like [ImageOptim](https://imageoptim.com/mac) for Mac or [something similar for Windows](https://imageoptim.com/versions.html#windows).

### A note on backgrounds images and responsive design

If you include a background image in your CSS and then override it with another background image in a media query, both background image files will be downloaded by the browser. As a best practice you should wrap each background image in a media query.
```
// In desktop view, browser will download both images
body {
    background-image: src(../img/body-bg_mobile.jpg);
}
@media only screen and (min-width: 768px) {
	body {
		background-image: src(../img/body-bg_desktop.jpg);
	}
}

// Browser will only download the appropriate image, regardless of screen size
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

## Git best practices

## Build process

Keep build processes simple--inevitably you will be pulled off the project and someone else will have to work on it. If your project has dependencies that you haven't listed in the package.json file, your going to have a bad time.

Your project should be structured so that all anyone has to do to get to work on your project is:
1. Clone the repository from Github
2. Navigate the repository folder
3. Run `npm install`
4. Read your `readme.md` file to see what commands to run
4. Then run the appropriate command to build the project. All appropriate files should be watched and rebuilt on change automatically.
