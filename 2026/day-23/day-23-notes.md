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
```



<img width="458" height="254" alt="image" src="https://github.com/user-attachments/assets/00c40bef-3da8-49c4-a0dc-0d1816bc20c1" />




## Try using git switch to move between branches — how is it different from git checkout?

git switch is used specifically for switching branches.

git checkout can switch branches, restore files, and move to specific commits.

git switch is the newer and safer command.


Make a commit on feature-1 that does not exist on main

Switch back to main — verify that the commit from feature-1 is not there

Delete a branch you no longer need

Add all branching commands to your git-commands.md


## Task 3: Push to GitHub

Create a new repository on GitHub (do NOT initialize it with a README)

Connect your local devops-git-practice repo to the GitHub remote

Push your main branch to GitHub

Push feature-1 branch to GitHub

Verify both branches are visible on GitHub




## Task 4: Pull from GitHub

Make a change to a file directly on GitHub (use the GitHub editor)

Pull that change to your local repo


## Task 5: Clone vs Fork

Clone any public repository from GitHub to your local machine

Fork the same repository on GitHub, then clone your fork
