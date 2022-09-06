# Web Extensions | Chrome Firefox

## How to automate process of deployment

You can use one of solutions:

- just basic html, css, js files and manually refresh extension after every change
- use [parcel](https://parceljs.org/recipes/web-extension/) with prebuild configuration for building web extensions
- use [rollup](https://rollupjs.org/) and [plugin](https://www.extend-chrome.dev/rollup-plugin#chrome-extension-boilerplates) for it
- use [web-ext](https://github.com/mozilla/web-ext) (special CLI) for mozilla extensions
- configure you own bundler with `webpack` or [esbuild](https://esbuild.github.io/getting-started/#install-esbuild)

## The architecture of web extension working

[Instruction](https://developer.chrome.com/docs/extensions/mv2/architecture-overview/#pages)

## How to create new google chrome extension

[How to create manifest file](https://developer.chrome.com/docs/extensions/mv3/manifest/)

[Manifest options](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json)

[Free Code Camp Tutorial](https://www.freecodecamp.org/news/building-chrome-extension/)

[Offical documentation](https://developer.chrome.com/docs/extensions/mv3/getstarted/)
