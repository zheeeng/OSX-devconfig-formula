# Git aliases

## Aliases predefined through git-config

```shell
git config --global alias.branches 'branch -avv'
git config --global alias.unstage 'reset HEAD --'
git config --global alias.tree 'log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit'
```

## Through alias-cli

alias       | command
----------- | ---------
g           | git
ga          | git add
gaa         | git add --all
gapa        | git add --patch
gac         | git add -A . && git commit
gac!        | git add -A . && git commit --amend
gacm        | git add -A . && git commit -m
gacm!       | git add -A . && git commit --amend -m
gacmsg      | gacm
gacmsg!     | gacm!
gb          | git branch
gba         | git branch -avv
gbranches   | gba
gbm         | git branch --merged
gbnm        | git branch --no-merged
gbus        | git branch --set-upstream-to
gbus~       | git branch --unset-upstream
gbunus      | gbus~
gbdm        | `_() { git branch --merged ${1-master} | grep -v " ${1-master}$" | xargs -n 1 git branch -d; }; _`
gbdmerged   | gbdm
gbl         | git blame -b -w
gbs         | git bisect
gbsb        | git bisect bad
gbsg        | git bisect good
gbsr        | git bisect run
gbsre       | git bisect reset
gbsreset    | gbsre
gbss        | git bisect start
gc          | git commit -v
gc!         | git commit -v --amend
gca         | git commit -v -a
gca!        | git commit -v -a --amend
gcm         | git commit -m
gcm!        | git commit --amend -m
gcam        | git commit -a -m
gcam!       | git commit -a --amend -m
gcmsg       | gcm
gcmsg!      | gcm!
gcamsg      | gcam
gcamsg!     | gcam!
gcf         | git config
gcfa        | git config --add
gcfg        | git config --get
gcfl        | git config --list
gcff        | `cat ``git rev-parse --git-dir``/config`
gcfrm       | git config --remove-section
gcfrn       | git config --rename-section
gcfu        | git config --unset
gcfua       | git config --unset-all
gcf~        | git config --local
gcfa~       | git config --local --add
gcfg~       | git config --local --get
gcfl~       | git config --local --list
gcff~       | `cat ``git rev-parse --git-dir``/config`
gcfrm~      | git config --local --remove-section
gcfrn~      | git config --local --rename-section
gcfu~       | git config --local --unset
gcfua~      | git config --local --unset-all
gcf!        | git config --global
gcfa!       | git config --global --add
gcfg!       | git config --global --get
gcfl!       | git config --global --list
gcff!       | `if [ -f "$HOME/.gitconfig" ]; then cat "$HOME/.gitconfig"; elif [ -f "$XDG_CONFIG_HOME/git/config" ]; then cat "$XDG_CONFIG_HOME/git/config"; fi`
gcfrm!      | git config --global --remove-section
gcfrn!      | git config --global --rename-section
gcfu!       | git config --global --unset
gcfua!      | git config --global --unset-all
gcl         | git clone --recursive
gclone      | gcl
gclean!     | git clean -df
gco         | git checkout
gcob        | git checkout -b
gcp         | git cherry-pick
gd          | git diff
gdca        | git diff --cached
gdt         | git diff-tree --no-commit-id --name-only -r
gdw         | git diff --word-diff
gf          | git fetch
gfa         | git fetch --all --tags --prune
gignore     | git update-index --assume-unchanged
gignored    | git ls-files -v \| grep "^[[:lower:]]"
gignore     | git update-index --no-assume-unchanged
gunignore   | git update-index --no-assume-unchanged
glg         | git log --oneline --decorate --color
glog        | git log --stat --decorate --color -p
glt         | `git log --graph --pretty=format:"%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset" --abbrev-commit`
glta        | `git log --graph --pretty=format:"%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset" --abbrev-commit --all`
gltw        | `git log --graph --pretty=format:"%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset" --abbrev-commit --all --reflog`
glast       | git log -1 --log-size -p
gls         | git ls-files
gls~        | git ls-files --others --exclude-standard
gm          | git merge
gp          | git push --tags
gpd         | git push --tags --dry-run
gpdr        | gpd
gpa         | git push --all --tags
gpl         | git pull --tags
gplr        | git pull --tags --rebase
gr          | git remote -v
gra         | git remote add
grrm        | git remote remove
grrn        | git remote rename
grgu        | git remote get-url
grsu        | git remote set-url
grp         | git remote prune
grs         | git remote show
gru         | git remote update
grb         | git rebase
grbi        | git rebase -i
grba        | git rebase --abort
grbc        | git rebase --continue
grbs        | git rebase --skip
grs         | git reset HEAD --
grsh        | git reset HEAD
grsh!       | git reset --hard HEAD
grt         | `cd $(git rev-parse --show-toplevel || echo ".")`
groot       | grt
grv         | git revert
grva        | git revert --abort
grvc        | git revert --continue
grvq        | git revert --quit
gs          | git status -sb
gss         | git status --ignored
gst         | git -c pager.status=less status -vv
gshow       | git show
gcat        | gshow
gsta        | git stash
gstaa       | git stash apply
gstad       | git stash drop
gstal       | git stash list
gstap       | git stash list pop
gstas       | git stash list show --text
gt          | git tag
gts         | git tag -s
gtv         | git tag -v
gvt         | git verify-tag
gwip        | `git add -A && git rm $(git ls-files --deleted) 2> /dev/null; git commit -m "--wip--" && echo "WIP\!"`
gunwip      | `git log -n 1 | grep -q -c -- "--wip--" && git reset HEAD~1`
gwip~       | gunwip
gwipe       | `git add -A && git rm $(git ls-files --deleted) 2> /dev/null; git commit -qm "WIPE SAVEPOINT" && git reset HEAD~1 --hard`

# Git-flow aliases

## Through git-config

```shell
git config --global alias.master 'checkout master'
git config --global alias.develop 'checkout develop'
git config --global alias.feature 'flow feature'
git config --global alias.release 'flow release'
git config --global alias.bugfix 'flow bugfix'
git config --global alias.hotfix 'flow hotfix'
git config --global alias.support 'flow support'
```


