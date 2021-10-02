# Sass

Sass is, as they themselves put it, CSS with superpowers.

It allows for functions, nesting selectors, extending selectors, and much more.

A browser cannot process `.scss` or `.sass` files, which means that you'll have to compile these files into `.css` files. Usually everything is compiled into one large file for the browser to read (see [usage](#usage) for the command to do this).

* [Install](#install)
  * [Prerequisites](#prerequisites)
  * [Project only](#project-only)
  * [Globally](#globally)
* [Usage](#usage)
* [Basics](#basics)

## Install

### Prerequisites

  * [node.js](docs/web/node/node_en.md) should be installed on the machine (and `npm` should be working)

### Project only

Before running the below command ensure that you have a node project setup (look for a `package.json` file) in the project root directory.

* `npm install --save-dev sass`
  * Shorthand: `npm i -D sass`

### Globally

To use anywhere, ensure that globally installed npm packages are added to your path. See [here](docs/web/node/node_en.md#unknown-command-installed-package-command) if you can't run `sass` after running the command below.

* `npm install -g sass`
  * Shorthand: `npm i -g sass`

## Usage

### With files

`sass <input file> <output file>`

* Example input file: `src/styles/main.scss`
* Example output file: `dist/bundle.css`

Full example: `sass src/styles/main.scss dist/bundle.css`

### With directories

`sass <input directory>:<output directory>`

* Example input directory: `src/styles`
* Example output directory: `dist/styles`

Full example: `sass src/styles:dist/styles`

### Watch for changes

Add the `--watch` flag to your command.

For example: `sass --watch src/styles/main.scss dist/bundle.css`

## Basics

See the [official website](https://sass-lang.com/guide) for a basic guide to syntax and functionality.
