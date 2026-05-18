# What is Linux?
Linux is an operating system (OS) — just like Windows or macOS. It manages your computer's hardware and lets you run programs.

•	Free and open-source — anyone can see, modify, and distribute its code

•	Highly stable and secure — powers most of the world's servers, phones (Android) and supercomputers

•	Created by Linus Torvalds in 1991

# What is Shell? 
The shell is a program that lets you talk to the OS by typing commands. It's the interface between you and the kernel.

When you type a command like ls (list files) or mkdir (make folder) below happens in background:

You type "ls"      

•	Shell (translates the command) 

•	Kernel (does the actual work — reads the filesystem) 

•	Shell (receives the result and displays it)  

•	You see the list of files on screen

# Layers of Linux

•	Applications - software programs, utilities, compilers and databases that run in the User Space

•	Shell – Acts as interface which takes commands and converts them into format the kernel understands

•	System Libraries – toolkits that programs use to talk to the kernel

•	Kernel  - Heart of Linux which manages memory, process and devices

•	Hardware – CPU, RAM and Hard disks 

# Kernel Space vs User Space 
To keep the system stable, Linux separates these two areas. Applications run in User Space where they have limited powers. 
The kernel runs in Kernel Space, which has full access to the hardware. This prevents a single crashing app from taking down the whole computer.

# What is process in linux? 
When you run a program, the OS creates a process — it's simply a program in execution.

# Types of processes
Foreground Process

•	Runs directly in your terminal

•	You have to wait for it to finish before typing next command

Background Process

•	Runs behind the scenes, terminal is free immediately

•	You add & at the end to run in background

Daemon Process

•	Runs silently in the background always — even without a user

•	Starts when Linux boots up

# Process States

A process is constantly changing states as the CPU switches between tasks

•	Running/Runnable: The process is either currently using the CPU or waiting in a queue to run.

•	Sleeping: The process is waiting for an event, such as user input or a file to be read.

•	Stopped: The process has been suspended, usually by a user signal (like pressing Ctrl+Z).

•	Zombie: A process that has finished execution but still has an entry in the system table because its parent hasn't

acknowledged its termination

# Daily commands used in Linux
•	date
•	uptime
•	mkdir
•	ls
•	df -h
•	cd
•	mv 
•	cat 
•	echo 
•	history 
•	pwd
•	rm 
•	top/htop 

