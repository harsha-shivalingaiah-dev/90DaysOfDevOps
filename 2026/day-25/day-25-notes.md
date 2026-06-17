
# Day 25 – Git Reset vs Revert & Branching Strategies

## Task 1: Git Reset

* What happens with git reset --soft?

Moves HEAD back one commit.

Removes commit from history.

Keeps all changes staged.

Ready to commit again.

* What happens with git reset --mixed?
Moves HEAD back one commit.

Removes commit from history.

Keeps changes in working directory.

Changes become unstaged.

* What happens with git reset --hard?
Moves HEAD back one commit.

Removes commit from history.

Deletes all changes permanently.

* Difference Between --soft, --mixed, and --hard
--soft → Removes commit but keeps changes staged.
  
--mixed → Removes commit and keeps changes unstaged.

--hard → Removes commit and deletes changes completely.

* Which One Is Destructive?

git reset --hard
Permanently removes commits and working directory changes.

* When Would You Use Each One?
  
--soft → Modify commit message or combine commits.

--mixed → Reorganize files before committing again.

--hard → Discard unwanted local changes.

* Should You Use Reset on Pushed Commits?

No. It rewrites history and can cause conflicts for collaborators.


## Task 2: Git Revert

* What Happens When Reverting Commit Y?
  
Git creates a new commit.

The new commit reverses the changes made by commit Y.

Commit Y remains in history.

* Is Commit Y Still in History?
Yes.
Git Revert preserves history.

* Difference Between Reset and Revert
  
git reset rewrites history and removes commits.

git revert preserves history and creates an undo commit.

* Why Is Revert Safer?
  
History remains intact.

Safe for shared repositories.

No force push required.

* When To Use Revert vs Reset?

Use Revert for shared or pushed commits.

Use Reset for local commits that haven't been pushed.


## Task 3: Reset vs Revert Comparison

| Feature | git reset | git revert |
|----------|-----------|------------|
| What it does | Rewrites history and removes commits | Creates a new commit that undoes changes |
| Removes commit history | Yes | No |
| Creates new commit | No | Yes |
| Safe for shared branches | No | Yes |
| Best use case | Local cleanup | Undo pushed commits |
