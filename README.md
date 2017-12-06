# git-workflow

Git team work flow ,

## 0 Git tools:

I recommend use sourceTree or gitKraken with git CLI together , so it’s more easy to see the commit tree ,and resolve conflicts , but it’s totally fine if you would like to stick to git CLI


## 1 Work on master branch 

If you think your changes do not deserve creating a branch , so you decide to work on master branch directly , for example some hotfix  or small quick feature . In this case  if you have done some changes on local  master , and there are new commits other people did on remote master before you push your changes to remote. Here is the options:

  
### Practice  not recommended:  

    git pull (it actually do :git fetch, git merge) , 
git will generate a merge master commit history which are useless and not look mess  

### Recommended  Option 1 : 

if you have not commit anything  ,use git stash and pop

    git stash 
    git pull
    git stash pop 

### Recommended Option 2 :  

if you have commit your changes (1 or more )

    git pull --rebase (it actually do : git fetch , git rebase ) . 


## 2  Work on your feature branch

Every one work on your own “feature” branch, and after you finish your work ,or you want to share your code within the team,merge it to master      
        
### Step 1 start point: you are in master branch now       

    git pull (get latest code from remote master)
    git branch feature-branch  (create a feature branch from master)
    git checkout feature-branch.    

Now working  on you stuff ….


### Step 2 if you want to get latest code from master and use it in your branch 

you could need this in 2 cases :
1 If master have new commits ,and you want to have that code 
2 you want to merge your change to master but remote master have commits ) 

    git checkout master
    git pull 
    git checkout feature-branch  (Make sure you are on your feature branch to to “rebase master”!!!! )
    git rebase master. 


You could face conflict, go fix the conflict , then 

    git rebase --continue


### Step 3  if you want to merge your changes to master and push to remote 

first redo step2 if there are new commits in master,then:

    git checkout master 
    git merge feature-branch  --no-ff (non fast forward way , always generate a merge commit)    
    git push

## 3 Name your branch

if the branch is only locally , it does not matter that much , but if you push your branch to remote, it's better we name it more structured ,combine the developer name and feature name is one option .
    
    jason-featurename
    jason/featurename (will have directory structure)


