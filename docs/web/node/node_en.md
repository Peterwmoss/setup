# node.js 

This page prefers installation using package managers.

For different versions than what is provided by your package manager, see [nodejs.org](https://nodejs.org/en).

* [Linux](#linux-source)
* [MacOS](#macos-source)
* [Windows](#windows-source)

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

## [Official instructions](https://nodejs.org/en/download/)

## Common problems

* Nothing here.. yet!
