---
sidebar_position: 1
---

# General

## How to copy text to browser clipboard

Use current user location:

```js
navigator.clipboard.writeText(document.location.href);
```

## How to handle errors and break execution in JS

Error object

<https://stackoverflow.com/questions/9156176/what-is-the-difference-between-throw-new-error-and-throw-someobject>

```js
const doSomething1 = () => {
  //...
  try {
    //...
  } catch (err) {
    //... handle it locally
    throw new Error(err.message)
  }
  //...
}
```

## What $ and $$ doing in the browser

$(selector, element)
Looks up a CSS selector string selector , returning the first node descended from element that matches. If unspecified, element defaults to document. Equivalent to document.querySelector() or calls the $ function in the page, if it exists.

See the QuerySelector code snippet.

$$(selector, element)
Looks up a CSS selector string selector, returning an array of DOM nodes descended from element that match. If unspecified, element defaults to document. This is like for document.querySelectorAll(), but returns an array instead of a NodeList.

<https://developer.mozilla.org/en-US/docs/Tools/Web_Console/The_command_line_interpreter#helper_commands>

## How initialize eslint in project with predefined configuration

```sh
npm install eslint -g
eslint --init

or

npm install eslit --save-dev
./node_modules/.bin/eslint --init
```

## Types of JS modules

1. ES Modules

```js
import eslint from 'eslint'
export eslint;
```

2. CommonJS

```js
const circle = require('circle.js');
exports.circle = circle;
```

3. AMD

```js
define(['jquery'] , function ($) {
    return function () {};
});
```

4. UMD
5. SystemJS

## Differences between ES modules and CommonJS

<https://nodejs.org/docs/latest-v14.x/api/esm.html#esm_differences_between_es_modules_and_commonjs>
