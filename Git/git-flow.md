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
* `bugfix/<bug name>`: When you encouter bugs, create a `bugfix` branch off from `develop`.
* `hotfix/<hotfix version>`: When you get feedbacks to patch a hotfix, create a `hotfix` branch off from `master`.
* `support`: To satisfy some customers, you cloud add some special features on a `support` branch which is based on a specific production version.

## Workflow

![git flow model](http://nvie.com/img/git-model@2x.png)
*The graphic workflow of git flow model*


