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
  - git revert: 1) it is used to revert the changes or commit
                2) it required extract commit while reverting the commit

  - git reset: 1) it is used to revert the changes or commit
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
  - clone the repositary to local work space
  - create feature branch form the master branch
  - update the content 
  - add the file to the staging area with git add
  - commit the chnages to the local repositary with git commit -m "commit message"
  - push the chnages to remote repo with git push origin main
    

## 7) what the purpose of the cheery pick
- git cherry-pick is used to apply a specific commit from one branch into another branch without merging the entire branch.
```
git cherry-pick <commit-id>
```
## 8) How do you check what modifications were done in a particular commit?
-   View changes of a specific commit (most common)
```
git show <commit-id>
```
## 9) waht is the difference bettweeen git clone and fork
## Git clone:
- Creates a local copy of a repository on your machine
- Used mainly for working on code locally
```
git clone https://github.com/org/repo.git
```
## git fork:
- Creates a copy of a repository in your GitHub account
- You own the forked repository
- Commonly used for open-source contributions
- Changes are shared via pull requests

## 10 ) how to create branch and swith to the branch
```
git checkout -b branchname
```
---
# 11) how to resolve git conflicts

- When you run git merge or git pull, Git will show conflicted files:
- Open the conflicted files then Git marks conflicts like this
```
<<<<<<< HEAD
your changes
=======
incoming changes
>>>>>>> branch-name
```
## Resolve the conflict
- Edit the file manually or use a tool like VS Code, Sourcetree, or git mergetool.

- Decide which changes to keep, remove conflict markers, and save the file.

- Mark the conflict as resolved
---
## 12.Interview Answer: How do you combine multiple commits into a single commit in Git?

- To combine multiple commits into a single commit, I use interactive rebase
```
git rebase -i HEAD~<number_of_commits>
```

