# Day 24 – Advanced Git: Merge, Rebase, Stash & Cherry Pick

## Task 1: Git Merge — Hands-On

* Create a new branch feature-login from main, add a couple of commits to it

* Switch back to main and merge feature-login into main

<img width="649" height="338" alt="image" src="https://github.com/user-attachments/assets/83131407-1062-412c-81dd-07ad3449c087" />

* Observe the merge — did Git do a fast-forward merge or a merge commit?

<img width="402" height="85" alt="image" src="https://github.com/user-attachments/assets/7520c4c0-caa9-4db5-b982-358c9e15c69c" />


* Now create another branch feature-signup, add commits to it — but also add a commit to main before merging

<img width="434" height="71" alt="image" src="https://github.com/user-attachments/assets/c77cc5da-d535-4b78-8f8e-539a35ba5a01" />


<img width="499" height="302" alt="image" src="https://github.com/user-attachments/assets/ee9bccca-71cd-42c9-8eb7-25545cedc1e7" />


<img width="424" height="85" alt="image" src="https://github.com/user-attachments/assets/47b035a0-5533-4d93-8dce-db86c4524a36" />



## Answer in your notes:

* What is a fast-forward merge?

A fast-forward merge occurs when the branch being merged has no new commits since it diverged from the main branch, allowing Git to simply move the branch pointer forward to the latest commit

* When does Git create a merge commit instead?

Git creates a merge commit when the branches have diverged, meaning both have new, unique commits since they split, requiring Git to combine the histories into a new common commit

* What is a merge conflict?

Merge conflicts happen because the same file is edited in two branches.Git cannot figure out which version of a file to keep during a merge.
