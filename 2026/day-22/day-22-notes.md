# Day 22 – Introduction to Git: Your First Repository

## Challenge Tasks

## Task 1: Install and Configure Git

1. Verify Git is installed on your machine

```bash
git --version
```

2.Set up your Git identity — name and email

```bash
git config --global user.name "harsha-shivalingaiah-dev"
git config --global user.email "harsha.shivalingaiah@gmail.com"
```
3.Verify your configuration

```bash
git config -l
```

<img width="269" height="75" alt="image" src="https://github.com/user-attachments/assets/8241d83d-79db-4f25-81f6-d6cb5e442195" />


## Task 2: Create Your Git Project

1.Create a new folder called devops-git-practice

```bash
mkdir devops-git-practice
```
2.Initialize it as a Git repository

```bash
git devops-git-practice
```

3.Check the status — read and understand what Git is telling you

```bash
git status
```
4. Explore the hidden .git/ directory — look at what's inside
   
```bash
cd .git
```

<img width="478" height="172" alt="image" src="https://github.com/user-attachments/assets/8c63b486-28d8-46cb-be2c-8309c48c9975" />



<img width="442" height="164" alt="image" src="https://github.com/user-attachments/assets/b0bf2148-8bd0-4882-9d83-d08134fca859" />



<img width="379" height="122" alt="image" src="https://github.com/user-attachments/assets/a714e2ed-fe82-4db7-9161-511e2df53e68" />


## Task 3: Create Your Git Commands Reference

1. Create a file called git-commands.md inside the repo
```bash
vim git-commands.md
```

2. Add the Git commands you've used so far, organized by category:
   
Setup & Config

Basic Workflow

Viewing Changes

```bash
git --version
mkdir devops-git-practice
git devops-git-practice
git config --global user.name "harsha-shivalingaiah-dev"
git config --global user.email "harsha.shivalingaiah@gmail.com"
git status
```

For each command, write:
What it does (1 line)
An example of how to use it



## Task 4: Stage and Commit

Stage your file

Check what's staged

Commit with a meaningful message

View your commit history

<img width="434" height="113" alt="image" src="https://github.com/user-attachments/assets/6ed077e4-1774-424f-95a5-550eaaa553f8" />


<img width="452" height="265" alt="image" src="https://github.com/user-attachments/assets/57ae30b6-5658-4320-80ce-f2862747e221" />


## Task 5: Make More Changes and Build History

Edit git-commands.md — add more commands as you discover them

Check what changed since your last commit

Stage and commit again with a different, descriptive message

Repeat this process at least 3 times so you have multiple commits in your history

View the full history in a compact format

<img width="409" height="152" alt="image" src="https://github.com/user-attachments/assets/9666837c-be2e-41f8-9970-7624d71c2217" />



<img width="524" height="296" alt="image" src="https://github.com/user-attachments/assets/6514d78e-cb09-4074-887e-a6e2af14f84a" />


<img width="358" height="45" alt="image" src="https://github.com/user-attachments/assets/53da35e0-a27d-4bae-bf67-ff09f454f1a8" />



