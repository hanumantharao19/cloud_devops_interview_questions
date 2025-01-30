## git commands

## 1) what is difference between git pull and git fetch
   - git pulll ---> it pull the changes form the remote repositary
         and merge teh local branch
   - git fectch ---> it fetch the changes for the remote repostary

## 2) what is the difference between git merge and git rebase
   -  git merge: 1) it is used to merge the one branch to other branch
                 2) it required extra commit to merge form one branch to other branch
                 3) it does not rewrite the commit history

      git rebase:
                1) it is used to merge the one branch to other branch
                2) it does not required extra commit to merge form one branch to other branch
                3) it rewrite the commit history
                4) commits in the feature branch are in the top of history ( tip of the branch)
## 3) what is the difference between git revert and git reset
  - git revert: 1) it is used to revert the change changes or commit
                2) it required extract commit while reverting the commit

  - git reset: 1) it is used to revert the change changes or commit
               2) it doest not required any commit while reset the commit
 

## 4) what is difference between soft reset and hard reset
 - git reset --soft HEAD~1  --> to reset the last commit and 
                               files also available in staging area
- hard reset: - git reset --hard HEAD~1  --> to reset the last commit and 
               files also not available in the workspace
## 5) what is purpose of git stash

- git stash is used if want to save data in present branch before
  moving to the other branch

## 6) how to commit the chnages to the remote repostary
  - 1) clone the repositary to local work space
    2) create feature branch form the master branch
    3) update the content 
    4) add the file to the staging area with git add
    5) commit the chnages to the local repositary with git commit -m "commit message"
    6) push the chnages to remote repo with git push origin main
    

## 7) what the purpose of the cheery pick


## 8) how to check the what are the modification done in the particulart commit


## 9) waht is the difference bettweeen git clone and fork


## 10 ) how to create branch and swith to the branch


# 11) how to resolve git conflicts







- git clone git@github.com:hanumantharao19/devops-sep-batch.git # clone rep
  from remote to local
- git add filename  # add file into staging area
- git add . #  added all files in the present location  to the staging area in
- git status #To know the status of the files(worksapace)
- git commit -m "commit message"  # commit the code to local repo
- git push origin main # push the code to remote repo
- git branch  --> list the branches in the repo
- git checkout branchname  --> switch form one branch to other branch
- git branch branchname --> create branch
- git branch -d branchaname ---Delete the branch
- git branch -D  branchname ---delete the branch forcfully
- git chekout -b branchname  -> creare the brancha and switch to that branch as well
- git checkout  filename  --> to discard the changes to the particular file
   before added to the stage
- git checkout *  -->if we want to discard the changes before addig to staging  area
- git log --> to see the commit history
- git log -5 -->to see the last 5 commits
- git show commitid --> to check what are changes are there in that commit
  reset
- git reset HEAD~1 --> to reset last(recent) commit and changes available in the workspace
## hard reset
- git reset --hard HEAD~1  --> to reset the last commit and 
  files also not available in the workspace
## softreset
- git reset --soft HEAD~1  --> to reset the last commit and 
  files also available in staging area
## git stash
- git stash is used if want to save data in present branch before
  moving to the other branch
- git stash  -> to save data in the prsent branch before moving to other 
  branch
- git stash apply  -> to come back the files
- git stash list --> to see the stash list
## git tag
- we can mark our code with  particular version and tag the code to rep ( in the form of zip files)
- git tag  --> list the tags  in local repo
- git tag -a 1.1  -m "message"   ---> create a tag
- git push origin 1.1  --> push tag to the remote
- git tag -d 1.1  --> to delete the tag
- git push --delete origin 1.1  --> delete the remote tag


1. File and Directory Management
 ls – List directory contents
 cd – Change directory
 pwd – Print working directory
 cp – Copy files and directories
 mv – Move or rename files and directories
 rm – Remove files or directories
 mkdir – Make directoriesfind – Search for files in a directory hierarchy
 locate – Find files by name
 tree – Display directories in a tree-like format
 chmod – Change file permissions
 chown – Change file owner and group
 chgrp – Change group ownership
 stat – Display file or file system statu
 rmdir – Remove empty directories
 touch – Change file timestamps or create empty files


