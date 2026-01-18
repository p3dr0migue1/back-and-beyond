+++
date = '2024-12-09T16:42:04Z'
draft = false
tags = ['Git']
title = 'Revert Git Commits'
+++

## The problem
How do I undo local commits in git?

## The solution
The git reset command will return the current branch to a specified previous commit.
By default, this command will remove commits from the current branch’s history while leaving the files in the working tree untouched.

This allows you to redo one or more commits without losing any work.
When calling git reset, you need to specify the commit to reset to.

You can get the hash of the commit you want from git log, or you can specify an ancestor of HEAD, the current commit, using the tilde (~) suffix.

```bash
git add .
git commit -m "This commit is a mistake"
git reset HEAD~
git add main.py # need to re-add files after reset
git commit -m "This commit corrects the mistake"
```

To undo the last two commits do:
```bash
git add .
git commit -m "This commit is a mistake"
# make changes
git add .
git commit -m "This commit is another mistake"
git reset HEAD~2
git add .
git commit -m "this commit corrects both mistakes"
```

If you don’t want to have to re-stage your files after a reset, you can use the --soft flag:
```bash
git add .
git commit -m "This commit is a mistake"
git reset --soft HEAD~
# no need to git add, as files are already staged
git commit -m "This commit corrects the mistake"
```

If you want to reset both the Git history and the working tree to the state of a previous
commit, you can use the --hard flag.

Note that this will reverse all changes made to tracked files, including ones that
haven’t yet been committed.
```bash
git add .
git commit -m ""
git reset --hard HEAD~
```

git reset --hard should be used with caution.
However, you can still retrieve any deleted commits using git reflog, up to 90 days after they
were deleted. When run, git reflog will show a list of commits previously on the
tips of branches.

From this list, you can pick out the partial hash of the commit (e.g. 5c8f5a7) to restore and
create a new branch for it:
```bash
git checkout -b restored-commit-branch 5c8f5a7
```

If you would like to preserve your repository’s history but return the files to a
previous state, you can use git revert to create new commits that do the opposite of
existing commits, i.e. removing lines and files that were added and adding lines and files that
were removed:
```bash
git add .
git commit -m "This commit is a mistake"
git revert HEAD # will create a new commit doing the opposite of the one above
```

See original [here]("https://sentry.io/answers/undo-the-most-recent-local-git-commits/")
