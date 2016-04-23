# Ruby

Ruby is an essential build tool for developing. Many utilities or their installation scripts are built with Ruby language, or the Ruby package manager, RubyGems. For the convenience for versions switching, and with the reason not messing up the native Ruby installed by OS X, we employee `rbenv` to manage the Ruby versions. An alternative is `RVM` and rbenv is incompatible with RVM. There is a [comic](http://jonathan-jackson.net/rvm-and-rbenv) showing you a comparison. 

## Installing Ruby with rbenv

> `rbenv` works by inserting a directory of shims at the front of your PATH through a process called rehashing. `rbenv` maintains shims in that directory to match every Ruby command across every installed version of Ruby—`irb`, `gem`, `rake`, `rails`, `ruby`, and so on.

### Installing rbenv

1. Install the `rbenv` suite which includes `rbenv`—The main utility, `ruby-build`—provides the `rbenv install/uninstall/build` command, `rbenv-default-gems`—hooks into `rbenv install` command to automatically install gems every time you install a new version of Ruby.

        brew install rbenv ruby-build rbenv-default-gems

2. Add `rbenv` plugin into `oh-my-zsh`. It initilize `rbenv` automatically when you are logining shell and changes the defualt `rbenv` variables.

    Check [Zsh plugins: rbenv](../iTerm2/zsh-plugins.html#rbenv) section:

    > Plugin `rbenv` changes the defualt `rbenv` variables and exports them, provides some useful related function, explicitly tells `rbenv` to use Zsh, and initilize the `rbenv` automatically.

    With the reason you install `rbenv` by Homebrew, this plugin will point the `rbenv` directory under Homebrew formulea repository, instead of `~/.rbenv`, to RBENV_ROOT. 

3. Reopen a new terminal tab or restart your shell for sourcing settings.

### Install Ruby

1. Get the versions of Ruby:

        rbenv install --list

2. Install the Ruby version:

        rbenv install <version>

3. Rehash for shims work:

        rbenv rehash

4. Set the Ruby version to replace the system built-in version:

        rbenv global <version>

5. Check the installed ruby versions or the current working version

        rbenv versions
        rbenv version

### Specifing the Ruby running version for shims

When you execute a shim, rbenv specifies the running version of Ruby for this shim by reading a specified env variable or some files in order:

1. `RBENV_VERSION` environment variable.
2. The first `.ruby-version` file in the directory of the target script or in the script's parent directories.
3. The first `.ruby-version` file in the current working directory or the parent directories.
4. The global `.rub-version` file located in the directory is pointed by RBENV_ROOT variable.

**Note:**
1. `rbenv local <version>` changes the content of `.ruby-version` file under current working directory.
2. `rbenv global <version>` changes the content of `.ruby-version` file under RBENV_ROOT.
3. `--unset` option cancel the version specifying.

### Binding gems with each new Ruby version

> `rbenv-default-gems` automatically installs the gems listed in `$(rbenv root)/default-gems` file every time you successfully install a new version of Ruby with rbenv install.

A Sample file:

```
# One per line
bundler
rbenv-gem-rehash
# Specifing a version
bcat ~>0.6
# Specifing prerelease version
rails --pre
```

## RubyGems

> RubyGems is a package management framework for Ruby. This gem is an update for the RubyGems software. You must have an installation of RubyGems before this update can be applied.

RubyGems is bounded to Ruby by default, to upgrade to the latest RubyGems, run:

    gem update --system

### Usages

```shell
# List installed or remote gems with/without details:
gem list [-r] [-d] [REGEXP]
# Install a gem with/without document:
gem install <gem> --no-document
# Show outdated gems
gem outdated
# Update installed gems or a particular gem:
gem update [<gem>]
# Clean up old versions of installed gems
gem cleanup [--dryrun]
# Show the dependencies of an installed gem, or reverse dependencies
gem dependency [-R]
```

**Note:** For a faster gem installation, add option `--no-document` disable documentation generation. Add a config into `~/.gemrc` make it be default for each installation command:

    echo 'gem: --no-document' >> ~/.gemrc

## Tab-completion

Check [Zsh plugins: gem](../iTerm2/zsh-plugins.html#gem) section:

Plugin `gem` for Zsh enables the tab-completion feature.