-----
2. File Viewing and Editing
 cat – Concatenate and display file content
 tac – Concatenate and display file content in reverse
 more – View file content interactively (page by page)
 less – View file content interactively (scrollable)
 head – Output the first part of a file
 tail – Output the last part of a file
 nano – Text editor (terminal-based)
 vim / vi – Advanced text editors
 emacs – Text editor
 grep – Search text using patterns
 sed – Stream editor for filtering and transforming text
 awk – Pattern scanning and processing language
 cut – Remove sections from each line of files
sort – Sort lines of text files
 uniq – Report or omit repeated lines
-----
3. Process Management
 ps – Report a snapshot of current processes
 top – Display Linux tasks
 htop – Interactive process viewer (advanced top)
 kill – Send a signal to a process, typically to terminate
 killall – Terminate processes by name
 bg – Resume a suspended job in the background
 fg – Bring a job to the foreground
 jobs – List active jobs
 nice – Run a program with modified scheduling priority
 renice – Alter priority of running processes
 uptime – Show how long the system has been running
 time – Measure program running time


------
4. Disk Management
 df – Report file system disk space usage
 du – Estimate file space usage
 fdisk – Partition table manipulator for Linux
 lsblk – List information about block devices
 mount – Mount a file system
 umount – Unmount a file system
 parted – A partition manipulation program
 mkfs – Create a file system
 fsck – File system consistency check and repair
 blkid – Locate/print block device attributes

-------
ifconfig – Configure network interfaces
 ip – Show/manipulate routing, devices, and tunnels
 ping – Send ICMP Echo requests to network hosts
Page | 3
 netstat – Network statistics
 ss – Socket statistics (faster than netstat)
 traceroute – Trace the route packets take to a network host
 nslookup – Query Internet name servers interactively
 dig – DNS lookup utility
 wget – Non-interactive network downloader
 curl – Transfer data with URLs
 scp – Secure copy files between hosts
 ssh – Secure shell for remote login
ftp – File Transfer Protocol client
-----
6. User and Group Management
 useradd – Add a user to the system
 usermod – Modify a user account
 userdel – Delete a user account
 groupadd – Add a group to the system
 groupdel – Delete a group
 passwd – Change user password
 chage – Change user password expiry information
 whoami – Print the current logged-in user
 who – Show who is logged in
 w – Show who is logged in and what they’re doing
 id – Display user and group information
 groups – Show user’s groups
7. System Information and
 uname – Print system information
 hostname – Show or set the system’s hostname
 uptime – How long the system has been running
 dmesg – Boot and system messages
 free – Display memory usage
 top – Display Linux tasks
 vmstat – Report virtual memory statistics
Page | 4
 lscpu – Display information about the CPU architecture
 lsusb – List USB devices
 lspci – List PCI devices
 lshw – List hardware configuration
8. Archiving and Compression
 tar – Archive files
o tar -czf archive.tar.gz /path/to/directory – Compress files
using gzip
o tar -xzf archive.tar.gz – Extract gzipped tarball
o tar -cf archive.tar /path/to/directory – Create a tarball
o tar -xf archive.tar – Extract tarball
 zip – Package and compress files into a ZIP archive
 unzip – Extract files from a ZIP archive
 gzip – Compress files using the gzip algorithm
 gunzip – Decompress files compressed with gzip
 bzip2 – Compress files using the bzip2 algorithm
 bunzip2 – Decompress files compressed with bzip2
 xz – Compress files using the xz algorithm
 unxz – Decompress files compressed with xz

-------------
9. Package Management (Depends on Distribution)
Debian-based (e.g., Ubuntu)
 apt-get – APT package handling utility
o apt-get install <package> – Install a package
o apt-get update – Update package list
o apt-get upgrade – Upgrade installed packages
o apt-get remove <package> – Remove a package
 apt-cache – Query APT cache
o apt-cache search <package> – Search for a package
o apt-cache show <package> – Show package details
-----
Red Hat-based (e.g., CentOS, Fedora)
Page | 5
 yum – Package manager for RPM-based systems
o yum install <package> – Install a package
o yum update – Update installed packages
o yum remove <package> – Remove a package
 dnf – Next-generation package manager (Fedora, CentOS 8+)
o dnf install <package> – Install a package
o dnf update – Update installed packages
o dnf remove <package> – Remove a package
----
General Commands
 rpm – RPM package manager
o rpm -i <package.rpm> – Install an RPM package
o rpm -e <package> – Remove an RPM package
 dpkg – Debian package manager
o dpkg -i <package.deb> – Install a Debian package
o dpkg -r <package> – Remove a Debian package

