# Images

## General Usage
Don't use images unless they are absolutely necessary.

Create design elements with CSS, not images. Many icons can be generated with unicode characters. Menu hamburger icons can be created with pseudo elements which also have the advantage of being animatable. Arrows and carets can be created with borders.

## SVGs
If you have to use an image, use an SVG when possible. Optimize your SVGs in your build process or by using [SVG OMG](https://jakearchibald.github.io/svgomg/)

## PNGs, JPGs
If you have to use an image and it can't be SVG, optimize it in your build process, manually with command line tools, or with an app like [ImageOptim](https://imageoptim.com/mac) for Mac or [something similar for Windows](https://imageoptim.com/versions.html#windows).

## Orphans
Orphan images (images that are not linked to from anywhere) should not be committed to the repo or uploaded to CrownPeak. Ideally, these images should be deleted as soon as the link to them is removed from the code. Since this doesn't always happen, it's a good idea to a check for orphans before pushing to the server.

### Checking for Orphans
You can check for orphans manually by doing a global search in your code editor for the images file name.

If the site is already live and you want to check to see what images are being used on the live site, you can scrape the site with [Wget](https://www.gnu.org/software/wget/). This command will scrape the entire site: `wget -r -E -k -p -D folderName http://www.yoururl.com/`.

From the [Wget Manual](https://www.gnu.org/software/wget/manual/wget.html):
* -r - recursive
* -E - adjust extensions (convert .aspx to .html)
* -k - convert documents for local viewing
* -p - download all files necessary to display a given HTML page (images, stylesheets)
* -D - limit domains
