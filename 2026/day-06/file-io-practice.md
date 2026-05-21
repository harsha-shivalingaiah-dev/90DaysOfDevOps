# Day 06 – Linux Fundamentals: Read and Write Text Files

## Tasks for today

•	Creating a file

•	Writing text to a file

•	Appending new lines

•	Reading the file back

## Commands and Output

touch demo-notes.txt : It created an empty file


```bash
ubuntu@ip-10-0-3-187:~/demo$ touch demo-notes.txt
ubuntu@ip-10-0-3-187:~/demo$ ls
demo-notes.txt
ubuntu@ip-10-0-3-187:~/demo$
```

echo "Line 1" > notes.txt : It will add contents into file and you can display using cat command

```bash
ubuntu@ip-10-0-3-187:~/demo$ echo "Today is Day 06 for 90DaysDevOps session" > demo-notes.txt
ubuntu@ip-10-0-3-187:~/demo$
ubuntu@ip-10-0-3-187:~/demo$ cat demo-notes.txt
Today is Day 06 for 90DaysDevOps session
```

echo "Line 2" >> notes.txt : It will append the contents to the file next to the existing lines (not overwrite the existing)

```bash
ubuntu@ip-10-0-3-187:~/demo$ echo Practising creating,writing text into file and appending new lines to file >> demo-notes.txt
ubuntu@ip-10-0-3-187:~/demo$
ubuntu@ip-10-0-3-187:~/demo$ cat demo-notes.txt
Today is Day 06 for 90DaysDevOps session
Practising creating,writing text into file and appending new lines to file
ubuntu@ip-10-0-3-187:~/demo$
```

echo "Line 3" | tee -a notes.txt : It will write and display the new line at same time, also it will append next to existing lines
```bash
ubuntu@ip-10-0-3-187:~/demo$ echo This line will be added and displayed at same time using tee command | tee -a demo-notes.txt
This line will be added and displayed at same time using tee command
ubuntu@ip-10-0-3-187:~/demo$
```

cat demo-notes.txt : This will display the contents of the file
```bash
ubuntu@ip-10-0-3-187:~/demo$ cat demo-notes.txt
Today is Day 06 for 90DaysDevOps session
Practising creating,writing text into file and appending new lines to file
This line will be added and displayed at same time using tee command
ubuntu@ip-10-0-3-187:~/demo$
```

head -n 2 demo-notes.txt : It will display first 2 lines of the file
```bash
ubuntu@ip-10-0-3-187:~/demo$ head -n 2 demo-notes.txt
Today is Day 06 for 90DaysDevOps session
Practising creating,writing text into file and appending new lines to file
ubuntu@ip-10-0-3-187:~/demo$
```
tail -n 2 demo-notes.txt : It will display last 2 lines of the file
```bash
ubuntu@ip-10-0-3-187:~/demo$ tail -n 2 demo-notes.txt
Practising creating,writing text into file and appending new lines to file
This line will be added and displayed at same time using tee command
```
