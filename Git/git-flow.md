# git-flow (AVH Edition)

The git-flow (AVH Edition) provides development model on repository operations enhenced from Vincent Driessen's [Git branching model](http://nvie.com/posts/a-successful-git-branching-model/). 

**Note:** AVH is the acronym of "A VirtualHome".

## Installing

    brew install git-flow-avh

## Branches

* `master`: It is used as the production branch and under long-term maintenance. Git-flow marks stable release versions and patched hotfix versions as tags on this branch.
* `develop`: It is the long-term development branch, merge all developed features, released versions and fixed bugs and hotfixes. 
* `feature/<feature name>`: It is used for feature development.
* `release/<release version>`: It is used for next release.
* `bugfix/<bug name>`: When you encouter bugs, create a `bugfix` branch start off from `develop`.
* `hotfix/<hotfix version>`: When you get feedbacks to patch a hotfix, create a `hotfix` branch start off from `master`.
* `support/<support version>`: To maintain the stability of some releases which are still in-use by some people, the `support` branch is suggested to patch and develop customizing features on it.

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
support     | &check;  | &check; |          |           |         |        |          |

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

### Develop a feature

1. Create && switch to a `feature` branch based on the latest commit on `develop` branch by default:

        git flow feature start <feature name>

2. Develop your feature and commit your changes.

    * If you cooperate with others, try pushing this feature and notify your partners:

            git flow feature publish <feature name>

        After a stage of development, push the recent commits:

            git push origin feature/<feature name>

    * Reversely, you may be notified to track a new added `feature` branch and assist the continuing development:

            git flow feature track <feature name>

        When you are going to receive the latest feature commits, checkout the `feature` branch, then pull down the commits:

            git checkout feature/<feature name>
            git pull --rebase origin feature/<feature name>

    * Maybe for some reasons, a `feature` under development is about to be discarded and won't be continued anymore:

            git flow feature delete -f <feature name>

        If this branch is published, notify your partners to force delete their local `feature` branch as you did above. You'd also need to delete the shared remote branch:

            git push origin :feature/<feature name>

3. Once you finished your feature development, run `finish` command. Git-flow will merge `feature` branch back to `develop` branch, delete the local and remote(if your branch is published) branches, and switch git `HEAD` into `develop` branch:

        git flow feature finish <feature name>

    Push the merged `develop` branch to remote and don't forget to remind your partners that you just closed a `feature` branch:

        git push origin develop

4. If you are one of the feature development collaborators, once you are notified that a feature development is finished, or you find a vanished remote `feature` branch after running `git fetch -p`, delete the local one manually:

        git flow feature delete <feature name>

    Prune the remote branch that doesn't exist anymore:

        git remote prune origin

### Make a release

1. Create && switch to a `release` branch based on the latest commit on `develop` branch by default. You cloud also specify a SHA-1 hash for releasing as you need:

        git flow release start <release version> [<base>]

2. Push the release to remote repository:

        git flow release publish <release version>

    Other people cloud pull release:

        git flow release track <release version>

3. After adding && committing the Version information, Changelog, License, README file and so on, pushing && pulling commits, making sure your release is fully tested, finish this final release:

        git flow release finish <release version>

    It merges the `release` branch to the `master` and `develop` branches, tags `<release version>` on the merged commmit node of `master` and also removes the `release` branch.

4. Push `develop` and `master` branches and your tags:

        git push origin develop; git push origin master; git push --tags

5. As a collaborator, pull down remote changes and don't forget to remove the tracked `release` branch that doesn't exist anymore at remote:

        git fetch -p
        git flow release delete <release version>

### Bugfix

1. Create && switch to a `hotfix` branch based on the latest commit on `develop` branch by default.

        git flow bugfix start <bug name>

2. After bugfixing commited, finish this branch:

        git flow bugfix finish <bug name>

    It merges the `bugfix` branch back to `develop` branch and removes the `bugfix` branch.


