# next.js

## How to configure prettier in project

https://paulintrognon.fr/blog/typescript-prettier-eslint-next-js

```sh
yarn add --dev prettier eslint-config-prettier
```

add file:

```sh
// .prettierrc.json
{
  "semi": false,
  "trailingComma": "es5",
  "singleQuote": true,
  "tabWidth": 2,
  "useTabs": false
}
```

```sh
// .eslintrc.json
{
  // ...
  "extends": [
    "next/core-web-vitals",
    "plugin:@typescript-eslint/recommended",
    "prettier" // Add "prettier" last. This will turn off eslint rules conflicting with prettier. This is not what will format our code.
  ],
  // ...
}
```

```sh
// .vscode/settings.json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  // Add those two lines:
  "editor.formatOnSave": true, // Tell VSCode to format files on save
  "editor.defaultFormatter": "esbenp.prettier-vscode" // Tell VSCode to use Prettier as default file formatter
}
```

### Default prettier configuration

```json
{
    "printWidth": 120,
    "trailingComma": "none",
    "tabWidth": 4,
    "semi": true,
    "singleQuote": true,
    "arrowParens": "avoid"
}
```
