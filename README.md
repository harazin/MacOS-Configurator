# Fresh MacOS Configurator

A clean, minimal setup for new MacOS installation specifically aimed at full-stack developers

## Prerequisites

This command installs the basic tools you need as a developer without having to install the entire Xcode application.

```bash
xcode-select --install
```

## Homebrew

Homebrew is package manager similar to apt-get on Linux. You should try to use this to install applications where possible.

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install cask
brew install tree
brew update
```
## Terminal

Before you continue, you should install the latest version of bash.

```bash
brew install bash
```

Then you can set this as your default shell by editing /etc/shells

```bash
open -e /etc/shells
```
and adding 

```bash
/usr/local/bin/bash
```
to the end of the file.

---

To change the colours and structure of the shell

```bash
open -e ~/.bash_profile
```

> If such a file doesn't exist, create it with `touch ~/.bash_profile`

Then add or update the following lines

```bash
# Display path as [username] in [path] (i.e. John in ~/Downloads)
export PS1="\[\e[31m\]\u\[\e[m\] \[\e[31m\]in\[\e[m\] \[\e[36m\]\w\[\e[m\] "

# Display ls items in color
export CLICOLOR=1;
export LSCOLORS=GxfxfxfxcxEhEhChChGxGx;
```

---

Optionally, install fortune and cowsay (credit: [w3cj](https://github.com/w3cj))

```bash
brew install fortune
brew install cowsay 
```

Setup the terminal startup commands by navigating to `Terminal > ⌘, > Profiles > Shell` and adding

```bash
fortune | cowsay
```
> If you have a default Project folder then use `cd Projects && clear && fortune | cowsay` instead.

## Git
MacOS comes with Git preinstalled, but we'll be using Homebrew version of Git, so begin by uninstalling the old version.

```bash
sudo rm -rf /usr/bin/git/
sudo rm /etc/paths.d/git
sudo rm /etc/manpaths.d/git
sudo pkgutil --forget --pkgs=GitOSX\.Installer\.git[A-Za-z0-9]*\.[a-z]*.pkg
```

Then install the new version.

```bash
brew uninstall git
brew update
brew install git
```

> `which git` should now return /usr/local/bin/git

From there, proceed with your standard git config.

## Window Management 

I like to use Spectacle, but feel free to use whichever app you want.

```bash
brew cask install spectacle
```

## Node.js & npm
Before installing Node.js using Homebrew, you should make sure that your `.bash_profile` file includes Homebrew's path `export PATH="/usr/local/opt/python/libexec/bin:$PATH"` somewhere in the file.

```bash
brew install node
```

> You can check if the install was successful by running `npm --version`

## Python

While MacOS already comes with a Python version, it's not the best version for up-to-date development, but removing it is also dangerous as the system may depend on it. You can simply instal Homebrew version of Python alongside whatever you currently have.

```bash
brew install python
```

> This will install Python 3 on your machine, which can be called using `python`. You can check this is correct with `python --version`

## Java

Oracle has a reputation for making it hard to install and configure java. Therefore I like to use OpenJDK which can be installed with Homebrew.

```bash
brew cask install java
```

> If you for any reason need to use an older version of Java, you can use `brew tap adoptopenjdk/openjdk`

> Then install the desired version.

```bash
brew cask install adoptopenjdk8
brew cask install adoptopenjdk9
brew cask install adoptopenjdk10
```

## Atom

Once again, Atom is a personal choice, feel free to use any IDE you like. I like Atom because of how simple it is.

```bash
brew cask install atom
``` 

## Browsers

I try to use native application where available, but as a web developer, you need to have at least Chrome installed for cross-browser development.

```bash
brew cask install google-chrome
```

## Extras

I also recommend getting a few optional applications which have helped me a lot during development.

* AdBlock for Safari
* JSONViewer for Safari
* Photoshop
* Word, PowerPoint, Excel
* Deluge
