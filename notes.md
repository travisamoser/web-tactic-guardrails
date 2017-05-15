# From meeting on 5/12/17
EditorConfig
- remove indent_size and let user settings control that?

Commenting code section?

HTML
 - Reword "Avoid blocking parsing with JS files"

CSS
 - don't use transition all (may be in the linter)

Images
 - images are optimized in build
 - remove reference to CrownPeak
 - orphan check in build process?

# HTML
Use HTML entities
- finds non-HTML entity versions of special characters
   - `[“”‘’°†‡®©™‹›«»⟨⟩⟪⟫❮❯]`

## HTML hint rules to ignore
- [tag-self-close](https://github.com/yaniswang/HTMLHint/wiki/Tag-self-close)

# CSS
- NPM package to remove unused CSS classes?
- clarify ruleset. Put background at end?
- attach media queries to linked stylesheets?
  - mixin method?

## SASS lint rules to ignore
- so many rules. Just start using it and adjust rules as we go

 # Git
- Lead dev has to accept pull requests. The lead dev does a code review before accepting pull request
- Never merge your own feature branches into develop, another developer should code review it and then merge it (check with Andy on this)
 - feature branch naming rules
  - feature/XXX
  - fix/XXX
  - refactor/XXX?
  - tie to an issue

# JS
 - ES6 + Babel as part of build process
 - ESLint

# Dustin
 - incorporate linters in build
 - 7-1 pattern in build
 - ES6 + Babel
 - SVGOMG
 - ImageMin
