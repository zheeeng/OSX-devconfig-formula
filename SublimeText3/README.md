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

## Package Control

Many Sublime Text developers submit plugins to The [Package Control](https://packagecontrol.io/). Learning, installing, and using it to make the developer's life easier.

1. Open the sublime console: `View` > `Show Console`, or via shortcut `ctrl+``.
2. Paste the Python code for installing Sublime Text 3:

    ```
    import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
    ```

### Paths

* Package Control and Sublime Text packages are installed in the `~/Library/Application Support/Sublime Text 3/Installed Packages/` directory.
* The default configurations of the installed packages locate in the `~/Library/Application Support/Sublime Text 3/Packages/` directory.
* User configurations locate in the `~/Library/Application Support/Sublime Text 3/Packages/User` directory. [This repository](https://github.com/zheeeng/sublime-configuration) is synchronized with my personal configuration.

## Command Palette

* Open Command Palette via shortcut: `⌘ + ⌥ + P`.
* Sublime support fuzzy matching, so in Command Palette you could:
    * Set syntax to python by `sspy`.
    * Toggle the mini map on the right side by `mini`.
    * Use Package Control functions: install packages—`pi`, remove packages—`pr`, ...
    * More be to be discovered by you ...


