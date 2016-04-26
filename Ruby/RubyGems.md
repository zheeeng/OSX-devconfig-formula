# RubyGems

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

