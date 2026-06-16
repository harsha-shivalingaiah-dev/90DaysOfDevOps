# Day 23 – Git Branching & Working with GitHub

## Task 1: Understanding Branches

### What is a branch in Git?

A branch is an independent line of development in Git. It allows developers to work on new features, bug fixes, and experiments without affecting the main codebase.

### Why do we use branches instead of committing everything to main?

Branches help keep the main branch stable. Developers can work on features separately, test them, and merge them into main only when they are ready.

### What is HEAD in Git?

HEAD is a pointer that refers to the current branch and the latest commit you are working on.

### What happens to your files when you switch branches?

Git updates your working directory to match the selected branch. Files and changes specific to that branch become visible.

## Task 2: Branching Commands — Hands-On

In your devops-git-practice repo, perform the following:

```bash 
List all branches in your repo
git branch

Create a new branch called feature-1
git branch feature-1

Switch to feature-1
git switch feature-1

Create a new branch and switch to it in a single command — call it feature-2
git switch -c feature-2

Try using git switch to move between branches — how is it different from git checkout?

git switch is used specifically for switching branches.

git checkout can switch branches, restore files, and move to specific commits.

git switch is the newer and safer command.

Make a commit on feature-1 that does not exist on main

Switch back to main — verify that the commit from feature-1 is not there

Delete a branch you no longer need

Add all branching commands to your git-commands.md