10. System Services and Daemon Management
 systemctl – Control the systemd system and service manager
o systemctl start <service> – Start a service
o systemctl stop <service> – Stop a service
o systemctl restart <service> – Restart a service
o systemctl enable <service> – Enable a service to start on boot
o systemctl disable <service> – Disable a service from starting
on boot
o systemctl status <service> – Check service status
 service – Older service management command (used in nonsystemd systems)
o service <service> start – Start a service
o service <service> stop – Stop a service
o service <service> restart – Restart a service
o service <service> status – Check service status
11. Scheduling Tasks
 cron – Daemon for running scheduled commands
o crontab -e – Edit cron jobs for the current user
o crontab -l – List the current user’s cron jobs
o crontab -r – Remove the current user's cron jobs
 at – Run commands at a specified time
o at 09:00 – Schedule a command to run at 09:00 AM
 batch – Run commands when the system load is low
 sleep – Delay for a specified time
o sleep 5s – Sleep for 5 seconds


------
12. File Permissions and Security
 chmod – Change file permissions
 chown – Change file owner and group
 chgrp – Change the group ownership of a file
 umask – Set default permissions for new files
 setfacl – Set file access control lists (ACL)
 getfacl – Get file access control lists (ACL)
 sudo – Execute a command as another user (usually root)
 visudo – Edit the sudoers file safely
 passwd – Change a user’s password
 sudoers – Manage sudo access for users
 gpasswd – Administer group password
 ss – Display socket statistics (for secure network connections)

----
13. System Backup and Restore
 rsync – Remote file and directory synchronization
o rsync -avz source/ destination/ – Synchronize files
o rsync -avz -e ssh source/ user@remote:/destination/ – Sync
over SSH
 cpio – Copy files to and from archives
 dd – Low-level copying and backup of entire filesystems
Page | 7
o dd if=/dev/sda of=/path/to/backup.img – Backup a
disk/partition
o dd if=/path/to/backup.img of=/dev/sda – Restore a
disk/partition

----
14. System Diagnostics and Troubleshooting
 dmesg – Print the kernel ring buffer messages (system boot and
hardware-related messages)
 journalctl – Query and view logs from systemd’s journal
 strace – Trace system calls and signals
o strace <command> – Trace a command’s system calls
 lsof – List open files (useful for debugging)
o lsof <file> – Show processes using a specific file
 vmstat – Report virtual memory statistics
 iostat – Report CPU and I/O statistics
 mpstat – Report CPU usage statistics
 pidstat – Report statistics by process
 free – Display memory usage
 uptime – How long the system has been running
 watch – Execute a program periodically, showing output
o watch -n 1 free – Watch memory usage every second
 lshw – List hardware configuration
 htop – Interactive process viewer (better than top)
 netstat – Network statistics (deprecated in favor of ss)
 ss – Show socket statistics (more efficient than netstat)
-----
15. Networking & Remote Management
 ifconfig – Configure network interfaces (older command,
replaced by ip)
 ip – A more modern alternative for managing network interfaces
