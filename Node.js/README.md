# Node.js 

> Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. 

Many utilities are built with Node, it's necessary for anyone installs it. If you are **not** a developer, just install it by:

    brew install node

If you are a developer, version manager for Node is the must-have. Two alternative choices are recommended, `n` modlues and `NVM`. [This article](http://www.mattpalmerlee.com/2013/03/23/installing-and-switching-between-multiple-versions-of-node-js-n-vs-nvm/) compare them in detail. For avoiding the global modules don't work after node version up/degrading, NVM is finally picked.

## Installing Node.js with NVM

NVM (Node Version Manager) is employeed for quick switching node to other versions. A simple bash script `nvm.sh` which is generated into `~/.nvm/` provides a series of shell commands to manage node versions. 

NVM works like `Virtualenv`, all nodes under a sandboxes, set $PATH containing your specified node. All installed versions locate at `~/.nvm/versions/node` by default.

### Installing NVM

1. Get `nvm.sh` and related files:

        git clone https://github.com/creationix/nvm.git ~/.nvm && cd ~/.nvm && git checkout `git describe --abbrev=0 --tags`

2. Active NVM:

        . ~/.nvm/nvm.sh

### Auto starting NVM upon login

Add `nvm` plugin into `oh-my-zsh`.

Check [Zsh plugin: nvm](../iTerm2/zsh-plugins.html#nvm) section:

> Plugin `nvm` source `~/.nvm/nvm.sh` automatically when you are logining shell.

### Installing Node

    nvm install node

### Upgrading NVM

    cd "$NVM_DIR" && git pull origin master && git checkout `git describe --abbrev=0 --tags`

## Common NVM usages

You can use the alias instead of the version pointer for nvm operation, such as

* 'node': the latest version of node
* 'iojs': the latest version of io.js'

```shell
# List all node versions or local versions
nvm ls-remote
nvm ls
# Install or uninstall node versions
nvm install node
nvm uninstall node
# Upgrade or install node with installed packages migration:
nvm install node --reinstall-packages-from=node
# Use a specific installed node or the system-installed version of node:
nvm use node
nvm use system
# Run node with a desired version of node:
nvm run 5.1 --version
# Run any arbitrary command in a subshell with the desired version of node:
nvm exec 3.3 node --version
# Display the path to the specific installed node:
nvm which 5.1
# Restore your PATH:
nvm deactivate
# Set a default node version to be used in any new shell:
nvm alias default node
```

### .nvmrc

You can create a `.nvmrc` file containing version number in the project root directory (or any parent directory). `nvm use`, `nvm install`, `nvm exec`, `nvm run`, and `nvm which` will all respect an `.nvmrc` file when a version is not supplied.

    echo "5.11" > .nvmrc

## Node-docs

Check [Zsh plugin: node](../iTerm2/zsh-plugins.html#node) section:

> Plugin `node` for Zsh allows you to run command `node-docs` to access the documentation of the current node version.

