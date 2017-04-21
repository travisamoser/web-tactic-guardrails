# web-tactic-guardrails

Instructions for the feeding and care of your web tactic project.

## General formatting
Use tabs instead of spaces. Tabs have a few advantages.
- They result in lower file size (one bit instead of 2 or 4)
- Their apparent width can be adjusted based on user preferences (they can appear to be the equivalent of 2 or 4 spaces)
- They require less key presses to navigate around a file (one hit of the arrow key instead of 2 or 4).

For CSS, SASS, and JS files, lines should be 80-characters wide or less. For HTML files, line-breaks should be added logically, not to keep line lengths below 80 characters. The developer can toggle word wrap in their code editor to visually wrap lines to avoid horizontal scrolling.

Each project should include a workplace settings config file that the developer can use install in their code editor of choice to keep the project formatting consistent.
[insert links to config files for VSCode and Atom]

## HTML
See the [HTML Overview document](html/01_overview.md)

## CSS
See the [CSS Overview document](css/01_overview.md)

## Sass
See the [Sass Overview document](sass/01_overview.md)

## JS

## Images
See the [Images Overview document](images/01_overview.md)

## Git best practices

## Build process

Keep build processes simple--inevitably you will be pulled off the project and someone else will have to work on it. If your project has dependencies that you haven't listed in the package.json file, your going to have a bad time.

Your project should be structured so that all anyone has to do to get to work on your project is:
1. Clone the repository from Github
2. Navigate the repository folder
3. Run `npm install`
4. Read your `readme.md` file to see what commands to run
4. Then run the appropriate command to build the project. All appropriate files should be watched and rebuilt on change automatically.