and routing
o ip addr – Show IP addresses
o ip link – Show or manipulate network interfaces
Page | 8
o ip route – Show or manipulate routing tables
 ss – Display socket statistics (useful for diagnosing network
issues)
nmap – Network exploration tool (can be used for security
auditing)
 nmap – Network exploration tool (can be used for securi
 telnet – User interface to the TELNET protocol (less common
nowadays)
 nc (Netcat) – Network utility for reading and writing from network
connections
o nc -l -p 1234 – Listen on port 1234
o nc <host> <port> – Connect to a host and port
 iptables – Administration tool for IPv4 packet filtering and NAT
(Network Address Translation)
 firewalld – Frontend for managing firewall rules (used in some
distros like Fedora and CentOS)
 ufw – Uncomplicated firewall (front-end for iptables)
o ufw enable – Enable firewall
o ufw allow <port> – Allow traffic on a specific port
 tcpdump – Command-line packet analyzer
 curl – Transfer data from or to a server using various protocols
(HTTP, FTP, etc.)
 wget – Download files from the web via HTTP, HTTPS, FTP
 scp – Secure copy over SSH (used to copy files between systems)
o scp file.txt user@remote:/path/to/destination/ – Copy file to
remote server
 rsync – Remote file and directory synchronization (often used for
backups)
o rsync -avz /local/path/ remote:/remote/path/ – Sync
directories

16. Text Processing Utilities
 grep – Search for patterns within files
o grep 'pattern' file.txt – Search for a pattern in a file
o grep -r 'pattern' /dir/ – Recursively search for a pattern
Page | 9
 sed – Stream editor for filtering and transforming text
o sed 's/old/new/g' file.txt – Replace old with new globally

 awk – A powerful text processing language
o awk '{print $1}' file.txt – Print the first column of each line in
a file
 cut – Remove sections from each line of a file
o cut -d ':' -f 1 /etc/passwd – Print the first field of each line,
delimited by ":"
 sort – Sort lines of text files
o sort file.txt – Sort file content in ascending order
 uniq – Report or omit repeated lines in a file
o sort file.txt | uniq – Sort and remove duplicate lines
 tee – Read from standard input and write to standard output and
files
o echo "text" | tee file.txt – Write to file and show output on
screen
 tr – Translate or delete characters
o echo "hello" | tr 'a-z' 'A-Z' – Convert lowercase to uppercase
 paste – Merge lines of files
o paste file1.txt file2.txt – Combine lines of file1 and file2 side
by side
 wc – Word, line, character, and byte count
o wc -l file.txt – Count lines in a file
o wc -w file.txt – Count words in a file

17. System Shutdown and Reboot
 shutdown – Shut down the system
o shutdown -h now – Immediately shut down
o shutdown -r now – Reboot the system
o shutdown -h +10 – Shut down after 10 minutes
 reboot – Reboot the system
 halt – Halt the system immediately (equivalent to turning off
power)
 poweroff – Power off the system
 init – Change the runlevel (old-style system manager)
o init 0 – Shutdown
o init 6 – Reboot
18. File System Mounting and Management
 mount – Mount a file system
o mount /dev/sda1 /mnt – Mount partition to a directory
 umount – Unmount a file system
o umount /mnt – Unmount the file system mounted at /mnt
 fstab – File system table (configuration file for mounting file
systems)
o /etc/fstab – View and configure persistent mount points
 blkid – Display block device attributes
 fsck – Check and repair a file system
o fsck /dev/sda1 – Check and repair /dev/sda1
19. Filesystem Permissions and Security
 chmod – Change file permissions
o chmod 755 file.txt – Give read, write, and execute
permissions to owner, and read-execute permissions to
others
 chown – Change file owner and group
o chown user:group file.txt – Change owner and group of a file
 chgrp – Change group ownership of a file
o chgrp group file.txt – Change the group of a file
 umask – Set default permissions for new files
o umask 022 – Set default permissions for newly created files
to 755
setfacl – Set access control lists (ACL) for file permissions
 getfacl – Get access control lists (ACL) for file permissions


20. Containerization and Orchestration
Docker
 docker – Docker command-line interface (CLI) for managing
containers
o docker run <image> – Run a container from an image
o docker ps – List running containers
o docker ps -a – List all containers, including stopped ones
o docker build -t <image_name> . – Build an image
from a Dockerfile
o docker exec -it <container_id> bash – Start an
interactive bash shell inside a running container
o docker stop <container_id> – Stop a container
o docker rm <container_id> – Remove a container


o docker logs <container_id> – View logs of a container
o docker images – List available images
o docker rmi <image_name> – Remove an image
o docker network ls – List Docker networks
o docker-compose – Manage multi-container Docker
applications
 docker-compose up – Start up a multi-container
environment
 docker-compose down – Stop and remove containers
created by docker-compose
 docker-compose logs – View logs from containers
managed by docker-compose

Kubernetes (k8s)
 kubectl – Command-line tool for interacting with Kubernetes
clusters
o kubectl get pods – List pods in the current namespace
o kubectl get nodes – List nodes in the cluster
o kubectl get services – List services in the cluster
o kubectl apply -f <file>.yaml – Apply configuration
from a file (e.g., a deployment or pod configuration)
o kubectl create -f <file>.yaml – Create a resource
from a file
o kubectl delete -f <file>.yaml – Delete a resource
defined in a file
o kubectl exec -it <pod_name> -- bash – Execute a
command inside a pod (e.g., open a shell)
o kubectl logs <pod_name> – View the logs of a pod
o kubectl describe pod <pod_name> – Get detailed
information about a pod
o kubectl scale deployment <deployment_name> --
replicas=<number> – Scale a deployment to the desired
number of replicas
o kubectl rollout restart deployment
<deployment_name> – Restart a deployment
o kubectl port-forward pod <pod_name>
<local_port>:<remote_port> – Forward a port from a
pod to localhost


Helm
 helm – Kubernetes package manager for deploying applications
o helm install <release_name> <chart_name> –
Install a Helm chart
o helm upgrade <release_name> <chart_name> –
Upgrade a Helm release
o helm list – List all Helm releases
o helm delete <release_name> – Delete a Helm release
o helm search <chart_name> – Search for a Helm chart


21. Automation and Configuration Management
Ansible
 ansible – Automation tool for configuration management
Page | 13
o ansible all -m ping – Ping all hosts defined in the
inventory
o ansible-playbook playbook.yml – Run an Ansible
playbook
o ansible -m command -a 'command' <host> – Run a
single command on a target host


o ansible-playbook --check playbook.yml – Dry-run
a playbook to see what would change
o ansible-playbook --limit <host> playbook.yml –
Run a playbook on a specific host or group
o ansible-playbook --extra-vars "key=value" –
Pass extra variables to a playbook

Terraform
 terraform – Infrastructure as code tool for provisioning and
managing cloud resources
o terraform init – Initialize a working directory for
Terraform configuration
o terraform plan – Show an execution plan (preview of
what changes will be made)
o terraform apply – Apply the changes described in a
Terraform configuration
o terraform destroy – Destroy infrastructure created by
Terraform

o terraform validate – Validate the configuration files
o terraform show – Show the current state of the
infrastructure

Jenkins
 jenkins – Continuous integration tool
o java -jar jenkins.war – Start Jenkins from a WAR file
o Access Jenkins through http://localhost:8080 by default


GitLab CI
 .gitlab-ci.yml – Configuration file for GitLab CI/CD pipelines
(typically resides in your repository)
o gitlab-runner register – Register a new runner with
GitLab
o gitlab-runner run – Run the GitLab Runner to process
jobs

GitHub Actions
 GitHub Actions uses YAML configuration files (typically located in
.github/workflows/)
o actions/checkout@v2 – Checkout the repository code in
your CI pipeline
o actions/setup-node@v2 – Setup Node.js for use in a
pipeline
o docker/setup-buildx-action@v1 – Set up Docker
Buildx for building multi-platform images


23. Cloud Services
AWS CLI (Amazon Web Services)
 aws – Command-line tool for managing AWS services
o aws configure – Configure AWS CLI with your credentials
Page | 15
o aws s3 cp file.txt s3://bucket-name/ – Copy a
file to an S3 bucket
o aws ec2 describe-instances – Describe EC2 instances
o aws ec2 start-instances --instance-ids <id> –
Start an EC2 instance
o aws ec2 stop-instances --instance-ids <id> –
Stop an EC2 instance
o aws s3 sync – Sync directories with an S3 bucket

Azure CLI (Microsoft Azure)
 az – Command-line tool for managing Azure services
o az login – Log in to your Azure account
o az vm list – List all virtual machines
o az vm start --name <vm_name> --resource-group
<resource_group> – Start an Azure VM
o az storage blob upload – Upload files to an Azure
blob storage
o az group create – Create a new resource group in Azure


Google Cloud SDK (gcloud)
 gcloud – Command-line tool for Google Cloud Platform
o gcloud auth login – Log in to Google Cloud
o gcloud compute instances list – List compute
instances
o gcloud compute instances stop <instance_name>
– Stop a Google Cloud VM instance
o gcloud app browse – Open the current Google App
Engine application in a browser


Prometheus
Page | 16
 prometheus – Open-source system monitoring and alerting
toolkit
o prometheus – Start Prometheus server (usually runs as a
service in the background)

prometheus --config.file=<config_file> – Start
Prometheus with a specific config file

Grafana
 grafana-cli – Command-line interface for managing Grafana
plugins
o grafana-cli plugins install <plugin-name> –
Install a plugin in Grafana


ELK Stack (Elasticsearch, Logstash, Kibana)
 elasticsearch – Search engine for logging and data analytics
o curl -XGET
'localhost:9200/_cluster/health?pretty' – Get
cluster health status
 logstash – Server-side data processing pipeline
o logstash -f <config_file> – Run Logstash with the
specified configuration file
 kibana – Web interface for visualizing Elasticsearch data
o Kibana is generally accessed through a web browser
(http://localhost:5601)


