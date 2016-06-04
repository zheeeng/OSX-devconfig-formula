# Homebrew Cask

Homebrew Cask extend Homebrew for OS X GUI applications management. It requires Homebrew version 0.9.5+.

It’s implemented as a homebrew external command called `cask`(You cloud execute commands like `brew cask search/install/uninstall...`). In `Homebrew-Cask`, we call formula as `Cask`.

## Installation

    brew tap caskroom/cask
    brew install brew-cask

`Homebrew-Cask` install Casks into `/opt/homebrew-cask/Caskroom/`. The downloaded installation files are stored in `~/Library/Caches/Homebrew/Casks`.

## Upgrade Casks

`Homebrew-Cask` is very good at installing, inconsistent on uninstalling, and mostly-incapable on upgrading. After you update `Homebrew-Cask` by `brew cask update`, if some installed casks exist newer versions, `brew cask info <the outdated Cask>`, `brew cask install <the outdated Cask>`, `brew cask uninstall <the outdated Cask>` and other cmds alike will report that the Cask is not installed, and you certainly installed it. `Homebrew-Cask`s' commands retrieve only on the latest Cask versions and detect whether the local Caskroom contains a Cask which its path match the latest version's installation path. Because of the path of Cask contains the version number, `Homebrew-Cask` can't handle the installed Cask well.

A hard way to upgrade a Cask is re-installing the latest version of the Cask. `brew cask uninstall` with `--force` option will uninstall all versions of a Cask. Therefore we cloud combine uninstallation and installation together to upgrade Casks.

In Github Gist, [atais/cask_upgrade.sh](https://gist.github.com/atais/9c72e469b1cbec35c7c430ce03de2a6b) provided a robust script doing such work. You cloud perform this script in oneline:

    curl -s https://gist.githubusercontent.com/atais/9c72e469b1cbec35c7c430ce03de2a6b/raw/1b7b891e6eff3b42edb4ada219764f12aefb04ca/cask_upgrade.sh | bash /dev/stdin

**Note:** As the official document mentioned, `cask uninstall --force` is currently imperfect. [Read Here](https://github.com/caskroom/homebrew-cask/blob/master/USAGE.md).

## Tab-completion

Add `brew-cask` plugin into `~/.zshrc`.

Check [Zsh plugins: brew-cask](../iTerm2/zsh-plugins.html#brew-cask) section:

> Plugin `brew-cask` for Zsh enables the tab-completion feature.

## Versioned Casks

Tap `caskroom/versions` provide alternate versions of Casks(e.g. betas, nightly releases, old versions).

    brew tap caskroom/versions

## Font Casks

Tap `caskroom/fonts` allows you to use the same friendly Homebrew-style CLI workflow for the administration of binary font files on your Mac.

    brew tap caskroom/fonts

Font searching is temporarily disabled, one workaround is to use a regular expression search:

    brew cask search /source-code-pro/

Reference: <https://github.com/caskroom/homebrew-fonts>

