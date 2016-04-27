# Sublime Text 3

> Sublime Text is a sophisticated text editor for code, markup and prose.

## Install

Homebrew tap caskroom/versions contains the Sublime Text 3 in beta, check your taps before installation:

    brew tap

If you have no tap `caskroom/versions`, add it:

    brew tap caskroom/versions

Install Sublime Text 3:

    brew cask install sublime-text3

Homebrew will create a symlink `subl` to an executable sublime command. You cloud edit a file with `subl file` or open a directory in Sublime Text by `subl directory`. If you want to use Sublime Text to manage a project which under the current working directory, just run `subl .` then save entire opened directory as an sublime project—`proj.sublime-project`.

