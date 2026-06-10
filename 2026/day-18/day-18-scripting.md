# Day 18 - Shell Scripting Functions & Intermediate Concepts

## Task 1 - Basic Functions

Create functions.sh with:

* A function greet that takes a name as argument and prints Hello, <name>!
  
* A function add that takes two numbers and prints their sum
  
* Call both functions from the script

```bash

#!/bin/bash

greet() {
    echo "Hello, $1!"
}

add() {
    echo "Sum: $(($1 + $2))"
}

greet "Harsha"
add 10 20

```

<img width="587" height="124" alt="image" src="https://github.com/user-attachments/assets/fef4d7ef-a8ad-40bf-9286-2d3141da47ed" />


## Task 2: Functions with Return Values

Create disk_check.sh with:

A function check_disk that checks disk usage of / using df -h

A function check_memory that checks free memory using free -h

A main section that calls both and prints the results

```bash

#!/bin/bash

check_disk () {
    echo "Disk Usage"
        df -h /
}
check_memory () {
    echo "Memory Usage"
        free -h
}
check_disk
check_memory

```

<img width="950" height="232" alt="image" src="https://github.com/user-attachments/assets/c440388a-6bd1-4549-a97c-6c61c0bef283" />


## Task 3 - Strict Mode

set -euo pipefail

Usage:

set -e → Exit on command failure

set -u → Exit on undefined variables

set -o pipefail → Detect failures inside pipelines

Benefits:

Safer scripts

Easier debugging

Prevents hidden errors

```bash

#!/bin/bash

set -euo pipefail

echo "Strict Mode Demo"

# Uncomment one at a time

# echo $UNDEFINED_VAR

# false

# cat missing_file.txt | grep hello

``` 
<img width="683" height="413" alt="image" src="https://github.com/user-attachments/assets/88ffc087-29d3-48c0-bf5b-f43012744ce6" />

# Task 4: Local Variables

Create local_demo.sh with:

A function that uses local keyword for variables

Show that local variables don't leak outside the function

Local variables stay inside functions
Regular variables remain accessible outside

Compare with a function that uses regular variables

```bash 
#!/bin/bash

local_var_demo() {
    local name="Harsha"
    echo "Inside function: $name"
}

regular_var_demo() {
    city="Bengaluru"
    echo "Inside function: $city"
}


local_var_demo

echo "Outside function local variable: ${name:-Not Available}"

regular_var_demo

echo "Outside function regular variable: $city"

``` 



