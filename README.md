# git-snippets-commands

[initialize a git repository](#initialize-a-git-repository) 

[add changes to staging area](#add-changes-to-staging-area)

[set github configuration](#set-github-configuration)

[reset changes in the staging area](#reset-changes-in-the-staging-area)

[commit changes to local repo](#commit-changes-to-local-repo)

[update commit message of recent commit](#update-commit-message-of-recent-commit)

[Push changes to remote repo](#Push-changes-to-remote-repo)

[adding and commiting at once](#adding-and-commiting-at-once)

[View the remote repository URL](#View-the-remote-repository-URL)

[viewing changes made in a file](#viewing-changes-made-in-a-file)

[viewing changes in the staging area](#viewing-changes-in-the-staging-area)

[Pull changes from remote branch to local branch](#pull-changes-from-remote-branch-to-local-branch)

[Stash Changes in Current Branch and Apply the changes in new branch](#stash-changes-in-current-branch-and-apply-the-changes-in-new-branch)

# initialize a git repository
```git
git init
```

# add changes to staging area

```git
git add --all
git add filename
```

# set github configuration

```git
git config --global user.name "username"
git config --global user.email "email"
```

# reset changes in the staging area

```git
git reset HEAD filename
git reset filename
git reset -- affects all files
```
# reset changes in current branch

```git
git reset --hard  // reset the current branch to a specific commit, discarding any changes and resetting the staging area.
git reset --hard HEAD~1  // If you've made a commit that you want to completely remove from your Git history, including the changes made in that commit.
```

# commit changes to local repo

```git
git commit -m "commit meesage"
```

# update commit message of recent commit

```git
git commit --amend -m "updated"
```

# Push changes to remote repo

```git
git push -u origin master (first time push)
git push
```
# Get History of commits

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
# adding and commiting at once

```git
git commit -am "commit message" #can only used when files that changed commited atleast once
```

# View the remote repository URL

```git
git config --get remote.origin.url
```

# viewing changes made in a file

```git
git diff # ++ denotes new changes, -- denotes previous changes
```

# viewing changes in the staging area

```git
git diff --staged
```

# deleting a file from local repo

```git
git rm filename  #never delete a file direclty using rm from repo, use git rm file
```

# checkout to previous commit

```git
git checkout 0d1d7fc32
```

# Revert to previous commit

```git
git add --all
git commit -m "Commit"
git revert --no-commit 0766c053..HEAD
```

# revert the changes made in a file to the previous commit in case any error pops up,

```git 
git checkout --filename
```

# clean/remove fiile not in the staging area

```git
-> git clean -f  # prompts to whether remove
-> git clean -n  #removes untracked files in the folder
-> git clean -f filename #remove a specific untracked file
   # only remove untracked files - cant remove tracked files
```

# ignoring files
- add files to .gitignore

# ignoring all files with a specific extension but tracking specific file in those
- add *.css to .gitignore  # ignored all css files
- add !file.css to .gitignore # tracked only one css file


# removing commited file from local repo

```git
git rm --cached filename   #it removes file from repo but not from the machine
```

# git branching - basics

```git
git branch  #all branches
git branch branchname #new branch
git checkout branchname #checkout to new branch
git checkout -b branchname #create nd checkout to new branch at same time
git branch -d branchname  # delete a branch - checkout to master before deleting.
```

# rename git branch

```git
git branch -m <oldname> <newname>
```

# incase while deleting branch saying branch is not fully merged,

```git
git branch -D branchname
```

# merging branches

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

# stashing changes

scenario:
	checkout to branch1 - changes to a file while in branch1 - checkout to branch2 - before not commiting changes in branch1 - raises error -abort the process - soluion: stash the changes before checkout to branch2. :)

- stash is a trash folder where v can put changes and restore them back any time

- to save changes to a stash,

```git
git stash save "message"
git stash list
```

# Grabing changes back from stash to the branch,

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

# drop all stashes

```git
git stash clear
```

# rollback/checkout to previous commit

```git
git checkout <commit_id> .
git checkout 09d483c .
```
- it will checkout to previous commit.

[StackOverflow](https://stackoverflow.com/a/2007704)

# Push local branch to remote repo

```git
git push --set-upstream origin new-branch
```

# Remove large files before git push

```git
git filter-branch --tree-filter 'rm -rf path/to/your/file' HEAD
```

# Pull changes from remote branch to local branch

- Use the git pull command with the name of the remote and branch you want to pull changes from. For example, if you want to pull changes from the main branch on the origin remote, you can use the following command:

```git
git pull origin main
```

Note that the git pull command is a combination of two commands: git fetch and git merge. If you prefer to fetch the changes separately before merging them into your current branch, you can use the following commands instead:

```git
git fetch origin main
git merge origin/main
```

# Stash Changes in Current Branch and Apply the changes in new branch

If you don't want to commit the changes in the current branch before creating a new branch, you can use Git's stash feature to temporarily save your changes and apply them to the new branch. Here's how you can do it:

1. **Stash your changes:** Use the following command to stash your changes:

   ```shell
   git stash
   ```

   This command will save your changes in a temporary area and revert your working directory to the last committed state.

2. **Create a new branch:** Now, create a new branch based on the current branch. You can use the following command to create a new branch:

   ```shell
   git branch new-branch-name
   ```

   This command creates a new branch with the specified name but doesn't switch to it yet.

3. **Switch to the new branch:** To switch to the new branch you just created, use the following command:

   ```shell
   git checkout new-branch-name
   ```

   This command switches your working directory to the new branch.

4. **Apply stashed changes:** Apply the stashed changes to the new branch using the following command:

   ```shell
   git stash apply
   ```

   This command reapplies the most recent stash to your working directory. If you have multiple stashes, you can specify a stash by using `git stash apply stash@{n}`, where `n` is the index of the stash.

After following these steps, the changes you stashed will be applied to the new branch. You can continue working on the new branch and commit your changes when you're ready.


---
