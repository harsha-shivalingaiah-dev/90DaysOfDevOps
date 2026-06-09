# Day 16 – Shell Scripting Basics

## Task 1: Your First Script

1.Create a file hello.sh

2.Add the shebang line #!/bin/bash at the top

3.Print Hello, DevOps! using echo

4.Make it executable and run it


<img width="634" height="187" alt="image" src="https://github.com/user-attachments/assets/aa6eab7a-6be3-4624-884e-67a71ba12e7a" />


<img width="541" height="226" alt="image" src="https://github.com/user-attachments/assets/fa8dbe98-35aa-4019-8537-76a2b524b4d6" />

```bash
#!/bin/bash

echo "This is a shell script"
```

# What Happens Without a Shebang?

The shebang (#!/bin/bash) tells Linux which interpreter should execute the script.

# Without the shebang:

Running the script with bash hello.sh still works.

Running the script directly using ./hello.sh may fail or use a different shell depending on the system configuration.

The script becomes less portable and predictable.


## Task 2: Variables

Script: variables.sh

<img width="662" height="150" alt="image" src="https://github.com/user-attachments/assets/95cdd42c-956a-4b19-bda0-435c0dd1ee78" />


<img width="595" height="172" alt="image" src="https://github.com/user-attachments/assets/fa9e8719-072e-470f-9251-dc7250baa8c7" />

```bash
#!/bin/bash

NAME="Harsha"
ROLE="Devops Engineer"

echo "Hello, I am $NAME and I am $ROLE"

```

## Single Quotes vs Double Quotes

NAME="Harsha"

echo '$NAME'

echo "$NAME"

## Output

$NAME

Harsha

## Observation

Single quote (' ') treats variables as plain text.

Double quotes (" ") expand variables and display their values.


## Task 3: User Input with read

Script: greet.sh

```bash 
#!/bin/bash

read -p "Enter your name: " NAME
read -p "Enter your favourite tool: " TOOL

echo "Hello $NAME, your favourite tool is $TOOL"
```

Execution

chmod +x greet.sh

./greet.sh

```bash
Sample Output

Enter your name: Harsha

Enter your favourite tool: Docker

Hello Harsha, your favourite tool is Docker
```

<img width="603" height="182" alt="image" src="https://github.com/user-attachments/assets/ca67c218-2af6-45e2-a380-41aa2cfa3463" />



## Task 4A: If-Else Conditions

Script: check_number.sh

```bash

#!/bin/bash

read -p "Enter a number: " NUM

if [ "$NUM" -gt 0 ]; then
    echo "Positive Number"
elif [ "$NUM" -lt 0 ]; then
    echo "Negative Number"
else
    echo "Zero"
fi

```

Output

```bash
Enter a number: 27
Positive Number

Enter a number: -1
Negative Number
```




