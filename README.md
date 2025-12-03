# Git Lifetime Notes

Below are Git commands you will use throughout your development life.
Categories are organized for clarity.

---

# Index

1. [Logging & History](#logging--history)
2. [Config](#config)
3. [Branching & Switching](#branching--switching)
4. [Rebase & Reset](#rebase--reset)
5. [Remote](#remote)
6. [Commit Editing](#commit-editing)
7. [Inspection & Recovery](#inspection--recovery)
8. [Merging & Conflicts](#merging--conflicts)
9. [Rebase (Advanced)](#rebase-advanced)
10. [Cleaning Up Commits](#cleaning-up-commits)
11. [Stashing](#stashing)
12. [Undoing & Diffing](#undoing--diffing)
13. [Picking Commits](#picking-commits)
14. [Debugging With Bisect](#debugging-with-bisect)
15. [Tagging](#tagging)

---

# Logging & History

### `git --no-pager log -n 10 --oneline --parents --graph`

Shows last 10 commits in a clean graph view.

### `git log --oneline --graph --all --parents`

Displays the entire commit history across all branches.

### `git diff`

Shows changes between working directory and last commit.

### `git diff HEAD~1`

Shows difference between the last two commits.

### `git diff <COMMIT1> <COMMIT2>`

Compare any two commits.

---

# Config

### `git config set --global/local section.key value`

Set Git configuration values.

### `git config --global user.name "Your Name"`

Set global username.

### `git config --global user.email "you@email.com"`

Set global email.

### `git config --global init.defaultBranch main`

Set main as default branch.

### `git config --global alias.st status`

Alias `git st` for status.

### `git config --system --list`

Show system config.

### `git config --global --list`

Show global config.

### `git config --local --list`

Show repo config.

---

# Branching & Switching

## Create Branch

### `git switch -c new_branch`

Create and switch to a new branch.

## Switch Branch

### `git switch branch_name`

Switch to an existing branch.

## Switch Back to Previous Branch

### `git switch -`

Return to last branch.

## List Branches

### `git branch`

List local branches.

### `git branch -a`

List local + remote branches.

### `git branch -vv`

Show branches with last commit.

## Rename Branch

### `git branch -m old_name new_name`

Rename a branch.

### `git branch -m new_name`

Rename current branch.

## Delete Branch

### `git branch -d branch_name`

Delete if merged.

### `git branch -D branch_name`

Force delete.

## Create Branch Without Switching

### `git branch new_branch`

## Create Branch From Commit

### `git branch new_branch <commit_hash>`

---

# Rebase & Reset

### `git rebase main`

Rebase current branch onto main.

### `git reset --soft HEAD~3`

Move HEAD back but keep changes staged.

### `git reset --hard`

Discard all local changes.

### `git reset --hard <COMMIT_HASH>`

Reset repo to a specific commit.

---

# Remote

### `git push origin <branch_name>`

Push branch to remote.

---

# Commit Editing

### `git commit --amend`

Edit the last commit.

### `git rebase -i HEAD~n`

Rewrite last n commits.

### `git rebase --continue`

Continue after editing a commit.

### `git rebase --abort`

Abort rebase.

### `git show <commit_hash>`

Show details of a commit.

---

# Inspection & Recovery

### `git reflog`

Show all HEAD states.

### `git cat-file -p <SHA>`

Inspect Git objects.

---

# Merging & Conflicts

### `git merge <branch>`

Merge a branch.

### `git merge HEAD@{1}`

Merge previous HEAD.

### Merge Conflict Rules

`HEAD` = your branch
Other branch = incoming changes

### After fixing conflicts

```
git add .
git commit -m "merge"
```

---

# Rebase Advanced

### `git rebase <branch>`

Reapply commits on another branch.

### After conflict:

```
git add .
git rebase --continue
```

### Enable rerere

Git auto-resolves previously fixed conflicts.

---

# Cleaning Up Commits

### `git rebase -i HEAD~n`

Squash / reorder / delete commits.

---

# Stashing

### `git stash -m "message"`

Save work-in-progress.

### `git stash list`

List stashes.

### `git stash apply stash@{n}`

Apply a stash.

### `git stash drop stash@{n}`

Delete a stash.

---

# Undoing & Diffing

### `git revert <commit>`

Undo via reverse commit.

### `git diff`

Show unstaged changes.

### `git diff HEAD~1`

Show difference between last 2 commits.

### `git diff <A> <B>`

Compare commits.

---

# Picking Commits

### `git cherry-pick <commit>`

Apply that commit on current branch.

---

# Debugging With Bisect

Git Bisect finds the commit that introduced a bug.

## Bisect Steps

1. Start bisect

   ```
   git bisect start
   ```

2. Mark a known good commit

   ```
   git bisect good <commitish>
   ```

3. Mark a known bad commit

   ```
   git bisect bad <commitish>
   ```

4. Git checks out midpoint
   Test the repository for the bug.

5. Mark current commit

   ```
   git bisect good
   ```

   or

   ```
   git bisect bad
   ```

6. Repeat until Git finds the exact commit.

7. Exit bisect mode

   ```
   git bisect reset
   ```

---

# Tagging

### `git tag -a "tagname" -m "message"`

Create an annotated tag.

---
