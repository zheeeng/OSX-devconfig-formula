# envconfig.sh

Reference to: <http://sourabhbajaj.com/mac-setup/iTerm/zsh.html>


	#!/bin/zsh

    # PATH
    export PATH="$HOME/.rbenv/bin:$HOME/.rbenv/shims:$HOME/bin:/usr/local/share/python:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
    export EDITOR='subl -w'
    # export PYTHONPATH=$PYTHONPATH
    # export MANPATH="/usr/local/man:$MANPATH"

    # Virtual Environment
    export WORKON_HOME=$HOME/.virtualenvs
    export PROJECT_HOME=$HOME/Projects
    source /usr/local/bin/virtualenvwrapper.sh
    if [ -f /usr/local/bin/virtualenvwrapper.sh ]; then source /usr/local/bin/virtualenvwrapper.sh fi

    # Owner
    export USER_NAME="YOUR NAME"
    export DEFAULT_USER="YOUR NAME"
    if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi

    # FileSearch
    function f() { find . -iname "*$1*" ${@:2} }
    function r() { grep "$1" ${@:2} -R . }

    #mkdir and cd
    function mkcd() { mkdir -p "$@" && cd "$_"; }

    # Aliases
    alias ccat=source-highlight --out-format=esc -o STDOUT -i
    alias cppcompile='c++ -std=c++11 -stdlib=libc++'
    alias -s tar="tar -xvf"
    alias -s gz="tar -xzvf"
    alias -s tgz="tar -xzvf"
    alias -s bz2="tar -xjvf"
    alias -s zip="unzip"%
    


