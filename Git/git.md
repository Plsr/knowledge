# Useful commands

## Remove local branches that have been deleted in the remote repository
`git fetch --prune` removes any remote-tracking references that no longer exist on the remote before fetching.

## Temporarily ignoring files
There are cases where you want to temporarily ignore files, but do not want them to be untracked in general (i.e. if you and your team aggreed to not check in `schema.rb` files in Pull Requests in a rails project). To acheive that, just run

```git
git update-index --assume-unchanged <file>
```

If you later want to track this file again (i.e. when you are checking out master), run

```git
git update-index --no-assume-unchanged <file>
```

## Undo the last commit but keep the changes

Sometimes, I do commit changes I did, but only want to do so temporarily. This is the case, for example, when wanting to change a branch, but having changes in the current branch, where `git stash` is not an option (e.g. because there are untracked files present).  
To undo this commit, simply use

```git
git reset HEAD^
```
