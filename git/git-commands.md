

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













Jenkins
 jenkins – Continuous integration tool
o java -jar jenkins.war – Start Jenkins from a WAR file
o Access Jenkins through http://localhost:8080 by default










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




