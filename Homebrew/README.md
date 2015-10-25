# Homebrew

Homebrew installs packages (or Formula in Homebrew vocabulary) to directory `/usr/local/Cellar/` and then symlinks their files into `/usr/local/bin`.

## Installation

1. ** Dependencies:** All are included in Xcode Command Line Tools.
2. Download & execute installation script in terminal:

		ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

3. Make sure Homebrew works fine:

		brew doctor

	if everything goes well, you will get message: `Your system is ready to brew.`

4. To tell shell to search the programs installed by Homebrew in first order, add directory of those executable files to environmental variable $PATH:

		export PATH="/usr/local/bin:$PATH"

	For making config work permanently, we employ `~/bin/envconfig.sh` to hold aliases, exports, path changes etc.

		echo 'export PATH="/usr/local/bin:$PATH"' >> ~/bin/envconfig.sh
		
	Details in `envconfig.sh Section`.

** Tips:**

1. To make custom shell search order work globally for all users, you can export paths to `/private/etc/paths`
2. `where xxx` list locations where program `xxx` located.
3. `Which xxx` list which `xxx` will the shell execute as usually. 
4. Sometimes ZSH and Bash cache contents of $PATH, you'd execute `hash -r` to forget all previously remembered utility locations.

## Usage

Search formulae:

	brew search <text>
	
Get Formula info:

	brew info <FORMULA>

Install a Formula:

	brew install <FORMULA>

List Formulae:

	brew list [--versions]

Fetch the newest version of Homebrew and all formulae from GitHub:

	brew update

Show outdated Formulae:

	brew outdated

Upgrade Formula:

	brew upgrade <FORMULA>

Remove older versions Formulae:

	brew cleanup

Uninstall a Formulae:

	brew uninstall [FORMULAE]

_More details: <http://brew.sh/> or execute `brew home`_
