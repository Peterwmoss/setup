# Vale

Vale is primarily a Markdown and HTML linter

* [Installing](#installing)
  * [Prerequisites](#prerequisites)
  * [Linux](#linux)
  * [MacOS](#macos)
  * [Windows](#windows)
* [Useful links](#useful-links)
* [Usage](#usage)
* [Good to know](#good-to-know)
* [Common problems](#common-problems)

## Installing

### Prerequisites

You'll need super user (root) access to install vale.

### Linux

#### Arch-based

There's an [AUR package](https://aur.archlinux.org/packages/vale) for arch based distributions

To install using `yay`: `yay -S vale`

#### Void linux

`xbps-install vale`

#### Others

Download the latest binary from [the releases page](https://github.com/errata-ai/vale/releases)

Extract the tarball: `tar xf /path/to/download/location/vale_<version>_Linux_64-bit.tar.gz`

##### Current user only (does not require root)

Move the file to a path included in your `$PATH` environment variable. E.g.: `mv ./vale ~/.local/bin`

##### Whole system

Move the file to a path available to all users' `$PATH`. E.g. (here using `sudo`): `sudo mv ./vale /usr/bin`

If unsure what path is included you can try printing `$PATH` with the following command: `echo $PATH` and look for something like the above example.

### MacOS

#### Homebrew

`brew install vale`

### Windows

#### chocolatey

`choco install vale`

## Useful links

* [Official documentation](https://docs.errata.ai/vale/about/)
* [Github page](https://github.com/errata-ai/vale)

## Usage

After installing a configuration file is needed in the root of the project you're wanting to lint.

The configuration file for `vale` is either: `.vale.ini` or `_vale.ini` - both will work, though on Linux the former is preferred since it will be hidden by default.

Minimal setup for linting all markdown files in the project (see [official documentation](https://docs.errata.ai/vale/config) for more configuration options):

```ini
[*.md]
BasedOnStyles = Vale
```

Save the file and linting can now be done with: `vale .`

## Good to know

* [Adding custom spelling](https://docs.errata.ai/vale/vocab) from the official documentation
* There's an [official GitHub action for vale](https://github.com/errata-ai/vale-action)

## Common problems

Nothing here yet.
