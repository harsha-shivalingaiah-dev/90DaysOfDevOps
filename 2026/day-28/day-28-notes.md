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




