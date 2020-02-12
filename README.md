# Basic GiT Commands

### Creating a repository online for the <b>1st time</b>!
```sh
# navigated into your folder you want to put on Github
$ touch README.md # create a file called README.md where you can put instructions/info about your folder like what you are reading right now!
$ git init # initialize your git repository locally
$ git add . # adds everything changed from local to staging
$ git commit -m "first commit" # commits everything in staging to be ready to be pushed to Github
$ git remote add origin https://github.com/quinnliu/GitCommands.git
$ git push -u origin master # the "-u" is so that the next time your push you don't need to type "origin master"
# put in a username & password
```

### When adding on to your repository online with changes
```sh
$ git add .
$ git add -u # when you have deleted a local file you want to remove from your repository
$ git commit -m 'what has changed'
$ git push 
# put in username & password
```

### No more username & password input for every push
```sh   
# Note that you must first generate a SSH key on your local computer and add it to your 
# Github account before using the following command. Follow the directions here:
# https://help.github.com/articles/generating-ssh-keys
$ git remote set-url origin git@github.com:yourUsername/yourReponame.git
```

### Working together from perspective of person that doesn't have the main repo
```sh
# fork repo you want to work on
$ git clone https://github.com/yourUsername/yourReponame.git
# add changes to your forked repo 
# make a pull request!
$ git pull # use this after someone else has made a change to the online repo 
           # your working on and you want to make your local repo up to date
```

### Want to remove a file frome online github repo but keep it locally
```sh
$ git rm --cached localFileName
# add localFileName to .gitignore file 
# then commit these changes
# push these changes to your repo!
```

### Commands for fixing problems
```sh
# undo multiple commits  
$ git reset --hard commitSHA###... # changes staging index and 
                                   # local folder to match online 
                                   # repository commit

# removing 3 commits from online github repo
$ git push -f origin HEAD^^^:branchNameToUndoLast3Pushs
```

### Branch Commands 
```sh
# creating a new branch
$ git branch -a # list all branches in working folder  
$ git branch newBranchName  
$ git checkout newBranchName # switch to branch newBranchName
$ git push -u origin newBranchName # adds new branch to github repo and "-u" lets 
#                                    you know when your local branch is different 
#                                    than the remote branch

# merging new branch to old branch
$ git checkout oldBranchName
$ git merge --no-ff branchName # "--no-ff" creates a commit that there was a branch merge
#                                   so in the future when you are looking at your commit log
#                                   you know when exactly when you merged one branch into another
$ git push origin oldBranchName 
$ git branch -D branchName # deletes local branch branchName
$ git push remoteName --delete branchName # deletes remote branch branchName
```

### When you need to have git_repo_2 inside git_repo_1
```sh
# have both git_repo_1 and git_repo_2 with setup correctly from above
$ cd git_repo_1
$ git submodule add git@github.com:yourUsername/git_repo_2.git
$ git add .; git commit -m 'what has changed'; git push 

# to update your git_repo_1 when git_repo_2 independently changes
$ cd git_repo_1
$ git submodule init
$ git submodule update
```
