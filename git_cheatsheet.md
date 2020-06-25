# Git Cheatsheet
1. [Introduction](#introduction)
	1. [Glossary](#glossary)
1. [Typical workflow](#typical-workflow)
	1. [Clone an existing remote repository to local](#clone-an-existing-remote-repository-to-local)
		1. [Master branch](#master-branch)
		1. [Other branch](#other-branch)
	1. [Check git status](#check-git-status)
	1. [Stage files](#stage-files)
	1. [Commit changes](#commit-changes)
	1. [Push](#push)
	1. [`git reset`](#git-reset)
1. [Branch](#branch)
	1. [Create a remote branch](#create-a-remote-branch)
	1. [Delete a remote branch](#delete-a-remote-branch)
	1. [Bring a remote branch](#bring-a-remote-branch)

## Introduction

### Glossary
`remote_repo`: Put an address of your remote repository. (Ex. `https://github.com/username/term_project.git`)  
`branch_name`: Put a name of your branch. (Ex. `network_function`)  

### Typical workflow
[Clone an existing remote repository to local](#clone-an-existing-remote-repository-to-local)  
→ Edit files  
→ [Check git status](#check-git-status)  
→ [Stage files](#stage-files)  
→ [Check git status](#check-git-status)  
→ [Commit changes](#commit-changes)  
→ [Push](#push)

### Clone an existing remote repository to local
#### Master branch
```
git clone remote_repo
```
If prompted to enter username and password, do it.
#### Other branch
```
git clone -b branch_name remote_repo
```
If prompted to enter username and password, do it.

### Check git status
```
git status
```
Shows if there is any change; if there is, shows if the changeis untracked or staged.

### Stage files
If files are staged, they are ready to be committed.
#### All files
```
git add -A
```
#### All files in current directory and all subdirectories (not superdirectories)
```
git add .
git add *
```
#### Selected files
- `git add pycode.py`: Stage only one file, `pycode.py` only.  
- `git add pycode.py ccode.c`: Stage only two files, `pycode.py` and `ccode.c` only.  
- `git add *code*.*`: Stage files such as `pycode1.py`, `pycode2.py`, `ccode.c`, etc.
- `git add *.py`: Stage all `.py` files only in current directory.  
- `git add \*.py`: Stage all `.py` files in current directory and all subdirectories.   
- `git add *.*`: Stage all files who have file extension only in the current directory.  
**How to add all files only in the current directory, even if they don't have file extensions?**  

### Commit changes
```
git commit -m "your_memo"
```
Present tense is recommended for `"your_memo"` such as `"Implement conversion function"`

### Push
```
git push
```
If this is your first time `push`ing, you will be prompted to type `git push --set-upstream remote_repo`. Please follow the instruction.

### `git reset`
Ref: [github.io](https://gmlwjd9405.github.io/2018/05/25/git-add-cancle.html)
- `git reset`: Cancel add
- `git reset --soft HEAD^`: Cancel commit

## Branch

### Create a remote branch
Ref: [github.io](https://trustyoo86.github.io/git/2017/11/28/git-remote-branch-create.html)  
1. Create a local branch:
	```
	git checkout -b new_branch
	```
1. Create a remote branch with the same name by `push`ing the local branch:
	```
	git push origin new_branch
	```
1. The two are not sychronized yet, so sync them:
	```
	git branch --set-upstream-to origin/new_branch
	```

### Delete a remote branch
Ref: [github.io](https://trustyoo86.github.io/git/2017/11/28/git-remote-branch-create.html)  
1. `checkout` to a branch NOT to delete:
	```
	git checkout branch_not_to_delete
	```
1. Delete the local branch:
	```
	git branch --delete branch_to_delete
	```
	If needed, use forceful deletion option `-D` instead of normal deletion option `-d`:
	```
	git branch -D branch_to_delete
	```
1. Delete the corresponding remote branch:
	```
	git push origin :branch_to_delete
	```

### Bring a remote branch
Ref: [github.io](https://cjh5414.github.io/get-git-remote-branch/)
1. Update locally stored information about remote repository.
	```
	git remote update
	```
1. Check existing branches.
	```
	git branch     : Shows local branches
	git branch -r  : Shows remote branches
	git branch -a  : Shows all branches
	```
1. Checkout to a desired branch (= Download a remote branch to local and be ready to edit it).  
If you have the following branches:
	```
	$ git branch -a
	* branch_1
	  branch_2
	  remotes/origin/HEAD -> origin/master
	  remotes/origin/branch_1
	  remotes/origin/branch_2
	  remotes/origin/branch_3
	  remotes/origin/branch_4
	  remotes/origin/master
	```
	and want to download `branch_3` and be ready to edit it:
	```
	git checkout -t origin/branch_3
	```
	If you want to use a different branch name for local, then:
	```
	git checkout -b new_branch_name origin/branch_3
	git checkout new_branch_name
	```
1. Pull.
	```
	git pull origin branch_3
	```
	The `checkout` brings not from remote but a local cached contents. Thus, if you don't `pull` explicitly, you will bring and outdated content.
