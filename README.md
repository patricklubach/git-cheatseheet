# git-cheatseheet

## Stages

1. workspace
1. index/stage
1. history

## Cheat Sheet

Configure git:

```bash
git config user.name "Patrick Lubach"
git config user.email "plubach1994@gmail.com"
```

Get changed and staged files:

```bash
git status
```

Get list of staged files:

```bsh
git diff --cached --name-only
```

Unstage all staged files / unstage specific files:

```bash
# uncommit changes, changes are left staged (index).
git reset --soft
# uncommit + unstage changes, changes are left in working tree.
git reset --mixed (default)
# uncommit + unstage + delete changes, nothing left.
gti reset --hard
# or
git reset HEAD
# or
git reset COMMIT_ID -- FILE1 FILE2
```

Hard reset of a single file (the `--` means: treat every argument after this point as a file name):

```bash
git checkout HEAD -- PATH_TO_YOUR_FILE
# or
git checkout YOUR_COMMIT_ID -- PATH_TO_YOUR_FILE
```

Get the commit history of the current branch

```bash
git log
# or
git log BRANCH_NAME
```

Get differences between two branches:

```bash
git diff BRANCH1..BRANCH2
# or
git diff LOCAL_BRANCH..origin/REMOTE_BRANCH
```

Get difference between two files from different branches:

```bash
git diff mybranch master -- myfile.cs
```

Save and revert work:

```bash
git stash       # Create git stash
git stash list  # Shows list of all stashes
git stash pop   # Applies changes to workspace
git stash clear # Clears stash list
```

Re-order commits or combine non-consecutive commits:

```bash
git rebase --interactive COMMIT_ID
```

Git will open an editor, and you see a file like this, ex: `git rebase --interactive HEAD~4`

```bash
pick aaaaaaa Commit A
pick bbbbbbb Commit B
pick ccccccc Commit C
pick ddddddd Commit D

# Rebase aaaaaaa..ddddddd onto 1234567 (4 command(s))
#
# Commands:
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```

Now you change the file that it looks like this:

```bash
pick aaaaaaa Commit A
squash ddddddd Commit D
pick bbbbbbb Commit B
pick ccccccc Commit C
```
