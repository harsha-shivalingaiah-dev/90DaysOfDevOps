# Day 26 – GitHub CLI: Manage GitHub from Your Terminal

## Task 1: Install and Authenticate

1.Install the GitHub CLI on your machine

2.Authenticate with your GitHub account

3.Verify you're logged in and check which account is active


<img width="565" height="42" alt="image" src="https://github.com/user-attachments/assets/c8f242ad-169e-4911-bb31-5540c2fb33d7" />


<img width="302" height="51" alt="image" src="https://github.com/user-attachments/assets/af17ec5b-1bee-4cc8-9b19-9a6500bfb90a" />




<img width="512" height="124" alt="image" src="https://github.com/user-attachments/assets/b522e43b-52dd-4878-9212-afaadb1f22c9" />



<img width="337" height="401" alt="image" src="https://github.com/user-attachments/assets/e02e19b9-c71c-48be-9b99-b56861bf3ff2" />


<img width="568" height="85" alt="image" src="https://github.com/user-attachments/assets/6cb06dc6-d31a-48e3-8b20-3051cd1b127a" />




<img width="329" height="239" alt="image" src="https://github.com/user-attachments/assets/028e785a-59a3-4972-b27d-23217025e83f" />


<img width="503" height="120" alt="image" src="https://github.com/user-attachments/assets/86662e16-8798-4fdc-bebb-555858375bc8" />


## What authentication methods does gh support?
* Personal Access Token
* SSH Key-based
* Browser-based login

## Task 2: Working with Repositories

Create a new GitHub repo directly from the terminal — make it public with a README

<img width="488" height="153" alt="image" src="https://github.com/user-attachments/assets/2d8165f6-d807-47c5-a554-48b21ea4f1c1" />

Clone a repo using gh instead of git clone

<img width="945" height="250" alt="image" src="https://github.com/user-attachments/assets/ab6a330b-f7ab-4f9c-bfd9-eb738f34b26a" />


View details of one of your repos from the terminal

List all your repositories

Open a repo in your browser directly from the terminal

Delete the test repo you created (be careful!)

<img width="692" height="187" alt="image" src="https://github.com/user-attachments/assets/3150dc36-b2fb-4361-ac1d-736194aa34f1" />


## Task 3: Issues

### Create an issue on one of your repos from the terminal — give it a title, body, and a label

<img width="449" height="104" alt="image" src="https://github.com/user-attachments/assets/53f588bd-1e66-4b47-884d-c224ec803c14" />


* List all open issues on that repo
* View a specific issue by its number
* Close an issue from the terminal

<img width="952" height="289" alt="image" src="https://github.com/user-attachments/assets/2a1bc9b4-b35e-45d0-8f98-ba7148fd26b1" />


### How gh issue can be used in automation
* Auto-create bug reports
* Create monitoring alerts
* Generate maintenance tasks
* Track CI/CD failures


## Task 4: Pull Requests

1. Create a branch, make a change, push it, and create a pull request entirely from the terminal
   
2. List all open PRs on a repo
   
3. View the details of your PR — check its status, reviewers, and checks
   
4. Merge your PR from the terminal

<img width="466" height="121" alt="image" src="https://github.com/user-attachments/assets/90620c59-06fc-441d-83af-1d6dd185f021" />


<img width="622" height="291" alt="image" src="https://github.com/user-attachments/assets/bcf6f2f7-ad59-4329-b6d7-7f0d003b4a9e" />


<img width="614" height="265" alt="image" src="https://github.com/user-attachments/assets/dc9ccca3-193f-4f28-9acd-64a5820b8476" />

### Answer in your notes:

What merge methods does gh pr merge support?

Merge Commit

Squash and Merge

Rebase and Merge

How would you review someone else's PR using gh?

gh pr review <PR-number>


## Task 5: GitHub Actions & Workflows (Preview)

* List the workflow runs on any public repo that uses GitHub Actions
* View the status of a specific workflow run

## How could gh run and gh workflow be useful in a CI/CD pipeline?

* They allow automation of workflows without interactive sessions, enable triggering, monitoring, and managing GitHub Actions directly from scripts or automation tools

