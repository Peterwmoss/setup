# node.js

This page prefers installation using package managers.

For different versions than what is provided by your package manager, see [nodejs.org](https://nodejs.org/en).

* Installing
  * [Linux](#linux-source)
  * [MacOS](#macos-source)
  * [Windows](#windows-source)
* [Useful links](#useful-links)
* [Good to know](#good-to-know)
  * [Files](#files)
    * [package.json](#packagejson)
    * [package-lock.json](#package-lockjson)
  * [Scripts](#scripts)
  * [Common commands](#common-commands)
* [Common problems](#common-problems)

## Linux ([source](https://nodejs.org/en/download/package-manager/))

Usually node.js is installed along with `npm` so this page will include both.

#### Prerequisites

* Root access (sudo or similar) to install node.js

### pacman

```sh
sudo pacman -S nodejs npm
```

### dnf

```sh
sudo dnf module install nodejs:16
```

### emerge

```sh
sudo emerge nodejs
```

### yum

```sh
sudo yum nodejs14
```

### apt / apt-get ([source](https://github.com/nodesource/distributions/blob/master/README.md#deb))

#### v16.x

```sh
# Using Ubuntu
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt-get install -y nodejs

# Using Debian, as root
curl -fsSL https://deb.nodesource.com/setup_16.x | bash -
apt-get install -y nodejs
```

#### v14.x

```sh
# Using Ubuntu
curl -fsSL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt-get install -y nodejs

# Using Debian, as root
curl -fsSL https://deb.nodesource.com/setup_14.x | bash -
apt-get install -y nodejs
```

### Other

See [here](https://nodejs.org/en/download/package-manager) for instructions on other package managers.

## MacOS ([source](https://nodejs.org/en/download/package-manager/#macos))

#### Prerequisites

* Root access (sudo or similar) to install node.js

### Homebrew

```sh
brew install node
```

### Manual

```sh
curl "https://nodejs.org/dist/latest/node-${VERSION:-$(wget -qO- https://nodejs.org/dist/latest/ | sed -nE 's|.*>node-(.*)\.pkg</a>.*|\1|p')}.pkg" > "$HOME/Downloads/node-latest.pkg" && sudo installer -store -pkg "$HOME/Downloads/node-latest.pkg" -target "/"
```

## Windows ([source](https://nodejs.org/en/download/package-manager/#windows-1))

### chocolatey

```sh
choco install nodejs
```

### Manual (.msi)

LTS: [v14.18.0](https://nodejs.org/dist/v14.18.0/node-v14.18.0-x86.msi)

Current: [v16.10.0](https://nodejs.org/dist/v16.10.0/node-v16.10.0-x86.msi)

## Useful links

* [Official instructions](https://nodejs.org/en/download/)
* [npm CLI documentation](https://docs.npmjs.com/cli/v7/commands)

## Good to know

### Files

#### `package.json`

This file includes information about your project (also referred to as an npm package).

In here you'll find your project name, version, scripts, dependencies among other things.

The most common reason to make updates manually to this file is to update:

* Package version number
* Scripts to run using `npm run <script name>`

#### `package-lock.json`

This file includes information about your current project dependencies. It describes the exact `node_modules` tree that has been created, e.g. when installing dependencies with `npm install <package>` (see [common commands](#common-commands))

If using a version control system (VCS), such as `git`, the `package-lock.json` file should be added to the VCS to ensure a common ground for a working project dependency tree.

### Scripts

Scripts are what makes your project run, build, deploy or whatever you have defined them to do.

Scripts use shell syntax.

Usual script names include:

* `start`
* `build`
* `dev`
* `serve`

Scripts are added under the `"scripts"` field in your `package.json` file.

When writing a command for your script to run, know that all installed `node_modules` are available (in `$PATH`) when running the script.

So if you have the `sass` package installed, a build script might look like this: 

`"build": "sass src/styles/main.scss dist/main.css"`

#### The `start` script

The `start` script is a special name for a script that even has a shorthand (`npm start`) to run.

The start script usually contain the commands to run your code in a production environment.

A very simple example could be: `"start": "node index.js"`

#### More info

See [the official documentation](https://docs.npmjs.com/cli/v7/using-npm/scripts) for more info on the scripts field.

### Common commands

* `npm init` - creates a project to use with npm. This creates a `package.json` file, which contain information about your project setup.
  * Optional parameter: `-y` or `--yes` to initialize with default values
* `npm install` - installs packages declared in `package.json` to a folder named `node_modules` which can then be referenced from your project source code
  * Shorthand: `npm i`
  * Alternative: `npm ci` - will perform a clean install, which means `node_modules` will be removed and that a `package-lock.json` will be used as a reference. This file **must** therefore be the present in project
* `npm install <package>` - installs `<package>` locally (saved in a `package.json` file) as a runtime dependency
  * Shorthand: `npm i <package>`
  * To globally install packages: `npm i -g <package>`
    * note: this will install to wherever: `npm root -g` points to.
* `npm install --save-dev <package>` - installs `<package>` locally (saved in a `package.json` file) as a development only dependency
  * Shorthand: `npm i -D <package>`
* `npm uninstall <package>` - removes `<package>` locally (and from the `package.json` file)
  * Shorthand: `npm un <package>`
* `npm run <script name>` - runs a script named `<script name>` found under the `scripts` field in `package.json`
  * Shorthand: `npm un <package>`

## Common problems

### `SyntaxError: Cannot use import statement outside of a module`

This is caused since your project is not a module. 
Usually you'll want your project to be a module to allow for ES6 or newer syntax, such as `import`. 
To do this add the following to your `package.json` file:

* `"type": "module"` and a comma if it's not the last field in your `package.json`
  * OBS: make sure to add this inside of the outermost `{ .. }` or npm will be confused

### `SyntaxError: Unexpected token 'export'`

Caused by, and fixed in the same way as [here](#syntaxerror-cannot-use-import-statement-outside-of-a-module)

### Unknown command `<installed package command>`

This is due to globally installed package binaries (executables) not being in your path.

To fix this run `npm root -g` and note the location printed by the command (e.g. `/home/<user>/.local/share/npm/lib/node_modules`)

Once you have this, remove the `/lib/node_modules` part of the path and replace it with `/bin`. Then you'll have something like: `/home/<user>/.local/share/npm/bin`

This is the path you'll want to add to your `$PATH` environment variable.

To do this see: [Adding to $PATH](/docs/system/path/path_en.md#adding-to-path)
