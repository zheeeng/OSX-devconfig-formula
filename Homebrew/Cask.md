# Homebrew Cask

Homebrew Cask extend Homebrew for OS X GUI applications management. It requires Homebrew version 0.9.5+.

It’s implemented as a homebrew external command called `cask`. (`brew cask search/install/uninstall...`)

## Install

	brew tap caskroom/cask
	brew install brew-cask

Homebrew Cask install formulae into `/opt/homebrew-cask/Caskroom/`. The downloads are stored in `/Library/Caches/Homebrew/Casks`.

## Tab-completion

Check [Zsh/plugins](../iTerm2/zsh-plugins.html) section:

Plugin `brew-cask` for Zsh enables the tab-completion feature.

## Versioned casks

Tap `caskroom/versions` provide alternate versions of Casks(e.g. betas, nightly releases, old versions).

    brew tap caskroom/versions

## Font casks

Tap `caskroom/fonts` allows you to use the same friendly Homebrew-style CLI workflow for the administration of binary font files on your Mac.

    brew tap caskroom/fonts

Font searching is temporarily disabled, one workaround is to use a regular expression search:

    brew cask search /source-code-pro/

Reference: <https://github.com/caskroom/homebrew-fonts>

