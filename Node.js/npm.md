# npm

npm is a package manager for JavaScript and the npm command-line tool is bundled with Node.js.

Global packages are installed in `/usr/local/lib/node_modules`, you can use these packages as command line tools. Adding option `-g` on your npm commands enables npm commands to work globally.

Local packages are used as modules to support your project work. You can declare the necessary packages as `dependencies` for production or `devDependencies` for development or testing in `package.json` file, then simply run `npm install` to install packages. While installing node modules, npm will look for the higher directories which contain `node_modules` folder or `package.json` file from current directory and installs modules in it.

## npm basic usage

```shell
# Install packages:
# - It is optional to save them as dependencies or devDependencies in `package.json`.
npm install <packages> [--save/--save-dev]
# Uninstall packages:
npm uninstall <packages> [--save/--save-dev]
# List installed global packages:
npm ls --depth=0 -g
# List outdated packages:
npm outdated
# Update all packages or specific packages:
npm update [<packages>]
```

Run `npm -l` or visit <https://docs.npmjs.com/cli/> for more informations.

### Tab-completion

Check [Zsh/plugins](../iTerm2/zsh-plugins.html) section:

Plugin `npm` for ZSH enables the tab-completion feature. Moreover, some command aliases for npm are added.

```
alias npmg="npm i -g "
alias npmS="npm i -S "
alias npmD="npm i -D "
alias npmE='PATH="$(npm bin)":"$PATH"'
alias npmO="npm outdated"
```

## `package.json` file

For generating `package.json`, just run `npm init` and follow the prompt instructions. Additionally, you can get a default `package.json` by running `npm init -y`. If there is no description field in the package.json, npm uses the first line of the `README.md` or `README` instead.

Check more [details](https://docs.npmjs.com/files/package.json) or run `npm help package.json`.

## `.npmrc` file

* `~/.npmrc` contains per-user config.
* `.npmrc` in project folder contains per-project config. 

It's recommended to set several config options for the init command:

    npm set init.author.email "your_email@example.com"
    npm set init.author.name "your_name"

These commands will add the config key value pairs into `~/.npmrc` file. You can create the `.npmrc` file manually for a single project.

Run `npm help config` getting more config info.



