## 1. What is a shell?

A command-line interpreter that executes the commands you type.

## 2. What is a shell script?

A text file containing shell commands that the system executes sequentially.

## 3. Common shells in Linux?

Bash (most common)

Sh

Zsh

Ksh

Csh

## 4. How to make a script executable?
chmod +x script.sh

## 5. How to run a shell script?
./script.sh
sh script.sh
bash script.sh

## 6. What is #!/bin/bash?

Shebang line that tells the OS which interpreter to use for the script.

## 7. How to define a variable?
name="Hanumanth"

## 8. How to access a variable?
echo $name

## 9. What are positional parameters?

Arguments passed to script.

 Parameter	Meaning
 $0	script name
 $1, $2...	first, second argument
 $#	number of arguments
 $@	all arguments
 $*	all arguments as single string
## 10. How to take input from user?
read name


## 11. How to write an if condition?
if [ condition ]; then
   commands
fi

## 12. How to write loops?

for loop

for i in 1 2 3; do
  echo $i
done


while loop

count=1
while [ $count -le 5 ]; do
  echo $count
  count=$((count+1))
done

## 13. What is $? in shell?

Exit status of last command.

0 → success

non-zero → failure

## 14. Difference between == and = in shell?

= used for string comparison

== supported in [[ ]]

## 15. Arithmetic in shell?
echo $((5+7))


## 16. Check if file exists
if [ -f file.txt ]; then
   echo "exists"
fi

## 17. Check directory exists
if [ -d /home/test ]; then
   echo "directory exists"
fi

## 18. Read file line-by-line
while read line; do
  echo $line
done < file.txt

## 19. Count lines in a file
wc -l file.txt

## 20. What is set -e?

Exit immediately when a command fails.

## 21. What is set -x?

Debug mode — prints every executed command.

## 22. What is a function in Shell?
myfunc() {
  echo "Hello"
}
myfunc

## 23. What is piping |?

Sends output of one command to another.

ls | grep txt

## 24. What are environment variables?

Variables used by shell or OS.

List:

printenv

## 25. How to export a variable?
export JAVA_HOME=/usr/local/java

## 26. Difference between soft link and hard link?
Soft Link	Hard Link
Points to file path	Points to inode
Breaks if source removed	Doesn’t break
Can link directories	Cannot
## 27. What is cron?

Scheduler used for automation.

List jobs:

crontab -l

## 28. What is grep?

Pattern search tool.

grep "error" logfile.txt

## 29. What is awk?

Text processing tool.

Print 1st column:

awk '{print $1}' file.txt

## 30. What is sed?

Stream editor used to replace text.

Replace:

sed -i 's/old/new/g' file.txt


## 31. Write script to find large files (>100MB).
find / -type f -size +100M

## 32. Script to monitor CPU/Memory?
top -b -n1 | grep "Cpu"
free -m

## 33. Delete all logs older than 7 days
find /var/log -type f -mtime +7 -delete

## 34. Script to check service is running
systemctl status nginx || systemctl start nginx

## 35. Script to check disk usage & alert
df -h | awk '$5+0 > 80 {print "Disk Full"}'

## 36. Script to backup a folder
tar -czf backup.tar.gz /home/data

## 37. Script to read usernames from file & create users
while read user; do
   useradd $user
done < users.txt

## 38. Script to ping a server & send alert
ping -c 1 google.com || echo "Server down"

🔹 SECTION 6 — ADVANCED DEVOPS-LEVEL QUESTIONS
## 39. Difference: #!/bin/bash vs #!/usr/bin/env bash?

/usr/bin/env bash → more portable.

## 40. What is here document (EOF)?

Used to pass multi-line data to command.

cat <<EOF
Hello
EOF

## 41. What is trap?

Catch signals like Ctrl+C.

trap "echo exiting" SIGINT

## 42. How to write parallel jobs (xargs)?
cat list.txt | xargs -n1 -P4 sh script.sh

## 43. Shell script for JSON parsing?

Using jq:

cat file.json | jq '.name'

## 44. How to check last executed command status?
echo $?

## 45. What is subshell?

Any command inside parentheses runs in new shell.

(ls; pwd)


## 46. Write script to reverse a string
echo "$str" | rev

## 47. Count number of files in directory
ls | wc -l

## 48. Find even numbers from 1–50
for i in {1..50}; do
  [ $((i % 2)) -eq 0 ] && echo $i
done

## 49. Script to validate email
[[ $email =~ ^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$ ]]

## 50. Remove duplicates from a text file
sort file.txt | uniq