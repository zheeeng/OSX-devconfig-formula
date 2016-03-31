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

## Homebrew tap

Homebrew provide `brew tap` usage for users to access other repositories.

For example,
1. you can access the versioned formulae by `brew tap homebrew/versions`
2. and then `brew install <formula>`.
3. If conflicts happens(formula is provided by multiple repositories), try `brew install homebrew/versions/<formula>`

## $Path problem

**Note: Sometimes the programs installed by Homebrew don't replace the native program provided by OS X immediately. Read the following suggestions:**

### Edit paths file

* To make the shell search order work globally for all users, you can export the path `/usr/local/bin` by edit `/private/etc/paths` file.

### Perform Hash command

* `where xxx` lists locations where program `xxx` located.
* `Which xxx` tell user which `xxx` will the shell execute as usually.
* Sometimes ZSH and Bash cache the contents of $PATH, you'd execute `hash -r` to forget all previously cached utility locations.

