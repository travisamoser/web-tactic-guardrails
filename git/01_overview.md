# Git

## Workflow
Generally, we use the [Feature Branch Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows#feature-branch-workflow).

> The core idea behind the Feature Branch Workflow is that all feature development should take place in a dedicated branch instead of the `master` branch. This encapsulation makes it easy for multiple developers to work on a particular feature without disturbing the main codebase. It also means the `master` branch will never contain broken code, which is a huge advantage for continuous integration environments.

See Atlassian's [Feature Branch Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows#feature-branch-workflow) documentation for more details.

## Feature branch naming standards
Features should be named by one of the following standards
- `feature/XXXXXXX` (for features)
- `fix/XXXXXXX` (for bug fixes)
- `refactor/XXXXXXX` (for refactoring or cleanup)

## Issue mentions
Use [issue mentions](https://github.com/blog/831-issues-2-0-the-next-generation) to integrate your issues and commit messages. You can also close issues with commit messages. The following keywords will close issues when used in commit messages:
- `fixes #xxx`
- `fixed #xxx`
- `fix #xxx`
- `closes #xxx`
- `close #xxx`
- `closed #xxx`

## How to Write a Git Commit Message

### The seven rules of a great Git commit message
1. Separate subject from body with a blank line
2. Limit the subject line to 50 characters
3. Capitalize the subject line
4. Do not end the subject line with a period
5. Use the imperative mood in the subject line
6. Wrap the body at 72 characters
7. Use the body to explain what and why vs. how

For more details, see [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/).

## Merging feature branches and code reviews
Developers should not merge their own feature branches into `develop`. Instead, they should notify another developer who will merge the branch into `develop` after completing a code review of the branch.
