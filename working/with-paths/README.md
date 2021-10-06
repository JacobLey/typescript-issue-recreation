Effective clone of broken package.

Only difference is that
```
"baseUrl": ".",
"paths": {
    "yargs/helpers": ["../../node_modules/@types/yargs/helpers.d.ts"]
}
```
 is declared in tsconfig.json.

Typescript will successfully build this package.
