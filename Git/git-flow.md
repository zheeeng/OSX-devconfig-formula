# git-flow (AVH Edition)

The git-flow (AVH Edition) provides development model on repository operations enhenced from Vincent Driessen's [Git branching model](http://nvie.com/posts/a-successful-git-branching-model/). 

**Note:** AVH is the acronym of "A VirtualHome".

## Installing

    brew install git-flow-avh

## Branches

* `master`: It is used as the production branch and under long-term maintenance. Git-flow marks stable release versions and patched hotfix versions as tags on this branch.
* `develop`: It is the long-term development branch, merge all developed features, released versions and fixed bugs and hotfixes. 
* `feature/<feature name>`: It is used for feature development.
* `release/<release version name>`: It is used for next release.
* `bugfix/<bug name>`: When you encouter bugs, create a `bugfix` branch start off from `develop`.
* `hotfix/<hotfix version>`: When you get feedbacks to patch a hotfix, create a `hotfix` branch start off from `master`.
* `support`: To satisfy some customers, you cloud add some special features on a `support` branch which is based on a specific production version.

## Commands

List of sub-commands on specific branch:

Branch name | `[list]` | `start` | `finish` | `publish` | `track` | `diff` | `rebase` | `delete`
:---------: | :------: | :------:|:-------: | :-------: | :-----: | :----: | :------: | :-----:
master      |          |         |          |           |         |        |          |
develop     |          |         |          |           |         |        |          |
feature     | &check;  | &check; | &check;  | &check;   | &check; | &check;| &check;  | &check;
release     | &check;  | &check; | &check;  | &check;   | &check; |        |          | &check;
bugfix      | &check;  | &check; | &check;  | &check;   | &check; | &check;| &check;  | &check;
hotfix      | &check;  | &check; | &check;  | &check;   |         |        |          | &check;
support     | &check;  | &check; | &check;  |           |         |        |          |

Other sub-commands:
* `git flow <branch> pull <name>` is about to be deprecated. Use `git flow <branch> track <name>` instead.
* `git flow <branch> checkout <name>` is about to be deprecated. Use raw git command `checkout` instead.
* `git flow init` initializes on an empty directory or a git repository for git-flow supporting.
* `git flow version` shows version information.
* `git flow config` manages your git-flow configuration.
* `git flow log` shows current branch log compared to `develop` branch.
* The usage `git flow <branch> diff` is recommend to be instead by `git diff <branch name>...<base branch>`.

## Workflow

![git flow model](http://nvie.com/img/git-model@2x.png)
*The graphic workflow of git flow model*

### Initialize git-flow

Initialize for git-flow supporting:

    git flow init [-d]

Option '-d' means using default settings. Two long term branches, `master` and `develop`, are settled.

### Link remote repository

To fully make use of the distributed version control, the preparation work on the upstream repository and branches is imperative. If you perform the initialization in a repository containing remote branches—`remotes/origin/develop` or `remotes/origin/master`, git-flow will add upstream tracking on `master` or `develop` branches respectively.

In other situations, you need to link remote repository through commands:

1. Check branches and the relationship to their upstream branches.

        git branch -avv

    We expect `master` and `develop` keep track on upstream branches:

        develop                         5bcfed9 [origin/develop] Release from a base branch gets errors on finishing.
        master                          43548ed [origin/master] Merge branch 'release/1.9.1'

    If the trackings is settled over, skip to next [part](#develop-a-feature), otherwise—

2. Add remote repository:

        git remote add origin git@gitserver:REPONAME.git

3. Manually make the `master` branch and the `develop` branch keep track on remotes':

        git push -u origin master; git push -u origin develop


