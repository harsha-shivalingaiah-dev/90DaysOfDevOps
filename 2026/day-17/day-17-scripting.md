# Day 17 – Shell Scripting: Loops, Arguments & Error Handling

## Task

### Level up your scripting — use loops, handle arguments, and deal with errors.

* Write for and while loops

* Use command-line arguments ($1, $2, $#, $@)

* Install packages via script

* Add basic error handling

# Task 1 - For Loop

for_loop.sh

Loops through a list of fruits and prints each one.

```bash

#!/bin/bash

for fruit in Apple Banana Mango Orange Watermelon Muskmelon Gauva 
do
    echo "$fruit"
done
```

Sample Output 

```bash
ubuntu@ip-172-31-33-163:~/scripts$ ./for-loop.sh
Apple
Banana
Mango
Orange
Watermelon
Muskmelon
Gauva
```
<img width="644" height="224" alt="image" src="https://github.com/user-attachments/assets/7498e6c4-03c7-416c-8806-a7bf43c5c871" />


count.sh

Prints numbers 1 to 10 using a for loop.

```bash
#!/bin/bash

for i in {1..10}
do
    echo "$i"
done
```

Sample Output 

```bash

ubuntu@ip-172-31-33-163:~/scripts$ ./count.sh
1
2
3
4
5
6
7
8
9
10
ubuntu@ip-172-31-33-163:
```

<img width="574" height="313" alt="image" src="https://github.com/user-attachments/assets/9ad47023-41bc-438a-ba45-01207be8710b" />


## Task 2 - While Loop

countdown.sh

Takes a number from the user, counts down to 0 and prints "Done!" when finished.

```bash

#!/bin/bash

echo "Enter a number:"
read num

while [ $num -ge 0 ]
do
    echo "$num"
    num=$((num-1))
    printf "countdown begins"
done

echo "Done!"
```
SAmple output

```bash
ubuntu@ip-172-31-33-163:~/scripts$ ./countdown.sh
Enter a number:
4
4
3
2
1
0
Countdown begins
Done!
```

<img width="649" height="220" alt="image" src="https://github.com/user-attachments/assets/e4b709c6-16d4-4e32-9b2a-59f3d92d3cc7" />



## Task 3 - Command-Line Arguments

greet.sh

Accepts a name as a command-line argument and prints a greeting message. If no argument is provided, it displays usage instructions.

```bash

#!/bin/bash

if [ -z "$1" ]
then
    echo "Usage: ./greet.sh <name>"
else
    echo "Hello, $1!"
fi

```

Sample output 

```bash

ubuntu@ip-172-31-33-163:~/scripts$ ./greet1.sh
Usage: ./greet1.sh <name>


ubuntu@ip-172-31-33-163:~/scripts$ ./greet1.sh Harsha
Hello, Harsha!

```

args_demo.sh

Script name using $0

Total number of arguments using $#

All arguments using $@

```bash 
#!/bin/bash

echo "Script Name: $0"
echo "Total Arguments: $#"
echo "All Arguments: $@"

```

<img width="653" height="367" alt="image" src="https://github.com/user-attachments/assets/40461f76-c744-4afd-a2c3-d2ccdbf5a219" />


## Task 4 - Install Packages via Script

install_packages.sh

* Defines a list of packages (nginx, curl, wget)

* Checks whether each package is installed

* Installs missing packages

* Skips already installed packages

* Displays status messages

```bash

#!/bin/bash

if [ "$EUID" -ne 0 ]
then
    echo "Please run as root"
    exit 1
fi

packages=("nginx" "curl" "wget")

for pkg in "${packages[@]}"
do
    if dpkg -s "$pkg" &>/dev/null
    then
        echo "$pkg is already installed"
    else
        echo "Installing $pkg..."
        apt update
        apt install -y "$pkg"
    fi
done

```

<img width="745" height="104" alt="image" src="https://github.com/user-attachments/assets/60cad4fc-ee2b-4736-9457-6d7494859d9b" />

Sample Output 

```bash

ubuntu@ip-172-31-33-163:~/scripts$ ./install-packages.sh
Please run as root

```

## Task 5 - Error Handling

safe_script.sh

Implemented error handling using:

set -e

|| operator for handling failures

Directory creation

Navigation into the directory

File creation

```bash

#!/bin/bash

set -e

mkdir /tmp/devops-test || echo "Directory already exists"

cd /tmp/devops-test || {
    echo "Failed to enter directory"
    exit 1
}

touch test.txt || echo "Failed to create file"

echo "Script completed successfully"

```

<img width="688" height="102" alt="image" src="https://github.com/user-attachments/assets/a875f0c9-9207-4e6c-99cf-ab0c1b49930d" />









