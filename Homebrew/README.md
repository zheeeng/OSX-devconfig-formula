# Homebrew

Homebrew is the most popular package manager for OS X.

## Related directories

1. Homebrew downloads formulae into `/Library/Caches/Homebrew`.
2. Then it installs formulae into `/usr/local/Cellar/`,
3. and symlinks they into `/usr/local/bin`.

## Install

1. ** Dependencies:** All are included in Xcode Command Line Tools.
2. Download & execute install script in terminal:

		/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

3. Make sure Homebrew works fine:

		brew doctor

    If everything goes well, you will get message: `Your system is ready to brew.` Otherwise, follow the prompted instructions.

## Uninstall

Execute the uninstall script in terminal:

    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"

## Basic commands

```shell
   # Search formulae and get the info about a specific formula:
	brew search <text>
	brew info <FORMULA>
	# Install or uninstall a formula:
	brew install <FORMULA>
	brew uninstall <FORMULA> --force
	# List installed Formulae:
	brew list [--versions]
	# Show outdated Formulae:
	brew outdated
	# Remove older versions of a formula or everything at once (with option '-n' dry-run cleanup):
	brew cleanup <FORMULA>
	brew cleanup
	brew cleanup -n
	# Update the formulae and Homebrew itself:
	brew update
	# Upgrade
	brew upgrade [--cleanup] <FORMULA>
	# Stop a specific formula from being updated/upgraded:
	brew pin <FORMULA>
	brew unpin <FORMULA>
```

_More details: <https://github.com/Homebrew/homebrew/blob/master/share/doc/homebrew/FAQ.md> or execute `brew home`_

## Advanced commands

```shell
# Access other repository, such as the repository contains versioned formulae:
brew tap <HOMEBREW REPOSITORY>
brew tap homebrew/versions
# remove a tapped repository:
brew untap <REPOSITORY>
# While installing a formula, if a formula is provided by multiple repositories, you'd specify the repository:
brew install homebrew/versions/<FORMULA>
# List the dependencies for an specific formula:
brew deps <FORMULA>
# List the installed formulae which specify a formula as dependency:
brew uses --installed <FORMULA>
# List the orphaned dependency packages:
brew leaves
```

### List the dependencies of all formulae

*Original links:<http://zanshin.net/2014/02/03/how-to-list-brew-dependencies/>*

```bash
brew list | while read cask; do echo -n "\e[1;34m$cask ->\e[0m"; brew deps $cask | awk '{printf(" %s ", $0)}'; echo ""; done
```

## Make new installed program work immediately

Sometimes you want to use the programs installed by Homebrew immediately, but the native programs provided by OS X is called. Read the following workarounds:

### Edit paths file

* To make the shell search order work globally for all users, you can export the path `/usr/local/bin` by edit `/private/etc/paths` file.

### Perform Hash command

* `where xxx` lists locations where program `xxx` located.
* `Which xxx` tell user which `xxx` will the shell execute as usually.
* Sometimes ZSH and Bash cache the contents of $PATH, you'd execute `hash -r` to forget all previously cached utility locations.

