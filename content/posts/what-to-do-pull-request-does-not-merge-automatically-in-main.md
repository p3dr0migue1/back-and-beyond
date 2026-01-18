+++
date = '2024-11-04T16:38:25Z'
draft = false
tags = ['Git']
title = 'What to Do Pull Request Does Not Merge Automatically in Main'
+++

The problem is that both in `main` branch and in your local branch some files have been changed, and their going in different directions.

The content of the file(s) in main is different from the one in your `feature_branch`, and git does not know which one to pick, or how to integrate them.

To solve this, you need to:

* Get the latest upstream/main
```bash
git fetch upstream
```

* Switch to your main branch
```bash
git checkout main
```

* Merge the latest remote main in your local main branch (Never develop in master, always develop in a feature branch)
```bash
git merge upstream/main
```

* Switch to your feature branch
```bash
git checkout my_feature_branch
```

* Merge main in your feature branch
```bash
git merge main
```

* Solve all the conflicts: this is where you decide how to integrate the conflicting files, and this can be done only by you because you know what you did, you can figure out what happened in main, and pick the best way to integrate them.
```bash
git mergetool
```

* Commit all the changes, after all the conflicts are solved
```bash
git commit -m "Decent commit message"
```

* Push your feature branch to your origin: the Pull Request will automatically update
```bash
git push origin my_feature_branch
```

References:
[What do I do when my Pull Request does not merge automatically in master?](https://blog.michelemattioni.me/2013/01/29/what-do-i-do-when-my-pull-request-does-not-merge-automatically-in-master/)
