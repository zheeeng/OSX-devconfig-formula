# Homebrew

Homebrew is the most popular package manager for OS X. It downloads formulae into `/Library/Caches/Homebrew`, and installs formulae into `/usr/local/Cellar/` and symlinks they into `/usr/local/bin`.

**Note: **

1. To make the shell search order work globally for all users, you can export the path `/usr/local/bin` by edit `/private/etc/paths` file.
2. Command `where xxx` lists locations where program `xxx` located.
3. Command `Which xxx` tell user which `xxx` will the shell execute as usually. 
4. Sometimes ZSH and Bash cache the contents of $PATH, you'd execute `hash -r` to forget all previously remembered utility locations.

## Install

1. ** Dependencies:** All are included in Xcode Command Line Tools.
2. Download & execute install script in terminal:

		/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

3. Make sure Homebrew works fine:

		brew doctor

    If everything goes well, you will get message: `Your system is ready to brew.` Otherwise, follow the prompted instructions.

## Uninstall

Exectue the uninstall script in terminal:

    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"

## Common Usage

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
	# Remove older versions of a formula or everything at once (with option '-n' dryrun cleanup):
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


