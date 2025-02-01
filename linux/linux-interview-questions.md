## 1)	How to know linux OS version
`
cat  /etc/redhat-release
`
## 2)	How to know present working directory
`
pwd
`
## 3)	How to create a directory 
Ans:  mkdir  directoryname
## 4)	How to many ways we create a file 
       Ans:   cat filename
                  Or 
                touch filename
                    or
               echo  this is hanumantharao  > filename
                  or
              vim filename
## 5)	how to remove the directory which is having sub  directories and files
`
rm -rf   directoryname
`
## 6)	how to remove the file
`
rm  filename
`
## 7)	how to move previous directory
`
cd  ..
`
## 8)	how to list the hidden files
`
ls -lart
`
## 9)	how to check the list of disks and usage of the disks
`
df -h
`
## 10 how to know size of the files and directories
`
du -sh 
`
## 10)	how to change the file permissions
`
chmod command is used to change the file permission
`
## 11)	how to change ownership of the file or directory
`
chown command is used to change the owner ship the file or directory
`
## 12)	which command is used to check the running logs
`
tail -f  filename
` 
## 13)	which command is used to list the frist  10 lines of the file
`
haed -10 filename
`
## 14)	which command is used to list the last 10 lines of the file
`
tail -10 filename
`
## 15)	how to check particular process is running or not
`
ps -ef  |  grep  process
`
## 15)how to check free memory  or available  memory of the server
`
free -m
`
## 16)	how to check which ports are running in the server
`
netstat -ntlp
`
## 17)	how to install particular package in the server
`
yum install is used to install any package
`
## 18)	how to check particular file in available in the server or not
`
find / -type f   filename
`
## 19)	how to removed the 30 day old directories  in the server
`
find  /  -type  d -mtime +30 -exec rm -rf {} \;
`
## 20)	how to mount the filesystem permanently
`
enter the file system  details in the /etc/fstab
`
## 21)	how to start a service example httpd
`
systemctl start httpd
`
## 22)	how to check the status of the servers
`
Ans:  systemctl status httpd
`
## 23)	difference between soft link and hardlink
softlink:
- symbolic or soft link is actual link to the original final
- if you delete the original file then there is nothing in the softlink
- ln -s /home/tcarrigan/demo/soft_link_test(original) /tmp/soft_link_new(new)

hardlink:
- hard link is a mirror copy of the original file
- f you delete the original file, the hard link will still has the data of the original file. Because hard link acts as a mirror copy of the original file.
- ln  /home/tcarrigan/demo/soft_link_test(original) /tmp/soft_link_new(new)
## 24) how to find the kernel version 
`
uname -r
`
## 25) Q) static ip stored in which location
ans) Static ip stored in below location
`
/etc/sysconfig/network-scripts/ifcfg-eth0
`

## 26) Q) Shell scripts arguments purpose

- $0 The filename of the current script.

- $# The number of arguments supplied to a script.
- $? The exit status of the last command executed.

$@  

$*

## 27)How to check file is available or not in server
```
file="/.config/backup.cfg"
if [ ! -f "$file" ]
then
    echo "$0: File '${file}' not found."
Fi
```

## 28) importent files in tomcat
 - #/usr/local/tomcat/bin/startup.sh
 - #/usr/local/tomcat/brin/version.sh
 - #/usr/local/tomcat/logs/catalina.sh
## Q can you please give regulary used command in linux 
	1) ls
    2) rm
    3) df -h
    4) netstat -ntlp
    5) find
    6) mkdir
    7) top
    8) ps -ef
    9) tail -f 
    10) grep 
    11) systemctl start/stop servicename

## Q how to generate public and private keys
 ans) ssh-key gen -t -b 2048
     - id_ras 
     - id_rsa.pub
## Q how to do permaent mount
  #Vim /etc/fstab
  ```
   /dev/xvda  /opt       ext4   ext4   defaults  0 0
  ```
  -  Mount –a
## Q Log paths in httpd web servers
  - /var/log/messges --> message logs available
  - /var/log/errorlogs  --> error logs available
  - /var/log/accesslogs --> Access logs available
  - /var/log/securelog  --> security logs available

## Q If some web servers are working on http port how can u change that is into https
  ans)add these lines in /etc/httpd/conf/httpd.conf to redirect http to https:
  ```
      RewriteEngine On
      RewriteCond %{HTTPS} off
      RewriteRule (.*) https://%{SERVER_NAME}/$1 [R,L]
  ```
