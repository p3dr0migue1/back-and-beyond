+++
date = '2024-11-04T15:40:40Z'
draft = false
tags = ['Git']
title = 'Changing Default Git Remote Push Default'
+++

To change which upstream remote is \"wired\" to your branch, use the `git branch` command with the upstream configuration flag.
Ensure the remote exists first:
```bash
git remote -v
```

Set the preferred remote for the current (checked out) branch:
```bash
git branch --set-upstream-to <remote-name>;
```

Validate the branch is setup with the correct upstream remote:
```bash
git branch -vv
```
