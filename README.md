# Lint

Currently for linting we have the `react/recommended` and `jsx-a11y/recommended` set of rules.

# [Husky](https://typicode.github.io/husky/) for pre-commit hook events

With Husky a pre-commit hook runs to lint staged .js and .jsx files that are not being ignored.

The pre-commit hook is under `.husky/pre-commit`. Contains the code to catch only .js and .jsx staged files and run the lint rules over them.

## Husky troubleshot

If you ran into `hint: The '.husky/pre-commit' hook was ignored because it's not set as executable.` message, you need to add executable permissions to `.husky/pre-commit`

`chmod +x .husky/<hookname>`

If not, check the [Husky troubleshot documentation](https://typicode.github.io/husky/#/?id=hooks-not-running)

# Added Github Actions

Inside of the folder `.github/workflows` there is a `javascriptLint.yml` file that contains all the configuration to run the Linter for .js and jsx over each PR and Push over the *development* branch.

The `javascriptLint.yml` contains:
 * Setups a Linux machine.
 * Picks up the node version from the project package.json file.
 * Pulls, if there is one, a previous yarn cache.
 * Install node dependencies from cache and those that aren't in the cache are installed as well.
 * Runs the Linter over the `./app/javascript/site/` folder
