# Git aliases

## Aliases predefined through git-config

```shell
git config --global alias.branches 'branch -avv'
git config --global alias.review 'diff -U99999'
git config --global alias.tree 'log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit'
git config --global alias.unstage 'reset HEAD --'
```

## Through alias-cli

alias       | command
:---------- | :--------------
galias      | get git aliases
----------  | ----------
g           | git
----------  | ----------
ga          | git add
ga!         | git add --force
gaa         | git add --all
gap         | git add --patch
**gapa**    | *gap*
gai         | git add --interactive
gau         | git add --update
gau         | git add --update -p
gac         | git add -A . && git commit
gac!        | git add -A . && git commit --amend
gacm        | git add -A . && git commit -m
gacm!       | git add -A . && git commit --amend -m
**gacmsg**  | *gacm*
**gacmsg!** | *gacm!*
----------  | ----------
gar         | git archive
gargz       | Details in [link][git-aliases.sh].
gartar      | Details in [link][git-aliases.sh].
gartgz      | Details in [link][git-aliases.sh].
garzip      | Details in [link][git-aliases.sh].
----------  | ----------
gb          | git branch
gb!         | git branch --force
gba         | git branch -avv
gbd         | git branch -d
gbd!        | git branch -D
gbm         | git branch -m
gbm!        | git branch -M
gbmerged    | git branch --merged
gbmerged~   | git branch --no-merged
gbu         | git branch --set-upstream-to
gbu~        | git branch --unset-upstream
----------  | ----------
gbdm        | <code>_() { git branch --merged ${1-master} \| grep -v " ${1-master}$" | xargs -n 1 git branch -d; }; _</code>
**gbdmerged** | *gbdm*
----------  | ----------
gbl         | git blame -b -w
----------  | ----------
gbs         | git bisect
gbsb        | git bisect bad
gbsg        | git bisect good
gbsr        | git bisect run
gbsre       | git bisect reset
**gbsreset**| *gbsre*
gbss        | git bisect start
----------  | ----------
gc          | git commit -v
gc!         | git commit -v --amend
gcgc        | git commit --amend --no-edit
**gcgc!**   | *gcgc*
gca         | git commit -v -a
gca!        | git commit -v -a --amend
gcm         | git commit -m
gcm!        | git commit --amend -m
gcam        | git commit -a -m
gcam!       | git commit -a --amend -m
----------  | ----------
gcf         | git config
gcfa        | git config --add
gcfe        | git config --edit
gcfg        | git config --get-regexp
gcfl        | git config --list
gcff        | `cat ``git rev-parse --git-dir``/config`
gcfrm       | git config --remove-section
gcfrn       | git config --rename-section
gcfso       | git config --show-origin
gcfsoa      | <code>gcfl \| cut -d= -f1 \| while read line; do git config --show-origin $line; done</code>
gcfu        | git config --unset
gcfua       | git config --unset-all
----------  | ----------
gcf~        | git config --local
gcfa~       | git config --local --add
gcfe~       | git config --local --edit
gcfg~       | git config --local --get-regexp
gcfl~       | git config --local --list
gcff~       | `cat ``git rev-parse --git-dir``/config`
gcfrm~      | git config --local --remove-section
gcfrn~      | git config --local --rename-section
gcfu~       | git config --local --unset
gcfua~      | git config --local --unset-all
----------  | ----------
gcf!        | git config --global
gcfa!       | git config --global --add
gcfe!       | git config --global --edit
gcfg!       | git config --global --get-regexp
gcfl!       | git config --global --list
gcff!       | `if [ -f "$HOME/.gitconfig" ]; then cat "$HOME/.gitconfig"; elif [ -f "$XDG_CONFIG_HOME/git/config" ]; then cat "$XDG_CONFIG_HOME/git/config"; fi`
gcfrm!      | git config --global --remove-section
gcfrn!      | git config --global --rename-section
gcfu!       | git config --global --unset
gcfua!      | git config --global --unset-all
----------  | ----------
gcl         | git clone --recursive
**gclone**  | *gcl*
----------  | ----------
gclean!     | git clean -df
gclean      | `echo "Running in dry-run mode. \n Note: Run \"gclean!\" to perform the UNRECOVERABLE clean operation."; git clean -dfn`
----------  | ----------
gco         | git checkout
gco-        | git checkout -
gcob        | git checkout -b
gcoB        | git checkout -B
gcoo        | git checkout --orphan
----------  | ----------
gco~        | git checkout -m
gco-~       | git checkout -m -
gcob~       | git checkout -m -b
gcoB~       | git checkout -m -B
gcoo~       | git checkout -m --orphan
----------  | ----------
gco!        | git checkout -f
gco-!       | git checkout -f -
gcob!       | git checkout -f -b
gcoB!       | git checkout -f -B
gcoo!       | git checkout -f --orphan
gco~!       | git checkout -f -m
gco-~!      | git checkout -f -m -
gcob~!      | git checkout -f -m -b
gcoB~!      | git checkout -f -m -B
gcoo~!      | git checkout -f -m --orphan
----------  | ----------
gcp         | git cherry-pick
gcpa        | git cherry-pick --abort
gcpc        | git cherry-pick --continue
gcpq        | git cherry-pick --quit
----------  | ----------
gcount      | git count-objects --human-readable
----------  | ----------
gd          | git diff
gda         | git diff -U99999
gdn         | git diff --name-status
**greview** | *gda*
gdck        | git diff --check
gdw         | git diff --word-diff
----------  | ----------
gd!         | git diff --cached
gda!        | git diff -U99999
**greview!**| *gda!*
gdck!       | git diff --cached --check
gdw!        | git diff --cached --word-diff
----------  | ----------
gdt         | git diff-tree --no-commit-id --name-only -r
----------  | ----------
gdvim       | git difftool --tool=vimdiff -U99999
----------  | ----------
gde         | git describe
**gdesc**   | *gde*
**gdescribe**| *gde*
gdet        | git describe --tags
----------  | ----------
gf          | git fetch
gfa         | git fetch --all --tags --prune
----------  | ----------
gi          | git init
gib         | git init --bare
----------  | ----------
gignore     | git update-index --assume-unchanged
gignored    | <code>git ls-files -v \| grep "^[[:lower:]]"</code>
gignore~    | git update-index --no-assume-unchanged
**gunignore** | *gignore~*
----------  | ----------
glg         | `git log --pretty=format:"%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset" --abbrev-commit`
glog        | git log --stat --notes --show-signature --decorate --color -p
glt         | *glg --graph*
glta        | *glg --graph --all*
gltw        | *glg --graph --all --reflog*
glast       | git log -1 --notes --show-signature --log-size -p
----------  | ----------
glf         | git ls-files
glf~        | git ls-files --others --directory
glfi        | git ls-files --others --ignored --exclude-standard --directory
----------  | ----------
gll         | `_() { ls -dlhG $(git ls-tree --name-only ${1-HEAD}) }; _`
gls         | `_() { ls -dG $(git ls-tree --name-only ${1-HEAD}) }; _`
gllr        | `_() { ls -lhG $(git ls-tree -r --name-only ${1-HEAD}) }; _`
glsr        | `_() { ls -G $(git ls-tree -r --name-only ${1-HEAD}) }; _`
----------  | ----------
gm          | git merge
gma         | git merge --abort
gm          | git merge --no-ff
gmsq        | git merge --squash
**gmsquash**| gmsq
----------  | ----------
gmv         | git mv
----------  | ----------
gmb         | git merge-base
**ganc**    | *gmb*
----------  | ----------
gp          | git push
gpu         | git push -u
gpdb        | git push --delete
gpp         | `_() {git push $1 && git push --tags $1}; _`
gpd         | git push --tags --dry-run
**gpdr**    | *gpd*
gpt         | git push --tags
----------  | ----------
gp!         | git push --force
gpu!        | git push --force -u
gpp!        | `_() {git push --force $1 && git push --tags --force $1}; _`
gpd!        | git push --tags --dry-run --force
**gpdr!**   | *gpd!*
gpt!        | git push --tags --force
----------  | ----------
gpl         | git pull --tags
gplr        | git pull --tags --rebase
----------  | ----------
gpl!         | git pull --tags
gplr!        | git pull --tags --rebase
----------  | ----------
gr          | git remote -v
gra         | git remote add
grrm        | git remote remove
grrn        | git remote rename
grgu        | git remote get-url
grsu        | git remote set-url
grp         | git remote prune
gru         | git remote update
----------  | ----------
grb         | git rebase
grbi        | git rebase -i
grba        | git rebase --abort
grbc        | git rebase --continue
grbs        | git rebase --skip
grbon       | git rebase --onto
----------  | ----------
grm         | git rm
grm~        | git rm --cached
----------  | ----------
grs         | git reset --mixed
grsh        | git reset --mixed HEAD --
**gunstage**| *grsh*
----------  | ----------
grs~        | git reset --soft
grsh~       | git reset --soft HEAD --
gunstage~   | grsh~
----------  | ----------
grs!        | git reset --hard
grsh!       | git reset --hard HEAD --
**gunstage!**| *grsh!*
----------  | ----------
grt         | <code>cd $(git rev-parse --show-toplevel \|\| echo ".")</code>
**groot**   | *grt*
----------  | ----------
grv         | git revert
grvn         | git revert -n
grva        | git revert --abort
grvc        | git revert --continue
grvq        | git revert --quit
----------  | ----------
gs          | git status -sb
gss         | git status --ignored
gst         | git -c pager.status=less status -vv
----------  | ----------
gshow       | git show
gcat        | git cat-file -p
----------  | ----------
gsl         | git shortlog
gslnm       | git shortlog --no-merges
----------  | ----------
gsm         | git submodule
gsma        | git submodule add
gsmf        | git submodule foreach
gsmfr       | git submodule foreach --recursive
gsmi        | git submodule init
gsmi~       | git submodule deinit
gsmi~!      | git submodule deinit --force
**gsmdi**   | *gsmi~*
**gsmdi!**  | *gsmi~!*
gsms        | git submodule status --recursive
gsmsum      | git submodule summary
**gsmsummary**| *gsmsum*
gsmsync     | git submodule sync --recursive
gsmu        | git submodule update --init --recursive
gsmpla      | `_() { git submodule foreach --recursive git pull ${1-origin} ${2-master} }; _`
gsmpla!     | `_() { git submodule foreach --recursive git pull --force ${1-origin} ${2-master} }; _`
----------  | ----------
gsta        | git stash -p
gstak       | git stash --keep-index
gstau       | git stash --include-untracked
gstaa       | git stash apply
gstac!      | git stash clear
gstac       | echo "CAUTION: Use \"gstac!\" to clear all stored stashes."
gstad!      | git stash drop
gstad       | echo "CAUTION: Use \"gstad!\" to drop the stash."
gstal       | git stash list
gstap       | git stash pop
gstas       | git stash show --text
----------  | ----------
gt          | git tag
gta         | git tag -a
gtp         | gpt
gtp!        | gpt!
gts         | git tag -s
gtv         | git tag -v
gvt         | git verify-tag
----------  | ----------
gwip        | `git add -A && git rm $(git ls-files --deleted) 2> /dev/null; git commit -m "--wip--" && echo "WIP\!"`
gunwip      | <code>git log -n 1 \| grep -q -c -- "--wip--" && git reset HEAD~1</code>
**gwip~**   | *gunwip*
----------  | ----------
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

[git-aliases.sh]: https://github.com/zheeeng/.dotfiles/blob/master/envconfig/git-aliases.sh
