# Day 20 – Bash Scripting Challenge: Log Analyzer and Report Generator

## Task 1: Input and Validation

Your script should:

* Accept the path to a log file as a command-line argument

* Exit with a clear error message if no argument is provided

* Exit with a clear error message if the file doesn't exist

```bash

#!/bin/bash

# ======================================
# Log Analyzer and Report Generator
# ======================================

# Task 1: Input Validation

if [ $# -ne 1 ]; then
    echo "Error: Please provide a log file."
    echo "Usage: $0 <log_file>"
    exit 1
fi

LOG_FILE="$1"

if [ ! -f "$LOG_FILE" ]; then
    echo "Error: File does not exist."
    exit 1
fi

DATE=$(date +%Y-%m-%d)
REPORT_FILE="log_report_${DATE}.txt"

echo "=================================="
echo "Log Analysis Started"
echo "=================================="

# Total lines
TOTAL_LINES=$(wc -l < "$LOG_FILE")

# Task 2: Error Count
ERROR_COUNT=$(grep -Ei "ERROR|Failed" "$LOG_FILE" | wc -l)

echo "Total Error Count: $ERROR_COUNT"

# Task 3: Critical Events

echo
echo "--- Critical Events ---"

CRITICAL_EVENTS=$(grep -n "CRITICAL" "$LOG_FILE")

if [ -z "$CRITICAL_EVENTS" ]; then
    echo "No critical events found."
else
    echo "$CRITICAL_EVENTS"
fi

# Task 4: Top Error Messages

echo
echo "--- Top 5 Error Messages ---"

TOP_ERRORS=$(grep "ERROR" "$LOG_FILE" \
| sed 's/.*ERROR] //' \
| sort \
| uniq -c \
| sort -rn \
| head -5)

if [ -z "$TOP_ERRORS" ]; then
    echo "No ERROR messages found."
else
    echo "$TOP_ERRORS"
fi

# Task 5: Generate Report

{
echo "=================================="
echo "Daily Log Analysis Report"
echo "=================================="
echo "Date of Analysis: $DATE"
echo "Log File: $LOG_FILE"
echo "Total Lines Processed: $TOTAL_LINES"
echo "Total Error Count: $ERROR_COUNT"
echo

echo "--- Top 5 Error Messages ---"
echo "$TOP_ERRORS"
echo

echo "--- Critical Events ---"
if [ -z "$CRITICAL_EVENTS" ]; then
    echo "No critical events found."
else
    echo "$CRITICAL_EVENTS"
fi

} > "$REPORT_FILE"

echo
echo "Report generated: $REPORT_FILE"

# Task 6: Archive Processed Logs

mkdir -p archive

mv "$LOG_FILE" archive/

echo "Log file moved to archive/"
echo "Analysis Complete"

```


Sample logs generator.sh 

```bash
#!/bin/bash

# Usage: ./log_generator.sh <log_file_path> <num_lines>

if [ "$#" -ne 2 ]; then
    echo "Usage: $0 <log_file_path> <num_lines>"
    exit 1
fi

log_file_path="$1"
num_lines="$2"

if [ -e "$log_file_path" ]; then
    echo "Error: File already exists at $log_file_path."
    exit 1
fi

# List of possible log message levels
log_levels=("INFO" "DEBUG" "ERROR" "WARNING" "CRITICAL")

# List of possible error messages
error_messages=("Failed to connect" "Disk full" "Segmentation fault" "Invalid input" "Out of memory")

# Function to generate a random log line
generate_log_line() {
    local log_level="${log_levels[$((RANDOM % ${#log_levels[@]}))]}"
    local error_msg=""
    if [ "$log_level" == "ERROR" ]; then
        error_msg="${error_messages[$((RANDOM % ${#error_messages[@]}))]}"
    fi
    echo "$(date '+%Y-%m-%d %H:%M:%S') [$log_level] $error_msg - $RANDOM"
}

# Create the log file with random log lines
touch "$log_file_path"
for ((i=0; i<num_lines; i++)); do
    generate_log_line >> "$log_file_path"
done

echo "Log file created at: $log_file_path with $num_lines lines."

```

## Task 2: Error Analysis

* Counts lines containing ERROR or Failed
  
* Displays total error count

## Task 3: Critical Event Detection

* Searches for CRITICAL entries
  
* Displays matching lines with line numbers

## Task 4: Top Error Messages

* Extracts ERROR messages
* Counts occurrences
* Displays top 5 most frequent errors
  
## Task 5: Summary Report
Generates:

log_report_.txt

Contains:

Analysis date

Log filename

Total lines processed

Error count

Top 5 errors

Critical events

## Task 6: Log Archiving

Creates archive directory if missing

Moves processed log file to archive/

Commands Used

grep
Used for:

Finding ERROR
Finding Failed
Finding CRITICAL
wc
Used for counting:

Total lines
Error lines
sort
Used for sorting error messages.

uniq -c
Used for counting duplicate error messages.

sed
Used for extracting only the error message text.

mv
Used to move processed logs into archive folder.

