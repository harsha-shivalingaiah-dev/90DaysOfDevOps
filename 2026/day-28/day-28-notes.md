# Day 28 – Revision Day: Everything from Day 1 to Day 27

## Task 1: Self-Assessment Checklist

Go through the checklist below. For each item, mark yourself honestly:

* Can do confidently
* Need to revisit
* Haven't done yet

## Linux

* [Confident] Navigate the file system, create/move/delete files and directories
* [Confident] Manage processes — list, kill, background/foreground
* [Confident] Work with systemd — start, stop, enable, check status of services
* [Confident] Read and edit text files using vi/vim or nano
* [Confident] Troubleshoot CPU, memory, and disk issues using top, free, df, du
* [Confident] Explain the Linux file system hierarchy (/, /etc, /var, /home, /tmp, etc.)
* [Confident] Create users and groups, manage passwords
* [Confident] Set file permissions using chmod (numeric and symbolic)
* [Confident] Change file ownership with chown and chgrp
* [Revisit]   Create and manage LVM volumes
* [Confident] Check network connectivity — ping, curl, netstat, ss, dig, nslookup
* [Revisit]   Explain DNS resolution, IP addressing, subnets, and common ports

## Shell Scripting

* [revisit]   Write a script with variables, arguments and user input
* [Confident] Use if/elif/else and case statements
* [Confident] Write for, while, and until loops
* [Confident] Define and call functions with arguments and return values
* [revisit]   Use grep, awk, sed, sort, uniq for text processing
* [revisit]   Handle errors with set -e, set -u, set -o pipefail, trap
* [Confident] Schedule scripts with crontab
  
## Git & GitHub

* [Confident] Initialize a repo, stage, commit, and view history
* [Confident] Create and switch branches
* [Confident] Push to and pull from GitHub
* [Confident] Explain clone vs fork
* [revisit]   Merge branches — understand fast-forward vs merge commit
* [revisit]   Rebase a branch and explain when to use it vs merge
* [revisit]   Use git stash and git stash pop
* [revisit]   Cherry-pick a commit from another branch
* [revisit]   Explain squash merge vs regular merge
* [revisit]   Use git reset (soft, mixed, hard) and git revert
* [Confident] Explain GitFlow, GitHub Flow, and Trunk-Based Development
* [Confident] Use GitHub CLI to create repos, PRs, and issues

----

## Task 2: Topics Revisited

### 1. Logical Volume Manager (LVM)

LVM provides flexible storage management compared to traditional disk partitions.

Key components:

* Physical Volume (PV)
* Volume Group (VG)
* Logical Volume (LV)

Important Commands:

```bash
pvcreate /dev/sdb
vgcreate data_vg /dev/sdb
lvcreate -L 5G -n app_lv data_vg
lvdisplay
```

Learning

* Storage can be extended without repartitioning disks.
* Multiple disks can be combined into one volume group.
* Logical volumes can be resized dynamically.
* LVM is widely used in enterprise Linux environments.

## 2. Shell Script Error Handling

Shell scripts should fail safely when unexpected situations occur.

Important options

```bash
set -e
set -u
set -o pipefail
```

Example 

```bash
#!/bin/bash

set -euo pipefail

echo "Starting script"
cp file.txt backupdir/
echo "Completed"
```

* set -e exits when a command fails.
* set -u prevents undefined variables.
* pipefail catches failures inside pipelines.
* trap can be used for cleanup actions.

------

## Task 3: Quick-Fire Questions

### What does chmod 755 script.sh do?

* Owner receives read, write, and execute permissions.
* Group and others receive read and execute permissions.

Permission breakdown:

```bash
7 = rwx
5 = r-x
5 = r-x
```

### Difference Between a Process and a Service

* A process is any running program currently executing on the system.
* A service is a background process managed by the operating system, usually through systemd.

Example:

* Process: Running Vim editor
* Service: Nginx web server

### How Do You Find Which Process Is Using Port 8080?

sudo ss -tulpn | grep 8080

Alternative:

sudo lsof -i :8080

### What Does set -euo pipefail Do?

It makes shell scripts safer by:

* Exiting on command failures
* Detecting undefined variables
* Catching pipeline failures

### Difference Between git reset --hard and git revert

git reset --hard 

Rewrites history,Removes commits,Risky in teams

git revert

Preserves history,Creates new undo commit,Safe in teams

### Branching strategy would you recommend for a team of 5 developers shipping weekly
Trunk-based development

### What Does git stash Do?

Temporarily stores uncommitted changes without creating a commit.

Useful when:

* Switching branches
* Pulling urgent fixes
* Testing another feature

Commands:

```bash
git stash
git stash list
git stash pop
```

### Run a Script Every Day at 3 AM

crontab -e 

0 3 * * *  /home/harsha/backup.sh 


### Difference Between git fetch and git pull

Git Fetch
* Downloads changes only.

git fetch

Git Pull
* Downloads and merges changes.

git pull

### What is LVM?
LVM (Logical Volume Manager) is a storage management system that provides flexible disk allocation, resizing, and management compared to traditional partitions.

Benefits:

* Easy storage expansion
* Better disk utilization
* Snapshot support
* Enterprise-ready storage management

### Task 4: Teach It Back
Explaining File Permissions to a New Linux User

* Every file and directory in Linux has permissions that determine who can read, write, or execute it.
* Permissions are divided into three categories: owner, group, and others.
* Each category can have read (r), write (w), and execute (x) permissions.
* Commands like chmod modify permissions, while chown changes ownership.
* Understanding permissions is essential because they help secure files and control access within multi-user environments.








