# git-snippets-commands


## initialize a git repository
```git
git init
```

## add changes to staging area

```git
git add --all
git add filename
```

## reset changes addeds to the stagin area

```git
git reset HEAD filename
git reset filename
git reset -- affects all files
```
## commit chnages to local repo

```git
git commit -m "commit meesage"
```

## update commit message of recent commit

```git
git commit --amend -m "updated"
```

## Pushing changes to remote repo

```git
git push -u origin master (first time push)
git push
```
## Get History of commits

```git
git log  #show all commit history
git log -1 #shows recent commit
git log --author="authorusername"  #shows commit of given author
git log --since="date"  #show commits after given date
git log --until="date"  #shows commits until given date
git log --oneline  #shows commits history in one line
git log --before = "date"  #same as --until
git log  --after = "date"   #same as --since
```
## adding and commiting at once

```git
git commit -am "commit message" #can only used when files that changed commited atleast once
```

## viewing changes made in a file

```git
git diff # ++ denotes new changes, -- denotes previous changes
```

## viewing changes added to staging area

```git
git diff --staged
```

## deleting a file from local repo

```git
git rm filename  #never delete a file direclty using rm from repo, use git rm file
```

## revert the changes made in a file to the previous commit in case any error pops up,

```git 
git checkout --filename
```

## clean/remove fiile not in the staging area

```git
-> git clean -f  # prompts to whether remove
-> git clean -n  #removes untracked files in the folder
-> git clean -f filename #remove a specific untracked file
   # only remove untracked files - cant remove tracked files
```

## ignoring files
- add files to .gitignore

## ignoring all files with a specific extension but tracking specific file in those
- add *.css to .gitignore  # ignored all css files
- add !file.css to .gitignore # tracked only one css file


## removing commited file from local repo

```git
git rm --cached filename   #it removes file from repo but not from the machine
```

## git branching - basics

```git
git branch  #all branches
git branch branchname #new branch
git checkout branchname #checkout to new branch
git checkout -b branchname #create nd checkout to new branch at same time
git branch -d branchname  # delete a branch - checkout to master before deleting.
```

##incase while deleting branch saying branch is not fully merged,

```git
git branch -D branchname
```

## merging branches

```git
git checkout -b branch2
```
- made some changes here and commit

```git
git commit -am "commited"
```

- later want to merge those changes/versions with our master branch/ or anpther branch

```git
git checkout master
git merge branch2
```
- so now commits made in branch2 is merged with master banch

Note: changes made in sub branch doesnt affect master branch unless they r merged.

## stashing changes

scenario:
	checkout to branch1 - changes to a file while in branch1 - checkout to branch2 - before not commiting changes in branch1 - raises error -abort the process - soluion: stash the changes before checkout to branch2. :)

- stash is a trash folder where v can put changes and restore them back any time

- to save changes to a stash,

```git
git stash save "message"
git stash list
```

## Grabing changes back from stash to the branch,

```git
git stash pop "stash@{0}"
```

- it cuts the stash with given stashid from the stash folder and put those changes back to the branch.
- using pop removes that stash from the folder 

```git
git stash apply "stash{@}0"
```

- it copies the stash from thr folder and put changes back to branch.
- using apply didn remove the stash from folder.
- once changes are stashed, user any checkout to other branch :)

**Note**: Always use stashid along with both commands. if not, it grabs the last stash added.

- To drop a stash from stash folder

```git
git stash drop "stash@{0}"
```
- it drop the stash with given stash id

## to drop all stashes

```git
git stash clear
```

## rollback/checkout to previous commit

```git
git checkout <commit_id> .
git checkout 09d483c .
```
- it will checkout to previous commit.

[StackOverflow](https://stackoverflow.com/a/2007704)

---
