---
title: "Git commands and tricks you must know"
date: 2018-09-08 18:29:07
tags: ["Git", "cmd", "diff", "zsh", commands]
---

## Recommend plugins

* Make your diff so fancy - [diff-so-fancy](https://github.com/so-fancy/diff-so-fancy)
* [ZSH Git alias](https://github.com/robbyrussell/oh-my-zsh/blob/master/plugins/git/git.plugin.zsh
)

## Commands

```bash
# Remove tracking branches no longer on remote
git fetch -p && for branch in `git branch -vv | grep ': gone]' | awk '{print $1}'`; do git branch -D $branch; done

# Roll back only one folder to one commit
git checkout hashOfCommit folderName

# Discard every change
git reset --hard

# Undo most recent commit
git reset HEAD~

# Rebase pull
git pull --rebase

# Push to target remote, -u is short for --set-upstream
git push -u <remote-name> <branch>

# Check commit's message and change(-p)
git log -p -2

# Update to latest submodules
git submodule update --recursive --remote

# Rebase
git rebase <commit SHA or branch>

# Rebase in interactive mode
git rebase -i <commit SHA or branch>

# Rebase interactive mode commands
git rebase --skip # you will need this if no change in some steps
git rebase --continue # After resolving conflict and git add <conflict file>

$ git rebase -i HEAD~3 # You need to edit "pick" part to tell git to do commands on the commit
pick 8b9100d add relative line mode
pick f175572 add gzip size measuring
pick 9bac799 :book: check progressive JPEG

# Rebase 9a4f60e..9bac799 onto 9a4f60e (3 commands)
#
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup <commit> = like "squash", but discard this commit's log message
# x, exec <command> = run command (the rest of the line) using shell
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified). Use -c <commit> to reword the commit message.
```
