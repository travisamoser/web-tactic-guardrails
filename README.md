# web-tactic-guardrails

Instructions for the feeding and care of your web tactic project.

## The Golden Rule
Leave your code the state you would have others leave their code for you.

## General formatting

### Tabs, not Spaces
Use tabs instead of spaces. Tabs have a few advantages.
- They result in marginally lower file size (one bit instead of 2 or 4)
- Their apparent width can be adjusted based on user preferences (they can appear to be the equivalent of 2 or 4 spaces)
- They require less key presses to navigate around a file (one hit of the arrow key instead of 2 or 4).

### Commented-Out Code
Don't commit commented-out code that you are "saving just in case." That's what version control is for. If you need it, you can just pull your old code from the repo's history.

### Line-length
For CSS, SASS, and JS files, lines should be 80-characters wide or less. For HTML files, line-breaks should be added logically, not to keep line lengths below 80 characters. The developer can toggle word wrap in their code editor to visually wrap lines to avoid horizontal scrolling.

### Minification
Generally files should be minified to remove whitespace resulting in reduced file size. Code should not be obfuscated or compressed in such a way as to modify the code. In the final build, CSS and JS files should be minified and (where it makes sense) combined. HTML files should be minified in the final build. This should be a part of the build process--not done manually.

## Workspace Config File
Each project should include a workplace settings config file that the developer can use install in their code editor of choice to keep the project formatting consistent.
[insert links to config files for VSCode and Atom]

## Topics

### HTML
See the [HTML Overview document](html/01_overview.md)

### CSS
See the [CSS Overview document](css/01_overview.md)

### Sass
See the [Sass Overview document](sass/01_overview.md)

### JavaScript
See the [JavaScript Overview document](js/01_overview.md)

### Images
See the [Images Overview document](images/01_overview.md)

### Git
See the [Git](git/01_overview.md)

### Build process

Keep build processes simple and easy to get up and running. Your project should be structured so that all anyone has to do to get to work on your project is:
1. Clone the repository from Github
2. Navigate the repository folder
3. Run `npm install`
4. Read your `readme.md` file to see what commands to run
4. Then run the appropriate command to build the project. All appropriate files should be watched and rebuilt on change automatically.

*Link to handlebars POC build