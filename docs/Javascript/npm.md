# npm

## Package.json configuration

> <https://docs.npmjs.com/cli/v7/configuring-npm/package-json#main>

## Informations about npm package

```sh
npm info package-name
```

## How to use local npm package in another project

For tests purposes you can add package to `package.json` from your local project folder:

```json
{
  "global-functions": "file:../global-functions",
}
```

## What is scope and how to use it

A scope allows you to create a package with the same name as a package created by another user or organization without conflict. The scope name is everything between the @ and the slash.

- Unscoped packages are always public.

You can setup different repository for specific scope using your `.npmrc` file:

```sh
@myscope:registry=https://mycustomregistry.example.org
```

or use command line for it: `npm config set @myco:registry http://reg.example.com`

## Private repository

Modify `.npmrc` file:

```js
registry=http://npm.differentpage.com/
```

## How to versionize packages

| Code status |        Stage       | Rule | Example version |
|:-:|:-----------------------:|:---:|:------:|
| First release | New product | Start with 1.0.0 | 1.0.0    |
| Backward compatible bug fixes | Patch release | Increment the third digit | 1.0.1 |
| Backward compatible new features | Minor release | Increment the middle digit and reset last digit to zero | 1.1.0    |
| Changes that break backward compatibility | Major release | Increment the first digit and reset middle and last digits to zero | 2.0.0 |

## How to use versions in `package.json`

- Patch releases: 1.0 or 1.0.x or ~1.0.4
- Minor releases: 1 or 1.x or ^1.0.4
- Major releases: * or x

## You can set up version of package

You can setup version of the package directly from npm repository.

Examples:

```sh
# npm version [<newversion> | major | minor | patch | premajor | preminor | prepatch | prerelease [--preid=<prerelease-id>] | from-git]
npm version patch
npm version minor
npm version major
# and combinations with preword "pre"
npm version prepatch
npm version preminor
npm version premajor
# or alfa or beta tags
npm version preminor --preid alfa
npm version prerelease --preid=beta
```

after that you should deploy npm package into the repository:

```sh
npm publish
```

## Packages installation flags for `npm install` command

`common options: [
    -P|--save-prod|
    -D|--save-dev|
    -O|--save-optional
    -E|--save-exact
    -B|--save-bundle
    --no-save
    --dry-run
]`

## Show installed npm packages

You probably have some packages installed globally already on your system. You can see them by typing:

```bash
npm list --depth 0 #for local project

npm list -g --depth 0 #for global npm

# or

ls `npm root -g`
```

## Print the folder where npm will install executables

```sh
npm bin
```

## Try to run package from the nearest (or local project) executor

```sh
$(npm bin)/package_name
```

[run-locally-installed-npm-packages-without-global-install](https://www.rockyourcode.com/run-locally-installed-npm-packages-without-global-install/)

## Link developement package to the project

Copy package from developement npm package into final project:

```bash
npm link #run in npm package
npm link @scope/package-name #run in project
```

After developement process unlink package using:

```sh
npm unlink --no-save @scope/package-name #clear linked packages in project
npm unlink #clear npm links
```

> You can always check if package in linked correctly looking into node_modules.

## How to configure eslint?

The easiest way to install eslint configuration is run command:

```sh
./node_modules/.bin/eslint --init
```

## How to run a code after npm package installation?

You can set up command postinstall in `scripts` property inside of package.json file:

```json
{
  "scripts": {
      "postinstall": "node bin/index.js"
  }
}
```

> <https://docs.npmjs.com/cli/v7/using-npm/scripts#npm-ci>

## How to set up registry url and/or @scoped registry link

```sh
npm config set registry https://registry.npmjs.org
npm config get @company_name:registry
npm config set @company_name:registry https://artifactory.company.page/artifactory/api/npm/npm/
npm install -g @company_name/package-name
```

## How to set up files which should be included in npm package

The optional files field is an array of file patterns that describes the entries to be included when your package is installed as a dependency. File patterns follow a similar syntax to .gitignore, but reversed: including a file, directory, or glob pattern (*, and such) will make it so that file is included in the tarball when it's packed. Omitting the field will make it default to ["*"], which means it will include all files.

Some special files and directories are also included or excluded regardless of whether they exist in the files array (see below).

You can also provide a .npmignore file in the root of your package or in subdirectories, which will keep files from being included. At the root of your package it will not override the "files" field, but in subdirectories it will. The .npmignore file works just like a .gitignore. If there is a .gitignore file, and .npmignore is missing, .gitignore's contents will be used instead.

> <https://docs.npmjs.com/cli/v7/configuring-npm/package-json#files>

## How to check package version

```sh
npm info YOUR_PACKAGE version
# or
npm list --depth=0
# or for global packages
npm list -g --depth=0
```
