# Homebrew

Homebrew is the most popular package manager for OS X.

## Related directories

1. Homebrew downloads formulae into `~/Library/Caches/Homebrew` (by run `brew --cache` in terminal).
2. Then it installs formulae into `/usr/local/Cellar/`.
3. and symlinks they into `/usr/local/bin`.

## Installation

1. ** Dependencies:** All are included in Xcode Command Line Tools.
2. Download && execute install script in terminal:

		/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

3. Make sure Homebrew works fine:

		brew doctor

    If everything goes well, you will get the message: `Your system is ready to brew.` Otherwise, follow the prompted instructions.

## Uninstallation

    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"

## Basic commands

```shell
# Search formulae and get the info about specific formulae:
brew search <text>
brew info <FORMULAE>
# Install or uninstall a formulae:
brew install <FORMULAE>
brew uninstall <FORMULAE> --force
# List installed Formulae:
brew list [--versions]
# Show outdated Formulae:
brew outdated
# Remove older versions of formulae or everything at once (with option '-n' dry-run cleanup):
brew cleanup [<FORMULAE>] [-n]
# Symlink/unsymlink a specific formula's files into the Homebrew prefix:
brew link <FORMULAE>
brew unlink <FORMULAE>
# Update the formulae and Homebrew itself:
brew update
# Upgrade
brew upgrade [--cleanup] <FORMULAE>
# Stop specific formulae from being updated/upgraded:
brew pin <FORMULAE>
brew unpin <FORMULAE>
```

_More details: <https://github.com/Homebrew/homebrew/blob/master/share/doc/homebrew/FAQ.md> or execute `brew home`_

## Tab-completion

Add `brew` plugin into `~/.zshrc`.

Check [Zsh plugins: brew](../iTerm2/zsh-plugins.html#brew) section:

> Plugin `brew` for Zsh enables the tab-completion feature. Moreover, some command aliases for brew are added:

```
alias brews='brew list -1'
alias bubo='brew update && brew outdated'
alias bubc='brew upgrade && brew cleanup'
alias bubu='bubo && bubc'
```

## Advanced commands

```shell
# Activate a previously installed version of a formula(I strongly recommend you use 'brew switch' to control the versions of your formulae if they don't have many global dependencies):
brew info <FORMULA>
brew switch <FORMULA> <VERSION>
# Download the source packages for the given formulae:
brew fetch --me <FORMULAE>
# Remove all downloads for formulae
rm -rf $(brew --cache)
# Access and install other taps, such as the tap contains versioned formulae:
brew tap <HOMEBREW TAP>
brew tap homebrew/versions
# remove a tapped repository:
brew untap <HOMEBREW TAP>
# List the dependencies for formulae:
brew deps <FORMULAE>
# List the installed formulae which specify formulae as dependencies:
brew uses --installed <FORMULAE>
# List the orphaned dependency formulae:
brew leaves
```

### Listing the dependencies of all formulae

*Original links:<http://zanshin.net/2014/02/03/how-to-list-brew-dependencies/>*

```bash
brew list | while read cask; do echo -n "\e[1;34m$cask ->\e[0m"; brew deps $cask | awk '{printf(" %s ", $0)}'; echo ""; done
```

## Making newest installed programs work immediately

Sometimes you want to use the programs installed by Homebrew immediately, but the native programs provided by OS X is called. Read the following workarounds:

### Editing paths file

* To make the shell search order work globally for all users, you can export the path `/usr/local/bin` by editing `/private/etc/paths` file.

### Running hash command

* `where xxx` lists directories where program named `xxx` located in.
* `Which xxx` tells users which `xxx` will be executed actually.
* Sometimes ZSH and Bash cache the contents of $PATH, you'd execute `hash -r` to forget all previously cached utility locations.

