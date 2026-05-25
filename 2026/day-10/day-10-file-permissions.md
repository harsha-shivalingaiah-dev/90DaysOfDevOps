# Day 10 – File Permissions & File Operations Challenge

## Task 1: Create Files

* Create empty file devops.txt using touch
  
* Create notes.txt with some content using vim or echo
  
* Create script.sh using vim with content: echo "Hello Doston, welcome to TWS Day 10 Challenge!!"


<img width="1330" height="277" alt="image" src="https://github.com/user-attachments/assets/f677e741-c673-463a-b777-dbdca67c96e3" />

* Verify: ls -l to see permissions

<img width="673" height="205" alt="image" src="https://github.com/user-attachments/assets/64873004-733c-43ff-8148-182a1c668f60" />


<img width="779" height="245" alt="image" src="https://github.com/user-attachments/assets/c6f865db-74af-4f32-9eda-14070aaafe68" />


## Task 2: Read Files

* Read notes.txt using cat

  <img width="781" height="120" alt="image" src="https://github.com/user-attachments/assets/2f5d54b0-b757-49b2-8d9f-f45a880ac865" />

  
* View script.sh in vim read-only mode

  <img width="773" height="760" alt="image" src="https://github.com/user-attachments/assets/e86a2604-ba10-40cf-a8ae-c1d8bcf30da6" />


  
* Display first 5 lines of /etc/passwd using head
  
* Display last 5 lines of /etc/passwd using tail

<img width="1103" height="560" alt="image" src="https://github.com/user-attachments/assets/f97a5602-cb5f-4790-b065-3d12d32f6aa8" />

## Task 3: Understand Permissions

* Format: rwxrwxrwx (owner-group-others)

r = read (4), w = write (2), x = execute (1)

<img width="928" height="206" alt="image" src="https://github.com/user-attachments/assets/42154256-459a-4c6e-8ea6-36a09603d693" />

By default all 3 files have same permissions (644)

owner : read + write but no execute

group : read + write but no execute

others: ready only but no write or execute 


# Task 4: Modify Permissions

* Make script.sh executable → run it with ./script.sh
  
<img width="806" height="318" alt="image" src="https://github.com/user-attachments/assets/dd7dcb7b-24b9-4a42-8b01-90c5375ea088" />

* Set devops.txt to read-only (remove write for all)

<img width="748" height="232" alt="image" src="https://github.com/user-attachments/assets/4eca48f7-b253-4d68-b068-7160f168ed17" />

* Set notes.txt to 640 (owner: rw, group: r, others: none)

<img width="803" height="241" alt="image" src="https://github.com/user-attachments/assets/a5079cd2-5d09-46ce-af4f-c15b9d2babb6" />

* Create directory project/ with permissions 755

<img width="736" height="159" alt="image" src="https://github.com/user-attachments/assets/b33cb62f-5fa8-48f7-b265-b90771567a3c" />


## Task 5: Test Permissions

* Try writing to a read-only file - what happens?

<img width="1129" height="118" alt="image" src="https://github.com/user-attachments/assets/349e7eb1-4136-4634-8a7a-4dab812a59ee" />

  
* Try executing a file without execute permission

<img width="744" height="246" alt="image" src="https://github.com/user-attachments/assets/82425336-fefa-414b-a980-9c29586b1452" />

----

## Learnings for today

* Managing files permissions effectively.
  
* Sudo can override read and write restrictions.
  
* By default linux creates a file with 644 permission and a directory with 755 permission.









