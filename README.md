# typescript-issue-recreation

## To Recreate Issue
Run `npm i`
Then run `npm run recreate-issue`

The script will first build the typescript projects in the `working` directory. This is to generally give a base case that typescript is installed/working correctly, and succeeds given slight variations of the broken case.

Then the script will try building the "broken" package, which fails to find typings for `yargs/helper` despite being installed, and successfully found in other packages. Note that the types for `yargs` root is found successfully.

## Working Cases

Two "working" cases are provided, to generally show how the issue may be fixable, or help diagnose the issue.

The first `with-paths` explicitly provides a mapping the the types file, using the `paths` property in `tsconfig.json`.

The second `with-esnext` changes the module (and therefore module resolution) to `esnext`, effectively ignoring `yargs` usage of package.json exports.

## Why Yargs?

This is the first package I personally had a problem with using Typescript 4.5 beta. It is a very popular npm package that is correctly using the package.json exports. It however does not come with types declared and requires installing `@types/yargs`.

This mix of 4.5's `nodenext` + package.json exports + `@types` appears to cause the issue for non-index files.
