# Day 19 – Shell Scripting Project: Log Rotation, Backup & Crontab


## Task 1: Log Rotation Script

Takes a log directory as an argument (e.g., /var/log/backup)

Compresses .log files older than 7 days using gzip

Deletes .gz files older than 30 days

Prints how many files were compressed and deleted

Exits with an error if the directory doesn't exist

```bash

#!/bin/bash

set -euo pipefail

LOG_DIR=$1

if [ ! -d "$LOG_DIR" ]; then
    echo "Error: Directory does not exist"
    exit 1
fi

compressed=0
deleted=0

while read -r file
do
    gzip "$file"
    ((compressed++))
done < <(find "$LOG_DIR" -type f -name "*.log" -mtime +7)

while read -r file
do
    rm "$file"
    ((deleted++))
done < <(find "$LOG_DIR" -type f -name "*.gz" -mtime +30)

echo "Files compressed: $compressed"
echo "Files deleted: $deleted"

```



## Task 2: Server Backup Script

Create backup.sh that:

* Takes a source directory and backup destination as arguments

* Creates a timestamped .tar.gz archive (e.g., backup-2026-06-11.tar.gz)

* Verifies the archive was created successfully

* Prints archive name and size

* Deletes backups older than 14 days from the destination

* Handles errors — exit if source doesn't exist

```bash

#!/bin/bash

set -euo pipefail

SOURCE=$1
DESTINATION=$2

if [ ! -d "$SOURCE" ]; then
    echo "Error: Source directory does not exist"
    exit 1
fi

mkdir -p "$DESTINATION"

DATE=$(date +%Y-%m-%d)
ARCHIVE="$DESTINATION/backup-$DATE.tar.gz"

tar -czf "$ARCHIVE" "$SOURCE"

if [ -f "$ARCHIVE" ]; then
    echo "Backup created successfully"
    echo "Archive: $ARCHIVE"
    du -h "$ARCHIVE"
else
    echo "Backup failed"
    exit 1
fi

find "$DESTINATION" -name "*.tar.gz" -mtime +14 -delete

```


## Task 3: Crontab

Read: crontab -l — what's currently scheduled?

Understand cron syntax:

```bash
* * * * *  command
│ │ │ │ │
│ │ │ │ └── Day of week (0-7)
│ │ │ └──── Month (1-12)
│ │ └────── Day of month (1-31)
│ └──────── Hour (0-23)
└────────── Minute (0-59)
```

Run log_rotate.sh every day at 2 AM ---> 0 2 * * *

Run backup.sh every Sunday at 3 AM ---> 0 3 * * 7

Run a health check script every 5 minutes ---> */5 * * * *



## Task 4: Combine — Schedule Maintenance Script

Create maintenance.sh that:

* Calls your log rotation function

* Calls your backup function

* Logs all output to /var/log/maintenance.log with timestamps

* Write the cron entry to run it daily at 1 AM

  0 1 * * *
