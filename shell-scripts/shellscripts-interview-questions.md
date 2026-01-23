## 1. What is a shell?
- A shell is a command-line interpreter used to communicate with the operating system.
## 2. What is a shell script?
- Shell scripting is writing a text file with Linux shell commands to automate tasks, where the commands are executed one after another by the shell.

## 3. What is Bash?

Bash is the most commonly used shell in Linux systems.

## 4 Common shells in Linux?

Bash (most common)

Sh

Zsh

Ksh

Csh

## 4. How to make a script executable?
```
chmod +x script.sh
```
## 5. How to run a shell script?
```
./script.sh
sh script.sh
bash script.sh
```
## 6 What is the shebang line (#!/bin/bash) in shell scripting?
- The shebang line (#!/bin/bash) tells the operating system which shell interpreter should be used to execute the script.
## 7. How do you declare a variable?
```
name="Hanumanth" # (no spaces allowed)
```
## 8. How to access a variable?
- echo $name

## 9. What are positional parameters?

- Arguments passed to script.
```
 $0	- It represents the script name.
 $1, $2...	They are positional arguments passed to the script.
 $#	It gives the number of arguments passed.
 $@ - It represents all arguments individually.
 $*	all arguments as single string
```
## 10. What is $??

- It gives the exit status of the last executed command.
## 11 How do you take input from the user in shell scripting?
- Use the read command to take input from the user and store it in a variable.
```
#!/bin/bash
echo "Enter your name:"
read name
echo "Hello, $name!"
```
## 12. How to write an if condition?
if [ condition ]; then
   commands
fi

## 13. How to write loops?

- A loop in shell scripting is used to execute a block of commands repeatedly until a certain condition is met.
```
for i in 1 2 3; do
  echo $i
done

##  while loop Runs as long as a condition remains true.

while loop

count=1
while [ $count -le 5 ]; do
  echo $count
  count=$((count+1))
done
```
## 14. What is $? in shell?

Exit status of last command.

0 → success

non-zero → failure

## 15. Difference between == and = in shell?

= used for string comparison

== supported in [[ ]]


## 16. What is logical AND?

&& – both conditions must be true.

## 17. What is logical OR?

|| – any one condition must be true.

## 18. What is arithmetic expansion?

- Used for calculations: $((a + b)).

## 19. Check if file exists
if [ -f file.txt ]; then
   echo "exists"
fi
## 20. Check directory exists
if [ -d /home/test ]; then
   echo "directory exists"
fi

## 21. Read file line-by-line
while read line; do
  echo $line
done < file.txt

## 22 What is set -x and how is it used for debugging in shell scripts?

- set -x enables debug mode in shell scripts by printing each command before it is executed, which helps identify conditional and logic issues.

## 23. What is set -e in shell scripting and why is it used?

set -e is used to stop the script or exit immediately when a command failure, ensuring error handling and script safety.


## 24. What is a function in Shell?
myfunc() {
  echo "Hello"
}
myfunc

## 25. What is piping |?

Sends output of one command to another.

ls | grep txt

## 26. What are environment variables?

Variables used by shell or OS.

List:

printenv

## 27. How do you export a variable?
export JAVA_HOME=/usr/local/java

## 28. Script to monitor CPU/Memory?
top -b -n1 | grep "Cpu"
free -m

## 29. Delete all logs older than 7 days
find /var/log -type f -mtime +7 -delete

## 30. Script to check service is running
systemctl status nginx || systemctl start nginx

## 31. Script to check disk usage & alert
df -h | awk '$5+0 > 80 {print "Disk Full"}'

## 32. Script to backup a folder
tar -czf backup.tar.gz /home/data

## 33. Script to read usernames from file & create users
while read user; do
   useradd $user
done < users.txt

## 34. Script to ping a server & send alert
ping -c 1 google.com || echo "Server down"

🔹 SECTION 6 — ADVANCED DEVOPS-LEVEL QUESTIONS
## 35. Difference: #!/bin/bash vs #!/usr/bin/env bash?

/usr/bin/env bash → more portable.

## 36. What is here document (EOF)?

Used to pass multi-line data to command.

cat <<EOF
Hello
EOF

## 37 What is trap in shell scripting and why is it used?
- trap handles signals like Ctrl+C and allows cleanup actions before a script exits.
- A notification sent to a process, like SIGINT when you press Ctrl+C
```
#!/bin/bash

trap "echo 'Script interrupted'; exit" SIGINT

while true; do
  sleep 1
done

```
## 38 What is xargs in Linux and why is it used?
- xargs is used to pass output of one command as arguments to another command.
## exmaple
```
find /tmp -name "*.log" | xargs rm

- find searches for all .log files in /tmp
- xargs passes those file names to rm
- rm deletes all the found .log files
```
## 39. Shell script for JSON parsing?
```
Using jq:

cat file.json | jq '.name'
```
## 40. What is subshell?

- Any command inside parentheses runs in new shell.

- (ls; pwd)

## 41. Write script to reverse a string
- echo "$str" | rev

## 42. Find even numbers from 1–50
```
for i in {1..50}; do
  [ $((i % 2)) -eq 0 ] && echo $i
done
```
## 43. Script to validate email
```
[[ $email =~ ^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$ ]]
```
## What does the uniq command do in Linux?
- The uniq command removes duplicate consecutive lines from a file or input.
```
sort file.txt | uniq
```
## 44. What is set -u?

- Throws an error when using undefined variables.

## 45. What is an environment variable?

- A variable available to all child processes.

## 46. What is $PATH?

- It stores directories where executable commands are located.

## 47. What is command substitution?

- Running a command and storing its output using $(command).

## 48. Difference between single and double quotes?

- Single quotes don’t expand variables; double quotes do.

## 49. How do you compare numbers?

- Using -eq, -gt, -lt.

## 50. How do you compare strings?

- Using = or !=.

## 51. What does unset do?

- Removes a variable.

## 52. What does break do?

- Exits the loop immediately.

## 53. What does continue do?
- Skips current iteration and moves to next.

## 54. What does -x check?
- Checks if a file is executable.

## 55. What is negation operator?

- ! reverses condition result.

## 56. What is an infinite loop?

- A loop that never stops unless forced.

## 57. How do you stop an infinite loop?

- Using break or CTRL+C.

## 58. What is idempotency?

- Script gives same result on multiple runs.

## 59 What is awk and what is its purpose in shell scripting?
- awk is a text-processing tool used to extract, filter, and format data from files or command output, especially column-based data.
## Print a specific column
```
awk '{print $1}' file.txt
```
## Print coloums if matching a condition
```
awk '$3 > 5000 {print $1, $3}' employees.txt
```
---
## 60. What is sed in shell scripting and what is its purpose?

- sed is used to search, replace, or delete text in files from the command line efficiently.
## Replace a word in a file
```
sed 's/oldword/newword/' file.txt
```
## Delete empty lines in a file
```
sed '/^$/d' file.txt
```
---
## 61 What is the cut command in shell scripting and why is it used?
- cut is used to extract specific columns or fields from text or files, often when working with structured data like CSV or logs.
## Extract the first column of a file
```
cut -d',' -f1 file.csv
-d',' → uses comma as a delimiter

-f1 → selects the first field/column
```
## 62 Why do we use cut and awk in shell scripting? What is the difference?
## Answer
- cut is used to quickly extract specific columns or characters from a file; it’s simple and fast.
- awk is used for advanced text processing, including filtering, formatting, and calculations on data.






