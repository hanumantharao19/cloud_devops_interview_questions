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





