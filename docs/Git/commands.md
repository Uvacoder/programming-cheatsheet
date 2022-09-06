# Commands

## Popular commands

```sh
git branch  -a #show all branches

git branch <branch_name> #create new branch

git push origin -d <remote_branch> #remove remote branch

git checkout <branch_name> #swich branch
git checkout -b <branch_name> #create branch and switch

git checkout -b test origin/<remote_branch>
git checkout -t origin/<remote_branch>

git checkout --orphan empty-branch #create empty branch without any history data

git reset --soft origin/<branch> #reset unpushed commits
git reset --hard origin/<branch>

git reset --soft HEAD~1 #reset one commit back
git reset --hard HEAD~1npm install --global emoji-cz

git fetch <remote_branch> #Update your branch when the original branch from official repository has been updated

git rm -rf . #remove all stashed files
```

[Commands docs](https://www.atlassian.com/git/tutorials/using-branches)

## How to overwrite remote branch with local version

```sh
git push origin <branch>:<remote_branch> #overwrite remote branch with local
```

## How to delete branch / remove branch

```sh
git branch -D feature/init-repo-code #local remove
# or
git push origin --delete test #from origin
```

## Create empty repo | Create empty branch | Overwrite master with empty project

```sh
git checkout another-branch
git branch -D master
git checkout --orphan master
git rm -rf .
git commit --allow-empty -m "Initial commit"
git merge another-branch --squash --allow-unrelated-histories
git checkout master
git push origin master -f
```

## Tag commit and push it

```bash
git tag v1.7.7-beta.20 d43bab9
git push origin master --tags
```

## How to check number of commits by person

```bash
git shortlog -s -n | head -n 20
```

## How to change https to ssh authorization in existing repo

Open file `config` from `.git` folder in you project repository: `code /project_name/.git/config`.

Change url address from one to another.

## Show linked remote repository

```sh
git remote show origin
```

## Change linked remote repository

From https to ssl for example.

```sh
ssh://git@domain.com:7999/project_name
```

## How to revert specific Merge

```sh
git fetch origin
git checkout origin/feature/name-of-branch -b feature/name-of-branch
git revert -m 1 b76a5f1f5d3b323679e466a1a1d
```

## Manage remote branches - show all remote branches and checkout to local version

```sh
# To list remote branches:
git branch -r

# Checkout to local version of remote branch:
git checkout -b LocalName origin/remotebranchname
```

## Add different remote address and push branch to different branch

```sh
# instead of github you can put any different name
git remote add github https://github.com/kubek93/chrome-extension-fill-form-fields.git
# remote-branch could have different name than local once
git push github local-branch:remote-branch
```

## Problem with rebase (if pipeline or git return issue about rebase instead of normal merge)

> You should have the newest version of master branch

```sh
git log
# Check sha of interesting commit
git reset --soft SHA_ID
git rebase master
# If you will have some conflicts resolve them and then use continue
git rebase --continue
git push origin branch_name
```
