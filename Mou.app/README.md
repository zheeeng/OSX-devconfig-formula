# Mou.app

## Installation

	brew cask install mou

Script `mou.sh` for using command open Mou in shell:

	#!/bin/zsh
	
	if [ -d /Applications/Mou.app ]; then
		if [ ! -f $@ ]; then
			touch $@
		fi
		open -a Mou.app $@
	fi
	
Store `mou.sh` at `~/scripts/` and execute `chmod +x mou.sh`, then cd to `~/bin/` and make symbolic link to `mou.sh`:

	ln -s ~/scripts/mou.sh mou
	
Now enjoy it just type `mou [filename]`

## Preferences

* Enable Math function isn't support well yet, wating for Mou.app 1.0 shipping, contact email: <hi@25.io> or @[Chen Luo](https://twitter.com/chenluois) on Twitter.
* Basic Font `Source Code Pro 12pt`, change font weight is still some bugs existing.
* Use Theme `Tomorrow+`.
* Use CSS `GitHub2`